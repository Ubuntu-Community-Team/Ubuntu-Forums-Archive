---
title: "executing commands in terminal through GUI"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by divparth on 2008-04-02
I have made a GUI using PYGTK.....It has 2 buttons....'SUBMIT' and 'BACK'...............It also has a text area where i have wriitten a command 'ls'...and another text area where the output is to be displayed.

what i want is...on clicking the 'SUBMIT' button....the command in the text area should automaticallly get executed in the terminal...and for that moment the GUI should get locked..........and after that the output of 'ls' should be displayed in the other text area.......

Is this possible????  if not, then is there any other way????

plz help.....

thanx
:KS

---

### Post by superprash2003 on 2008-04-02
yes its possible, but it may get a little complicated incase you require to execute sudo commands..if its a sudo command then the command should be something like this echo password | sudo -S ls where password is the sudo password and ls is the command.. almost every programming language has the ability to communicate with the terminal.. with java its the Process or runtime function. .with c or php its system() etc etc

---

