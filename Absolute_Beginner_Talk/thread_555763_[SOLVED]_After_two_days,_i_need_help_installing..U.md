---
title: "[SOLVED] After two days, i need help installing..Ubuntu error during boot up"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by computergeek13 on 2007-09-20
ok a brief history: 

I am attempting a dual-boot on my school laptop between vista ultimate and ubuntu 7.04.

I am in the computer science field taking a intro to linux class this quarter and an apache class next quarter.

Along with a few Windows classes down the road. 

So my goal is to get a running solution where i dont have to boot from the live cd each time.

I have the hard drive wiped, i installed vista fine (created 2 partitions during install, vista installed to first, 2nd partition, blank)

When i go to boot from the ubuntu CD, i get the menu, i select START/INSTALL UBUNTU

after about 45 seconds i get the error:

BusyBox v1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built-In Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

*********************************************

So i have scoured the forums here for an answer... one suggested manually pointing to the partition in grub, but i think that had to deal with a working install of linux.

one suggests plugging in a usb key or floppy, didnt work for me...

So i  am at a loss here.... MY last attempt i was reading Linux has problems reading NTFS? so i am begginning to wonder if linux can install when the first partition is all NTFS Vista partition..

I really appreciate the help or even pointing in the right direction.

Thanks so much.


'

---

### Post by Pumalite on 2007-09-20
You might need the Alternate CD. Post your specs or go and try it.

---

### Post by computergeek13 on 2007-09-20
Sony FZ-190 - brand new
Intel Core 2 Duo 2.4 ghz
2 GB RAM
160 GB HD
Blu-Ray

I really dont know a lot about this laptop, i just got it and didnt build it.

what does this alternate cd do?

---

### Post by overdrank on 2007-09-20
> **computergeek13 said:**
> ok a brief history: 

I am attempting a dual-boot on my school laptop between vista ultimate and ubuntu 7.04.

I am in the computer science field taking a intro to linux class this quarter and an apache class next quarter.

Along with a few Windows classes down the road. 

So my goal is to get a running solution where i dont have to boot from the live cd each time.

I have the hard drive wiped, i installed vista fine (created 2 partitions during install, vista installed to first, 2nd partition, blank)

When i go to boot from the ubuntu CD, i get the menu, i select START/INSTALL UBUNTU

after about 45 seconds i get the error:

BusyBox v1.1.3 (Debian 1:1.1.3-3Ubuntu3) Built-In Shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

*********************************************

So i have scoured the forums here for an answer... one suggested manually pointing to the partition in grub, but i think that had to deal with a working install of linux.

one suggests plugging in a usb key or floppy, didnt work for me...

So i  am at a loss here.... MY last attempt i was reading Linux has problems reading NTFS? so i am begginning to wonder if linux can install when the first partition is all NTFS Vista partition..

I really appreciate the help or even pointing in the right direction.

Thanks so much.


'

Hi if you could give us some specs on the system, and you can try to add break=top to the kernel this has helped some. To do this, when you get to the start/install screen use the F6 key and remove *quite splash* and add **break=top** then hit enter. You will receive the message as before but then at that prompt enter **modprobe piix** then hit enter, then enter **exit** and enter again and hopefully this will continue to the live session.

---

### Post by computergeek13 on 2007-09-20
> **overdrank said:**
> Hi if you could give us some specs on the system, and you can try to add break=top to the kernel this has helped some. To do this, when you get to the start/install screen use the F6 key and remove *quite splash* and add **break=top** then hit enter. You will receive the message as before but then at that prompt enter **modprobe piix** then hit enter, then enter **exit** and enter again and hopefully this will continue to the live session.

its a brand new sony fz-190 laptop. what kind of specs do ya need? ill try and dig up specifics. I didnt build this so i am pretty vague on the hard specs.

I just entered what you suggested and it looks like it is doing something.. will post back in a sec.

---

### Post by Pumalite on 2007-09-20
He is right that's another possibility of booting the live CD. Your graphics are still a big question though and depending on them you might need the Alternate CD anyway.

---

### Post by computergeek13 on 2007-09-20
> **Pumalite said:**
> He is right that's another possibility of booting the live CD. Your graphics are still a big question though and depending on them you might need the Alternate CD anyway.

graphics? this laptop has a nvidia 8400m GT.

not sure if that helps

---

### Post by computergeek13 on 2007-09-20
after entering break=top, modprode piix, exit

it continued the install process up to the line...

Running local boot scipts (/etc/rc.local)

it appears to be frozen.

It did pop up a X window error saying something was the problem and it would be started again later. then hung.

---

### Post by overdrank on 2007-09-20
> **computergeek13 said:**
> after entering break=top, modprode piix, exit

it continued the install process up to the line...

Running local boot scipts (/etc/rc.local)

it appears to be frozen.

It did pop up a X window error saying something was the problem and it would be started again later. then hung.

Ok you can try safe graphics mode at the start/install screen and then use the same commands as before and hopefully it will get you to the GUI.

---

### Post by computergeek13 on 2007-09-20
Error: Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like ot view the x server output to diagnose the problem.  yes or no.


thats the current error the install stopped on.  It was going pretty steadily there for awhile too. :(

---

### Post by computergeek13 on 2007-09-20
> **overdrank said:**
> Ok you can try safe graphics mode at the start/install screen and then use the same commands as before and hopefully it will get you to the GUI.

ok that got me to the live contents of the cd, it did make it to a GUI.

thank you so much in getting me there.

I think the hard part may be over *crosses fingers*

---

### Post by overdrank on 2007-09-20
> **computergeek13 said:**
> Error: Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like ot view the x server output to diagnose the problem.  yes or no.


thats the current error the install stopped on.  It was going pretty steadily there for awhile too. :(

Ok you can try to add vga=771 with the break=top command and hopefully this will work. If not then I am at a lost because I have not had that experience. You can try the alternate cd to install, it is a text based installation without a GUI. If you have not tried the live cd and are SURE you want to install then I agree with Pumalite and suggest the alternate cd.
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Once you install you will more than likely have to reconfigure you xorg with this command
```
sudo dpkg-reconfigure xserver-xorg
``` Good luck!

Edit to late

---

### Post by computergeek13 on 2007-09-20
it is officially up and running. Thanks again for the help.

Could someone explain for my own knowledge what exactly happened? What did those commands  "Modprobe piix" do?

thanks

---

### Post by overdrank on 2007-09-20
> **computergeek13 said:**
> it is officially up and running. Thanks again for the help.

Could someone explain for my own knowledge what exactly happened? What did those commands  "Modprobe piix" do?

thanks

Hi great and glad it works, Dannyboy explains it best in this thread
[http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=job+control+turned+off)
And if you could mark this thread as solved. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Good luck!

---

