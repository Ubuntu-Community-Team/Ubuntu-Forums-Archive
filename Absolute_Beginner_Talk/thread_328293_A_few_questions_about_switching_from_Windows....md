---
title: "A few questions about switching from Windows..."
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Good Ol' Ramos on 2006-12-30
I'm downloading Ubuntu as I type this (57% done, homiez!!!) and I just have two concerns: Windows, while upsetting me greatly, has never let me down in the realm of networking and wireless networking. What will Ubuntu offer me in that realm? I have 2 desktops and 1 laptop in this network, and I want to keep it that way, not to mention only this (my main) PC will be without Windows. How will I be able to configure that? Also, what about my games? Halo, Call of Duty 2, Sim City, The Sims... all for PC. Am I to never play those games again? Thank you kind folks for your prompt responses, and I must say, I've been browsing these boards for a while and am impressed at the vast resources present. Thank you all so much in advance.;)

---

### Post by raul_ on 2006-12-30
With the Live CD you can see if your wireless works or not. I've read some threads about wireless configuration nightmares though. Abotu your games, i think at least some of them can be played with wine (kind of an emulator). I would suggest dual-boot nevertheless, at least for the first months

---

### Post by PriceChild on 2006-12-30
What wireless card do you have?

And none of those games you listed work in any way afaik on linux. - dual boot! :)

---

### Post by Good Ol' Ramos on 2006-12-30
Well my Dell Latitude laptop comes with a built-in 802.11b card (not fast, but it gets the job done so whatever), I think it's Intel PRO/Set or something like that... and the desktop downstairs has a PCI 802.11g Linksys card. As for dual-boot, I'm too paranoid of messing with my already-established hard drive, so I'm just putting Ubuntu on a spare 40GB I have in my PC. So it's kiiiind of dual boot. I just go into BIOS and change the boot sequence. My question about that, though, will it be a problem because the partitions will be so different between the two drives?

---

### Post by gh0st on 2006-12-30
> **raul_ said:**
> With the Live CD you can see if your wireless works or not. I've read some threads about wireless configuration nightmares though. About your games, i think at least some of them can be played with wine (kind of an emulator). I would suggest dual-boot nevertheless, at least for the first months

Yeah the Live CD should enable you to check out your network connectivity before you install. That's very handy. Setting up your Ubuntu machine with a Windows network can be done with a program called Samba. I use Samba to share files and printers between Windows and Linux. It shouldn't be too hard to get going. There are loads of good Samba setup guides on here. Here's one to get you started. [http://www.ubuntuforums.org/showthread.php?t=202605](http://www.ubuntuforums.org/showthread.php?t=202605)

As for games, I'm not an expert in that field but I know that a lot of the more popular games can be run with WINE or Transgaming Cedega on Linux. A visit to the gaming section of the forum would be a good idea to find out more though I reckon.

Hopefully all should go well for you with Ubuntu. Good luck :)

---

### Post by Good Ol' Ramos on 2006-12-30
....Live CD? I'm downloading Ubuntu from the Ubuntu website, and then burning the ISO... is the final product of that what you're talking about?

---

### Post by Step on 2006-12-30
That is the Live CD, you can just boot with it and click on install ubuntu, then you will be booted into the OS and have the chance to look around the OS to see if you like it and what possibilities you have. After that you can click the icon on the desktop to install it to your harddisk.:)

---

### Post by riven0 on 2006-12-30
> **Good Ol' Ramos said:**
> ....Live CD? I'm downloading Ubuntu from the Ubuntu website, and then burning the ISO... is the final product of that what you're talking about?

If you're burning the regular cd image for desktops and laptops, then that's the liveCD. The alternate cd is the text based installer.

When you burn the iso, however, make sure it's at the lowest speed possible, (4kb is good), otherwise you may get a bad burn.

---

### Post by floke on 2006-12-30
Just one other thing...

Before you install (if you decide to), check the disc for errors using the choice from the initial start-up menu with the LiveCD. And make sure - if you are installing to a disc previously used by/shared with windows - that you defrag the disc and check it for errors (disc scan or whatever it's called in Win) first - just to be on the safe side (you're supposed to run the memcheck too, from the LiveCD menu, but it takes aaaaaaaaages!).

Good luck!

---

### Post by rccharles on 2006-12-30
> **Good Ol' Ramos said:**
> How will I be able to configure that? 

See link:  
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Don't miss the section on Mount Windows.

Robert

---

### Post by in_flu_ence on 2006-12-30
I think Ubuntu is one of the best linux in terms of hardware support compared with other distro. I have gotten all my wireless card (desktop and laptop) working right through installation. Of course, you might need some setup to link up with the other windows based computer.

Games might be a nightmare though. Dual boot or try search around the forum.

---

### Post by Good Ol' Ramos on 2006-12-30
I just burned the .iso, and I can apparently boot from this CD without affecting my system whatsoever? If that's the case, can I go ahead and do it? I don't feel like going inside my PC right now to unplug this HDD and plug in my empty one. Also, how about partitions? The other one is NTFS format. Will that change?

---

### Post by gn2 on 2006-12-30
> **Good Ol' Ramos said:**
> As for dual-boot, I'm too paranoid of messing with my already-established hard drive, so I'm just putting Ubuntu on a spare 40GB I have in my PC. So it's kiiiind of dual boot. I just go into BIOS and change the boot sequence. My question about that, though, will it be a problem because the partitions will be so different between the two drives?

You may not have to actually enter the BIOS and swap the boot order aroud every time if you can bring up a "Boot Device Selection Menu" by pressing F8 or whatever at boot time. 

More info here: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by raul_ on 2006-12-30
Yes, just put the cd in the drive and you're good to go :) The Live CD includes a partition manager. You can even browse the web (if your wireless works out of the box) and post here while you're installing!

---

### Post by neewby on 2006-12-30
yeh is good , no games will work , networking is the linux realm

---

### Post by Good Ol' Ramos on 2006-12-30
Well, I'm on LiveCD now. I gotta say, it's pretty brilliant. I am having a hard time getting my hands on (what I believe I need...) a driver for my video card. Apparently, it's been detected as it shows up in the hardware list thingy (Windows equivalent to Device Manager... what's it called?) but everything is slow and choppy. Screensavers look like t3h crapz0rz. :p  So, what's this Universe I hear about? Is that where I would get all the software I need for my hardware?



:mrgreen:

---

### Post by raul_ on 2006-12-30
Maybe it's choppy because you're running the Live CD :P it's not actually on the disk so it takes a lot of RAM. After you're done with the install maybe you should give a look at this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

don't read it like a book. I use ubuntu for almost a year and that's still a MUST in my bookmarks. Whenever you need something look there first. For instance, about installing software, take a look at section 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Where_to_look_for_new_programs]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Where_to_look_for_new_programs")

---

### Post by Good Ol' Ramos on 2006-12-30
Wow.... thank you very much. That helps uber.

---

