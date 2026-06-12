---
title: "iBook specific questions"
date: 2006-06-20
forum: Apple PPC Users
---

### Post by unconquerable on 2006-06-20
I am in the process of backing up all of my data for the transition to Ubuntu 6.06 on my iBook G4, I have a few questions and concerns for this process.

1)	What should my external hard drive that I use for backup be formatted as.  Can Ubuntu read Mac partitions?  What about fat32 are those readable in Ubuntu?

2)	Will I be able to get functionality of the F1-F5 keys, the keys that control brightness and volume?

3)	Since it is a notebook, what type of power management does Ubuntu have.  When it is not plugged in will it limit performance like OS X does?

4)	What about fan control, is this done by the firmware or the OS?

5)	Will apple honor my Apple care warranty if Ubuntu is installed on it?

6)	Is there support for VGA out?

7)	Does sleep mode when lid closed work?  Does it resume with lid open?

a few more

8 )  What is bluetooth functionality like?  I have a razr I would like to pair with Ubuntu.

9) Apps that are made on x86 will not work for PPC?

Feel free to answer any of the questions you have an answer for!  I hope this could serve as a sort of guide for those planning on making the conversion on thier iBooks.

---

### Post by bogoliubov on 2006-06-21
Hello. I just tried Dapper on my iBook G4, and here is what I know so far. Some questions I want to know myself!

> **unconquerable]
1)	What should my external hard drive that I use for backup be formatted as.  Can Ubuntu read Mac partitions?  What about fat32 are those readable in Ubuntu?
[/QUOTE]
FAT32 should be ok, but if you only wish to use it with OS X and Ubuntu you can use hfs (OS X), but turn Journaling off!

[QUOTE=unconquerable]
2)	Will I be able to get functionality of the F1-F5 keys, the keys that control brightness and volume?
[/QUOTE]
Don't know yet. Dapper can control the brightness (In the Energy settings thingy), but how one can map keys to this I don't know. The volume buttons you can set in "keyboard shortcuts".

[QUOTE=unconquerable]
3)	Since it is a notebook, what type of power management does Ubuntu have.  When it is not plugged in will it limit performance like OS X does?
[/QUOTE]
It scales CPU freq. It can dim the LCD when you removed the power chord. Also, you can set different energy settings for battery and "normal" operation.

[QUOTE=unconquerable]
4)	What about fan control, is this done by the firmware or the OS?
[/QUOTE]
Don't know. I think the iBook gets hotter in Ubuntu than in OS X said:**
> 
5)	Will apple honor my Apple care warranty if Ubuntu is installed on it?

No idea. 

[QUOTE=unconquerable]
6)	Is there support for VGA out?
[/QUOTE]
It works on my iBook G4 12" 1.2GHz (2005). But I haven't found a nice way of using two screens with different resolution yet...
Cloning works and extending the desktop to two screens with the same resolution also.

[QUOTE=unconquerable]
7)	Does sleep mode when lid closed work?  Does it resume with lid open?
[/QUOTE]
It works, though it takes a little more time to fall asleep. It takes more time to wake up and some people report that it wakes up in a bad mood.

a few more
[QUOTE=unconquerable]
8 )  What is bluetooth functionality like?  I have a razr I would like to pair with Ubuntu.
[/QUOTE]
Haven't tested yet.

Hope it helps. Let me know how it goes...

---

### Post by robino on 2006-06-21
[QUOTE=unconquerable]2)	Will I be able to get functionality of the F1-F5 keys, the keys that control brightness and volume? [/QUOTE]

Yes you will. They work automatically in combination with the FN-key. You can change it as well to work without the FN-key by changing the settings with the configuration of a application called pbbuttonsd. This is installed by default and you can install a GUI by installing either powerprefs  or gtkpbbuttons. With this application you can also change keys such as the eject-button and works rather easy with 'teach-in', ie. it recognizes the keys.

```
sudo apt-get install powerprefs
```

[QUOTE=unconquerable]3)	Since it is a notebook, what type of power management does Ubuntu have.  When it is not plugged in will it limit performance like OS X does? [/QUOTE]
The powermanagement is good, you can change the management just like you are used to do so in OSX. The only thing is I find the battery-life better in OSX than in Linux. When I am on the road and need longer battery, I normally use OSX

[QUOTE=unconquerable]5)	Will apple honor my Apple care warranty if Ubuntu is installed on it? [/QUOTE]
Yes they will in the hardware-way. The only things is that when Apple Care would like to use your computer, they want to see OSX on it, since they do not support Linux - and thus they cannot judge if it is a software-error. I have been there myself when I had a problem with my battery-charger, & there was no problem having a dual-boot.

[QUOTE=unconquerable]7)	Does sleep mode when lid closed work?  Does it resume with lid open [/QUOTE]
It works. The only problem is the wireless. I cannot resume it when my wireless was working when I put it into sleep. In Gentoo there was a similar problem and a solution, but I haven't searched yet what the solution is in Ubuntu. You could disable wireless before bringing it into sleep, but that's more a work-around than a solution.

Hope it helps. Do you have a 2/3 usb-mouse btw? It makes it easier, otherwise you have to give a special button on your keyboard this function of second mouse button.  By default this is F12 I thought. The scroll-button of your mouse is by default copy-paste, very nice feature.

---

### Post by zachws on 2006-06-25
this is a good read, after i re-install ubuntu im going to try the powerprefs install.

thanks

---

### Post by LettuceandPickles on 2006-06-29
[QUOTE=unconquerable]
5)	Will apple honor my Apple care warranty if Ubuntu is installed on it?[/QUOTE]

This has been answered but I just want to reiterate:

Absolutely the hardware warranty or AppleCare Protection Plan will be valid; the only thing Apple would hold to void a warranty (afaik) are physical damages caused by opening the machine, intentional or not; (opening the machine would not, by itself, void an Apple warranty or Protection Plan) or accidental damage.  (This assumes the machine is under warranty and/or covered by an AppleCare Protection Plan.)

That said, it is correct that to troubleshoot the machine it would be very useful to have a supported version of Mac OS installed, although some troubleshooting and diagnosis could be done even without Mac OS using utilities on a Mac OS install disk, OpenFirmware (iBooks would all have OpenFirmware) or the relevent version of Apple Hardware Test or other internal Apple utilities any Apple technician you might go to would have access to. (In all those cases the technician could either boot to an operational version of OS X from the media or could issue commands in OpenFirmware.)

You won't get any software support outside of OS X, but you knew that.

And don't forget to hug your technician.

---

### Post by LettuceandPickles on 2006-06-29
Oh, uh, duh....

And any Mac technician is likely to have either an external FireWire device with Mac OS installed that he can boot your machine from or a portable or other Mac at his disposal that he can use to troubleshoot your machine by booting yours into target mode.

Installing Ubuntu would in no way turn off the ability to boot the machine to the boot manager, openfirmware or target mode.  Nor would it stop the machine from booting into OS X from an external drive.

So, really, I can't see any issue at all with not having OS X on the machine from the technician's point of view.

---

