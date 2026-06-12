---
title: "[ ADVICE NEEDED ] New HDD, Old BIOS"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-12-03
Hello everybody,

I'm facing a small issue here and I need your advice on what to do...

Here's the plot: I need to replace my old 20 GB Seagate HDD with a bigger one that I'll buy in a few days. 

The problem is that I heard that some (big) HDDs have some problems with Linux (or Ubuntu, more specific) and that this problem is somewhat related with an old BIOS.

I need a new HDD with IDE interface (ATA100, I *think*, I'm not quite sure) and I'll go for Seagate or Western Digital (I would appreciate if you could give me some pros & cons for this two trademarks, too).

My computer is a P3 Compaq with an Intel processor of 1 GHz.

I don't know any manufacturing date details, since I bought it second hand from a local computer shop... but I think that it's got a somehow old BIOS - its main screen reads "*Compaq Computers Corporation Setup Utility*" and that's all.

I'd appreciate some thoughts on what type of HDD to buy that would go on well with any GNU/Linux distro :)

Thanks in advance !

Regards,

LLRNR

---

### Post by ReaderRat on 2006-12-03
I would take a good look at the BIOS you have. Get into "setup" and see what's there....Can you boot from a CD?....Do you have onboard sound or video?....Is an update available for the BIOS, or is it not "flashable". Seagate and Western Digital are solid brands (They are the only thing I use.) I have had problems with Maxtor in the past. Hope this helps....

---

### Post by LLRNR on 2006-12-03
ReaderRat, thank you for your quick input.

I took your advice and took another good look at my BIOS... stupid me, there was an "About" entry in one of the menus that I never noticed before... err... here it is:
```
System BIOS and Setup Utility
Copyright 1982-2001
Compaq Computer Corporation
All Rights Reserved

Boot Integrity Services
Copyright 1998-1999
Intel Corporation
All Rights Reserved
```

The title bar (the thing above the menu bar) reads "Compaq Computers Corporation Setup Utility".

So, I guess if this was (c) in 2001 I shouldn't have *too* much problems, huh ?

To answer your questions, yes, I can change the boot order whenever I like, and I have an integrated sound device (there's an onboard video device too but I added a nVidia card a year ago).

Ummm... what's that thing about BIOS update you said ? I don't think I caught that... can BIOS-es be updated ?! If so, how ? (I'm sorry, I'm quite dumb when it comes to hardware...)

Thanks again,

LLRNR

---

### Post by Mimsy on 2006-12-03
Yes, they can. I actually reinstallde WinXP on my Compaq laptop (from early 2002), to be able to update the BIOS. I had to go to the HP/Compaq website, find my exact model, and download the update from there. The downloader/installer absolutely refused to work with Ubuntu, as expected, hence the WinXP reinstall. It made for a very long evening... At least installing Ubuntu all over again was a lot quicker! As a general rule with BIOSes though, if it's not broken, don't try to fix it.

Btw, buried somewhere in your BIOs should be an entry called "BIOS start date", if you're still wondering exactly how old your system is. 

/Mimsy

---

### Post by az on 2006-12-03
Neither linux nor Ubuntu have problem with such hard drives when you use such a motherboard.  The problem is that in old computers, the people who made the bios never figured that hard drives would be big.  They never made the BIOS be able to access the higher portions of the drive.

Typically, a very old (486 - type) computer bios would have trouble beyong 1.2 gigs (or something like that) and less old computers (pentium one) would have trouble seeing past eight gigs.  And once linus is booted, the linux kernel will be able to see your whole 80-gig drive, if you have one.

That's all fine and dandy if your boot loader, kernel and initrd (ram disk with all the neede stuff to boot) are found within that space.  If your bios is really that old (I doubt it is) you can avoid any headaches by creating a small /boot partition within the first gig of your hard drive.  

But really, you should look up the manual for your motherboard (compaq is excellent with putting them online and making them accessible - HP now hosts their stuff since they bought compaq)  The manual will tell you if you need to update your bios to use a big hard drive without any hassle.

---

### Post by LLRNR on 2006-12-03
Thanks, Mimsy !

> **Mimsy said:**
>  As a general rule with BIOSes though, if it's not broken, don't try to fix it.

So, you suggest that I try to plug in whatever HDD I buy, see if it works, and *only* if I do have problems, try a BIOS update... I guess you're right, it's a smart thing to do.

I looked today on some websites of local computer shops and I was terrified by the 160+ GB HDDs I saw... wow, the biggest one I had was a Maxtor of 80 GB that c-r-a-s-h-e-d two years after I bought it, I'll never do such a stupid thing again. (In fact, it crashed so bad, that after I checked it with the diagnosis tool provided by Maxtor on their website - which returned, of course, a nice "*This drive is failing blah*" stuff -, I couldn't even make it recognized by BIOS... it was as if it wasn't there at all !)

LLRNR

---

### Post by Mimsy on 2006-12-03
> **LLRNR said:**
> So, you suggest that I try to plug in whatever HDD I buy, see if it works, and *only* if I do have problems, try a BIOS update... I guess you're right, it's a smart thing to do.

Pretty much, yes. It was such a hassle, and chances are that the problems can be solved by fixing and tweaking settings in Ubuntu. :)

I would take azz' advice and go find the manual for your Compaq model through the new HP website though. I got the manual for mine through there, it's surprisingly easy to find it. I did a site search for "[model number] manual".

/Mimsy

---

### Post by LLRNR on 2006-12-03
Thanks, Azz ! (I didn't see you posted right before me)

I was thinking about the thing you suggested - to make a small /boot partition to avoid any troubles - and you reinforced my idea, thank you. I'll do a check on-line as well.

Alright then, I guess that with this valuable info I'll be able to figure things straight... 

Thank you all for your time and suggestions !

Cheers,

LLRNR

---

