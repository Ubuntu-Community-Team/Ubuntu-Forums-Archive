---
title: "Unable to Install Ubuntu"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by tj71587 on 2007-08-28
Hey everyone, I posted a similar topic a couple months ago, but I was still unable to and got busy.  So I am running a core 2 duo with 2 gig ram, asus board, and an NVIDIA GeForce 8800GTS and I am unable to run Ubuntu.  When I install it I get a black screen to go from the regular installer.  When i go to the text based installer I am able to install, but when I go to boot up, it goes to a black screen.  Is there any fix for this or has anyone went through this like me.  

Thanks,

T.J.

---

### Post by splintercellguy on 2007-08-28
Uhm, Recovery Mode, sudo dpkg-reconfigure xserver-xorg? What video card do you have?

---

### Post by FuturePilot on 2007-08-28
> **tj71587 said:**
> Hey everyone, I posted a similar topic a couple months ago, but I was still unable to and got busy.  So I am running a core 2 duo with 2 gig ram, asus board, and an NVIDIA GeForce 8800GTS and I am unable to run Ubuntu.  When I install it I get a black screen to go from the regular installer.  When i go to the text based installer I am able to install, but when I go to boot up, it goes to a black screen.  Is there any fix for this or has anyone went through this like me.  

Thanks,

T.J.

Boot into recovery mode. And enter this command
```
nano -w /etc/X11/xorg.conf
```
Go down to the Device section and where it says Driver "nv" change the "nv" to "vesa"
Press Ctrl+X to quite, press Y to save and then hit Enter to write the file. Then type exit and it should continue to boot into a graphical environment. Then you should probably use [Envy]("http://albertomilone.com/nvidia_scripts1.html") to install the Nvidia driver so you can get good performance out of your card.:)

---

### Post by Hobo Joe on 2007-08-28
Yes you can fix it pretty easily, assuming that it is merely the fact that you don't have drivers installed.

Follow these commands:
```

wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb

dpkg -i envy_0.9.7-0ubuntu8_all.deb

envy -t

```

Then just press install nVidia drivers. Make sure to let it configure your xorg.conf  for you.

---

### Post by tj71587 on 2007-08-28
I never get to a point where i can type command line...how do i get there?

---

### Post by FuturePilot on 2007-08-28
> **tj71587 said:**
> I never get to a point where i can type command line...how do i get there?

Use the Recover Mode option in Grub when you first turn on your computer.

---

### Post by st33med on 2007-08-28
Try Ctrl Alt F1

Or FuturePilot's suggestion :)

---

### Post by tj71587 on 2007-08-28
Does doing any of this put my xp partition at risk, as last time i did it, it killed my xp partition (blue screen of death) one of the reasons i would really like to change over.

---

### Post by FuturePilot on 2007-08-28
> **tj71587 said:**
> Does doing any of this put my xp partition at risk, as last time i did it, it killed my xp partition (blue screen of death) one of the reasons i would really like to change over.

No it shouldn't

---

### Post by tj71587 on 2007-08-28
Thanks alot guys, I'll try this out tomarrow hopefully.

---

### Post by Hobo Joe on 2007-08-28
> **tj71587 said:**
> Does doing any of this put my xp partition at risk, as last time i did it, it killed my xp partition (blue screen of death) one of the reasons i would really like to change over.

No, the only thing that could damage your XP partition is directly editing the files/partitions. These things just configure Ubuntu/install drivers for Ubuntu.

I'd recommend running what future pilot said, then following what I said. That way, you'll be able to get into your desktop before you install the drivers.

---

### Post by mikewhatever on 2007-08-28
Your thread title says you are unable to install Ubuntu, however, in the initial post, you are saying you've installed successfully in the text mode. Can you clarify the issue? Is or is not Ubuntu installed on the hard disk? Do you see the Grub Menu with boot options on startup?
To save time, I am going to do some guesswork and assume the following:
1. Nothing is wrong with the installation and you have Feisty on the disk.
2. The problem is, you can not bring up the GUI.

I suspect that your graphics card is too new for Feisty, so there is no driver included. 
[http://www.buildyourown.org.uk/forums/topic.asp?topic_ID=27305](http://www.buildyourown.org.uk/forums/topic.asp?topic_ID=27305)
[http://forums.nvidia.com/index.php?showtopic=42675](http://forums.nvidia.com/index.php?showtopic=42675)
You should try installing the driver yourself. Envy seems to be the best solution.

---

### Post by FuturePilot on 2007-08-28
Yes the 8600 is too new for Feisty. The nv driver does not support the GeForce 8000 series cards yet and the Nvidia binary drivers in the Feisty repos do not support it either. Envy will get you going though. I had problems getting a GUI going with an 8400 GS.

---

### Post by Hobo Joe on 2007-08-28
> **mikewhatever said:**
> Your thread title says you are unable to install Ubuntu, however, in the initial post, you are saying you've installed successfully in the text mode. Can you clarify the issue? Is or is not Ubuntu installed on the hard disk? Do you see the Grub Menu with boot options on startup?
To save time, I am going to do some guesswork and assume the following:
1. Nothing is wrong with the installation and you have Feisty on the disk.
2. The problem is, you can not bring up the GUI.

I suspect that your graphics card is too new for Feisty, so there is no driver included. 
[http://www.buildyourown.org.uk/forums/topic.asp?topic_ID=27305](http://www.buildyourown.org.uk/forums/topic.asp?topic_ID=27305)
[http://forums.nvidia.com/index.php?showtopic=42675](http://forums.nvidia.com/index.php?showtopic=42675)
You should try installing the driver yourself. Envy seems to be the best solution.

That's pretty much the same assumption I came too. 

As for that card, yeah, it's pretty new, I have one though, so I know that at least mine worked with vesa till I got the normal nVidia drivers running. Seems a bit weird to me that he has that problem with the same card... 
Ah well, gotta love Envy text mode I guess!

---

