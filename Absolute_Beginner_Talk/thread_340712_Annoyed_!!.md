---
title: "Annoyed !!"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Dave-C on 2007-01-17
The amount of times i've had to reinstall ubuntu is unreal and its just after i get the computer the way i like it and i keep getting the same problem and its a real shame cause i'm a really big fan of linux am teaching myself sudo so i can help use developers out i'm being let down all the time my first problem was the abstract hald layer on boot up of ubuntu 6.06 then i reinstalled it and fixed the computer to the way i wanted (not much just a few media programs from the add and remove programs list) then i got the same problem so i installed again then i got it the way i wanted and it was working good then when i put my USB FAt32 drive to get files it couldnt read it and wouldnt run the admin program that you manage removable devices [-(  i donno whats wrong am just really annoyed with it any 1 got any suggestion on what i should do that don't involve going back to 300,000 mil spyware on windows!!

---

### Post by Josh1 on 2007-01-17
> **Dave-C said:**
> The amount of times i've had to reinstall ubuntu is unreal and its just after i get the computer the way i like it and i keep getting the same problem and its a real shame cause i'm a really big fan of linux am teaching myself sudo so i can help use developers out i'm being let down all the time my first problem **was the abstract hald layer on boot up of ubuntu** 6.06 then i reinstalled it and fixed the computer to the way i wanted (not much just a few media programs from the add and remove programs list) then i got the same problem so i installed again then i got it the way i wanted and it was working good then when i put my** USB FAt32 drive to get files it couldnt read it and wouldnt run the admin program that you manage removable devices** [-(  i donno whats wrong am just really annoyed with it any 1 got any suggestion on what i should do that don't involve going back to 300,000 mil spyware on windows!!

Are you sure USB would not work? And what is "abstract hald layer on boot up of ubuntu"?

---

### Post by emarkay on 2007-01-17
Dude,  - I feel your pain, but slow down!  Take a breath - use a comma or two.

Define your prob in specifics.   I still fight with Linux, but it's starting to make sense.  It can never replace Windows completely, but it can do the job.

Be methodical when asking for help.

---

### Post by bodhi.zazen on 2007-01-17
First plug in the device .... wait a minute ....

Now open a terminal

Post the output of:```
sudo fdisk -l
```

Assuming the device is /dev/hda1:

In a terminal:```
pmount /dev/sda1 usb
```

Also, are you sure the device is not mounting ? Look in system and make sure you haev selected auto mount ....

---

### Post by jvc26 on 2007-01-17
Hi there, I'm sure people out here can help you, a calm reasoned post will help :) If you can post up the specifics of this abstract hald layer? What app did you install which is causing the problems?
Il

---

### Post by Tomosaur on 2007-01-17
It's difficult for us to help you when your entire post is one long sentence. Please break your problem up into little chunks rather than just throwing them all at us in one go. What, exactly, is your current problem? As far as I can tell, you've had previous problems which are now not problematic. Is your problem the usb drive?

---

### Post by pmasiar on 2007-01-17
> **Dave-C said:**
> The amount of times i've had to reinstall ubuntu is unreal and its just after i get the computer the way i like it and i keep getting the same problem ... then i reinstalled it and fixed the computer to the way i wanted (not much just a few media programs from the add and remove programs list) 

maybe try to NOT install media programs - try to learn basics using basic Ubuntu (without universe). proprietary drivers and codecs might cause something strange. Less software - less things to break and configure ;-)

One tool which saved me many times is midnight commander (mc). It is visual without GUI - try it.

---

### Post by phossal on 2007-01-17
lol C'mon, seriously? You've all been trolled.

---

### Post by jvc26 on 2007-01-17
what?
Il

---

### Post by mistypotato on 2007-01-17
Dave-C....

I was feeling the same at one point.

As a newbie it seemed I spent more time re-installing Linux than using it.   It's a "Newbie" thing.


Do yourself a BIG FAVOR, GET SOMETHING LIKE MONDOARCHIVE and make a set of restore disks at the point where you have everything the way you want it.   It's like WindowsXP System Restore.

I did and now re-installation for me is about 3 or 4 mouse clicks and viola, my sytem is back where it was before I messed it up. :D 

But I'm getting better and my system is almost where I want it to be so I'm needing it less.

---

### Post by Dave-C on 2007-01-17
Ok sorry for throwing everything at once i was away for a while reinstalling my linux again, when linux boots it says that there is something wrong with the hald service but when i go into services theres no hald service there, if i'm right the hald service is for hardware and stuff, any1 help me ?   ...  i'm begening to think its my computer :o

---

### Post by riven0 on 2007-01-17
In the terminal, can you try this:
> 
sudo /etc/init.d/hotplug restart

Can you automount your usb drives now?

---

### Post by Dave-C on 2007-01-17
acer@acer-laptop:~$ sudo /etc/init.d/hotplug restart
sudo: /etc/init.d/hotplug: command not found

Not Good.....  :confused:

---

### Post by riven0 on 2007-01-17
Hmmm, :-k alright how about this:

> sudo invoke-rc.d dbus-1 restart

That should restart HAL for you...

---

### Post by Dave-C on 2007-01-17
acer@acer-laptop:~$ sudo invoke-rc.d dbus-1 restart
invoke-rc.d: unknown initscript, /etc/init.d/dbus-1 not found.
acer@acer-laptop:~$ 

I dont think i have hald service

---

### Post by Dave-C on 2007-01-17
is there a remote desktop program for ubuntu that mite be helpful

---

### Post by riven0 on 2007-01-17
> **Dave-C said:**
> acer@acer-laptop:~$ sudo invoke-rc.d dbus-1 restart
invoke-rc.d: unknown initscript, /etc/init.d/dbus-1 not found.
acer@acer-laptop:~$ 

I dont think i have hald service

That could explain it. So try installing it, (or re-installing it if it got messed up somehow):

> sudo apt-get install --reinstall hal hal-device-manager

And then try rebooting the comp.

---

### Post by Dave-C on 2007-01-17
It Working !!! Thanks !!! al keep a note of that sudo incase it happens again thanks

---

