---
title: "GNOME, Bonobo, Nautilus Errors"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by Dreyco on 2006-09-15
I'm new to Linux in general, but am pretty adept it figuring things out on my own, but these problems have me stumped. I tried posting this in the installation forum, but I think it will get more help here. I appologize for the double thread, moderators please delete my other thread.

System:
iMac DV 400mhz G3
512MB PC133
10GB HDD
ATI Rage128Pro


After logging in I'm greeted by three errors. The '-' indicates a new line.

Nautilus
-Nautilus can't be used now, due to an unexpected error from Bonobo when attemping to register the file manager view server


Error
-There was a problem registering the panel with the bonobo activation server
-The error code is 3
-The panel will now exit

Error
-There was a problem starting the GNOME Settings Daemon
-Some things such as themes, sounds or background settings may not work correctly.
-The Settings Daemon restarted too many times
-The last error message was:
-System exception: IDLmg.org/CORBRA/COMM_FAILURE:1.0
-GNOME will still try to start the Settings Daemon next time you log in.


Anyone have some insight on how to fix these?

Thanks in advance,
Dreyco

---

### Post by syntheticminds on 2006-09-15
I had a similar problem with my Powerbook of the same generation. I got an alternate CD of Xubuntu and formated my hard drive using the LVM option in your partition guide. IT got thru for me, UI popped. Then i went back to try to install Ubuntu for the apps and another problem popped up with partitions, but That's what i did. My post is in this forum if you guys  can help me out too.

---

### Post by 3rdalbum on 2006-09-16
Are your system clocks set correctly?

---

### Post by syntheticminds on 2006-09-16
My clock was not set correctly because my clock never sets correctly. But its also not connected to the internet. If i set my clock at 6 oclock and come back and turn it on an hour later, its probable gonna be around 7 35 or something like that, not 7 oclock.

---

### Post by Dreyco on 2006-09-16
Yea, I'm sure my system clock is not set correctly, I'll look into how to set it and will get back on later to report any changes.

Edit: I won't be able to connect to the internet easily with the computer I'm installing this onto because I am on a UofMinnesota Campus LAN where it uses MAC filtering and logon. I suppose I could set my windows machine to have the same MAC address and logon real quick.

hmm fun stuff, but I love it!

---

### Post by Dreyco on 2006-09-16
Ok I cant figure out how to change my system clock at all, I've googled for about 30min with no luck

My computer thinks its December 31 1903

hmmm I found the error, I guess its a big one. Anyone know of a fix for this?

[https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/23426](https://launchpad.net/distros/ubuntu/+source/gnome-session/+bug/23426)

---

### Post by mramirez on 2006-09-28
Hi, I have the same problem with my little girl's imac. Now that I'm seeing the problem is the date I know how to change the date in console mode and the proccess is the following:

After Power on the imac, wait for the login screen and press Control+Alt+F1 in the keyboard to get the login screen in console mode, type your user name and password, then type the following command:

sudo date -s 2006/09/28

after that Press Alt+F7 to switch to graphics mode and login as usual.

I haven't done it in the imac because I'm at work now, but I'll try it later and tell you what happened.

I know this doesn't correct the problem, but maybe you will be able to login succesfully.

---

### Post by mramirez on 2006-09-29
I tried the command in the imac and everything worked just fine, I must admit I'm using Ubuntu Edgy Knot 2, that was because I was having problems with the installation of edubuntu 6.06 (CD problem).

I will download again the iso of edubuntu 6.06.1 to burn it again and after install it in the imac I'll try the same command. If that works I will post the results.

---

