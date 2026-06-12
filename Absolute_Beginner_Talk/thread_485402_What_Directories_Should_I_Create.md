---
title: "What Directories Should I Create?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-06-26
I may be wrong, but it seems Ubuntu/Linux gives you free reign as to what directories an application should be installed to (as opposed to WIndows, which typically goes to a default path and folder.) 

What typical directory structures do you create? Where should I install a new application to? For example, under bin, or usr, etc? 

Thanks for your help.

---

### Post by KIAaze on 2007-06-26
Generally, applications always get installed in a bin directory.
But I also still don't understand which one is for what:
/bin
/usr/bin
/usr/local/bin

I think /bin is for system administration tools, while the /usr/bin and /usr/local/bin are for general user apps.

Why don't you just use the default locations, i.e either just install the packages or use ./configure without prefix?

I read an article about the debian filesystem somewhere. Trying to find it now...

---

### Post by FleetAdmiral74 on 2007-06-26
I use synaptic and let it do all the work. I don't set anything myself, for fear Synaptic will stop working for that package. And I really like how it tracks everything for you, so I keep it simple.

---

### Post by Rocket2DMn on 2007-06-26
As KIAaze said, those are the typical directories.  If you are extracting precompiled stuff, you can put it in something like /usr/bin or /usr/local/bin - this pretty much follows standard.  In reality, you can install anywhere, but it just creates confusion later.  In general, you should let program managers like apt-get and synaptic do it for you (ie install from repositories)

---

### Post by charles.g.moore on 2007-06-26
If you are installing things from source, you could do like I do.  I have a folder in my home folder named applications, within that folder I have folders named for each of the applications i installed from source.

I do all of my unzipping and installation from within the respective directory, once you install a program linux automatically adds the files into /usr, /usr/bin, ,or wherever it needs to.

Just as a side note I have come across applications in the repo's that are not up to date and sometimes just plain old.

Aside from upgrades when i want to install an application i always google that app, find the site and make sure I am getting the most recent build.  %70 of the time i get stuff from the repo's but 30% is from source...

---

### Post by dpbaker99 on 2007-06-26
You seem to be as green as I am. I'm contemplating making the switch and loaded Feisty on a spare machine. I still can't decide if I'm ready to 'pull the trigger' or not. I REALLY don't want to go to Vista. I'm preparing to build a new machine and will probaly put Feisty on that one. Until then...???? Your thoughts?

---

### Post by Sleestack on 2007-06-26
Thanks for your help, everyone!

---

### Post by charles.g.moore on 2007-06-26
To tell the truth it is cool to install from source cause you feel like you are doing something that is kinda "geeky"
rather than just letting the GUI do it for you...

---

### Post by charles.g.moore on 2007-06-26
> **dpbaker99 said:**
> You seem to be as green as I am. I'm contemplating making the switch and loaded Feisty on a spare machine. I still can't decide if I'm ready to 'pull the trigger' or not. I REALLY don't want to go to Vista. I'm preparing to build a new machine and will probaly put Feisty on that one. Until then...???? Your thoughts?

If you are going to build your system make sure to check for hardware compatibility with Linux.

I still use Dapper 6.06 the only reason is because it will be supported until 2009.  You might want to think about using Dapper, getting it up, running, and installed.  I like the long term support and you can always upgrade when you feel "froggy"

The upgrades will be good experience for you also...

Just my opinion

---

### Post by dpbaker99 on 2007-06-26
My biggest concern... am I geek enough? Geek, certainly, but geek enough?

---

### Post by dpbaker99 on 2007-06-26
Hardware compatibility? Such as?

---

### Post by charles.g.moore on 2007-06-26
> **dpbaker99 said:**
> Hardware compatibility? Such as?

For sure you should get a compatible Video Card, with Nvidia it is hard to go wrong.
When I say hardware compatibility I really mean drivers...

For sure though Video card, 64bit vs 32bit system my laptop is a dual core 64bit processor but I am running the 32bit version of dapper because many applications and 'tweaks' are not available in the 64bit OS.

Don't fret i have some packages installed that "supposedly" maximize my 32bit OS on my 64bit sys but who knows???

If you were thinking wireless you should definitely check into supported wireless cards...

you can search the forums for a hardware compatibility list that is pretty extensive but a bit hard to read...

---

### Post by Nekiruhs on 2007-06-26
I find this easy too. Just create a bin folder in your Home folder. Theres a special file in your home folder like .bashrc or .profile or .bash_profile. Well a line in one of those adds the ~/bin to your path. Meanong. If you install a program to ~/Apps/Music/Songbird then to run it you type ~/Apps/Songbird/EXECUTABLENAME, well anything in /bin /usr/bin or ~/bin will be executable just by typing the name, like say I put a porgram called songbird in ~/bin. Instead of typing the full address, I could just type songbird. Also its easier to install programs there because you don't need root permission to write to ~/bin

---

### Post by dpbaker99 on 2007-06-26
i'm only looking to do standard stuff. Lots of photo editing. Can I use Photoshop? Graphic card is important, thanks for the Nvidea tip.

---

### Post by KIAaze on 2007-06-26
_First of all concerning the original post:_
I finally found the 2 pages I was searching for:
[http://oreilly.com/catalog/debian/chapter/book/]("http://oreilly.com/catalog/debian/chapter/book/") (Appendix A&B)
[http://www.debian.org/doc/FAQ/index.en.html#contents]("http://www.debian.org/doc/FAQ/index.en.html#contents")

Others found while searching:
[http://www.linuxnovice.org/main_focus.php3?VIEW=VIEW&t_id=126]("http://www.linuxnovice.org/main_focus.php3?VIEW=VIEW&t_id=126")
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html")
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

And maybe this might interest you if you are curious or don't like the current filesystem:
[http://www.gobolinux.org/?page=at_a_glance]("http://www.gobolinux.org/?page=at_a_glance")

_And now for dpbaker99:_
> **dpbaker99 said:**
> My biggest concern... am I geek enough? Geek, certainly, but geek enough?

Once you've solved all your hardware problems (and hopefully, you'll have none by choosing the right hardware), you should be able to use Ubuntu just like Windows, i.e: without ever using the command-line. ;)

Unless of course, you want to special stuff like dual-screen setup, try out the latest bleeding edge technology like compiz-fusion, use Windows apps through Wine, use VirtualBox to use multiple OSes without rebooting, etc...
But even in those cases, you can mostly just copy/paste command-lines from the net and press enter, so it's not that hard.

If you don't feel ready, spend some time dual-booting.
And you can always dual-boot forever if you want. ^^
I still dual-boot after two years. I have a legal copy of XP which I can't return since I already used it, so why shouldn't I use it? All I know is that for my next PC, I probably won't have that possibility (except illegally...). :p

> Hardware compatibility? Such as?
Such as a Wifi card with an Atheros chipset. Worked perfectly for me. :)
Or the Philips ToUCam Pro II, which I can guarantee works with GNU/Linux.
I also bought a Logitech Quickcam messenger for my mother, which apparently works under GNU/Linux, but I never managed to make the driver work and since my mother uses Windows...
The Dell 720 Printer also worked for me, but I only tried it with black&white text...

For other things, google on the internet and check these sites:
[http://tldp.org/HOWTO/Hardware-HOWTO/]("http://tldp.org/HOWTO/Hardware-HOWTO/")
[http://www.dohickey-project.com/]("http://www.dohickey-project.com/")
[http://www.linux-drivers.org/]("http://www.linuxcompatible.org/compatibility.html")
[http://www.linux.org/hardware/]("http://www.linuxcompatible.org/compatibility.html")
[http://www.linuxcompatible.org/compatibility.html]("http://www.linuxcompatible.org/compatibility.html")
Webcams:[http://wiki.kdenews.org/tiki-index.php?page=Kopete+Webcam+Support]("http://wiki.kdenews.org/tiki-index.php?page=Kopete+Webcam+Support")

And feel free to ask on the forums to be sure.

Edit:
_First of all concerning the original post:_
I finally found the 2 pages I was searching for:
[http://oreilly.com/catalog/debian/chapter/book/]("http://oreilly.com/catalog/debian/chapter/book/") (Appendix A&B)
[http://www.debian.org/doc/FAQ/index.en.html#contents]("http://www.debian.org/doc/FAQ/index.en.html#contents")

Others found while searching:
[http://www.linuxnovice.org/main_focus.php3?VIEW=VIEW&t_id=126]("http://www.linuxnovice.org/main_focus.php3?VIEW=VIEW&t_id=126")
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html")

And maybe this might interest you if you are curious or don't like the current filesystem:
[http://www.gobolinux.org/?page=at_a_glance]("http://www.gobolinux.org/?page=at_a_glance")

_And now for dpbaker99:_
> **dpbaker99 said:**
> My biggest concern... am I geek enough? Geek, certainly, but geek enough?

Once you've solved all your hardware problems (and hopefully, you'll have none by choosing the right hardware), you should be able to use Ubuntu just like Windows, i.e: without ever using the command-line. ;)

Unless of course, you want to special stuff like dual-screen setup, try out the latest bleeding edge technology like compiz-fusion, use Windows apps through Wine, use VirtualBox to use multiple OSes without rebooting, etc...
But even in those cases, you can mostly just copy/paste command-lines from the net and press enter, so it's not that hard.

If you don't feel ready, spend some time dual-booting.
And you can always dual-boot forever if you want. ^^
I still dual-boot after two years. I have a legal copy of XP which I can't return since I already used it, so why shouldn't I use it? All I know is that for my next PC, I probably won't have that possibility (except illegally...). :p

> Hardware compatibility? Such as?
Such as a Wifi card with an Atheros chipset. Worked perfectly for me. :)
Or the Philips ToUCam Pro II, which I can guarantee works with GNU/Linux.
I also bought a Logitech Quickcam messenger for my mother, which apparently works under GNU/Linux, but I never managed to make the driver work and since my mother uses Windows...
The Dell 720 Printer also worked for me, but I only tried it with black&white text...

For other things, google on the internet and check these sites:
[http://tldp.org/HOWTO/Hardware-HOWTO/]("http://tldp.org/HOWTO/Hardware-HOWTO/")
[http://www.dohickey-project.com/]("http://www.dohickey-project.com/")
[http://www.linux-drivers.org/]("http://www.linuxcompatible.org/compatibility.html")
[http://www.linux.org/hardware/]("http://www.linuxcompatible.org/compatibility.html")
[http://www.linuxcompatible.org/compatibility.html]("http://www.linuxcompatible.org/compatibility.html")
Webcams:[http://wiki.kdenews.org/tiki-index.php?page=Kopete+Webcam+Support]("http://wiki.kdenews.org/tiki-index.php?page=Kopete+Webcam+Support")

And feel free to ask on the forums to be sure.

Edit:
> i'm only looking to do standard stuff. Lots of photo editing. Can I use Photoshop? Graphic card is important, thanks for the Nvidia tip.
For editing pictures:
[the Gimp]("http://www.gimp.org/") (GNU Image Manipulation Program)
[Gimpshop]("http://gimpshopdotnet.blogspot.com/")
[Krita]("http://www.koffice.org/krita/")

Or use the non-Free photoshop under Ubuntu using crossover office...:
[http://www.desktoplinux.com/articles/AT7770280571.html]("http://www.desktoplinux.com/articles/AT7770280571.html")

Other non-Free:
[http://www.kanzelsberger.com/pixel/]("http://www.kanzelsberger.com/pixel/")

Also, next time, please start a new thread if you have another question. ;)

---

