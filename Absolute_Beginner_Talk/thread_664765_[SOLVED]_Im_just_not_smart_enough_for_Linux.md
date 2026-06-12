---
title: "[SOLVED] Im just not smart enough for Linux"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by gr8dane on 2008-01-11
That is my conclusion at this point.  I have 7.10 Live CD and have been playing with it and liking it very much.  Then I tried to set up the wireless and thus the source of my frustration.  I have gone through the forum and tried to read everything relating to connecting off of the Live Cd but I have no luck.

I am using a Compaq Presario 2500 (it was just a cheap buy when I needed a laptop fast a few years ago) it has the BCM4306 wireless card.  I have tried manual set up and everything but I just can't get it to connect.  I assume it is possible to configure 7.10 to work but I just can't get it to work.  So before I give up on what seems like a very good OS, someone point me in the right direction so I can test the internet on this version.  Thank you.

---

### Post by Niniel on 2008-01-11
Don't give up!

That's a Broadcomm chip, and for me it was very easy to set up, no manual work required. I just enabled the restricted driver for it, and that was it. Took less than a minute. :)

---

### Post by aysiu on 2008-01-11
*I'm just not smart enough for Linux* in this case translates to *I am installing and configuring an operating system manually and happen to have a Linux-incompatible piece of hardware*

Niniel, can you walk gr8dane through the Restricted Driver process step by step?

---

### Post by Niniel on 2008-01-11
Sorry, no, I'm not sitting in front of my home box right now, and I don't remember the menu well enough to do this from memory. :(

---

### Post by USFMD82 on 2008-01-11
System-->Administration --> Restricted Drivers Manager

If that does not work try this thread, its how I fixed mine on a Compaq Presario v2000

[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by gr8dane on 2008-01-11
> **Niniel said:**
> Sorry, no, I'm not sitting in front of my home box right now, and I don't remember the menu well enough to do this from memory. :(

Wow did you read my mind!!  LOL  My next question is that something that can be done running the Live CD?  I'll research enabling that now.  Thank you again.

---

### Post by gr8dane on 2008-01-11
My son has taken over my laptop to watch Shrek so I'll give that a go a little later.  Thank you!

---

### Post by stchman on 2008-01-11
> **gr8dane said:**
> That is my conclusion at this point.  I have 7.10 Live CD and have been playing with it and liking it very much.  Then I tried to set up the wireless and thus the source of my frustration.  I have gone through the forum and tried to read everything relating to connecting off of the Live Cd but I have no luck.

I am using a Compaq Presario 2500 (it was just a cheap buy when I needed a laptop fast a few years ago) it has the BCM4306 wireless card.  I have tried manual set up and everything but I just can't get it to connect.  I assume it is possible to configure 7.10 to work but I just can't get it to work.  So before I give up on what seems like a very good OS, someone point me in the right direction so I can test the internet on this version.  Thank you.

Linux is not that difficult.  It just requires a certain level of commitment.  Remember, Linux is not more difficult than Windows just different.

---

### Post by gr8dane on 2008-01-11
I guess the best way to describe me is and outside of the box thinker that needs prozack.  What I am liking about Linux is that it is ment to be tinkered with and I love to tinker and figure things out, my problem is that I am impatient.  Not a good combination.  My gratitude to everyone for getting my "want to" tinker back in full drive.  Cheers!

---

### Post by Het Irv on 2008-01-11
I have little to no experience in matters of the kernel, but do the restricted drivers change something in the kernel?  and if so would that be the problem?

I am thinking it has to do with the Kernel being on the CD and the user not being able to change it.  

Remember I have no experience with the kernel so I am just floating Ideas.

---

### Post by Dravah on 2008-01-11
Installing and updating Ubuntu should work. At least it did for me.

My network card did not work at all with the Live CD, but after installing and running the updater it worked like a charm. Didn't have to enable any restricted drivers or anything, everything worked out of the box. 

Good luck!

---

### Post by exactopposite on 2008-01-11
> **Niniel said:**
> Don't give up!

That's a Broadcomm chip, and for me it was very easy to set up, no manual work required. I just enabled the restricted driver for it, and that was it. Took less than a minute. :)

i'm not sure that the restricted drivers manager works from the cd. i remember reading that it doesn't, but i might be wrong.

---

### Post by gr8dane on 2008-01-11
Yeah at this point is still is not working.  It can't find fwcutter when I try to enable it.  I just wanted to try this distro out compared to other distro's and I know that it would be bias to ask this group what is the "best" learning distro out there for Linux.

I have already allocated 16MB on the HD and I would like to set it up for a dual boot (I unfortunately still need M$ for work) so I should just bite the bullet and do the full install and go from there.  My question is with the install and update, wouldn't I need the internet connection for the update anyway?  That would sort of be a mute point since I can not connect right?

---

### Post by Het Irv on 2008-01-11
If you have the space. allocate about 5 to 10 Gigs on your hard drive and set it up for a dual boot.  With a Broadcom card you should not have any problems connecting.  It is also posible to download the 2 files need to use the Restricted Drivers and Install them offline.  If you like the other functions of the Live CD you should not have any problems with installing it.

---

### Post by macogw on 2008-01-11
> **gr8dane said:**
> 
I have already allocated 16MB on the HD and I would like to set it up for a dual boot (I unfortunately still need M$ for work) so I should just bite the bullet and do the full install and go from there.  My question is with the install and update, wouldn't I need the internet connection for the update anyway?  That would sort of be a moot point since I can not connect right?
16MB?  The CD is 700MB!

Yes, you need an internet connection to do it.  Or, just download [this](http://macoafi.googlepages.com/firmware.tar.gz) from another computer and use a flash drive and copy and paste it to your desktop.  Then do this:
```

cd Desktop
tar xf firmware.tar.gz
sudo mv firmware/* /lib/firmware/
sudo chown root:root /lib/firmware/*

```
copy and paste one line at a time hitting <enter> after each one.  That'll just copy the firmware into the right folder for you.

---

### Post by nikoPSK on 2008-01-11
Don't put yourself down man! I felt that way when I started 3 years ago but look now! :KS

---

### Post by gr8dane on 2008-01-12
[QUOTE=macogw;4119504]16MB?  The CD is 700MB!

I meant to say 16GB, it really does look foolish now that I re-read 16MB.  I bit the bullet and installed it but wasn't sure how to install it on the partition that I created.  So now I have my HD split up into 4 sections now.  So once I get it working and play with it for a while, I reformat the entire drive and start from scratch and repartition the drive better.

I'll give it a go on that file and hopefully my next post will be from Ubuntu.  :D

---

### Post by gr8dane on 2008-01-12
Good news and bad news!  Good news is that I am now connected and typing this from my laptop wirelessly as I hoped.  The bad news, macogw is that your suggestion didn't work for some reason??

I decided to just connect the laptop hardwire instead of trying to do it wirelessly.  Yes I know you are thinking duh should have done that a long time ago!  Yes but I am a do it to learn it type of person and wanted to give it a shot on my own.  

So plugged in straight from the modem and downloaded updates and then installed the restricted files.  Thus I am in the game again and hope to ask TONS more questions and learn to be a Linux head!  Thank you to all that helped and pointed me in the right direction.

Please have your favorite beverage of choice on me today!  CHEERS!

---

