---
title: "file not found in terminal"
date: 2015-10-24
forum: Apple Hardware Users
---

### Post by cherries_chang on 2015-10-24
[FONT=Menlo]Last login: Sun Oct 25 00:32:40 on ttys000[/FONT]
[FONT=Menlo]Qings-MacBook-Air:~ Cherries$ ls[/FONT]
[FONT=Menlo]Desktop		Downloads	Movies		Pictures	cs118[/FONT]
[FONT=Menlo]Documents	Library		Music		Public[/FONT]
[FONT=Menlo]Qings-MacBook-Air:~ Cherries$ cd cs118[/FONT]
[FONT=Menlo]Qings-MacBook-Air:cs118 Cherries$ ls[/FONT]
[FONT=Menlo]DumboController2.java	DumboController3.java	maze-environment.jar[/FONT]
[FONT=Menlo]Qings-MacBook-Air:cs118 Cherries$ javac -classpath maze-environment.jar DumboController.jar DumboController.java[/FONT]
[FONT=Menlo]javac: file not found: DumboController.java[/FONT]
[FONT=Menlo]Usage: javac <options> <source files>[/FONT]
[FONT=Menlo]use -help for a list of possible options[/FONT]
[FONT=Menlo]Qings-MacBook-Air:cs118 Cherries$

WHEN TRYING TO COMPILE AND RUN MY PROGRAM, IT CANNOT BE FOUND, NEARLY DRIVE ME CRAZY.


[/FONT]
import uk.ac.warwick.dcs.maze.logic.IRobot;


public class DumboController5
{
    
    public void controlRobot(IRobot robot) {


    System.out.println("I'm going  ");
	int randno;
	int direction;


	// Select a random number




	// Convert this to a direction


	do {randno = (int) Math.round(Math.random()*3);
		if (randno == 0)
	    direction = IRobot.LEFT;
	else if (randno == 1)
	    direction = IRobot.RIGHT;
	else if (randno == 2)
	    direction = IRobot.BEHIND;
	else 
	    direction = IRobot.AHEAD;
    } 
	while (robot.look(direction) == IRobot.WALL)


     
	robot.getHeading(direction);  /* Face the robot in this direction */   
    }


}

---

### Post by blm-ubunet on 2015-10-24
javac -classpath maze-environment.jar DumboController.jar DumboController3.java
possibly??

---

