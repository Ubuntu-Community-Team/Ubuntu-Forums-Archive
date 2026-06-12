---
title: "My Ubuntu corrupted after a failure in resuming from Hibernation"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by jenson on 2007-09-13
Hi guys,

I have another bad experience with Ubuntu now. I happen to use my battery (80% spoilt) when running Ubuntu, then I set it to hibernate whenever the battery power reaches critical level.

I left it untouched and when I came back from shower, I noticed that it has been hibernated, thus, without thinking twice, I just go on and boot into Ubuntu again, everything seems to be running quite smooth. But then, after the loading screen, everything went blank! I can't do anything but to press the POWER button to shut it down.

Then I boot up again, this time again, everything is fine until after the loading screen, but it goes in to do system checkup and failed in the last two parts. And it shut down after giving warning that it will shutdown in a few seconds time. Then I boot up again, praying hard nothing happen, and I managed to boot in and entered in my username and password.

I launch everything I want, ok, it seems now it's corrupted as I can only run one application in one time, the rest just load and disappear. And the funniest thing is, I can only load Skype successfully, the rest just won't come out but only showing me that they are loading, after a while, everything is just not there and disappear, only left with my Skype running quite well.

I wonder what should I do now :(

Thanks.

Regards,
Jenson

**EDIT: I'm now using Windows XP, else I would not have the chance to ask for help now, but to reformat it right away >.<"**

---

### Post by tgalati4 on 2007-09-13
What is your hardware?

Look for errors in /var/log.

---

### Post by digitalbenji on 2007-09-13
that is strange.  have you tried running an fsck?  type this:
sudo touch /root/forcefsck
then reboot.

---

### Post by jenson on 2007-09-13
> **tgalati4 said:**
> What is your hardware?

Look for errors in /var/log.

Hi tgalati4,

What you mean? My spec is like this:

Toshiba Satellite M30
40GB Hard Disk Drive
512MB RAM
NVIDIA GeForce Go 5200 32MB
Intel Centrino 1.5GHz

Are these the one you need to know?

Btw, after I checked the error in /var/log  what should I do next?

Thanks.

Regards,
Jenson

**EDIT : It's quite taxing to boot into Ubuntu and check the log file, then boot back to XP again, but I will do that and show it here when I get it.**

---

### Post by jenson on 2007-09-13
> **digitalbenji said:**
> that is strange.  have you tried running an fsck?  type this:
sudo touch /root/forcefsck
then reboot.

Hi digitalbenji,

What does that command do? Is it do like a disk check? When it failed to resume from hibernation, the system did do a check for me, but they failed to check on the last two things, which I forgot what are them now. 

Hmm. Do I run that command when I'm in Gnome? But my Terminal won't load as well.

Regards,
Jenson

---

### Post by Chris S. on 2007-09-13
Can you try pressing Ctrl+Alt+F1 to get into the terminal and run the command?  You can try the Ctrl+Alt combination with anything between F1 and F6, then login and run that command, then press Ctrl+Alt+F7 to get back to gnome.

Also, be careful when forcing a shut down by pressing the power button like that.  It can corrupt or damage your hard drive.  If you have to do it, which will happen sometimes, then make sure the hard drive light is not blinking (if you have one that is) and you'll probably be okay.  You don't want to shut down while the disk is being accessed.

---

### Post by Chris S. on 2007-09-13
One more thing, you can get a program called Ext2Ifs, which will allow you to access any EXT3 partition on your system from Windows.  You can even create and write to files, so you don't have to boot into your potentially damaged Ubuntu to check files or create this forcefsck file.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jenson on 2007-09-13
> **Chris S. said:**
> Can you try pressing Ctrl+Alt+F1 to get into the terminal and run the command?  You can try the Ctrl+Alt combination with anything between F1 and F6, then login and run that command, then press Ctrl+Alt+F7 to get back to gnome.

Also, be careful when forcing a shut down by pressing the power button like that.  It can corrupt or damage your hard drive.  If you have to do it, which will happen sometimes, then make sure the hard drive light is not blinking (if you have one that is) and you'll probably be okay.  You don't want to shut down while the disk is being accessed.

Not, it is not accessing hard disk, I have tried to avoid pressing the power button when the light is blinking, at least I'm pretty sure that when I pressed it, the HDD light is not blinking. I will try to use the shortcut you've provided to see whether it work out fine.

Regards,
Jenson

---

### Post by jenson on 2007-09-13
> **Chris S. said:**
> One more thing, you can get a program called Ext2Ifs, which will allow you to access any EXT3 partition on your system from Windows.  You can even create and write to files, so you don't have to boot into your potentially damaged Ubuntu to check files or create this forcefsck file.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Hmm, it seems to be quite complicated to me? Why it will ask me to mount a drive for Ext2 since I have Ext3? Hmm, I don't really understand how it works though. I think I'm simply too dumb.

Regards,
Jenson

---

### Post by jenson on 2007-09-13
Ok, now I get it working, previously I don't dare to give it a try, it's quite easy, how foolish I am >.<"

Regards,
Jenson

---

### Post by jenson on 2007-09-13
> **tgalati4 said:**
> What is your hardware?

Look for errors in /var/log.

Btw, what should I look for after I'm inside that folder?

I've managed to go in using the little application but I'm not sure which file should I look at.

Regards,
Jenson

---

### Post by jenson on 2007-09-13
Alright I have tried the command, it doesn't help me to rectify the problem.

No luck yet. I did sudo touch /root /forcefsck  but nothing seems to be happen after i issued the command, it only asked for my root password, then i typed in,then nothing happen as if the command has run once very quickly and it returns me to command like ready for next command.

Then I issue sudo reboot to restart the notebook.

I don't know where should I look at the error message yet.

If it's a windows XP, I would just reinstall it once again and try my luck, can I do the same with Ubuntu while keeping all my files intact?

Thanks.

Regards,
Jenson

---

### Post by Chris S. on 2007-09-13
1) That command "sudo touch /root/forcefsck": touch is a command to create a file.  What that command does is create a file named "forcefsck" under the /root directory.  That may not mean much to you, but it's natural that you won't see a message, because all you're doing is creating the file.  Make sure you type the command in exactly as shown (there's no space between /root and /forcefsck, it's just "sudo touch /root/forcefsck")

However, the purpose of that seems to be to force your computer to check for errors on your hard drive when it is booting up, which is a good time to do it.  If there are errors, then you may or may not have to reinstall.  In fact, you may have to get a new hard drive, because once a few sectors on the disk are damaged, the damage tends to start spreading.  It's still very possible there is no damage, so don't get too worried.

2) If you reinstall, you may or may not lose your files, depending on how you install.  Most of your files are probably in your /home directory.  If you made a partition just for the /home directory when you installed, then when you reinstall, you do not need to format it, and it will still be there afterwards.

The thing is, Ubuntu forces you to format the partition where you are putting the root, "/", directory.  Which means if you didn't give /home a separate partition, then you will have to format it and you'll lose those files.  At least, it forced me to format it.

So, if you are unsure about where the /home partition is, then just try to back up as many of your files as you can.  Burn them on a CD, copy them to a USB drive, or transfer them to another computer somehow.  But you don't need to reinstall just yet.  Give the people here a chance to help first.

---

### Post by tgalati4 on 2007-09-13
From a terminal:

>dmesg | more

(spacebar to move forward, q to quit)

>more syslog

Turn off hibernation until you figure out what is going on.  With a Toshiba Satellite with Win XP, it is possible that you have a hibernate parition that is being used by the BIOS in Windows.  When Ubuntu tries to use it, it will surely screw things up.

I've experienced this with other laptops, so proceed carefully.  You can generally use 'standby' which is a low-power mode, but doesn't write a hibernate file to disk.  If this hibernate file gets written over by Windows, then you will have problems.

Of course, it could be something else, that is why you need to check the files in /var/log.

---

### Post by jenson on 2007-09-13
Hmm, these are the files that might be helpful, Ill be outstation for two days, so I wouldn't be able to fix the problem yet, meanwhile, please help me check through the file, I got them through the Ext2 program from my windows partition and acessed them through that program, works great!

Regards,
Jenson

**P/S: They are in zipped format though**

---

### Post by tgalati4 on 2007-09-13
Looking at your syslog, you have some networking issues.  Your DHCP server is not behaving or there is some other issue that is preventing rapid assignment of an IP address to your computer.  Linux does not handle poor network conditions and will appear to hang, but in fact is still waiting for the network to come up.

It looks like it hibernated OK and then came out of hibernation with the network waiting and waiting until you killed it with the power-off button.  And it looked like it shut down cleanly each time.  It's all in the syslog, just go through it and you will see the details.

Perhaps you should assign a static IP and not rely on dynamic IP assignment, as in your case it is causing problems.

There is nothing in the syslog that indicates file system corruption.  If there was, then you would get a boatload of errors referring to filesystem problems.  That is not the case here.

---

### Post by jenson on 2007-09-13
> **tgalati4 said:**
> Looking at your syslog, you have some networking issues.  Your DHCP server is not behaving or there is some other issue that is preventing rapid assignment of an IP address to your computer.  Linux does not handle poor network conditions and will appear to hang, but in fact is still waiting for the network to come up.

It looks like it hibernated OK and then came out of hibernation with the network waiting and waiting until you killed it with the power-off button.  And it looked like it shut down cleanly each time.  It's all in the syslog, just go through it and you will see the details.

Perhaps you should assign a static IP and not rely on dynamic IP assignment, as in your case it is causing problems.

There is nothing in the syslog that indicates file system corruption.  If there was, then you would get a boatload of errors referring to filesystem problems.  That is not the case here.

Hi tgalati4,

Thanks for the reply, it makes me feel better now. By the way, does that means my DHCP is giving me problem? But why has it caused my other application not working at all, including the Terminal in Gnome, but not for the Skype? Hmm, I'm finding it giving me funny problems. I can't load anything in Gnome, which I tested out yesterday, so far only Skype work out nicely, but Terminal windows won't load, same for other application, but it work just fine for me, except I can't do anything except for using Skype in Gnome, that's quite funny.

Thanks for helping me to look through the files, seems like it has nothing wrong there, and I wonder what has caused all these problems for me.  Now I'm working in the office and hence do not have access to my notebook at home right now.

But when I came out from hibernation, it appeared dark and blank screen, with the hard disk light blinking occasionally with the same interval, let's say every 10 seconds. If the DHCP problem can be resolved and make everything work back just fine, I would give it a try and stay back with static IP, by the way if DHCP is not working well, why my Skype can connect to the server and allow me to chat with people? That's quite strange, isn't it?

Thanks.

Regards,
Jenson

---

### Post by tgalati4 on 2007-09-13
It does appear to connect eventually, it just seems to take a long time.  Linux can behave badly when there are networking problems.  Normally, DHCP is a few milliseconds, ask for an address, get an address.  Simple.

It's helpful to print out a copy of the syslog and go through it and search the forums for things that you don't understand.  This is an important part of learning Linux.  Once you can read the syslog and dmesg, you can fix most problems in Linux.

It's your computer, you should take some control of it.  At least you can see what is going on.

---

### Post by jenson on 2007-09-13
> **tgalati4 said:**
> It does appear to connect eventually, it just seems to take a long time.  Linux can behave badly when there are networking problems.  Normally, DHCP is a few milliseconds, ask for an address, get an address.  Simple.

It's helpful to print out a copy of the syslog and go through it and search the forums for things that you don't understand.  This is an important part of learning Linux.  Once you can read the syslog and dmesg, you can fix most problems in Linux.

It's your computer, you should take some control of it.  At least you can see what is going on.

Alright, I will try to see what's inside and what problems to resolve by printing it out later.

Thanks tgalati4.

Regards,
Jenson

---

