---
title: "Keep returning to the logon screen after entering in my username and password"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Kiwi Si on 2006-12-14
Hi all,

I'm not having a very good run with Ubuntu at the moment.  :(

I have just rebooted my PC (running Ubuntu v6.10) and get to the logon screen just fine.  I enter in my username and password (which are correct), press enter and then recieve a black screen for a few seconds before it returns me back to the logon screen again.  

I don't appear to be receiving any error messages and have tried logging on via KDE and Gnome.

Any ideas?

Thanks,


Simon

---

### Post by Ecthelion on 2006-12-15
> I have just rebooted my PC (running Ubuntu v6.10) and get to the logon screen just fine. I enter in my username and password (which are correct), press enter and then recieve a black screen for a few seconds before it returns me back to the logon screen again.

Can you login after pressing Ctrl-Alt-F1 ? 
This should move you to a terminal panel. There you can put in your username and password.
 (Pressing Ctrl-Alt-F7 should bring you back to your login screen if you want)
I don't know if it helps, but you can try to reconfigure your xserver...

first backup your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```
If you mess things up you can go back to your old xorg.conf with this:
```
sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf
```

Stop your current xserver
If you use gnome by default
```
sudo /etc/init.d/gdm stop
```
If you use kde by default
```
sudo /etc/init.d/kdm stop
```

Then reconfigure your xserver:
```
sudo dpkg-reconfigure xserver-xorg
```
Fill in what you know, if your not sure, leave the default.

After that restart your xserver:
If you use gnome by default
```
sudo /etc/init.d/gdm start
```
If you use kdm by default
```
sudo /etc/init.d/kde start
```

I hope this helps...

---

### Post by tatimmer on 2006-12-15
If you have ever had problems logging in 
(i.e. you cant get past the login screen), 
and you know that you are typing the correct username and password, 
boot into recovery/safe mode 
now you are the root user and can change anything
this is a non-graphical, text mode only operation
check the file permissions 
on your home directory.

You should have the following permissions set on the home directory:
rwxr-xr-x
chmod u=rwx,g=rx,o=rx /home/username

---

### Post by rama on 2006-12-15
Also check if you have any disk space left on /home .When I had this problem I had about 100K free space left !

---

### Post by louis_nichols on 2007-02-16
Also, you should remove from the home directory 2 files called like *.dmrc-something* and *.Xauth*

This is actually the first thing I would try.

---

### Post by Jason Weiss on 2007-02-16
Thats the clue. 

Iam having the same problem and the good news is I think I have found the cause but I do not know how to fix it, 

i only have 42 m of free space. 
so I think the problem is caused by low disk space. 

But I dont know how to remidy it.

I tried using the live cd then logging in as root to nautilus to delete some files from my mounted hdd 

but i dont think it worked. 

any suhestions I am desperate!!

This is the 2nd time the same thing has happened to me and I always lose so much data.

---

### Post by Jason Weiss on 2007-02-16
forget it that is not the cause 

I did sucsesfully delete data from my HDD but it did not fix the problem 

any other sugestions

---

### Post by shareMenaPeace on 2007-02-16
Here is a thread about a full hd and how to fix it

[http://ubuntuforums.org/showthread.php?t=353453&highlight=GDM+could+to+your+authorization+file](http://ubuntuforums.org/showthread.php?t=353453&highlight=GDM+could+to+your+authorization+file)

And try login with failsafe.

---

### Post by malmjako on 2007-02-16
I just experienced this problem, and a full disk was the reason. df gave me 0 bytes available... So, thanks for the tip rama!

---

