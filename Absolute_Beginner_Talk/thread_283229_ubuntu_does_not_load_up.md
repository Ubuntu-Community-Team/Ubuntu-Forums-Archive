---
title: "ubuntu does not load up??"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Jay the Great on 2006-10-23
When I start ubuntu (after the splash screen) I log in, but nothing happens anymore. The wallpaper doesn't even load up! It's not frozen though because I can ctrl+alt+backspace to bring up the login window again. As many times as I log in, I can't get ubuntu loaded. It was working fine but now it's suddenly doing this. :confused:

---

### Post by MontanaMax on 2006-10-23
I had this issue a few weeks ago on the first reboot after I downloaded an updated application. After much looking around, I finally tried apt-get check from the command line in recovery mode.

```
apt-get check
```

This discovered an incompatibility with installed packages, corrected it automatically, and I was up and running again in a few minutes.

I also found a fairly detailed article on what to try if the apt-get check finds an error that it can't correct.

[http://www.linux.com/article.pl?sid=05/10/12/1952217]("http://www.linux.com/article.pl?sid=05/10/12/1952217")

Good luck!!  :-$

---

### Post by Jay the Great on 2006-10-24
Thanks, but that didn't work.

I can't even boot into ubuntu with recovery mode. :confused:

---

### Post by jegerjensen on 2006-10-24
You need to provide some more information about what is going on with your system. 

At the login screen, press ctrl-alt-F1  to login in text-mode.  From there 

```
$ cd /var/log 
```

In this directory there are many log files, which may provide useful information. For example Xorg.0.log and the files in gdm/ .

View the files with

```
$less Xorg.0.log
```

or you can post them here if by copying them over to a usb-stick with 

```
$cp X.org.log /media/<the name of the usb pen> 
```

you find the name of the usb-pen by inserting the pen, and then 

```
$ls /media 
```

If you  post the log-files, someone might help diagnose your system...

cheers!

---

### Post by Jay the Great on 2006-10-24
I'm about to try this...

---

### Post by Jay the Great on 2006-10-25
I tried that, but it said that:
$less Xorg.0.log

was not a command.

---

### Post by jegerjensen on 2006-10-25
oooops, I think the confusion lies in my notation.  You are not supposed to enter the dollarsign, I included it to symbolize the prompt at the commandline, like:

```
oy@ubuntulaptop:/var/log$
```  

I realize that my previous post may be confusing, but please try again:)

To prevent a future deja vu of this situation, I should clearify the command which I suggested,
```
$ cp X.org.log /media/<the name of the usb pen>
```
You are not supposed to write the < and >.  Use for example
```
$ cp X.org.log /media/usb-storage
```
Only with the correct name for the usb-pen

---

### Post by Jay the Great on 2006-10-25
-edit-

OK, I did that but I don't have a usb device yet.

---

### Post by jegerjensen on 2006-10-26
From the thread 

[http://ubuntuforums.org/showthread.php?t=41157]("http://ubuntuforums.org/showthread.php?t=41157")

It looks like the most interesting log file could be .xsession-errors in your home directory.

---

