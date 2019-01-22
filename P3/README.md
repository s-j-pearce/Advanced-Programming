![state_machine](https://user-images.githubusercontent.com/31927590/51537962-e8472a00-1e47-11e9-9753-01187e3e21ab.png)

```c++
#include <iostream>

class gumballMachine { //Creates the class 'GumballMachine'
	public: //Declares that the below are public functions and variables
	
		gumballMachine(int qty) { //This is a constructor that sets the amount of gumballs in the machine and sets the initial state
			std::cout << "Welcome to my Gumball Machine\n"; //Prints the message in the "". \n prints a new line
			std::cout << "There are currently 3 Gumballs in the machine\n";
			setGumballsLeft(qty); //This sets the number of gumballs left
			setState(NoCoinInserted); //This sets the starting state to NoCoinInserted
		}
		
		int getState() { //This function returns the current state of the machine
			return state; //Returns the current state of the machine
		}
		
		const int NoCoinInserted = 0; // sets a constant of NoCoinInserted to equal the value 0
		const int CoinInserted = 1; //sets a constant of CoinInserted to equal the value of 1
		const int CrankTurned = 2; // sets a constant if CrankTurned to equal the vlaue of 2
		
		void insertCoin() { //Creates the insertCoin function
			if (state == NoCoinInserted) { //Checks that the current state is NoCoinInserted
				std::cout << "Coin Inserted\n"; //Prints message
				setState(CoinInserted); //Sets the state to CoinInserted
			} else { //If the current state is not NoCoinInserted, this will run instead.
				std::cout << "Connot Insert Coin!\n"; //Prints Message
			}
		}

    void ejectCoin() {//declares function ejectCoin
      if (state == CoinInserted) {//checks that the current state is CoinInserted
        std::cout << "Coin Ejected\n";//prints message
        setState(NoCoinInserted);//sets the state to NoCoinInserted
      } else {//if the current state isn't CoinInserted, this runs instead
        std::cout << "Cannot Eject Coin, No Coin Inserted\n";//prints message
      }
    }
		
		void turnCrank() {//declares function turnCrank
		if (state == CoinInserted) {//checks that the current state is CoinInserted
        std::cout << "Crank Turned\n";//prints message
        setState(CrankTurned);//sets the state to CrankTurned
		} else {//if the current state isn't CoinInserted, this runs instead
        std::cout << "Cannot Turn Crank, Please Insert Coin\n";//prints message
		}
		if (state == CrankTurned) {//checks that the current state is CrankTurned
        std::cout << "Attempting to Dispense Gumball\n";//prints message
          if (gumballsLeft > 0) {//checks how many gumballs are left, if there is more than 0, this runs
            std::cout << "Gumball Dispensed, Enjoy!\n";//prints message
            gumballsLeft = (gumballsLeft - 1);//takes one away from gumballsLeft
            setState(NoCoinInserted);//sets the state to NoCoinInserted
          } else {//if there are 0 gumballsLeft, this runs instead
            std::cout <<"No Gumballs Left, Please Refil\n";//prints message
          }
		}
		}
	
	private: //declares private functions and values 
    int state;// declares an int called state
    
    void setState (int newState) { //creates the function that changes the current state of the machine
      state=newState;
    }

    int gumballsLeft; //declares an int called gumballsLeft

    void setGumballsLeft (int newGumballsLeft) { //creates the function that changes the amount of gumballsLeft
      gumballsLeft=newGumballsLeft;
    }
};

int main() {
  
  gumballMachine gumball(3);

    std::cout << "Current State: " << gumball.getState();
    std::cout << "\n";

    gumball.insertCoin();
    gumball.turnCrank();
    gumball.turnCrank();
    gumball.insertCoin();
    gumball.turnCrank();
    gumball.ejectCoin();
    gumball.insertCoin();
    gumball.ejectCoin();
    gumball.insertCoin();
    gumball.turnCrank();
    gumball.insertCoin();
    gumball.turnCrank();

}	
```
