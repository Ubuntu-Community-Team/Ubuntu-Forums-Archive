---
title: "Live CD is too slow -- I mean WAY too slow"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-09-09
Hi,
I'm trying to check out Ubuntu, but the live CD is way to slow.
I'm talking about slow to the tune of fiteen-twenty minutes to load up the word processing app.

I'm trying to check it out on my ACER Aspire 3000 laptop. It has an AMD Sempron processer, but I'm not sure about everything else. There is plenty of room on the hard-drive too.

Any ideas?

Thanks,
Tom

---

### Post by jordanmthomas on 2006-09-09
The LiveCD is really really slow, and OpenOffice.org is really bloated.  
Imagine having to put all that in RAM.  If you like Ubuntu, but are put off by the speed of the CD, don't be.  It's much faster once you actually install it.

---

### Post by bulldog on 2006-09-09
Well the CD isn't slow,your computer is slow I think.

To run a live cd you need to have a reasonable amount of memory and ditto CPU.

---

### Post by clesage on 2006-09-09
Still that **is** way too slow.

I don't know how familiar you are with Linux, but try typing "dmesg" in a terminal.

You will see how your hardware loaded up, and see if there are any errors that might have happened. Maybe your computer couldn't load enough memory. Just read through it, and see if anything seems suspicious.

Also, do you know how fast your cd drive is?

-sage

---

### Post by fatsheep on 2006-09-09
I bet it's a slow CD drive causing the problem - not a slow computer.

---

### Post by kdnoel on 2006-09-09
If it runs from the Live cd then install it!

---

### Post by Mushed Mango on 2006-10-24
When I clicked the install icon on the desktop, it took way too long to open. In fact, it didn't open at all. I have an iMac G3 Powerpc (600mhz). Do I have to wait longer?

---

### Post by Mushed Mango on 2006-10-25
On a second thought, do you think I could use another computer's cd drive and connect it to mine? How would I do that? I know you can do it through OSX.

---

### Post by englandc299 on 2006-10-25
btw ubuntu's live cd is a bootable cd.  So go into your BIOS settings and put the cd-rom drive as primary boot drive.  It will then boot ubuntu.  Make sure you don't overwrite your partition with OCX on.

---

### Post by Rhubarb on 2006-10-25
[http://reviews.cnet.com/Acer_Aspire_3003WLCi_Mobile_Sempron_3000_1_8_GHz_15_4_TFT/4505-3121_7-31515132.html](http://reviews.cnet.com/Acer_Aspire_3003WLCi_Mobile_Sempron_3000_1_8_GHz_15_4_TFT/4505-3121_7-31515132.html)
> 256MB to 512MB of slow 333MHz memory
Every Aspire 3000 features a cost-cutting DVD-ROM/CD-RW drive

I'm guessing you've got 256MB RAM, which is enough to run the live CD, but it might slow it down.
The Optical drive you've got is probably cheap.
The media (the Ubuntu DVD) might be a poor burn, or you drive may be having problems reading it.

If you install Ubuntu, it will run much much faster for you.
... You'll just have to wait for it to install.
You could try installing it from the alternative CD (without the GUI).

---

### Post by Mushed Mango on 2006-10-26
> **Rhubarb said:**
> [url]You could try installing it from the alternative CD (without the GUI).

Do you mean being able to install it without live? Can you run that through live somehow on the terminal, or do you need a different CD altogether?

If I do need another CD, is it the "Alternate install CD" on the download page? I'd like the reassureance before I start downloading. It does say:

>     * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 


Is that what I should get if I want a fast, painless installation? (I can't even load the installer on live!) Or would it be better just to use a faster CD drive? I have plenty of RAM, so I don't see it as a problem.

---

### Post by Rhubarb on 2006-10-31
Yes, it's the "Alternate install CD" iso that you'll need to download and burn.
I haven't used the alternate install cd myself, but I don't think it'd be too hard to install it.  You probably just need to follow the menus / default settings.

---

### Post by DarkN00b on 2006-10-31
I agree that you need to use the alternate cd to install. I installed Dapper on my laptop with the GUI liveCD and it took forever. I'm running an Intel 1.3Ghz processor w/256 Megs of memory and believe me when I say that you really shouldn't try to use the GUI liveCD on anything less. The thing took like 15 minutes to load to a usable desktop and soon started to bog down. It became almost unusable by the time the install completed. Once installed though, Ubuntu/Gnome runs smoothly and sooo much better than WinXP ever did.

---

### Post by //yardo on 2008-02-18
I have the same Acer Inspire 3000. This may not be the best way to go about solving this but it worked for me. First I installed the "server" version of Ubuntu and after that the Live CD install with full GUI worked flawlessly. I wasn't slow or choppy at all.

Hope that helps.

Edit-----

I didn't even realize this was 2 years old. Anyway, I'll leave my resolution in case it helps anyone.

---

### Post by thomasaaron on 2008-02-18
Yeah, I'm pretty much *WAY* past that. I ended up installing Dapper (way back when) using the alternate CD. Had to tinker with the wireless to get it up and running (used ndiswrapper). A while back, I gave that laptop to my father-in-law, who is still enjoying it. I liked that Acer. It was pretty slow, but definitely solid.

Now I have two System76 laptops. [http://system76.com](http://system76.com)

Best,
Tom

---

