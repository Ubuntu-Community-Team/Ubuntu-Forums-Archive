---
title: "Will ANYTHING run on this?!"
date: 2008-06-20
forum: Apple Hardware Users
---

### Post by BlueBell1142 on 2008-06-20
Hi all, I've got an original iMac G3 that I want to put Xubuntu on, since I've heard it runs better on slower machines. (this is the 233 MHz version.)

The problem is, I only have the stock 32 MB of RAM that came with the machine. Mac OS 8.6 even runs slow on it, so I thought some form of Xubuntu could help me.

My question is, is there any version of Xubuntu (or just any kind if Linux for that matter) that has a GUI already included, that runs on a PPC machine and will run on 32 MB of RAM?

Thanks in advance!

---

### Post by oswaldkelso on 2008-06-20
Not xubuntu 8.04. not with X and any speed. ebay is your friend RAM RAM and more RAM.

---

### Post by BlueBell1142 on 2008-06-20
> **oswaldkelso said:**
> Not xubuntu 8.04. not with X and any speed. ebay is your friend RAM RAM and more RAM.

Well it doesn't have to be 8.04 it can be the first version for all I care. It doesn't even have to be Xubuntu, that's just my preference. I just want something that runs.

One day I will get more RAM, but I'm looking for a short term solution.

---

### Post by kerry_s on 2008-06-20
give debian a try:
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso)

i have my doubts though, anything that slow, with that little ram, i would go custom on. build it from the base up with light alternatives.
net installer, if you want to go that way:
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-netinst.iso)

---

### Post by stream303 on 2008-06-21
32mb is going to be tough, although you may want to look at the following for building up a very light install - it works for Intel as well as PPC, so don't let the intro fool you.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Personally, I'd try to install Feisty 7.04 "server", and when prompted to install server apps, just uncheck them.  From there, you can use the instructions above to get a lightweight X and a couple of xterms going for cli use.  Again, 32mb is going to be tough, although I did get the Dillo browser working ok once on 24mb.

You can grab Feisty server for ppc here:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

It still has some support life left, but then again, so does Dapper, 6.06x.  Your choice obviously for any others as well, including Debian, etc.

Although a ram upgrade would be the first thing I'd do, you could approach this as a very cool project to see how using the cli can overcome such obstacles. :)  With only 32mb I would definitely not install a gui logon manager, or if you do maybe just xdm, and even a super lightweight window manager such as LWM - my fav for slim, yet somewhat modern.

Getting way off track, so I'll reel myself in.  You have to approach a low-mem box with a slightly different outlook and they can be a blast trying to eek the most performance out of them.

---

### Post by joninkrakow on 2008-06-21
I just recently read about a cli window manager, of sorts. I forget what it's called, and I'm hoping somebody here can remember (is it curses related?) But it basically, is a multi-window text-based interface, using cli tools. BTW, you can do a lot just from the command line, and without a gui. There are email apps, RSS readers, web browsers--the works. All have some sort of interface, not just a blank screen. In fact, it is even possible to watch movies--though I tend to doubt that 32 meg of RAM would be sufficient. Also, I don't know how many of these will work on PPC, but it's worth investigating this. I have thought about trying out a cli interface just for nostalgia and kicks (started on DOS 3.11, back in the 80s, when there was no such thing as a gui, except for the Mac--no Windows, etc.). I can't find the page I was reading now, but when I find it, I'll come back and post it here. I'm sure I downloaded a tutorial for doing cli stuff, which is what I'm looking for.

-Jon

---

### Post by marshag63 on 2008-06-21
BlueBell1142,
What kind of things are wanting to do on this Mac - i.e., surf the net, email, listen to music?  With such little ram it will be very tough - I would follow stream303's suggestion.  You would be amazed what you can do via cli.

I can surf the net via links2 or even netrick, chat via CenterICQ, listen to CDs (via tcd), listen to mp3s/ogg saved on the harddrive via mocp, rip CD's to ogg or MP3 via ripit or abcde, simple text editing via vi (though there are lots of console editors out there), use Midnight Commander to find files anywhere on my computer to edit/copy them, and email with Elmo or Mutt.  I'm sure there's lots more that can be done, but still learning.  I too have experienced the low ram situation - once got Damn Small Linux running on a very old Compaq running 100 MHz with 16 MB ram (but X environment was quite a strain).  

Dive in!  By the way, Screen is wild little program to give you multiple consoles - you can split them and stuff.   If there is anything in particular you are needing to do, I am sure someone here can suggest a way to do it via cli until you can get more ram.

I wish you the best - keep us updated!

marshag63

---

### Post by joninkrakow on 2008-06-23
A few days ago, I said:

> **joninkrakow said:**
> I just recently read about a cli window manager, of sorts. I forget what it's called...<snip> ...I can't find the page I was reading now, but when I find it, I'll come back and post it here.
-Jon

Well, I finally found the page. Here it is:
[http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/](http://www.terminally-incoherent.com/blog/2007/05/21/a-day-without-x/)

I hope this helps, but I suspect it would be something worth trying.

-Jon

---

### Post by jtappin on 2008-06-23
> **kerry_s said:**
> give debian a try:
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-xfce-CD-1.iso)

i have my doubts though, anything that slow, with that little ram, i would go custom on. build it from the base up with light alternatives.
net installer, if you want to go that way:
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-netinst.iso)
I'm pretty sure that with only 32Mb even XCFE is not an option as I recall using Debian Sarge on an Intel box PII 266 with 64Mb and XFCE was runnable then but only just.

---

### Post by joninkrakow on 2008-06-23
> **jtappin said:**
> I'm pretty sure that with only 32Mb even XCFE is not an option as I recall using Debian Sarge on an Intel box PII 266 with 64Mb and XFCE was runnable then but only just.

I can't imagine any desktop environment working in 32 megs of ram--I can't even see LXDE running under 32 megs of ram. At best, one of the simpler window managers would work. Maybe jwm? It's snappy on my 128mb pcs. icewm always feels snappy, even on my Mac running under the X11 app (which generally runs slower than straight under Linux). But there are others, too. 

-Jon

---

### Post by blazercist on 2008-06-23
DSL is my standby answer, damn small linux, the iso is less than 50Mb itself I think it will run even with only 32Mb RAM.

from the damnsmalllinux.org website

"Run light enough to power a 486DX with 16MB of Ram"

---

### Post by joninkrakow on 2008-06-23
> **blazercist said:**
> DSL is my standby answer, damn small linux, the iso is less than 50Mb itself I think it will run even with only 32Mb RAM.

from the damnsmalllinux.org website

"Run light enough to power a 486DX with 16MB of Ram"

And there's the rub. This is an ancient PowerPC iMac, not a 486. :-( None of these ultra-lightweight distros will run on this guy.

I have been looking for, and just found a good link for installing a super-lightweight Ubuntu.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal). In fact, there are several articles on this site that would help, and may work on this device. It's definitely worth giving it a whirl.

-Jon

---

### Post by oswaldkelso on 2008-06-23
DSL wont run on ppc :( 

some reading for you.

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

as you can see no really light distro fo ppc, with 32 mb you really need to run without X

If you really want X you will need and older kernel 2.4 Debian sarge or the ubuntu equivelent. Other distros that may be made lighter on ppc are gentoo or slackintosh.

Some ideas though with etch, but the info is good and the concepts can be carried across.

[http://forums.debian.net/viewtopic.php?t=13828](http://forums.debian.net/viewtopic.php?t=13828)

[http://forums.debian.net/viewtopic.php?t=5484](http://forums.debian.net/viewtopic.php?t=5484)

TBH the horse died a long time ago and the only thing that will bring it back is Ram!

---

### Post by durand on 2008-06-23
I think the problem here is the fact that its PPC arch. I was going to suggest deli linux but its x86 only :(

---

### Post by blazercist on 2008-06-24
ahh I forgot the old macs were PPCs, good luck in your search.

---

### Post by Phonan on 2008-06-25
It seems to me too that your best bet is to do a CLI install and then get a lightweight GUI installed from there. I doubt there are really any pre-available distros out there that will run on such a system. If you choose to build from the core up, there's plenty of help out there.

---

### Post by brons2 on 2008-06-25
> **joninkrakow said:**
> I can't imagine any desktop environment working in 32 megs of ram

Windows95?  ;-)

(j/k)

---

### Post by bcschmerker on 2008-06-25
I had some experience with an even earlier Apple Power Macintosh under MacOS 8.6.  As I understand things, with most LinUX distros you're looking at cross-compilation to PowerPC from source.  Exactly what type of memory module does your system take?  It may help me determine whether an XUbuntu install is going to be worthwhile.

---

### Post by stream303 on 2008-06-25
32mb with Xubuntu - even with special compiling?

I have to side with Oswaldkelso on this - the ends may not justify the means with 32mb unless you absolutely have to have *something* running or don't mind the cli for most of your work.

Even if a lightweight desktop could be made to work, any gui application run with it that is not feather-weight, would bring the system to it's knees.

I suppose one could go the Gentoo route, strip the kernel of everything, but in the end, you'd *still* be limited to the cli - gui apps are just going to be too big or end up swapping endlessly, so it would just end up being a technical exercise.

What is really amazing is that a thread that is only about 4 days old seems to have about 100 reads a day!  Maybe there are more low-mem users lurking out there than we thought! :)

---

### Post by blampars on 2008-06-25
i just checked on my g3 ibook and i can run a stock JWM with conky at startup on about 24mb ram usage. this still doesnt leave you enough ram to run kazehakase web browser (mines running on about 17.5mb ram right now). there may be something lighter than that i'm not sure..

as everyone else says, you're pretty much limited to cli unless you get a bit more ram ;)

---

### Post by owlgorithm on 2008-06-27
what about enlightenment? according to their [[COLOR="Blue"]website[/COLOR]]("http://www.enlightenment.org/p.php?p=about/e17&l=en"), it can be run on machines with 64 megs of ram.

and, blackbox requires even less, according to their [[COLOR="Blue"]website[/COLOR]]("http://blackboxwm.sourceforge.net/BlackboxPerformance").

---

### Post by fn_tool on 2008-07-08
I've had some success in using a USB Thumb drive to get through the partitioner.  I tried this on an iMac G3, 266, 64Meg Ram, 6Gig HD.

I think your real challenge will be actually trying to do ANYTHING with only 32Meg Ram once you have ubuntu installed.

1)  Boot & Run off the CD (if you don't have one, burn it)
2)  Once the desktop is up and the machine is finished booting, simply plug in a USB Thumb Drive into an avialable USB port.  ubuntu will recognize the thumb drive automatically.
3)  Open a Terminal Window and login as root (be careful!) by typing: "sudo su -"    gets you in as root (w/o dbl quotes)
4)  Type: "mount" to see where your thumb drive is mounted.
5)  Now, you need to make a swap file on the Thumb Drive:
type: " cd /media/disk"  where /media/disk is where your thumb drive is mounted.
6)  Type "dd if=/dev/zero of=swap count=300"  this creates a 300Meg file on the USB drive.
7)  Type "mkswap swap" to make the file a swap file
8)  Type " swapon swap" to make the swap file on the thumb drive activate.

ubuntu will now be able to finish it's install on the machine, HOWEVER, I highly doubt 32 Meg will run anything, the 64Meg runs FireFox, Open Office etc, but it is kinda slow.

Also, at the end of the exercise, you will need to track down all the current multi-media plug-ins for the powerpc + browser in order to surf the current web.

Personally, if you are inclined to, upgrade the RAM in the G3, and have some fun with it.

---

### Post by AlyCat on 2008-07-08
I installed Debian Sarge on my old iMac 266MHz, but it was so slow it was practically unusable. So I bought another 96 megs of RAM on ebay and installed System 8.6 over it. It hardly ever gives me any problems, but I realize a lot of people hate classic :/

There aren't any new multimedia codecs of course, but you get all the proprietary codecs of the day, including Flash 7 and Audion media player supports classic.

---

### Post by owlgorithm on 2008-07-08
I have literally bags full of working memory modules for Mac because I used to salvage the machines my university threw out. Anyway, I'm about to dispose of a lot of it because it takes up so much space. I am pretty sure I have [[COLOR="DarkOrchid"]what you need[/COLOR]]("http://lowendmac.com/imacs/rev-c-imac-g3-266-mhz.html"), but I'll check if you're interested.

If I have some, I can send it to you free of charge (and I don't care about postage, either). I know that memory costs way more than it should because no one stocks it anymore. If you're curious why I'd suggest this, it's because your iMac's shortage of memory is the obvious holdup here, and also because the iMacs have a special place in my heart -- I first learned Ubuntu using a purple one :-)

UPDATE: I do not have this kind of memory after all. I just looked, and all the 144-pin modules I have are DDR, but the iMac 266 can't use that. I also looked in my own iMac, but it's slightly newer and uses 168-pin modules. I apologize to have spoken without checking first -- I got excited about helping someone with my stockpiled parts.

---

