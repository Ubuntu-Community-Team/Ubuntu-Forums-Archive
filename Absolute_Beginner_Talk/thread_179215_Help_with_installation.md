---
title: "Help with installation"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Rojay on 2006-05-19
okay i downloaded the ubuntu live CD and burnt it and it was just awesome
all i had to do is shove it in the cd-rom and i thought installing ubuntu would be as easy as this but it wasnt
first
its all fine till it asks me for the user name and password, i type in my full name then press enter, then a user name then enter, then a password then enter, password again then enter .... but it takes me back to the first screen the "Enter your full name" screen :s so i pressed 'Esc' button and skipped this step and went on with the installation and everything went fine till it asked me for the login and password
i enter the login fine but when it asks me for the password it takes nothing fromt he keyboard unless its an enter or esc :s
so i restarted the PC and then it gave me an error about X server that i didnt configure the graphics card correctly and it sent me back to the login screen which i cant get pass

so what is going on ?

---

### Post by JShadow on 2006-05-19
It sounds like you might have more than one problem.

First off you won't be able to log in if you didn't sucessfully create a user. What did you choose for username? Some names are reserved. Otherwise, maybe you mistyped your password the second time?

Do you know exactly what the X server error was? Do you know what kind of graphics card you have in your system?

---

### Post by Rojay on 2006-05-19
well i choose "Rojay Magdy" then it automatically named the username "rojay"
and it happend mre than just once like 6 times and it kept sending me to the first screen again

its nvidia geforce 5200
it kept asking me about on what pci slot it is and poped a window with "pci:0:0:2" or something like that and just pressed enter

---

### Post by Rojay on 2006-05-19
Bump

---

### Post by mcduck on 2006-05-19
One thing that causes that kind of problems is if you try to use a FAT partition as / or /home. If you did that, you should install again and use some linux filesystem this time (like Ext3).

---

### Post by Rojay on 2006-05-19
the problem is fixed but now when i use the terminal
"sudo aptitude install gstreamer0.8-mad" command it asks for the password but wont let me type it in
like i type it on the keyboard but nothing on the screen

---

### Post by mcduck on 2006-05-19
that's how it's supposed to work. Nothing is displayed on screen when entering your password so that nobody can see what you are typing, or even how many characters your password has.

Just don't mind it, and type your password & press enter.

---

