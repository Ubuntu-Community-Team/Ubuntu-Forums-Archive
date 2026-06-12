---
title: "Installation stops at after cupsd (&amp; GNOME?)"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by ObscureReferenceMan on 2007-05-10
I am brand new to ubuntu. But I heard good things about it, so I thought I would load it on an old PC.

The old PC is a Dell Pentium III. It had been running Windows 98, but I recently wiped the hard drive (with Darik's Boot & Nuke). It has 128 MB RAM and 25GB hard drive. It's got a CD-ROM drive, DVD drive, floppy drive and ZIP drive.

I tried to load ubuntu 7.0.4 (the boot CD checked OK), but it got a little hung up after "Starting common Unix printing system cupsd". The screen then went beige, and after a while there seemed to be a few icons in the center of the screen, and got a window in the upper left that said:

[I]"There was an error starting the GNOME settings daemon.
Some things such as themes, sounds or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include; the remote application did not send a reply,[/I] <there was more, but I didn't write it down>
*GNOME will still try to restart the settings daemon next time you log in."*

The window had a "Close" button, but I couldn't access it, because the mouse no longer controlled the cursor.

Then I tried loading ubuntu version 6.0.6. It seemed to progress nicely, but then froze at a red screen with ubuntu logo. This time the cursor could be moved with the mouse. After a few minutes, the logo disappeared, and got what appeared to be menu bars at the top and bottom of the screen. But this is where things hung up completely.

Any ideas? Thanks!

---

### Post by hsweet on 2007-05-10
I think there is a gnome issue.  I'm pretty sure it's a bug.

I had the same problem with a 7.04 Edubuntu server.  If you can manage to get to a terminal while in gnome try ```
sudo gnome-settings-daemon
```.  That cleared it for me.

If that does not work but you you get an error about settings manager running or some-such, try to figure out the process and kill it.  You might lost your session, but log back in and you might be ok.

You can also switch to kbuntu xbuntu which don't use gnome.

good luck

---

### Post by ObscureReferenceMan on 2007-05-10
I have no idea how to do that. Also, I'd have no idea when to do it either - I've yet to get to a workable interface.

Maybe kbuntu is worth a shot...

---

### Post by ObscureReferenceMan on 2007-05-11
By the way... Once I'm done, I am hoping to donate my PC to my friend's parents. They are in their 70's, and not "power users" by any means. They will be using the computer for very basic stuff; email, web surfing, etc.

Is kbuntu a good idea for them?

---

### Post by hsweet on 2007-05-11
Probably the computer you are using would be happier with Xbuntu.  It uses fewer resorces than either KDE or GNOME.  Or get another 128mb of ram.

---

### Post by ObscureReferenceMan on 2007-05-11
Thanks hsweet! But I've already burned a kubuntu disk. So I'll try that for now. Maybe I'll try it my next time!

---

### Post by ObscureReferenceMan on 2007-05-11
Grrrr.... Tried kubuntu and xbuntu. Results were, basically, the same. Any more suggestions/help would be appreciated.

---

### Post by ObscureReferenceMan on 2007-05-14
Just curious... Would the fact that I ran Boot & Nuke matter? I assumed not, but does anyone know for sure?

---

### Post by ObscureReferenceMan on 2007-05-30
Would more RAM solve the problem? I would consider getting more - a 128MB chip looks to be around $25. And I have at least one slot open. That would bring me to 256MB. So... is it worth the investment?

And one quick update: On the advice from a friend, I tried to update the BIOS. But was unsuccessful. I had downloaded all the available BIOS from the Dell site (versions A02 - A06), but none worked (each time I got a lengthy error message that ended with something like "...contact your administrator").

I really want to get this working. I hate to have to throw this computer out. I'd much rather give it a good home. Thanks!

---

### Post by lsalminen on 2007-05-30
After all this work, why don't you just put good old windows on the machine? I don't know if you're a computer expert, but after all this work you put into Ubuntu, maybe just good old windows 2000 would work.

---

### Post by ObscureReferenceMan on 2007-05-30
I considered that (I'm FAR from a computer expert). But I don't have a spare copy of Windows 2000. I could install my old copy of Windows 98, but I've heard it is not very "secure". Also, I'd like to keep the amount of money I throw at this project to a minimum. 

That being said, it looks like I'll have to at least buy some RAM. Checking the system requirements for ubuntu (which I missed initially), it recommends 256MB of RAM. So it looks like I'll have to get a 256MB chip (for a total of 384MB). I want to be able to run more than just ubuntu!

---

### Post by ObscureReferenceMan on 2007-06-05
Well, I broke down, and got a 512MB chip (for a total of 640MB of RAM). But now I have a new problem. I'll do some searching. Maybe I'll start a new thread...

---

