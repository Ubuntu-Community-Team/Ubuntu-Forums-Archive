---
title: "Download Torrent via Azureus BUg Help please"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by athiwatc on 2007-11-18
When i use bittorrent or other when i load the torrent file from firefox it work normaly

Then i uninstall all of them and install azureus for some reason

when i downlaod a torrent from firefox it said "associated helper application does not exist"

and when i download it and open it will lets me choose but it doesn't have azureus in there

help please

---

### Post by atomkarinca on 2007-11-18
right-click on the file and select properties, under "open with" tab if you can't see azureus then select "+add", if you still can't see azureus there select "use a custom command" and type azureus (if it doesn't work, try /usr/bin/azureus)

---

### Post by athiwatc on 2007-11-18
> **atomkarinca said:**
> right-click on the file and select properties, under "open with" tab if you can't see azureus then select "+add", if you still can't see azureus there select "use a custom command" and type azureus (if it doesn't work, try /usr/bin/azureus)

Thanks alot.

---

### Post by athiwatc on 2007-11-18
One more thing.
now when i open azureus when it done loading it just close it self without any error.

---

### Post by atomkarinca on 2007-11-18
start terminal and run azureus through the terminal

```
azureus
```

when it exits please note the output. it would be helpful.

---

### Post by tyggna1 on 2007-11-18
I got the same problem, the only fix I have for it is to delete the log files (under /home/usrname/.azureus/logs/)  after exiting.   It's a bug, but that'll fix it--you'll just have to do that every time.

---

### Post by athiwatc on 2007-11-19
> **atomkarinca said:**
> start terminal and run azureus through the terminal

```
azureus
```

when it exits please note the output. it would be helpful.

here

> changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb45f374b, pid=6199, tid=3084876688
#
# Java VM: Java HotSpot(TM) Client VM (1.6.0_03-b05 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0xb74b]
#
# An error report file with more information is saved as hs_err_pid6199.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)


---

### Post by athiwatc on 2007-11-19
> **tyggna1 said:**
> I got the same problem, the only fix I have for it is to delete the log files (under /home/usrname/.azureus/logs/)  after exiting.   It's a bug, but that'll fix it--you'll just have to do that every time.

Thanks it does work

---

### Post by hyper_ch on 2007-11-19
does azureus support a "watch folder"? If so, you should just save all your .torrent files in that watch folder and they will be auto-added to azureus when it's running.

---

### Post by athiwatc on 2007-11-19
Thanks but that not the POINT the POINT is it will never open

---

### Post by athiwatc on 2007-11-19
One more thing is it save to install azureus 3.0.3.4 on ubuntu gusty

---

### Post by badguyanil on 2007-11-19
As athiwatc said...

install jdk 1.6
install Azu 3.X

there is a how to at sourceforge.net about how to install on linux distros. It is a simple walkthru where you just need to extract from the tar and place it in your root folder. I have been using it for quite some time without any problem. Used to have these auto closing problems with azu 2.5.... so i suggest you shift to azu 3.X.

---

### Post by athiwatc on 2007-11-19
> **badguyanil said:**
> As athiwatc said...

install jdk 1.6
install Azu 3.X

there is a how to at sourceforge.net about how to install on linux distros. It is a simple walkthru where you just need to extract from the tar and place it in your root folder. I have been using it for quite some time without any problem. Used to have these auto closing problems with azu 2.5.... so i suggest you shift to azu 3.X.

The same thing as me i got a problems that why i trying to change.

^ ^ thanks

---

### Post by athiwatc on 2007-11-19
And how do i make a shortcut for it thanks

---

### Post by badguyanil on 2007-11-19
to run azu all you have to do is to run the file named azureus in the folder. You can create a launcher on the desktop (right click on dektop > create new launcher). Give the path as 
~/.azureus/azureus. Give the name as Azureus, and any description you like.

Alternatively you can launch azu from terminal, which will also let you c what the software does and debug any problems you face while runnign the app. To do so, 
1. open terminal
2. browse to the folder .azureus(in your home dir)
3. type "azureus" and hit enter.

wait for a few secs and Vuze (azu 3.X) loads!

---

### Post by athiwatc on 2007-11-19
> **badguyanil said:**
> to run azu all you have to do is to run the file named azureus in the folder. You can create a launcher on the desktop (right click on dektop > create new launcher). Give the path as 
~/.azureus/azureus. Give the name as Azureus, and any description you like.

Alternatively you can launch azu from terminal, which will also let you c what the software does and debug any problems you face while runnign the app. To do so, 
1. open terminal
2. browse to the folder .azureus(in your home dir)
3. type "azureus" and hit enter.

wait for a few secs and Vuze (azu 3.X) loads!

thanks cool

---

