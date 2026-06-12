---
title: "Thinking About Installing Ubuntu 7.04"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-07-30
The only thing that is preventing me from making a decision has to deal with compatibility. I'm not sure if windows applications can be downloaded onto Ubuntu. Here are the things that I have, please tell me which ones are compatible with Ubuntu and which one's aren't:

Logitech webcamera
Microsoft mouse (you never know)
HP keyboard
HP psc 750 all-in-one printer
Guitar Pro 5
Steam
The Movies

All of these said you need Microsoft but since this OS is new maybe they could be compatible

Also if I make something using a Ubuntu application, will I be able to open it on a windows computer? eg. Making a slideshow presentation on Ubuntu and opening it on Microsoft Powerpoint.

Any help would be greatly appreciated!

---

### Post by jkvv_1973 on 2007-07-30
Ive upgraded from DaPPER...had to reinstall 2x coz grub wasnt right...must be my fault...
anyways I realized that feisty has more utilities looks are kinda same...

Im not an avid Ubuntu user...but I recommend it. I still have XP on my other PCs...

****was tinkering and saw a spare desktop AMD xp3000...and a spare HD I can erase...took out the xp HD...popped in the Feisty Fawn Live...and everything is a breeze >compared to DSL and Puppy (no manual stuff to do)

I like that you can share folders via MICROSOFT from one PC to another...although not succesful yet I have to read on SAMBA...it asks for a USER PASS...gotta find it in the wiki...

---

### Post by Orochi on 2007-07-30
Steam and The Movies (and most games) won't work without maybe running WINE (a windows compatibility layer). I don't know what Guitar Pro 5 is, but I'm guessign that program won't work either (there might be a similar equivalent for Ubuntu though). The mouse should be fine, for the printer google the name to see if there are Linux drivers available (or check linuxprinting.org). 

You shouldn't have any problem with transferring powerpoint and word documents, OpenOffice is compatible with MS Office.

---

### Post by Mr. Swiveller on 2007-07-30
* Webcam - I don't know whether it is supported;
* Mouse - mice generally work straight away; I never had any problems getting them to work;
* Keyboards are largely generic; HP-specific buttons MIGHT not work;
* I don't know whether your printer would work; HP support is generally good, though;
* Windows programmes: firstly, you need to install wine in order to be able to run Windows programmes. It is not included with (K)Ubuntu, yet [www.winhq.org](www.winhq.org) makes packages for Ubuntu available. Note that not all Windows programmes work. 'Steam' is a framework used for games, right? I believe it works quite well if run through Wine.

cheers,

Swiveller

---

### Post by ron999 on 2007-07-30
I've looked in the 'add printer' wizard and there are drivers for HP PSC 750 and PSC 750xi

---

### Post by Malh on 2007-07-30
i'm using an HP notebook and my keyboard works completely--including hp specific keys such as the "Ok" button, volume controls, and the "Back" button.  my touchpad works but i had to disable tapping, which was quite easy to do.  i suggest you use the ubuntu live CD to see what works, and if some things don't work automatically there's usually a way to fix it.  what i did was i resized my XP partition(i keep it for playing LotRO and other games) and i made an ubuntu partition which i use for everything besides gaming.  you can resize your partition using Hiren's Boot CD and Partition Magic Pro to resize it.

hope this helped steer you in the right direction

---

### Post by Hospadar on 2007-07-30
In terms of what programs will run well under wine, you should check the database at the wine website ([http://appdb.winehq.org/](http://appdb.winehq.org/)).  Steam is on the gold list for working applications, but how well an app works under wine is often very distro/hardware/driver specific, so there isn't any garuntee, although if it's on the gold list you can most likely get it working pretty well, especially if you are willing to put in a little effort poking around on wikis and forums.  I'd be willing to bet that for something as common as steam there are some pretty complete guides (I know that is the case for  warcraft)

As for transferring documents from ubuntu/linux to windows, most documents will transfer pretty well.  In openoffice (the default office suite) you can save all the documents (slide shows/powerpoints, documents, tables, etc to MS office formats, and you can also install openoffice on windows for garunteed interoperability.

Anything like pictures or music or videos should transfer just fine as well, jpegs, mp3s, and most video formats (divx, mpeg, etc) are easy enough to get to work on any system.

Also depending on your system hardware, you will want to look and see what drivers if any the vendor provides for linux (especially for graphics cards), I use the nvidia supplied linux drivers and while the default drivers work on my card, the nvidia ones are superior.

Hope this helps!

---

### Post by cotcot on 2007-07-30
Your printer has good linux support with the HPIJS driver.

---

### Post by sailor2001 on 2007-07-30
don't know what guitar pro is, but checked synaptics and there is a bunch of guitar stuff there including type setting sheet music for guitar. Someone familiar with guitar pro can help you with that

---

### Post by Bofur on 2007-07-30
I use a Microsoft Windows Notebook Optical Mouse 4000(USB) and Ubuntu automatically detected it. So I'd imagine your mouse would work with Ubuntu.

I believe HP releases open source drivers so you should also be good there.

For steam, there are many options, but the two most common are running it through either Cedega or Wine.

Movies work fine on Ubuntu, I prefer VLC Media Player, but there are others.

Good luck!

---

### Post by feistyfirsttimer on 2007-07-30
If you're a complete newbie to Linux, it might be an idea to do what I do - keep Windows on your hard drive and install Ubuntu onto a different partition, thereby making your computer a dual-boot system.

This can be very useful if you're used to the Windows way of doing everything but fancy giving Linux a go.  When you switch on, you'll be presented with a choice of which operating system to log into.  So you can give Ubuntu a really good trial, giving yourself plenty of time to see how good it is - and in the meantime if you need to do something urgently or haven't found a Ubuntu-equivalent for your guitar software or something, you can boot into Windows.

The dual-boot gives you a sense of confidence... you can play with Ubuntu as much as you like without any worries, cos you have the "safety net" of the familiar Windows ready to catch you if you fall.

I installed Ubuntu Feisty next to XP Pro, and now I very rarely boot into the Windows partition - there are just a couple of apps that I haven't found Ubuntu-equivalents for yet.  But that day will come... maybe when I next upgrade my Ubuntu, I'll wipe the XP off my hard disk!

---

### Post by amneziac on 2007-07-31
I think thats the best idea for now, just to see if Ubuntu can run my programs well. But when you partition it, will it make my computer any slower or anything?

I also have a nvidia graphics card and according to many people, ubuntu works great with it :)

---

### Post by splintercellguy on 2007-07-31
Performance will not be degraded by partitioning.

---

### Post by atomkarinca on 2007-07-31
> **amneziac said:**
> 
Guitar Pro 5
Steam
The Movies

i haven't tried guitar pro 5 via wine but finale works so it shouldn't be a problem. there is tuxguitar -more like guitar pro4- but it doesn't have realistic sound engine. so bummer...

steam works like a charm. no problem.

and i haven't had any problems with movies. and i really pushed it. i played mkv and ogm files without a glitch. and never had any problems playing dvd movies using mplayer.

---

