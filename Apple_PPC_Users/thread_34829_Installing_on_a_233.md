---
title: "Installing on a 233"
date: 2005-05-16
forum: Apple PPC Users
---

### Post by SuperNintendoChalmers on 2005-05-16
Okay,

How would I go about installing ubuntu on my dreadfully old, circa 98 bondi blue 233, 4gb  imac? I've read some posts where people talk about difficulty booting ubuntu on a mac from CD. Will I have this problem on this machine?  However, there is a chance, that my cd-drive on that imac is toast. It is very picky on which cd it reads. Are there any non-cd ways to install umbutu? 

I plan on zapping and clearing the entire computer when I come home this summer. It is very slow, and does not see much action aside from email. I would like to set it up so that is a bit faster, more stable, and easier to do the simple things that my parents would like to do. Check email, surf the internet, thats about it. I think I should try Linux, specifically ubuntu on this old imac. If I zap the hard drive, will I lose OS 9, and revert to 8.6? Will ubuntu even work on 8.6?

Can my vision of breathing a new Linux life into an old, but quite dependable machine come to be this summer? How can I make it a reality? 

THanks, sorry for so many question, I do value your opinions.
-pete

---

### Post by Bug on 2005-05-16
Hi Pete,

Your imac is what's called a 'newworld' machine, so it should be able to boot off the CD as long as the CD drive is working. First thing I'd suggest is blowing out the CD with some canned air, it could just be dust. Then, make sure you have a OS 8 or 9 cd laying round (and your drive will read it) because you WILL lose everything on your hard drive if you have not partioned it before installing Linux. Last, and perhaps most important, make sure you've got at least 128mb of ram. Anything smaller and it be too slow to use. 96 may work, but 64 does NOT work well on a machine of that speed.

Good luck, It should bring some life back to that machine. I'm typing this on a Wallstreet powerbook that was a paperweight before I tried linux (and ubuntu specifically) on it, and I use it for just the stuff you asked about (surfing and email). 

Adam

---

### Post by SuperNintendoChalmers on 2005-05-16
Thanks, I'll give it a shot. Where in Brooklyn are you? I will be living in Bay Ridge this summer. What if I didn't want to partition, there is nothing of much importance on that computer anymore. I planned on erasing the disc anyway. Can I use Ubuntu and get rid of Mac OS completely? Is that a smart idea.

---

### Post by pvz on 2005-05-17
It should work fine on your 233mhz IMac. I installed Kubuntu with no problems on mine, with 96 MB memory, which is the absolute minimum I think. Although not a speedmonser, it is quite usable. I just use it as a jukebox, with a 80GB HD in it, but other tasks like mail and webbrowsing should be fine too, even if Firefox can be a bit slow on this machine. If you can get more memory, go for it. You could also opt for a more lightweight windowmanager like IceWM, instead of more resource hungry KDE or Gnome.

---

### Post by Bug on 2005-05-18
You should be able to use yaboot to just use linux, but I haven't played around with it so I'm not much help. I've only got a 'oldworld' powerbook using ubuntu.

I'm in dyker heights btw,

Adam

---

### Post by SuperNintendoChalmers on 2005-05-18
Dyker Heights?

You wouldn't know of any sublets for june-aug would ya? My plans kind of fell though yesterday.

Anyway, This is my plan so far. Juice up that 233 in the mempory dept. Max it out. Come home, erase the disc and start fresh. Pop in the Ubuntu disc and install it, maybe partition the HD to 2gigs Linux, 2gigs OS 9?

 If I get comforable using the Ubuntu, how could I get those 2gigs back from the OS 9? So I'll have four gigs of Linux and zero reminants of the Mac OS. Is that a smart idea?

How would I run a cable conncection through Ubuntu?

---

### Post by Bug on 2005-05-18
Don't know of any but if I hear anything I'll PM you.

I don't think that'll be a problem, but  you can also mount that drive now as another volume in HFS. It's something like mount /dev/hda1 /home/adam/Classic. I did it on my PC to keep my windows parition mounted to share files. Sorry I can't remember the whole command, I'll take a look when I reboot in ubuntu (Anyone know a way to mount a ext3 formatted drive in windows?? or in OS 9?).

The cable connection should just work, I've got Roadrunner and a Linksys router for my network. Ubuntu just picks up the DHCP address from the router which gets it's address from the cable modem. If you don't have a router, plugging the modem into the iMac will work fine. Only catch is if you switch machines with different different MAC addresses, the modem might need to reset or it won't give a valid address. But basically, whatever your doing now should also work in ubuntu. 

Adam

---

### Post by chascon on 2005-05-18
Gnome and especially KDE on your computer is asking for trouble.  Try a custom install with xfce4, it's rather complete and runs on the memory of a browser. 

See:
[https://www.ubuntulinux.org/wiki/LowEndSystemSupport](https://www.ubuntulinux.org/wiki/LowEndSystemSupport)
and 
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by chascon on 2005-05-18
[QUOTE=][/QUOTE]
 by the way if you don't know don't use xdm, it's awefull.  Instead use gdm. I also installed xfce4 without the bug reported for icewm. You really only need 
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) to minimize processing power to full benefit.

---

### Post by Len on 2005-05-18
2 GB Ubuntu/2GB OS 9 is a good idea. If you like Ubuntu, you can format the OS 9 partition and use it under Ubuntu as your documents disk, Linux can mount the partition in a directory (for example in '/home' which causes all data in that folder being written on the other partition).

128 MB RAM really is the minimum, even if you tweak Ubuntu for low memory machines. 64 or 96 MB is possible, but way too slow. Memory for that iMac luckily is cheap. If you already have a 64 MB memory chip installed, don't replace it but take out the processor board to find a hidden 32 MB chip to replace.

---

### Post by SuperNintendoChalmers on 2005-05-18
Okay, I should be studying. But I checked this thread out and felt compelled to write back. What the hell are:
KDE
xfce4
xdm, it's awefull.
gdm. 
icewm.

---

### Post by Ptero-4 on 2005-05-18
[QUOTE=SuperNintendoChalmers]Okay, I should be studying. But I checked this thread out and felt compelled to write back. What the hell are:
KDE
xfce4
xdm, it's awefull.
gdm. 
icewm.[/QUOTE]
 KDE , xfce4 (and gnome) are desktops, KDE looks like windows, xfce4 looks like Mac OS X w/o the top bar and gnome looks like Mac OS 9/X. KDE and GNOME are heavy and use a lot of RAM, HD and CPU (your Mac doesn't have enough of those three to run any of those desktops), xfce4 uses less RAM, HD and CPU than KDE/GNOME but is a bit harder to learn and a lot awfull looking. xdm is the default graphical login tool (a login tool is what makes the username/password box appear on the screen), but is ugly and hard to use. gdm is the gnome login tool, it's easier and more intuitive, but installs a bunch of gnome stuff with it. and icewm is a window manager (a window manager gives you the window titlebar, buttons and borders, and maybe a launcher or menu, but lacks of a filemanager, terminal app, web browser, games, office apps, etc) that gives you a windows taskbar with a start menu and uses less RAM, HD and CPU than xfce4.

Hope this answers your doubts.

---

### Post by SuperNintendoChalmers on 2005-05-21
[QUOTE=Ptero-4]KDE , xfce4 (and gnome) are desktops, KDE looks like windows, xfce4 looks like Mac OS X w/o the top bar and gnome looks like Mac OS 9/X. KDE and GNOME are heavy and use a lot of RAM, HD and CPU (your Mac doesn't have enough of those three to run any of those desktops), xfce4 uses less RAM, HD and CPU than KDE/GNOME but is a bit harder to learn and a lot awfull looking. xdm is the default graphical login tool (a login tool is what makes the username/password box appear on the screen), but is ugly and hard to use. gdm is the gnome login tool, it's easier and more intuitive, but installs a bunch of gnome stuff with it. and icewm is a window manager (a window manager gives you the window titlebar, buttons and borders, and maybe a launcher or menu, but lacks of a filemanager, terminal app, web browser, games, office apps, etc) that gives you a windows taskbar with a start menu and uses less RAM, HD and CPU than xfce4.

Hope this answers your doubts.[/QUOTE]

Well, it just seemed to raise more doubts. So, do you mean that a 233 imac with max memory would still not have what it takes to run Ubuntu with a GNOME?

---

### Post by Rxke on 2005-05-21
stuffed with a decent amount of memory, it should run ok. Not superfast, but ok. Diskspace should be sufficient, esp. if you'll run Ubuntu-only.

I use a 350MHz G3 ( though with 384Mb) and it runs fine. Gnome, KDE, XFce4... All living together heehee...

XFce4 isn`t ugly looking, IMO, you can choose pretty nice themes, and esp. if you come from OS9, it`l look prettier than what yo used to. You can even use some pretty convincing pseudo OSX themes!

BTW: fitting memory into a rev A iMac isn`t really simple, if you're not the screwdriver-wielding-at every-electronic-aplliance type of guy, be sure to download a servicemanual somewhere and have a look at it before deciding to spill its guts!

---

### Post by wvslkr on 2005-05-21
I would suggest trying it and see how you like it.

I'm not using a mac, but an old P233 with 192meg of ram. I use both Gnome and
KDE. It is no speed demon by any means but I am quite happy with it.

I use Konqueror or Opera for web browsing.  Either is faster than Firefox on this machine.

Most programs take a bit longer to load, but run acceptably after loading.  Depending
on patience threshold. :)

Note that if you have one of the heavier DE's installed, you can use one of the lighter
window managers and still use any of the applications installed.  Just frees a bit of memory. 

In short.  Go for it.  Nothing to lose but a little time. :)

---

### Post by Xanf on 2005-05-23
I use a 350 MHz P-II box with 128 Mb RAM, 4Gb HDD, ATI Mach64 with 4Mb v-card.
Dual boot with W98 (very well tuneed, really).
Installed both XFCE and GNOME, removed O-Office and installed Abiword instead.
First load of Gnome is slow, but when loaded - not bad, comparable to W98 on the same PC. Usage of the swap partition is much less aggressive than in Win. XFCE is much more responsive in terms of the interface - so I use it more often. Have plans to maybe remove Gnome at all (if/when become low of disk space :-) ). XFCE seems to win my preferences after they offer a better file manager.

From the web-browser point of view - I tried FF 1.0.4, Mozilla 1.7.6 suite and Opera 8.
FF is the SLOWEST in my experience. Mozilla - is almost twice better. Opera - is a WAY better!
It's not so slow in terms of loading and starting rendering the pages (depends more on the connection - and is almost the same for all in my experience, since I|ve got ADSL), but it's extremely slow in switching between the tabs, especially if the tabs contain complicated pages with Jscript, flash, etc. 
E.g. I open 4 tabs with CNN.com, Gmail, dpreview.com and ebay.com - and start switching between them in any order.
In simple terms - it goes like "click - wait one, two - got rendered" in FF.
In Mozilla  - like "click - one.., - got rendered".
In Opera  - like "click - o! - got rendered".
What's interesting - this problem of sluggish FF happens only under Linux. In W98 on that box FF is undistinguishably fast from other browsers (I compared with all IE, Mozilla and Opera on W98).
So I think it's a problem of how the rendering and tabs switching done in FF/Mozilla under Linux.

All in all - I was really very impressed with Ubuntu on that old box - it became normally useful piece of HW. And much more responsive than XP on the same HW with comparable set of applications, bells and whistles. All the progs require the same time to start as comparable apps on Win98 - but after start work more responsive and fine.
Kudos, Ubuntu!

So, in your case - I'd really recommend to give Ubuntu a try.

---

### Post by kostkon on 2005-05-23
I've installed Ubuntu on a Pentium MMX 200MHz with 128MB RAM, an archaic S3 Vision968 graphics card, 10GB, 3GB hard disks and I am impressed with the result!

I use Gnome and it is far more responsive and fast that I've anticipated. After the login Gnome loads very fast. The whole OS is incredibly responsive even with Gnome and if you think, all these happen on a P1 200MHz!!

Apps load fast enough and are very responsive. The only bad thing actually is Firefox where I have the same problems as mentioned before. I don't know why this is happening with firefox in Linux. When I was using Windows ME, Firefox was one of the fastest apps in the OS, not the slowest!!

But generally, compared with Windows ME, Ubuntu is more responsive, fast and of course light years more stable. The most important, I run a bleeding edge technology OS on a very old PC; the PC becomes useful again, like new! You could not do that using windows.

I know that I could get more speed using another window manager like XFCE, but for the time I'm even satisfied with Gnome. Maybe this sounds a little stupid or even mazochistic, but it' s a sensible truth!!

In the past I was dual booting Windows and Mandrake 9.0. Mandrake 9.0 was an absolute distaster even when I was using WindowMaker. Gnome 2.6 was out of reach of course! But then I found Ubuntu. At first I was thinking: 'Hmmmm I don't think I'll gain anything, it has also an 2.6.x kernel (Mandrake 9.0 had 2.4.x), it will be way out more heavy."

But I took the risk and I was utterly impressed. I use only Ubuntu now. Gnome 2.10 is in another world compared with Gnome 2.6, it is far more optimised.

---

### Post by eric71 on 2005-05-24
[QUOTE=chascon]by the way if you don't know don't use xdm, it's awefull.  Instead use gdm. 
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html) to minimize processing power to full benefit.[/QUOTE]
I've removed all of gnome a few times, as well as GDM in an effor to get a lean and mean XFCE system with no Gnome or KDE libraries (or as few as possible).  I tried XDM and it was awful, but than I discovered WDM in the Ubuntu repositories.  Much lighter than GDM, but much nicer than XDM.  I highly recommend it for anyone wanting an XFCE only system on old hardware.

---

### Post by Rxke on 2005-05-24
heehee...

you know what's also great about Ubuntu and its community?

Here we are, PC and Mac users, merrily posting in the same thread, exchanging experiences, and I've yet to see the first 'my system's better than yours' nonsense! Brilliant.

Actually, I used to be a die hard user of Mac hardware, mainly old stuff (G3's) but now I'm considering buying/skipdiving an old pc, to see how ubuntu compares to Ubuntu on a PPC architecture. PPC has lack of some stuff, like Skype, which forces me to keep dual-booting... reading here how well it works on 'obsolete' hardware makes me happy.

BTW: any of you people tried KDE on a low-spec machine?

---

### Post by kostkon on 2005-05-24
[QUOTE=Rxke]heehee...

you know what's also great about Ubuntu and its community?

Here we are, PC and Mac users, merrily posting in the same thread, exchanging experiences, and I've yet to see the first 'my system's better than yours' nonsense! Brilliant.[/QUOTE]

That's a fact!! I haven't thought about this. Thank you for pointing it out! Very good thought!!

[QUOTE=Rxke]BTW: any of you people tried KDE on a low-spec machine?[/QUOTE]

I have seen some posts here where people are saying that KDE is actually faster than Gnome! I always had the impression that Gnome is faster that's why I'm using it. But I don't know. 

The only way to find out is to test them both. I haven't done that because I think that a second big window manager will eat a lot of space. I am OK with Gnome right now. I always prefer Gnome apps from their KDE equivalents (like Anjuta instead of KDevelop etc.) just to avoid to install the KDE libs. It's only a misery thing of me, I actually think KDE is great and back in my mind I always doubt that Gnome is faster!

But I recommend if you have a sensible amount of space have them both. Nevertheless, some people decide to stick with only one window manager (like me).

---

### Post by kahlil88 on 2005-11-25
I installed Ubuntu 4.10 on an iMac 233, but it doesn't find the modem, ethernet and a bunch of other things. Does Ubuntu 5 have drivers for these?

---

