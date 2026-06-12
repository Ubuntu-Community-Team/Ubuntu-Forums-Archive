---
title: "System - Administration - Printing hangs?"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by carloyyz on 2006-04-17
I followed the procedure to install the Lexmark z600 printer driver.  The installation went well until I got to the point where I need to set up the printer.  When I select System - Administration - Printing it just hangs for about 10 minutes or more than does nothing.

Can anyone show me the way to fix this problem as it is one of only a few problems I need to resolve before I can justify the switch to Ubuntu permanently.

Thanks.

---

### Post by trivialpackets on 2006-04-17
I don't know, nor am I at my computer.  Just a tip that I've found very useful.  When you get an issue like that, call it from the command line.  anything that you can call as a click can be called via command line.  I don't know if you can, but just create a shortcut to this on your desktop.  Then right click on it and get the properties.  Usually if it's just hanging, I find that when you call it from the command line it give a lot more info as to what is causing the problem.  I'll check in later see what's going on.  Good luck.

---

### Post by carloyyz on 2006-04-17
[QUOTE=eric.proctor]I don't know, nor am I at my computer.  Just a tip that I've found very useful.  When you get an issue like that, call it from the command line.  anything that you can call as a click can be called via command line.  I don't know if you can, but just create a shortcut to this on your desktop.  Then right click on it and get the properties.  Usually if it's just hanging, I find that when you call it from the command line it give a lot more info as to what is causing the problem.  I'll check in later see what's going on.  Good luck.[/QUOTE]
If you can lead me by the hand I will gladly try your suggestion.

---

### Post by trivialpackets on 2006-04-18
I'll try of course.  I just did as I stated, brought up system-administration.  Right clicked on item and chose to add launcher to panel.  Then I right clicked on it in the panel and found properties.  The command to run it is:


     gnome-cups-manager


Try running that from the command line in terminal(SHOULD NEED SUDO).  run that and if you see any errors or dependencies, hopefully it will point us in a direction.   Again, something I always recommend when having problems.  Run it from the CLI.  More information is available to you and the forums when looking for help.  The more info you have, the better people can help!

---

### Post by carloyyz on 2006-04-18
[QUOTE=eric.proctor]I'll try of course.  I just did as I stated, brought up system-administration.  Right clicked on item and chose to add launcher to panel.  Then I right clicked on it in the panel and found properties.  The command to run it is:


     gnome-cups-manager


Try running that from the command line in terminal(SHOULD NEED SUDO).  run that and if you see any errors or dependencies, hopefully it will point us in a direction.   Again, something I always recommend when having problems.  Run it from the CLI.  More information is available to you and the forums when looking for help.  The more info you have, the better people can help![/QUOTE]
Issuing the command in a terminal 

sudo  gnome-cups-manager

had the same result as through the panel but with the following warning:

** (gnome-cups-manager:8235): WARNING **: IPP request failed with status 1280

---

### Post by sailor2001 on 2006-04-19
I have had the same problem....... I think it may have something to do with time running out before localhost:6xx can kick in. Haven't found anyone that could help with that either

---

### Post by carloyyz on 2006-04-19
I guess I'll have to wait and see if someone can find a solution in the near future, otherwise I'll have to buy a new printer.  Printing is essential to me.

Thanks for the replys.

---

### Post by carloyyz on 2006-06-09
Update:
This problem resolved itself after I upgraded to Dapper. I can now print.

---

### Post by paule100 on 2007-02-21
I have the same problem with Dapper. The reason in my case is, that I use a laptop, and when I want to install the printer at home, the cups server at my office is not available. So gnome-cups-manager hangs some time and finally stops working. Have no solution yet.

---

