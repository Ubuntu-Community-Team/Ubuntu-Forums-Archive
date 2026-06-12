---
title: "Installation troubles!"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by uberzorz on 2006-12-10
Hi, I successfully installed Ubuntu and it seemed to work. But when I logged in it said Xserver is not configured (your graphical interface) and it asked me if I wanted to diagnose it. I clicked yes and it brought me to a list of info and at the bottom it said:

 Error: no devices found
 and
 Error: no screens found

and all the graphics were replaced with weird symbols. I installed the latest Ubuntu (alternate version, not server).

Thank you for your help!

---

### Post by uberzorz on 2006-12-10
Help me please!

---

### Post by bscbrit on 2006-12-10
Firstly, please be patient while waiting for a reply - 47 minutes isn't long to wait.  I am just getting out of bed on a Sunday morning and I will get round to helping answer questions once I am fully awake.

But, while you are waiting for me, perhaps you can provide details of your computer hardware, particularly the graphics card,if you know it.  My crystal ball is still asleep and you will have to help it by telling us the details. :-k 

By the way, I'm always grumpy until I've had my first cup of coffee....

---

### Post by bscbrit on 2006-12-10
On a command line, type 

sudo dpkg-reconfigure xserver-xorg

and follow the wizard.  If you do not know the answers to a question, simply press [Enter]. It will reconfigure your system.

---

### Post by uberzorz on 2006-12-10
How 'bout your first cup of Ubuntu? :D  

   Anyway, I'm sorry for that I wasn't patient, I have 2 monitors
My main one is hooked up to an Intel 915GV 128 MiB video card.
I was wondering why it didn't work with the normal/live version, or the alternate one... If you can help; I would greatly appreciate it!

---

### Post by bscbrit on 2006-12-10
I'm sorry, I didn't understand your last post.  Are you saying that the computer did not work when you used the Live CD i.e. before you installed Ubuntu?

---

### Post by uberzorz on 2006-12-10
I tried the live cd and it didn't work, I'm sorry about this newbish question, but how do you enter that into a command line? ](*,)

---

### Post by bscbrit on 2006-12-10
Well, I'm not sure that I would have installed the software if it didn't work on my hardware but.......

Reboot the computer.  During the initial boot phase, you should see a menu asking how you want to boot.  If the menu is not visible, press [Escape] while the Ubuntu boot countdown is taking place (immediately that the BIOS load is complete).

One of the options should be to Boot into Recovery Mode.  Select this, and let the machine finish booting.

You should now be logged in at a command line, as 'root' - this is the equivalent of Administrator in Windows.

On the command line, type

dpkg-reconfigure xserver-xorg

When you press [Enter], a simple wizard should begin.  Accept default answers (by pressing [Enter]) unless you have a specific setting that you want to use.  The defaults are normally good enough to get you going.

When the wizard is complete, type

reboot -f

and this time let the computer begin without any input from you.  It should take you to a nice graphical log on screen.  If it doesn't, log on as a simple user:

[log-on-name]
[password]

and, once you are logged on, type

startx

Your graphics display should burst into life - or at least it will if Ubuntu works with your hardware.

Tip:  you might find it easier to go back to a single display until you have your problem sorted out.  But there is no danger with trying to set up 2 screens at once.....

---

### Post by uberzorz on 2006-12-10
Thank you so much!, it worked!... But it only displayed really old graphics drivers (like xp :) ), But I'll fix that in a sec!, Thank you soo much!

---

### Post by bscbrit on 2006-12-10
You're welcome - see you around the forum. :-D

---

