---
title: "Dumber than a box of rocks"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by gettinoriginal on 2007-03-12
I know this question must have been asked before, but I now have a splitting headache trying to find the answer!!  I am trying to download and install some programs to ubuntu, but they keep telling me I must have JRTE to install them.  I did find and article on downloading java via the terminal, which I followed, and now, searching my files, I have 88 java files.  But the program downloads still tell me I don't have it !! :mad:

---

### Post by igknighted on 2007-03-12
How are you downloading these programs?  Try finding them in the repositories first if you are not already, it is best to only search outside the repo's as a last resort (its a security thing mostly, but it is also the best way not to damage your install with broken packages/missing dependencies/inability to uninstall).

EDIT: to install java, go to system->administration->software sources and enable all available repositories.  The type in a terminal:
```
sudo apt-get update
sudo apt-get install sun-java6-jre
```
If you prefer, you can find the package by the same name (sun-java6-jre) in synaptic and install from there.

---

### Post by dhughes on 2007-03-12
You probably need to make a symbolic link of some sort....but

 It would be easier to get Automatix2 and install it from there, or apt-get or aptitude (a better choice than apt-get) if it is available through them. [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

 Be wary this is from a guy just slightly smarter than that box of rocks.

---

### Post by igknighted on 2007-03-12
> **dhughes said:**
> You probably need to make a symbolic link of some sort....but

 It would be easier to get Automatix2 and install it from there, or apt-get or aptitude (a better choice than apt-get) if it is available through them. [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

 Be wary this is from a guy just slightly smarter than that box of rocks.

When installing java (a program with few dependencies) aptitude doesn't really add any extra functionality.  It is with big meta packages (*buntu-desktop, beryl, etc.) that you find aptitude really useful.  Also, the new and improved apt-get installed with edgy is just as good at removing orphaned dependencies (you have to run 'apt-get autoremove', but it tells you when it is needed).  I find that apt-get is easier to type, so I typically use it, but both are equally good choices.

---

### Post by gettinoriginal on 2007-03-12
OK, but once I get apt-get or automatix installed, how do I access them to install my programs ??  Sorry, but as the title implies, I slipping beyond dumb  LOL

---

### Post by igknighted on 2007-03-12
> **gettinoriginal said:**
> OK, but once I get apt-get or automatix installed, how do I access them to install my programs ??  Sorry, but as the title implies, I slipping beyond dumb  LOL

If you use apt-get it installs java and configures it for you.  If you install automatix you need to run the automatix program, it should add itself to you applications menu.  Once it loads its pretty self explanatory.  Check the programs you want and then OK and it does all the work.  It should add everything to your menus for you.

---

### Post by gettinoriginal on 2007-03-12
Thank you all for your help, I did get it installed.  Now one more question.

Everytime I boot ubuntu, my web cam comes on, broadcasting to what or where, I have no idea!!  How do I turn it off, I cannot find any application using it, and cannot locate it in files to try to fix it.

---

### Post by Najand on 2007-03-12
Click:
System => Prefernces => Remvoable Drives and Media
Click on Camera tab and remove  the check for "Edit Video When connected"

---

### Post by gettinoriginal on 2007-03-12
well, that didnt work, any other suggestions ??

---

### Post by jackrobinson on 2007-03-12
> **gettinoriginal said:**
> Thank you all for your help, I did get it installed.  Now one more question.

Everytime I boot ubuntu, my web cam comes on, broadcasting to what or where, I have no idea!!  How do I turn it off, I cannot find any application using it, and cannot locate it in files to try to fix it.

```
sudo apt-get install camorama
```
and then run 
```
camorama 
```
it will start your cam. when u close it, the cam will turn itself off.

---

### Post by gettinoriginal on 2007-03-12
now this is wierd, when I run camorama, my cam shows on screen, but the light is out, then when I close camorama, the cam light comes back on !!!!!!!!!!!!!   Damn, I need my advil  LOL  been at this since 9pm, and it is 3:30am

---

