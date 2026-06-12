---
title: "Ok, Screwed up."
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2005-12-11
I installed a theme from kde-look.org it was for KDE 3.2 or 3.3 and i have 3.5 final so maybe that has something to do with it. I rebooted and now im just presented with the console 

ubuntu login: darren
password:

darren:$ 

That's basically what i get too. No gui login it's as if it has disappeared! 

What have i done wrong?

---

### Post by Estariel on 2005-12-11
in my opinion that can't have anything to do with installing a theme. 
If the theme was the problem, KDE would either display an error or just look really weird, but you don't even get to KDE.

Thus, I think you somehow messed up your XServer.

Please log into the text console (that you get instead of the graphical log in screen).

Then type
```
startx
```

This will try to start the xserver. You will probably get an error, please post it here.

---

### Post by Rackerz on 2005-12-11
Ok here's what i got;

Log file: "/var/log/Xorg.log"

Using config file: "/etc/X11/Xorg.conf"

Parse error on line 21 of section Files in file /etc/X11/Xorg.conf
":unscaled" is not a valid keyword in this section.

(EE) Problem parsing config file
(EE) Error parsing the config file

Fatal Server error:
no screens found

XIO:    Fatal IO error 104 (connection reset by peer) on X Server "0:0"
After 0 results (0 known processed) with 0 events remaining.

Hope that's enough :).

EDIT: the log file;

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Fri Nov 18 11:51:02 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:02 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Dec 11 19:58:46 2005
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 21 of section Files in file /etc/X11/xorg.conf
	":unscaled" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.X.Org](http://wiki.X.Org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

---

### Post by Rackerz on 2005-12-11
Hmmm nobody knows what's happened?

---

### Post by k1kwg on 2005-12-11
I had a simular experance, so I tried startx.  When I did it said it is already running on Display 0. How do you get out of the screen and back to it?

---

### Post by Rackerz on 2005-12-11
All i can do is try to type 'kdm' or 'kde' to start up the GUI. Or 'startx' which just blurts out the above errors. To get out and reboot i just type 'reboot'

---

### Post by Mustard on 2005-12-11
> Parse error on line 21 of section Files in file /etc/X11/Xorg.conf
":unscaled" is not a valid keyword in this section.

So what have you got on line 21?

Did you backup your original xorg.conf?

You could use the dpkg-reconfigure command shown in the first comments section of your xorg.conf to get it back to a working state.  It would most likely overwrite any changes you have made, so you could make a backup of your current xorg.conf before doing so.  Its seems at the moment that your xorg.conf has a syntax error in it of some kind anyway.  The command in your comments section of your xorg.conf looks like this,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

So either do that one above, or more commonly the one below.

The most common advice for solving xorg.conf problems is to do this command,

```
sudo dpkg-reconfigure xserver-xorg
```

This will ask you a whole lot of questions about how you want to configure your xorg.conf and then create a new xorg.conf file.  If you don't know any of the answers to the questions it asks, you just choose the default setting that it suggest.

---

### Post by Rackerz on 2005-12-11
How can i backup my Xorg.conf? It's set to use my fglrx from ATI.

---

### Post by Mustard on 2005-12-11
To backup your xorg.conf you can use the cp command (copy),

An example of this is here,

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup1

```

NOTE (latter edit): I just noticed that your xorg.conf file is using a capital 'X'.  I'm not sure why that is the case, but you would need to reflect that difference in the command above so that the file names are correct.

To read the manual for the cp command so you understand what you are doing type this

```
man cp
```

Press 'q' to exit the manual. Or close the terminal window.

I've chosen to call the backup xorg.conf_backup1, and store it in the same directory as the xorg.conf is in.  You could call it whatever name you like and store it wherever you like.  Convention seems to be to store the backups in the same directory as xorg.conf.  You might even see a number of backups in there already.  They will usually be called xorg.conf<something> where 'something' is quite often a series of numbers that could refer to the date and time the backup was made.

When you use one of the reconfigure commands above you will most likely find the option to enable your ATI drivers.  If they don't work because you need to edit the xorg.conf by hand to get them working, just use the VESA drivers, as they will get you up and running again.  I'm sure you know more than me with regards to getting ATI drivers functioning.  If you don't there are a number of HOW TO's around either in this forum or in the wiki.

---

### Post by Rackerz on 2005-12-11
Ok, im back in. But all my screen is messed .. is there anyway i can get back to using my previous config? I have it saved.

---

### Post by Mustard on 2005-12-11
To go back to a previous config you would use the same cp command but in reverse.

```
sudo cp /etc/X11/whateveryoucalledyourbackup /etc/X11/xorg.conf
```
NOTE: Again noting that your file is called Xorg.conf rather than xorg.conf.  I'd love to know why this is, but I have no clue. :)

It might be best to describe what you mean by 'messed up' and to give some indication of what drivers you are running now.  Did you choose your ATI drivers or VESA drivers when you reconfigured xorg.conf?

If you chose your ATI drivers then it might be case of there still being some editing to do of your xorg.conf before they will function properly.

These links below are to HOW TO's on ATI drivers,

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
[http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)

---

### Post by Mustard on 2005-12-11
I've been asking some questions in #kubuntu-offtopic on IRC and I really don't understand why your xorg.conf file is called Xorg.conf.  Did you have any idea why it is using a capital X?  This might be part of the issue, I don't know for sure.  If you are editing a file called Xorg.conf and the system is only looking at a file called xorg.conf to get its settings from then I would suggest you try just using using xorg.conf rather than Xorg.conf.

---

### Post by Rackerz on 2005-12-12
It's using xorg.conf. Both config files look the same. Espcially on line 21 -22 where it gets the errors. Im guessing it has something to do with drivers. Do you want me to attach both configs?

---

### Post by Mustard on 2005-12-12
xorg.conf would seem to be the only relevant one, so you could attach that if you like.  It would also be helpful to know what drivers you were running when it worked for you and you described it as 'messed up'.

---

### Post by Rackerz on 2005-12-12
Well messed up was just a figure of speech. I was using the ATI drivers for about 2 days, i must have rebooted about 10 times going in between Windows and Kubuntu, and it didn't fail me then.

I have attached two files;

xorg.txt - My previous one that is 'broken'
xorgworking.txt - The current working one.

They both look very similar espcially on line 21 where i get this error:

Parse error on line 21 of section Files in file /etc/X11/Xorg.conf
":unscaled" is not a valid keyword in this section.

---

### Post by Mustard on 2005-12-12
Have you tried removing the word ':unscaled' from both those lines?

---

