---
title: "Xorg Woes After Update Now No Display Help!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by gigi1234 on 2006-08-22
Hey everyone, I am running Dapper on a Thinkpad T21. All has been fine until this morning when I ran the update manager. I saw that one of the updates had something to do with Xorg. 

After the update ran I rebooted and got a message that Xorg wasn't working and there is no display.

I have ABSOLUTELY no idea where to even begin to fix it.

Can someone provide me with a hint? I don't know anything about X and how it works, where it lives, how to troubleshoot, etc.

Thanks in advance!

---

### Post by b_martinez on 2006-08-22
Read the 1t sticky in this sub-forum. It will help you get back up and running.
Bill

---

### Post by Nrvnqsr on 2006-08-22
if your connected to the internet? if true

go past all the Xorg errors and you'll be at the login prompt
type your login and password

and just

> 
sudo apt-get update 
sudo apt-get upgrade


there should be a new update for the xorg problem

EDIT: beat me to it ;) 
here's the direct link
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by confused57 on 2006-08-22
When you log in, you'll get the error message...press Ctrl+Alt+F1.
Login in console...enter:

sudo apt-get update
sudo apt-get upgrade

When the upgrade is completed, enter

sudo reboot

or  

sudo shutdown -r now

This should fix your problem...I had to do this on 3 computers earlier.

---

### Post by gigi1234 on 2006-08-22
Thanks for the suggestions. I will try the apt-get approach. I tried the fix posted at the beginning of the sticky but it didn't work at all.

BTW This is really going to KILL absolute newbies who can't connect to the Internet using console commands.

So, if you are reading this and need a hint, try configuring wvdial in the console and this will allow you to dialup a connection.

---

### Post by gigi1234 on 2006-08-22
This fix worked for me!

Thanks again!

---

### Post by confused57 on 2006-08-22
> **gigi1234 said:**
> This fix worked for me!

Thanks again!
Glad it worked.

Worked for me...as was mentioned in the sticky, it would probably be prudent to keep a Live CD handy to boot up with and, hopefully, be able to configure an internet connection  to check out the problem on the forums.
  Also, it was interesting to note that you could downgrade to the previous xserver-xorg version without an internet connection, by reinstalling it from the /var/cache/apt/archives file where updates are stored that are downloaded using Synaptic...of course, you'd need an internet connection to find this out.

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

---

### Post by tsumi on 2006-08-23
:biggrin: awesome. worked great for me too. was it just the xorg-core? i guess it had to be, thats all the apt-get upgrade snagged.

thanks a bunch!

---

