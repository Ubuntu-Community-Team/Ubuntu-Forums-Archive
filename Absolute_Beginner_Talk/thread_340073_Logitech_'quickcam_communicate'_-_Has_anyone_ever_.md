---
title: "Logitech 'quickcam communicate' - Has anyone ever got this  to work?"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by stoer on 2007-01-16
Hi all.
This noo* has spent the last three days trying to set up a logitch we*cam communicate in U*untu, my hair has turned grey and my Laptop is now missing the '*' key !!! ( *ugger *ugger *ugger it!).

I've tried the following 2 threads,

[http://ubuntuforums.org/showthread.php?t=322218](http://ubuntuforums.org/showthread.php?t=322218)

[http://ubuntuforums.org/showthread.php?t=303330](http://ubuntuforums.org/showthread.php?t=303330)

Neither work for this camera, *ugger!

And i've nearly gone *lind reading all that i can find through Google. Although the following 3 links all looked promising.

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)        didn't work

[http://ovcam.org/ov511/install.htm](http://ovcam.org/ov511/install.htm)    couldn't follow

Logitech QuickCam Communicate
[http://www.rdegraaf.nl/index.asp?sND_ID=331541](http://www.rdegraaf.nl/index.asp?sND_ID=331541)   *eyond my limited skills.  ](*,) 

Some code for those amongst you that understand these things, i don't include myself in your hallowed num*ers.

```
steve@laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08f5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000


steve@laptop:~/gspcav1-20070110$ ls /dev/video*
/dev/video  /dev/video0



steve@laptop:~/gspcav1-20070110$  dmesg|tail -30
~
~
~
~
[17183040.360000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17183041.036000] usbcore: registered new driver snd-usb-audio
[17184327.588000] usb 3-1: USB disconnect, address 2
[17184331.104000] usb 2-2: new full speed USB device using uhci_hcd and address 2
```

Is there anyone, anyone at all that has gotten even near to installing one of these acursed gizmo's in Linux? Or am i P***ing into the wind with this one ?  ](*,)   ](*,)   ](*,) 

I tried using *oth camorama and Ekiga, Both (enough  with the Bloody 'B's') see my television card on /dev/video0, but no camera.

Just to keep me sane, and so that i to can learn along the way...
I had as standard, /dev/videoand /dev/video0 - having read the last 3 links i added /dev/video1 thinking maybe that is where my  camera might be hiding.  Do i need to "mount" or "activate" these devices in any way to use them? as i would say with a dvd drive or new partition?

If, in your accumulated wisdom this camera is a lost cause - presently.  Then what is relatively cheap and works 100% under Ubuntu?  My 4 year old son wants to see his grandparents aswell as talk to them, we're along way from home here. Any advice, help or just  some encouragement would be greatly appreciated.

---

### Post by Rackerz on 2007-01-16
Did you try easycam2? It's an old package now but it had good camera support.

---

### Post by stoer on 2007-01-16
> **Rackerz said:**
> Did you try easycam2? It's an old package now but it had good camera support.

Hi and thanks for the rocket reply.
Just looked with synaptic and couldn't find it...(easycam2)

I'm using Gnome/KDE in Dapper.
I think also that there are issues with actually seing my camera in Ubuntu (could be wrong of course, maybe I can't see my camera anymore...)
Or at leat 'driver' issues.

---

### Post by Duppy on 2007-01-16
i cant help with your problem, but i have some advice.

copy this "b" and then press ctrl+v instead of shift + 8

:)

---

### Post by stoer on 2007-01-16
> **Duppy said:**
> i cant help with your problem, but i have some advice.

copy this "b" and then press ctrl+v instead of shift + 8

:)


  UGGER OFF!!

 BUGGER OFF  !!, hmmm? Yep you're right, it looks better already, thnks ;) ;)  :p 

ps now the bloom'n a's having a paddy aswell, stick - stick - stick - stick

---

### Post by stoer on 2007-01-17
> **Rackerz said:**
> Did you try easycam2? It's an old package now but it had good camera support.

Ok, so now i've slept for a few hrs, ;) 
Easycam2, search and je shall find.  Got it!
And......
Looks like a winner, at least the early results look good.  After alot of tweaking i'm getting a picture in Camorama, Ekiga (after i figured that i needed to set ntsc instead of pal), kopete and aMSN (need to set up my firewall to allow access - it looks promissing).
Just haven't  managed  sound yet.
Had some freezes late last night and had to restart a couple of times, Camorama doesn't like a large format picture.
Still working on it, but i do have pictures, excellent and many, many thanks for this tip...appreciate it! :D

---

### Post by stoer on 2007-01-19
I have picture via the cam, quality is pretty poor especially colour.
Camorama still crashes after a time or freezes when using the cam.
Ekiga gives a washed out almost black and white picture and no sound.
All pretty dissapointing when compared to the results using the logitech driver under windows; ok, the results in windows are also not spectacular, it is just a cheap cam, but the results are much better.
From reading the boards it would seem this is not something that's goinig to be improved using Edgy,  yes i know - the problem is with companies such as logitech that provide no multi os support and that reverse engineerig the official drivers is never going to give the same quality, still dissapointing though.
I'm still wondering if anyone has had more success?  and if so with what cams?  Is there a webcam that comes with linux support?

---

### Post by stoer on 2007-01-19
Just tried reinstalling Easycam2,
looks for what ever reason a whole lot better. :-k 
Now getting sound in Ekiga, with some feedback, but what the heck picture and sound!
Now just waiting for a friend or 2 to get home from work and i'll give aMSN a try to see if it all comes together or not.

Anybody getting better  quality than these....?

---

### Post by OldGaf on 2007-04-18
> **stoer said:**
> Just tried reinstalling Easycam2,
looks for what ever reason a whole lot better. :-k 
Now getting sound in Ekiga, with some feedback, but what the heck picture and sound!
Now just waiting for a friend or 2 to get home from work and i'll give aMSN a try to see if it all comes together or not.

Anybody getting better  quality than these....?

I am trying to get this cam working under Feisty. Can you please post what you get from lsusb

---

