---
title: "setting up SSH"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by neelabhro on 2006-02-11
One of the main reasons i acquired linux was to move away from a CYGWIN interafce in windows which i use  in relation to my university course. 

I am absolutely new to Linux and have no clue as to how i even start in terms of getting an ssh system gooing, or which one to install fromthe applications list..

any help/tips would be appreciated

---

### Post by FrankTM on 2006-02-11
this is quite easy

in a terminal type: **sudo apt-get install ssh**
this will probably ask for your password, after that it will install both the client and the server

---

### Post by souteneur3190 on 2006-02-11
A.    Applications--->Internet---->Terminal Service Client
Use the above to ssh into a nother computer FROM YOUR computer

B.    System--->Prefrences---->Remote Desktop
Us the above to enable ssh to your computer

C.  To ssh into a ubuntu computer do the steps in B.  If ssh'ing into a windows  computer download vnc and run (VNC Server- [COLOR="Red"]User Mode[/COLOR])

When you setup the server you can choose to have a password or not....i dont have 1.  All you need to know is the ip adresses for each comp.  To find these out in windows press start...run...type in cmd
when in the command prompt type ipconfig

in ubuntu...
Applications--->system tools---->network tools
where it says network device make sure its on ethernet and you should see your ip

---

### Post by Ufo on 2006-02-12
I just came across this document "Getting started with SSH".

[http://kimmo.suominen.com/docs/ssh/](http://kimmo.suominen.com/docs/ssh/)

Hope you find it helpful :)

---

### Post by BoyOfDestiny on 2006-02-12
[QUOTE=souteneur3190]A.    Applications--->Internet---->Terminal Service Client
Use the above to ssh into a nother computer FROM YOUR computer

B.    System--->Prefrences---->Remote Desktop
Us the above to enable ssh to your computer

C.  To ssh into a ubuntu computer do the steps in B.  If ssh'ing into a windows  computer download vnc and run (VNC Server- [COLOR="Red"]User Mode[/COLOR])

When you setup the server you can choose to have a password or not....i dont have 1.  All you need to know is the ip adresses for each comp.  To find these out in windows press start...run...type in cmd
when in the command prompt type ipconfig

in ubuntu...
Applications--->system tools---->network tools
where it says network device make sure its on ethernet and you should see your ip[/QUOTE]

I don't think B. (Remote desktop) uses ssh... I don't have an ssh server installed, yet I could use remote desktop from another machine (using vncviewer...)

---

### Post by FrankTM on 2006-02-12
very true

ssh is used to do an (secure) remote login to the text-based part of your computer, the shell
vnc is used to login into an already running X session

---

