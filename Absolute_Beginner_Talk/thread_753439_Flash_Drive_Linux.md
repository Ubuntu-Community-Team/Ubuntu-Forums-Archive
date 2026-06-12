---
title: "Flash Drive Linux"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by caseyo on 2008-04-12
Hello! Here are my plans. I would like to install DSL or Puppy Linux on a flash drive, and if that goes well, I'd buy a bigger one and install Xubuntu or something a little more heavy duty than DSL on it.

I've found a pretty straight forward guides on the subject, but they are for Windows, well they only explain how to do it on a Windows machine. I have a Mac, and a computer with Ubuntu installed on it. Doing it with Ubuntu would be the best.

I'm not exactly brand new to Linux, but I don't know that much. Please don't hesitate to over explain everything. *Please*, over explain everything. I'm not arrogant and I won't feel bad if you treat me like a newbie. :)

Thanks for the help!

By the way... My flash drive is a [[COLOR="Red"]Kingston[/COLOR]]("http://www.kingston.com/flash/datatraveler.asp"), it's a few years old. It has 128MB, I just erased everything off of it. Thanks again.

---

### Post by will1911a1 on 2008-04-12
Did a search and hopefully this thread will help you out:

[http://ubuntuforums.org/showthread.php?t=752253&highlight=installing+from+usb]("http://ubuntuforums.org/showthread.php?t=752253&highlight=installing+from+usb")

I hope that helps. :)

---

### Post by KLR650 on 2008-04-12
I'm a noob, and have been playing with linux for about a year.  I have settled on Ubuntu and Puppy Linux.  Ubuntu for a big, solid linux distro to replace XP and Puppy as a small, portable flash drive linux to play with and muck around with the command line and it is so cool to take your operating system with you.  And they both have great communities and forums to get help.

Puppy is super simple to get on a flash drive. (It must be, it was the only one I could get to work!)  Download Puppy (3.01 is the latest and is about 100MB, so it will probably just fit on your flash drive) from [http://puppylinux.com/]("http://puppylinux.com/") and burn the iso onto a CD.  I used Burn4free because the burning software that came with my computer won't do iso's.

Boot off the CD into puppy (by changing the boot order by pressing esc or F8, etc. a few seconds after turning on your computer) then run the Puppy Universal installer and install to the flash drive.  

Boot off the flash drive into puppy, and you're there!  At shutdown you will be able to save your settings, wallpaper and anything else you have changed.   Lots more good info at the Puppy forum [http://www.murga-linux.com/puppy/]("http://www.murga-linux.com/puppy/")

I'm sure DSL is great too, but it just wouldn't work for me.

You could also try a wubi install of Ubuntu Hardy to try it out.  Wubi installs Ubuntu like you would install a program in Windows and allows you to boot into Windows or Ubuntu.  There are  downsides, and it is still beta, but has worked great for me.

Right now, I am (kind of) triple booting Puppy (off a flash drive), wubi Ubuntu and XP.  But no messing around with GRUB or the MBR.  It's not real triple booting but it works for me right now.

Whew... one more thing.  Puppy can install as a multisession live cd or dvd.  It boots slower than a usb installation, but it can save all your files/changes to the cd every time you shut down.

Good luck

---

