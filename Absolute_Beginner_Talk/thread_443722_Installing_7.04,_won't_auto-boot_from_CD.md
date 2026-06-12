---
title: "Installing 7.04, won't auto-boot from CD"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by rdomanski on 2007-05-14
Hi there.  I'm trying to upgrade from 6.10 to 7.04, have burned a CD with 7.04 on it, however when I put in in my CD drive and restart the machine, it does not automatically begin the installation.  I know this should be mindless, but previous Ubuntu versions just auto-started for me, so I never had to deal with this.

I did try from the terminal: sudo apt-get install ubuntu-desktop

Nothing was upgraded and I was given a message that ubuntu-desktop is already the newest version (but it's still 6.10).

Meanwhile that "Ubuntu 7.04" CD icon is still staring at me from my desktop screen like it's taunting me!

Any help is greatly appreciated.  Thanks.

---

### Post by oilchangeguy on 2007-05-14
are you sure the bios is set to boot from the cd drive first?

---

### Post by rdomanski on 2007-05-14
Holy fast reply!!!

I don't know how to check my BIOS or make changes.

---

### Post by oilchangeguy on 2007-05-14
this varies depending on who made your computer. but when the computer starts look for a prompt to enter setup (bios), once there tab over to boot. from there you can change the boot order, so that the cd drive is first.

---

### Post by rdomanski on 2007-05-14
Ok, I entered BIOS and reached the point where i could edit the boot command.  It had simply said "Boot", so I changed it to say "Boot CD", which I'm sure you can guess did not work.

So my question is what is the boot command that will start the auto-install from the CD?

Thanks for all the help.

---

### Post by oilchangeguy on 2007-05-14
> **rdomanski said:**
> Ok, I entered BIOS and reached the point where i could edit the boot command.  It had simply said "Boot", so I changed it to say "Boot CD", which I'm sure you can guess did not work.

So my question is what is the boot command that will start the auto-install from the CD?

Thanks for all the help.

i'm not sure what you got into. but it's probably not the bios. you can't enter words in the bios. your keyboard is limited to using the tab key, up/down arrows, esc, and enter. that's about it.

---

### Post by rdomanski on 2007-05-14
You were right, I was somewhere else.  But NOW I am definitely in the BIOS (AMIBIOS, to be precise).  I still have no idea what to do now that I'm here though.  How can I find out?  What am I even trying to do here?

---

### Post by oilchangeguy on 2007-05-14
> **rdomanski said:**
> You were right, I was somewhere else.  But NOW I am definitely in the BIOS (AMIBIOS, to be precise).  I still have no idea what to do now that I'm here though.  How can I find out?  What am I even trying to do here?
you should see a series of tabs along the top of the page. one of them being boot. using the tab key get over to boot, press enter. look for the boot order. then make your changes (how this is done varies). then press f10 to exit, y to save. and the computer will reboot.
also wherever you were make sure you undid what you changed.

---

### Post by rdomanski on 2007-05-14
I feel like I'm getting somewhere.  Without changing anything, my boot sequence already had the CDROM in the first position, followed by the USB.  However, when I reboot the message flashes across the screen: "Searching for boot record from CDROM: Not found".

I still don't understand why any of this is necessary.  Only a few weeks ago I threw a 6.10 CD in the same machine and it automatically starte the install without me doing a thing.  I liked that  :-)

---

### Post by oilchangeguy on 2007-05-14
> **rdomanski said:**
> I feel like I'm getting somewhere.  Without changing anything, my boot sequence already had the CDROM in the first position, followed by the USB.  However, when I reboot the message flashes across the screen: "Searching for boot record from CDROM: Not found".

I still don't understand why any of this is necessary.  Only a few weeks ago I threw a 6.10 CD in the same machine and it automatically starte the install without me doing a thing.  I liked that  :-)

the main reason is of course, the process of elimination. do you still have the 6.10 cd? if so, try it, to see if the computer boots from it. it seems there may be a problem with the cd you are trying to use.

---

### Post by rdomanski on 2007-05-21
I just wanted to post this follow-up for others' use in future reference.  After tinkering with the BIOS and re-burning numerous ISO disk images in various ways, my problem was far more simple (naturally).

My computer has two CD drives. Apparently, only one of them is checked upon startup for a boot loader. I just put the installation CD in the wrong CD drive.

Problem solved. However, this prolonged agony begs the question, "Why don't ALL CD drives get checked when booting?"

---

