---
title: "I have Ubuntu Installed but..."
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-09-28
I have ubuntu installed but cannot use it because I had it installed before I installed Windows XP and now the bootloader has been overwritten with windows, and GRUB no longer comes up. Can someone please tell me how to get it working again please? 
Im desperate to use linux again and need to for my degree but am worried about corrupting my windows installation with valuable files on it.

Hope someone can help.. Thanks, Tom

---

### Post by bulldog on 2006-09-28
Yes ,boot the live cd and do the following,

When you get to the desktop open a terminal and enter. 


```
sudo grub
```


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands


```
find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)


```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr


```
setup (hd0)
```

Finally exit the grub shell


```
quit
```

That is it. Grub will be installed to the mbr.

---

### Post by tommy1987 on 2006-09-28
the following?...

---

### Post by bulldog on 2006-09-28
Yep.:D

---

### Post by tommy1987 on 2006-09-28
thanks very much I will give it a go now...

---

### Post by tommy1987 on 2006-09-28
from...
find /boot/grub/stage1

I got... (hd0,1)

I tried to enter root(hd0,1) and it says:

Error 27: Unrecognized command, it throws the same error if i try setup(hd0)

Can someone please help? I am in ubuntu on the live CD right now!

Thanks

---

### Post by Sef on 2006-09-28
This is GRUB error 27:

> 27 : Unrecognized command
    This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a configuration file and that entry is selected.

Here is the Ubuntu help about [reinstalling GRUB.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by bulldog on 2006-09-28
You do
I tried to enter root(hd0,1) and it says:
Try              root (hd0.1) a space can be important:D

---

### Post by tommy1987 on 2006-09-28
Okay have completed the above steps upto the point it said GRUB restored. Having rebooted GRUB is there but... when it tries to boot my ubuntu (from GRUB on boot up) it says the follwoing:

root(hd0,2)
 Filesystem type unknown, partition type 0x5

 kernel /boot/vmlinuz-2.6.12-9-386 root = /dev/hdb3 ro quiet splash

Error 17: cannot mount selected partition

Press any key to continue...

I must be close! one thing i notice is that when typing find blah blah... into terminal on the live CD it says hd(0,1) and it appears to be looking at hd0,2?? Could that be it and if so how do i rectify it?

Thanks a lot, i hope to be back on ubuntu shortly!!

-Tom

---

### Post by bulldog on 2006-09-28
Don't exactly what you're talking about.

But if you type ```
 gksudo gedit /boot/grub/menu.lst 
```

your menu.list can be altered,but be carefull you could mess things up.

But it gives you a passebillity to try things out.

You can always mount your existing install with the live cd and alter things back.

Can you give me te outcome of ```
 sudo fdisk -l 
```
its an l as in like

---

### Post by tommy1987 on 2006-09-28
yes will get it now.. brb

---

### Post by bulldog on 2006-09-28
Are you in Ubuntu with the live cd then do the following ```
 sudo mkdir /mnt/rescue 
```
this will make a mount dir then do ```
sudo /mount/dev/hda? /mnt/rescue 
```
look if hda? is right :D 
this wil mount your ubuntu
then do
```
 gksudo gedit /boot/grub/menu.lst 
```

and make (hd0.2) (hd0.1) and try if it boots up.

---

### Post by tommy1987 on 2006-09-28
here is the link to the screenie, is the above still applicable? I just dont want to mess anything up thats all..

[http://img172.imageshack.us/my.php?image=screeniecu7.jpg]("http://img172.imageshack.us/my.php?image=screeniecu7.jpg")

Thanks for your help..

---

### Post by tommy1987 on 2006-09-28
when attempting the second step I get:

sudo: /mount/dev/hda: command not found

This is so annoying! All I want to do is restore GRUB :-( :oops: :oops:

---

### Post by Joh_ on 2006-09-29
First of all, it should be a comma, not a dot, like: [FONT="Courier New"](hd0,1)[/FONT].

Second, did you try running this? Always worked fine for me after installing windows. :)
```
grub-install (hd0)
```

---

