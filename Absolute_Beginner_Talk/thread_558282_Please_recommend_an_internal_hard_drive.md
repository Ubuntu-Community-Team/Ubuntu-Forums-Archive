---
title: "Please recommend an internal hard drive"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by GA_M on 2007-09-23
Hi!

Could you recommend an internal hard drive, hopefully a very affordable one (this is my older learning computer and I am in no way "financially gifted") that YOU have had no problems installing and using Xubuntu or Ubuntu on?

If you can't think of a specific, very affordable hard drive that you KNOW will work, could you at least kindly tell me _which kind_ I should get? ***(ATA-33, FAST SCSI, SATA, EIDE, ATA-100, IDE, ATA-133, ULTRA2 WIDE SCSI, ULTRA ATA)?***

*I don't know anything about hardware and even less about Ubuntu*, so please help me test (X)Ubuntu/transition to it _as effortlessly as possible_!

Thank you. **I appreciate your help**.

PS  (The specs of the rest of the computer are: about 440 mb RAM, 800 mhz Intel Pentium 3, ASUS AWARD BIOS P3V4X, JumperFree PC-133 AGP/4X motherboard, ethernet card, and ATI Rage128 (32 mb?) video card -- an OLD computer, all right.)

PPS A completely unrelated question: can I insert just about ANY internal hard drive in an external hard drive's case? (The external hard drive itself, that once was in the aluminum shell, has gone to a better world).

---

### Post by Dr Small on 2007-09-23
If the motherboard in this older computer is a few years old, then you will most likely need a PATA hard drive, which takes a ribbon, whereas the new SATA drives take a SATA cable, which most new motherboards have.

The old motherboards probably don't have a SATA connector on it, so a SATA drive would be no good without an adapter.

I have no idea if you can place an internal hard drive into a external hard drive shell, as I have never tested it myself, but most likely you could.

---

### Post by kerry_s on 2007-09-23
best thing to do is take the old 1 out and take it with you, the computer guy can point you to the right one. comp usa has very good service.

---

### Post by Dr Small on 2007-09-23
The last three things I bought from comp usa were trash... Of course, it probably depends upon the store/location, but the motherboard and brand new computer was bad. Then the computer replacement had a bad motherboard on it...

But, yeah. Lol. If you take it to some technition, he should be able to find one that will work.

Dr Small

---

### Post by jimrz on 2007-09-23
Probably ATA 100 would do and 133 may. If you have a small "mom and pop" computer shop nearby you could most likely find a used 12 - 20 Gb for very low price.

---

### Post by w4ett on 2007-09-23
I've bought from there guys before....60Gb Maxtor for $27:

[http://www.pcpartsohio.com/BookDetail.aspx?item_id=60](http://www.pcpartsohio.com/BookDetail.aspx?item_id=60)

Great Deal

---

### Post by GA_M on 2007-09-23
Hi,

The old hard drive on that computer is a 10 gig Enhanced IDE one: although it worked with Windows 98 it's given installation problems to Xubuntu, Ubuntu and Debian (even the "download it and install it version" that bypasses most of the CD-Rom, which at some point someone though might have been the problem).

The hard drive has given me so many problems installing the base system (such as "the ext3 file system created in partition #1 if IDE1 master (hda) failed" or "cannot mount volume" or "debootstrap warning -- failure trying to run: chroot /target dpkg ~force  --install var/cache/apt/archives/debconf_1.4.72ubuntu9_all.deb  check /var/log/sylog or see virtual console4 for details") that I just want to give (x)ubuntu / debian one last try, with a hard drive I know will work.

---

### Post by overdrank on 2007-09-23
> **GA_M said:**
> Hi,

The old hard drive on that computer is a 10 gig Enhanced IDE one: although it worked with Windows 98 it's given installation problems to Xubuntu, Ubuntu and Debian (even the "download it and install it version" that bypasses most of the CD-Rom, which at some point someone though might have been the problem).

The hard drive has given me so many problems installing the base system (such as "the ext3 file system created in partition #1 if IDE1 master (hda) failed" or "cannot mount volume" or "debootstrap warning -- failure trying to run: chroot /target dpkg ~force  --install var/cache/apt/archives/debconf_1.4.72ubuntu9_all.deb  check /var/log/sylog or see virtual console4 for details") that I just want to give (x)ubuntu / debian one last try, with a hard drive I know will work.

I recently saw those same errors and it was a memory problem. I had to remove one stick of ram and then the system flew. You may try that or a memory test on each stick! :guitar:

---

### Post by GA_M on 2007-09-23
Thank you overdrank.

You may well be right!  In fact, the only thing that changed with the computer (besides the removal of Windows Ninety-Eight) is that a friend of mine added extra RAM from an old computer!

Figuring out what's wrong would sure relieve me of a lot of headaches...

:)

---

### Post by GA_M on 2007-09-23
PS  -- ...But I did do 3 passes of the memory test before attempting to install the OS, and nothing seemed wrong.  Hmm  :confused:

---

### Post by overdrank on 2007-09-23
> **GA_M said:**
> PS  -- ...But I did do 3 passes of the memory test before attempting to install the OS, and nothing seemed wrong.  Hmm  :confused:

So did I and still got random errors until I removed that stick of ram. It was just a Idea. :guitar:

---

### Post by w4ett on 2007-09-24
Might be dirty contacts on the memory sticks too.....use a pencil eraser and LIGHTLY clean the contacts...sometime this can help.

---

### Post by GA_M on 2007-09-24
So many variables -- but that's life.

Thanks again!

:)

---

### Post by w4ett on 2007-09-24
Yeah, well with older used components...there are a few more concerns.  I refurb a lot of older boxes and do contact cleaning, vacuuming and blowing out of components as a matter of course.  Time, heat and dust (not to mention nicotine) can play havoc on electronics.

---

### Post by LowSky on 2007-09-24
try newegg.com
I by all my computer hardware from them, never one problem over the last 5 years.
IDE is ATA... i know its all confusing, but since you computer is that old try to find a ATA100 drive

Western digital is a good company, so is Seagate, and none of the Maxtors I have used have failed either (except one, but that was my fault  (dont keep a hard drive on yuo bed with it on... bad idea...lol)

check this out -- it a list of hard drives under $50
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014%204025&bop=And&Order=PRICE]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010150014%204025&bop=And&Order=PRICE")

---

### Post by alienexplorers on 2007-09-24
W4ett,
If you use a pencil eraser on the contacts of the ram there is a good chance the gold plating could be removed.  I recommend using alcohol on a q-tip to clean the contacts and the wipe then with a clean. soft, white cloth.

I use to build super-computers and have seen people ruin boards that cost 100,000.00 dollars using a pencil eraser

---

