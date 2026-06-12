---
title: "Installation won't begin!"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Kristianpedersen on 2006-10-29
I'm running winxp sp 2

I've tried this both with deamon tools and an actual CD, but the same happens (or doesn't happen) both times.

I double-click on the cd, and the info pops up. It says that I must leave the cd in, and reboot. It will then run in demo mode and I can choose to install etc...

But when I have rebooted, nothing happens. I log in and it's just like normal. No sign of ubuntu.

So what should I do to make it work??

---

### Post by tommy1987 on 2006-10-29
You need to go into your BIOS and change the boot priority to CD first, then when prompted press any key to boot from CD.

Hope this helps

---

### Post by Tamil on 2006-10-29
Welcome to Ubuntu forums.

---

### Post by mahy on 2006-10-29
> **Kristianpedersen said:**
> I'm running winxp sp 2

I've tried this both with deamon tools and an actual CD, but the same happens (or doesn't happen) both times.

I double-click on the cd, and the info pops up. It says that I must leave the cd in, and reboot. It will then run in demo mode and I can choose to install etc...

But when I have rebooted, nothing happens. I log in and it's just like normal. No sign of ubuntu.

So what should I do to make it work??

You have to tell the BIOS to boot from the CD. Press something at bootup (usually Del) and it'll get you to the BIOS setup. Then find something like "boot sequence". Put the CD drive to the first rank. That should help. Feel free to ask more questions, but i think you should find someone to help you out in person (i get an impression it's your first time installing any OS ;)  )

---

### Post by Kristianpedersen on 2006-10-29
> **tommy1987 said:**
> You need to go into your BIOS and change the boot priority to CD first, then when prompted press any key to boot from CD.

Hope this helps

How do I do that? I don't even know what BIOS is. It would be most kind if you could set up a step-by-step explanation on how to do all of the above, if it wouldn't be too much trouble.

---

### Post by tommy1987 on 2006-10-29
Well when you restart your system, in the early stages, before you get to any login screen or anything tap F2 and Del (because it is one of these buttons for sure). A large scary lookin window will pop up and it is here you need to snoop around and find an option such as boot priority and change it to have the CD at some point before the Hard Drive. Then you need to save the settings (on my system it is F10 and then you have to press y to confirm changes). Your computer will reboot then you need to look out for it saying press any key to boot from CD, and do that, then it will load the live CD if you have the latest Ubuntu build.

Its just a case of seeing your BIOS really, they are all really the same with subtle differences, see what you can do..

---

### Post by unisol on 2006-10-29
when you start up your pc there is a line that says press f2 or del key to change system settings do it. when it opens go to boot sequence make sure your cd or dvd is set to boot first

---

### Post by Kristianpedersen on 2006-10-29
Thanks.. I'll try that. I just hope I don't cause any problems, cause I've never done stuff like that before ;P

---

### Post by Bartender on 2006-10-29
You don't know how to get into your BIOS?

You have some [reading]("http://burks.bton.ac.uk/burks/pcinfo/hardware/bios_sg/bios_sg.htm") to do grasshopper

---

### Post by Kristianpedersen on 2006-10-29
> **Bartender said:**
> You don't know how to get into your BIOS?

You have some [reading]("http://burks.bton.ac.uk/burks/pcinfo/hardware/bios_sg/bios_sg.htm") to do grasshopper

Well, I've never learned about it before. Anyways, I got it working, yayy!!!!

All I need to figure out now is how the heck I can get on the internet on ubuntu. It rocks ;D

---

### Post by tommy1987 on 2006-10-29
If you connect through a wired network, you should be fine..

---

### Post by Kristianpedersen on 2006-10-29
Well, I'm on a wireless network. I fooled around a little bit, but I couldn't figure out how to connect to it.

Do I search for the network's name or will it connect automatically like it does now in winxp?

---

### Post by Bartender on 2006-10-29
If it were me I'd take your new Linux PC over to the modem and plug in directly.  You may need to make one or two simple tweaks, such as disabling IPV6.  Get online, update, etc.  make sure it's working.  Then work back from there.  Wireless is not as fool-proof as wired.

---

### Post by mahy on 2006-10-29
Wireless? What make of wifi adapter? If it's a laptop with Intel processor, i can help you out. Anyway, run a command

sudo apt-get install network-manager-gnome

which is a handy tool to begin with.

Good luck!

---

### Post by Kristianpedersen on 2006-10-29
How do I run commands? I've never used anything else than windows in the past. Also how do I access the c and d drives? And can I run windows applications on ubuntu?

Please keep the replies as simple as possible, as I know nothing about linux or ubuntu.

---

### Post by Bartender on 2006-10-29
Kristian -
There are hundreds of command guides out there.  Let me get you started.  Go to Applications>Accessories.  Find the Terminal icon.  Drag & drop it to your desktop.  Now right-click on it, choose "Stretch Icon" and squish it down a little bit.  That's optional of course :D .  Now click on your new Terminal icon and you'll get a funny little line of code ending with a dollar sign.  Type in ```
top
``` and hit enter.  You'll get a list of the processes that are running on your PC.  The one using the most resources is on top.  Cool, huh?  Wiggle your mouse around quickly or start up OpenOffice and watch how the list changes.  Close the terminal and open it again.  Now type ```
sudo top
```into the terminal and watch what happens.  One space between the words.  You're asked for your password before it'll go to top.  That's cause "sudo" means you're asking Ubuntu to give you clearance to make changes even if you're not going to make any.  
 
OK, another one.  Close the terminal, and open it again.  Type in ```
sudo cat /etc/fstab
``` and you'll see a list of the devices that are automatically mounted, and where they mount.  One space between sudo & cat, and another between cat & /etc.

OK, feeling braver yet?  Type ```
sudo gedit /etc/fstab
``` and you'll see the same information, but this time it was accessed via gedit, a program that you can use to actually CHANGE the fstab file.  Just close out of gedit, tell it you want to close without making any changes if it asks.  When gedit closed, your terminal window was still there, right?  Waiting for the next command?  Hey, this ain't so bad.

There are about 18 million different combinations of code you could put into the terminal.  I plan to learn about eighteen of those.  That should be enuf.  Don't panic.  "The Official Ubuntu Book" recommends this [site]("http://linuxcommand.org/") to learn more about the command line.

---

### Post by Kristianpedersen on 2006-10-29
Thanks a lot, that's helpful. Now what do I do with the keyboard problem I just figured out occures in ubuntu? All the +-/^\? etc signs are on totally different keys, and some of the letters are swapped out with numbers.

I'm sorry if it seems like I'm asking too much, but everything lags and goes slowly on windows xp, while things seem to run smoothly on ubuntu.

It would be especially great to be able to use it at school if I could just figure out wireless internet and how to run apps like mathcad, cabri and datastudio on linux.

I'm also having troubles accessing the c and d drives btw.

---

### Post by Bartender on 2006-10-30
I've seen keyboard questions pop up but never dove into them cause mine works.  Can you try shutting the PC off and plugging in the plainest old standard keyboard you can find?  If you type 'keyboard keys' into Search there are many posts on the subject.  Maybe some of them will make sense?
Take a read thru [this]("https://help.ubuntu.com/community/MountingWindowsPartitions") and see if it makes any sense.  Almost everyone has to go thru a coupla extra steps to get their devices working.  Maybe it's the unofficial Linux initiation rite, I don't know.  That's one of the reasons I gave you directions for accessing fstab via gedit.  You may have to add a few lines of code to that file.  It's scary the first time, but only because it's all new.
Do you have a printer working yet?  I'd advise printing out your fstab file and your fdisk -l (that's an "ell", not a "one") file
```
sudo fdisk -l
```
Another thing I started doing lately is saving a copy of stuff like this on the PC.  I've just been saving them to the desktop, but once you get the hang of how Linux file mgmt works (easier than Windows but takes time to re-learn old habits) you can save them wherever you want.  The simplest thing I found for saving a file that I was looking at in gedit (such as fstab) was copy the file (same as in Windows, swipe and Ctrl+C or right-click>Copy) open another gedit window (Applications>Accessories>Text Editor), File>New, paste in your text, name the file something that will make sense to you (such as 'first fstab'), save to desktop.  Do that with fstab, fdisk -l, and whatever else you venture into the next coupla weeks and you'll have a reference.  If you change any of these files, copy/paste or print the new files.  You want to  feel confident with the new Linux terminology (dev/hda2, dev/hda5, etc.) before you make changes.  Don't worry, it's generally really easy to get Ubuntu to see your other drives - er - devices.  A few more steps and you'll be showing off your Linux PC to everyone.

---

