---
title: "[SOLVED] is there a way to see active processes?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
like in windows, its CTRL + ALT+DELETE, is there something that allows you to monitor the active processes in ubuntu?

---

### Post by caro on 2007-08-09
System > Administration > System Monitor and select the Processes tab.  Or in the terminal use the command "top"

---

### Post by bjarneh on 2007-08-09
several:

type: 

ps -ef 

into a terminal or shell

for a gui version

System --> Adm. --> System-monitor


or install pstree, to get a nice tree in your terminal or shell :-)

you can also write "top" into your terminal or shell to see what process is hogging the resources...

---

### Post by Skidpad on 2007-08-09
I'm running Edgy, so this may be different on your Feisty system, but on mine, you can go System>Administration>System Monitor.

Another way (that would be the same on any version) would be to open a terminal and type "top" (without the quotes).

---

### Post by UltraMathMan on 2007-08-09
Open a terminal and run ```
top
``` or install htop for a more enhanced version. As far as a GUI utility I'm sure one exists but I can't remember it off the top of my head (I'm on a macbook at the moment).

-Hope this helps :)

EDIT: Blast, I was a bit slow there :)

---

### Post by jake16424 on 2007-08-09
wow,, my proc hasnt ever had it so easy,, in windows,, its always under at least 20% load, and over 500megs of ram used,, haha,, thats with no viruses,, or anything O_O ,,, ubuntu, is light compaired to bloated outdated shity windows,, thankyou guys for the speedy response :D:popcorn:

---

### Post by foxholeunder on 2007-08-09
Alternately you an install conky 

```

sudo apt-get install conky

```

Conky is easily custom configurable and will display on your desktop full time behind all other windows but on top of your background.

This link has a great and easy install and pre-configured example to get conky up and running. Simply adjust the size and color scheme to fit your desires!

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html]("http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html")

Have fun customizing!

colors are changed by using hex-color codes and or 'named-colors' 

This example script uses both named-colors and hex-color codes.

This site offers a vast amount of different colors and their hex equivalents. 
[http://www.december.com/html/spec/color.html]("http://www.december.com/html/spec/color.html")

Ironically I am working on setting up my own color-code site however, it is not complete yet...

---

