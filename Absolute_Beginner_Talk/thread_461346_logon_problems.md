---
title: "logon problems"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by kannedheat on 2007-06-01
I was reconfiguring my mouse to work with microsoft's 5 button optical mouse and now I can't logon. My screen keeps going back to the login screen. I was trying to follow a post that I cant find now but it went something like this:

[https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons](https://help.ubuntu.com/community/IntellimouseMousemanBackForwardButtons)

---

### Post by greenstar on 2007-06-01
Sounds like you're having problems with X after changing your mouse settings.

Try this, it will back up your xorg.conf as xorg.conf.backup and reconfigure your xserver, this should allow you to log in again.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg

```
HTH,
Greenstar

---

### Post by kannedheat on 2007-06-01
I tried sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup and the command not found; then I tried sudo dpkg-reconfigure xserver-xorg and I had conflicting action -e(--control) and -r(--remove)

I also tried 

dpkg --configure -a

And I had an error clamav-base

also dpkg-reconfigure xserver-xorg complains:

chown: cannot access ' /var/run/clamav' ... no such file or directory

---

### Post by kannedheat on 2007-06-02
Please disreguard my last post, I had a type o error.

Anyway, I did like you said, but it is still the same. my screen goes blank and returns to the login screen.

kannedheat

---

### Post by kannedheat on 2007-06-02
I dont know, but I did install Automatix2 KDE desktop and I do have the same problem like [http://ubuntuforums.org/showthread.php?t=450602]("http://ubuntuforums.org/showthread.php?t=450602")  I also set the processor speed up on high. I'm going to try this code like suggested.

```

dh-h

```

kannedheat

---

### Post by greenstar on 2007-06-02
Given the additional information, my first answer is no longer applicable. 

With all of these different issues:

[QUOTE=kannedheat] I was reconfiguring my mouse to work with microsoft's 5 button optical mouse and now I can't logon.

I did install Automatix2 KDE desktop and I do have the same problem like [http://ubuntuforums.org/showthread.php?t=450602](http://ubuntuforums.org/showthread.php?t=450602)  I also set the processor speed up on high.


I tried sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup and the command not found.

And I had an error clamav-base.

also dpkg-reconfigure xserver-xorg complains: 
chown: cannot access ' /var/run/clamav' ... no such file or directory
[/QUOTE]


Sounds like you have a whole bundle of problems. Likely from overtweaking. Don't take that personally, most geeks have overtweaked before, myself included. That's how you find the limits of your machine and/or tweaking skills. Good luck untangling that mess. 

If I were you, this is what I'd do:

First, I'd remove clamav, probably with (or similar):
```
sudo aptitude purge clamav
```

Then I'd see where that got me, as clamav does seem to have significant involvement. 

If I was no closer to finding the solution at that point, I'd grab my data by doing the following: (adjust as necessary)
```
cp -a ~ /media/my-external-storage-device
``` or maybe ```
cp -a ~ /dev/sda1
```

Using ~ only copies the current user's home, for all users' home directories, use /home. The "-a" argument for cp (copy) tells bash to copy recursively preserving ownership & permissions. For this reason, you can use sudo in front of cp with -a if you're backing up a system directory such as /etc where your configuration files live. This is home to most of the text files you have probably customized. You might want some of them such as /etc/fstab with your custom mount points or something. So you'd do:
```
sudo cp -a /etc /media/my-external-storage-device
``` or maybe ```
sudo cp -a /etc /dev/sda1
```

Then I'd wipe the disk clean & reinstall fresh.

HTH,
Greenstar.

---

### Post by kannedheat on 2007-06-03
Ouch! Now that's going to leave a mark. Okay I'll give it a go 

TYVM, 
kannedheat

---

### Post by kannedheat on 2007-06-03
I ran this code which ultimatly said that I was only using 15% of my hda. 
```
df -h
```

So basically I just decieded to do a fresh install.  8-[ 

This time I'm not going to overclock my cpu.

---

### Post by greenstar on 2007-06-04
I hope I managed to be helpful in some way.

Greenstar

---

### Post by nawhki on 2007-06-04
Hi..

First thing is, i myself a newbie but had encountered the blank screen prob 3 times
If you are using the Ubuntu/Kubuntu 3.5.6 feisty the backup for the xorg.conf is saved in the same directory and named xorg.conf.1 (or 2 or 3  and so on ..and i found out the 1 is the 1st one u had when it was working ...)..

so try this on the terminal (boot recovery mode)

sudo cp /etc/X11/xorg.conf.1  /etc/X11/xorg.conf

It helped me..and its advisable to copy this file and save it somewhere safe (another directory) for future use :)

I hope i was of help...

---

### Post by greenstar on 2007-06-04
> **nawhki said:**
> Hi..

First thing is, i myself a newbie but had encountered the blank screen prob 3 times
If you are using the Ubuntu/Kubuntu 3.5.6 feisty the backup for the xorg.conf is saved in the same directory and named xorg.conf.1 (or 2 or 3  and so on ..and i found out the 1 is the 1st one u had when it was working ...)..

This problem is much deeper than xorg.conf. And Feisty is v. 7.04, I think Kubuntu's KDE might be v. 3.5.6 but that's definitely not Feisty's version number, or any other version of Ubuntu for that matter. Ubuntu uses release dates as version numbers:
Feisty 7.04 = April 2007; Hoary 5.04 = April 2005; Breezy 6.06 = June 2006; Dapper 6.10 = Oct 2006.

> **nawhki said:**
>  so try this on the terminal (boot recovery mode)

sudo cp /etc/X11/xorg.conf.1  /etc/X11/xorg.conf 

That should be: ```
sudo cp /etc/X11/xorg.conf.1 /etc/X11/xorg.conf
```> **nawhki said:**
>  It helped me..and its advisable to copy this file and save it somewhere safe (another directory) for future use :)

Good advice, no, excellent advice. I usually just back up *all* of /etc so I get all my config files.

That should be: [code]sudo cp /etc/X11/xorg.conf.1 /etc/X11/xorg.conf[/CODE

Hope this was informative,
Greenstar

---

### Post by kannedheat on 2007-06-04
I was playing around with my 57xmodmap and added some changes from post [http://ubuntuforums.org/showthread.php?t=178574#5]("http://ubuntuforums.org/showthread.php?t=178574#5")

```
 killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```

I changed 63xmodmap to 57xmodmap because I didn't have 63xmodmap. Now I couldn't login again after restarting... This was very bad! Now I can't login again. Well learning from past experience, I opened up my Konsole terminal and enter:

```
kate /etc/X11/Xsession.d/57xmodmap

```



Kate opened up 57xmodmap and I undid my previous editing then I reboot. This time I was able to login again! I only wish the I thought of this before, then I wouldn't of ran into the problems I had before.

Now I only need to reconfigure my IntelliMouse Optical map so that it works correctly.

---

### Post by kannedheat on 2007-06-04
My mouse configuration post is at:

[http://ubuntuforums.org/showthread.php?t=464369]("http://ubuntuforums.org/showthread.php?t=464369")

 I appreciate all of your time and help.:D

TYVM,
Kannedheat

---

### Post by greenstar on 2007-06-05
> **kannedheat said:**
> I was playing around with my 57xmodmap and added some changes from post [http://ubuntuforums.org/showthread.php?t=178574#5](http://ubuntuforums.org/showthread.php?t=178574#5)

```
 killall imwheel
 xmodmap -e "pointer = 1 2 3 4 5 6 7"
 BINARY=$(which imwheel)
 $BINARY -k -p -b "67"
```I changed 63xmodmap to 57xmodmap because I didn't have 63xmodmap. Now I couldn't login again after restarting... This was very bad! Now I can't login again. Well learning from past experience, I opened up my Konsole terminal and enter:

```
kate /etc/X11/Xsession.d/57xmodmap

```Kate opened up 57xmodmap and I undid my previous editing then I reboot. This time I was able to login again! I only wish the I thought of this before, then I wouldn't of ran into the problems I had before.

Now I only need to reconfigure my IntelliMouse Optical map so that it works correctly.

Thanks for following up so that others might benefit from your experience. That's what makes the Ubuntu forums such an excellent resource. These forums are our collective experience with Ubuntu.

Greenstar

---

### Post by kannedheat on 2007-06-06
Thank you

---

