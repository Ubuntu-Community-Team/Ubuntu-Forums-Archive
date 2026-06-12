---
title: "[SOLVED] Which Ubuntu - recommendations please"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by spind on 2007-12-08
Hi, I have a new Toshiba satellite A200-06V with 1gb ram and intel  centrino core2 duo.

Its running Vista premium and would love to get rid of it.  Can i get by only running the ubuntu os or do i still need windows xp as the primary os.

Which Ubuntu, Kubuntu is best? - and how do i find out how my harddirve is partitioned.

You can probably tell by the way i've written this that i'm not fully clued up about this all - i tried to get ubuntu to run from the cd but gets stuck somewhere in dos mode and i don't know the code to keep it running.

Any recommendations before i format the harddrive.

Thanks

---

### Post by PmDematagoda on 2007-12-08
Well, if you like a "Unique and simple" desktop environment then I suggest you use Ubuntu(GNOME), if you prefer a "Windows" look, then I suggest Kubuntu(KDE).

Could you please specifically mention what problem you are getting with the Live CD.

---

### Post by AngryMallard on 2007-12-08
I'd recommend Ubuntu over Kubuntu if you're new to Linux, although in March when Kubuntu is packaged with KDE4 it might be worth a try. DEFINITELY scrap Vista, you can do everything in Ubuntu that you can in Windows, only faster, more reliably, and more securely. 

You will be able to see how your hard drive is set up in the partitioner on the Ubuntu install disc, but you should be able to see it in Vista now.

And you can dual-boot to both operating systems if you want, although I personally consider it a waste of hard drive space.

Also, try the alternate install disc rather than the LiveCD if you're having problems with the install.

---

### Post by Frak on 2007-12-08
I recommend trying out Ubuntu, Kubuntu, and Xubuntu, maybe even Geubuntu and see which one you like best by using the LiveCD.

This type of thing is relative to the user.

EDIT
The liveCD doesn't overwrite anything unless you tell it to do so.

---

### Post by StephUb on 2007-12-08
Why would you say that Kubuntu is the best ?
You have different possibility of GUI Gnome or Kde, that's your call, for me there is no best, they are different.

For your HD, dowload Live CD Gparted and look at your HD
If you wanna get rid of windows, get rid of the partition for recovery but make CD/DVD beforehand

But first, if the live CD isn't running, don't get rid of windows now.
You could have a hardware problem somewhere.

My recommendation, HAVE THE LIVE CD RUN BEFORE REMOVING WINDOWS

---

### Post by Gadren on 2007-12-08
Well, it's been said that Kubuntu/KDE is more "Windows-like" and Ubuntu/GNOME is more "Mac-like," but I don't really think that's true.  They each look somewhat like those proprietary counterparts by default, but that can easily be changed.

One main difference between them is that Ubuntu is very much about having a simple, sensible environment.  Some people say that goes too far, removing needed options.  KDE is very integrated, with many programs part of a suite that interact with one another.  It also focuses on having lots of options available to the user to customize -- some say that it goes so far as to make the interface confusing or messy.

Personally, even though I use KDE, I would recommend you start with Gnome, if only because it's what most Ubuntu users use, and it'll be easier to get support.

As for seeing partitions in Vista, go to Start, right-click on Computer, click Manage, then go to something like "Disk management", and it should show the partitions.  You can even shrink or extend some of the partitions there.  In fact, that's probably what you'll want to do if you're dual-booting; you're more assured that your data will be intact in Vista if you carve out a block of free space from Vista to use for Ubuntu.

---

### Post by spind on 2007-12-08
> **PmDematagoda said:**
> Well, if you like a "Unique and simple" desktop environment then I suggest you use Ubuntu(GNOME), if you prefer a "Windows" look, then I suggest Kubuntu(KDE).

Could you please specifically mention what problem you are getting with the Live CD.


After startup i press F12 and select the cd to boot from and the ubuntu cd begins to run - then i get this: - 

/bin/sh cant access tty - job control turned off

Thanks for all the other help.

---

### Post by Frak on 2007-12-08
> **spind said:**
> After startup i press F12 and select the cd to boot from and the ubuntu cd begins to run - then i get this: - 

/bin/sh cant access tty - job control turned off

Thanks for all the other help.
Does the CD still boot fine? If it does then that can usually be ignored since bash is used over sh.

Else, make sure the md5sum of the image (considering you burned it) is the same as the site implies, and the CD was burned at a low speed.

---

### Post by sports fan Matt on 2007-12-08
I agree with all the suggestions, and if there is something you like thats windows based even though you may wipe the vista partitiion, you still may be able to run windows based programs with WINE, but thats another day...

I would as steph says run the live cd just to see if you like it as well...

---

### Post by aysiu on 2007-12-09
These two links may help:
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by spind on 2007-12-09
> **Frak said:**
> Does the CD still boot fine? If it does then that can usually be ignored since bash is used over sh.

Else, make sure the md5sum of the image (considering you burned it) is the same as the site implies, and the CD was burned at a low speed.

The cd just stops at the dos message i mentioned which comes after the initial Ubuntu screen offering me the choices and then the ubuntu screen with the horizontal bar -then nothing happens - just the message. So i do a forced shut down.

I'm unclear as to the md5sum is but i did burn it with the infra recorder recommended on the site. As for the speed - i don''t know.

I am downloading ubuntu to this laptop and will burn it again or can i simply run it from the harddrive?

---

### Post by Frak on 2007-12-09
> **spind said:**
> The cd just stops at the dos message i mentioned which comes after the initial Ubuntu screen offering me the choices and then the ubuntu screen with the horizontal bar -then nothing happens - just the message. So i do a forced shut down.

I'm unclear as to the md5sum is but i did burn it with the infra recorder recommended on the site. As for the speed - i don''t know.

I am downloading ubuntu to this laptop and will burn it again or can i simply run it from the harddrive?
You can try something called Wubi, it is still in development, but you can try it by putting in the disk while in Windows, exploring the CD and double clicking Wubi.

Wubi allows you to install a pre-configured Ubuntu to your hard drive.

---

### Post by spind on 2007-12-09
Thanks for wubi, Frak!  Wooopee! it worked and installed ubuntu and sending this off my new os after an easy comfiguration to wireless internet! - so i'll check out how it works and give kubuntu a try sometime in the future.  Thanks again.

---

### Post by PmDematagoda on 2007-12-09
You don't need to do a full install of Kubuntu to use it, simply execute:-

```
sudo aptitude install kubuntu-desktop
```

Then log out, go to the Sessions menu, select KDE, and log back in, then you are good to go.

---

### Post by aysiu on 2007-12-09
> **PmDematagoda said:**
> You don't need to do a full install of Kubuntu to use it, simply execute:-

```
sudo aptitude install kubuntu-desktop
```

Then log out, go to the Sessions menu, select KDE, and log back in, then you are good to go.
Details (with screenshots) here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

