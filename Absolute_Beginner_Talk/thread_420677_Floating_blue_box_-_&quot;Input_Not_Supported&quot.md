---
title: "Floating blue box - &quot;Input Not Supported&quot; monitor problem resolved"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by mcse37 on 2007-04-23
I thought I should post this.  I recently did a fresh install of 7.04 & was getting a monitor error from my Rosewill R912E LED stating "Input Not Supported".  The error disappears after logging on.  I had to make the following two changes to my xorg.conf to fix the problem:

Add these lines to the "Device" section:

       Option          "IgnoreEDID" "1"
       Option          "UseEdidFreqs" "0"

--------------------------------------------

Added the following to the "Monitor" section:

HorizSync      30.0 - 83.0
VertRefresh    55.0 - 75.0 


Bob

---

### Post by Dave54 on 2007-04-23
Congratulations on fixing the problem, and it's always helpful to share a solution. However, I have some recommendations.

> Option "IgnoreEDID" "1"
That option is deprecated, and no longer affects behavior of the X driver.
> Option "UseEdidFreqs" "0"
Rather than that, I'd recommend using:
```
Option "UseEDID" "FALSE"
```
instead.

Click [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html") for more information.

Also, if you found something that works, you might want to just stick with it ;)

---

### Post by The Grand Falloon on 2007-04-24
Since I'm completely clueless about all things linux, i have to ask.  How do I find this creature you call xorg.conf?  I have the exact same issue when I try to start 7.04 or the Edgy release.  Please use small words,  I'm a windows user.  :-D

---

### Post by mcse37 on 2007-04-24
Location of xorg.conf:

From Gnome, click "Places".
Select "Computer" - "File System" - "etc" - "X11".

Bob

---

### Post by lamalex on 2007-04-24
or you can edit via command line
```
sudo nano /etc/X11/xorg.conf
```
that's my recommended method for editing such files.

---

### Post by The Grand Falloon on 2007-04-25
Nevermind, got it...




Heh... yeah, so i blew that pretty good.

So, i seem to have made a typo in there (forgot an N), now i can either run the LiveCD or i can get to a command line.  Which i haven't used much since Windows 3.1.  So, if i'm gonna try and edit that xorg.conf, what would be my command?  and once i'm in there, how do i actually read the whole file?  I tried "sudo nano /etc/X11/xorg.conf" and it was pretty much blank with some options i didn't understand...

---

### Post by jaksh_eet on 2008-03-29
I had to use the following option under my Device that had my nVidia card info:

```
 Option "UseEDIDFreqs" "FALSE"
```

and finally got rid of the silly box floating around.

---

### Post by pirabu on 2008-05-19
tried to chg the file lsited above. I got an erro rmessage that I can not save it. Could Some one help me please....

---

