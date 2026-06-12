---
title: "NDISwrapper help"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-02-24
Im trying to install a windows driver for my wireless RTL8187B card.

I've got the the stage where I get the GUI of the new..

System > Administration > Windows Wireless Driver

I've found the driver I need. Its a Windows 98 one. 
Installed that.

This is what is says:

~/Desktop/Win98$ ndiswrapper -l
net8187b : driver installed

I should be getting this:

  {name of driver} : driver installed
       device ({Chipset ID}) present

But its not :( 
It doesn't detect my wireles card. 

When I do this:

lsusb

Bus 007 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.

It knows its there. But It doesnt want to work :/

How will I get it to work?
What do I need to do?


Thanks in advance :)
Tom

---

### Post by Crooksey on 2008-02-24
Have you tried the xp driver with the .inf extension?

---

### Post by harold4 on 2008-02-24
Make sure the ndiswrapper module is running?

```
sudo modprobe ndiswrapper
```

---

### Post by Tom--d on 2008-02-24
:~$ sudo modprode ndiswrapper
sudo: modprode: command not found

?

---

### Post by harold4 on 2008-02-24
Double check your spelling

---

### Post by Tom--d on 2008-02-24
Installed the xp driver

ndiswrapper -l
net8187b : driver installed

No wireless card :/

---

### Post by harold4 on 2008-02-24
"sudo modprobe ndiswrapper" executed successfully?

---

### Post by Tom--d on 2008-02-24
Tripled checked. 
Still comes up with command not found.

---

### Post by harold4 on 2008-02-24
sudo modproBe ndiswrapper

EDIT: Same problem [here]("http://ubuntuforums.org/showthread.php?t=571046") and was solved.

---

### Post by Tom--d on 2008-02-24
sudo modprobe ndiswrapper

When I press enter. it jsut goes to a new line. Nothing happenes

And wooop on the d bit xD

---

### Post by Tom--d on 2008-02-24
Read it...

before the ndiswrapper. I used the modifed driver. It was really buggy and didnt connect to my wireless. (it was WEP)

My problem is (like a lot of peoples) is that the Win98 driver doesn't recogise my wireless card. Ubuntu does. but Win98 doesnt. 
Statik11 says he has modified the Win98 driver so that it will recogise the wireless card.
I've mail him. But his last action was 1 week ago.

Does anyone have this modified driver? If so, please mail me :) 

Thanks!

Or is anyone else has any solutions, please post :)

---

### Post by Tom--d on 2008-02-24
Bump
Anyone?

---

### Post by harold4 on 2008-02-24
sudo modprobe ndiswrapper not giving you any output is a good thing.  Means the command did what it was supposed to.  

From what I've seen this driver seems to be very finicky, so maybe a better howto will come along at some point. :confused:

---

### Post by Tom--d on 2008-02-25
mm...I'm not giving up on it. 

Thanks for all your help :)

Just have to wait it out.

---

### Post by harold4 on 2008-02-25
I have a broken ndiswrapper myself.  I'm able to connect to G with my broadcom 4328 and can see N, but not connect.  

The joys of a non-intel wireless card :-p

---

