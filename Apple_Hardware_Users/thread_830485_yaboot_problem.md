---
title: "yaboot problem"
date: 2008-06-15
forum: Apple Hardware Users
---

### Post by gtcoffee on 2008-06-15
Hi guys, i had messed up the yaboot.conf and i couldn't boot the ubuntu now.
Is there any way i can mount the ubuntu partition under macosx, or configure the yaboot.conf under macosx ?? 

Thanks for advance.

---

### Post by stream303 on 2008-06-16
Problem is, even if you can get to it via OSX, you'd still have to issue a Linux ybin command to make the system aware of your changes.

What is your hardware and how did you install it?

If you were able to run the live-cd, you could boot that, and then go back and edit out your mistakes in /etc/yaboot.conf, and in a terminal issue:

```
sudo ybin -v -C /etc/yaboot.conf
```

Otherwise, you can boot with an "alternate" image, and get to a rescue-shell from the second stage yaboot boot: prompt.  When you reach the second stage, hit -tab- to stop the countdown.  You should see some options like

rescue-powerpc

From there, you can drop into a root shell on your root partition, and edit your yaboot.conf via the nano or vi editors.  Again, you'll have to issue the sudo ybin command to make the system aware of the changes.

One thing I like to do when I have a working system, is to make a backup copy of yaboot.conf:

```
sudo cp /etc/yaboot.conf  /etc/yaboot.conf.bak
```

That way, if I totally mess up yaboot.conf for some reason, I can boot to a rescue shell, and just issue this to get me working again:

```
sudo ybin -v -C  /etc/yaboot.conf.bak
```

---

### Post by blampars on 2008-06-16
i had this exact problem last week.

i used the ubuntu 8.04 server cd i had..

take a look here at what i did to fix things..
[http://ubuntuforums.org/showthread.php?t=820577&page=2](http://ubuntuforums.org/showthread.php?t=820577&page=2)

hope it helps some

---

