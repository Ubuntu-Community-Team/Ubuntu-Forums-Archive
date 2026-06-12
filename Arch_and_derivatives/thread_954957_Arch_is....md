---
title: "Arch is..."
date: 2008-10-21
forum: Arch and derivatives
---

### Post by OutOfReach on 2008-10-21
So yesterday I wanted to try out Arch since I've heard a lot of talk about it. I downloaded the core ISO and booted up from it and I got thrown into a console, I logged in as root and began the installation process. Installation wasn't as hard as I've heard it was. The only part I struggled with is setting up my internet, the installer didn't set it up right but eventually I remembered some commands to get my wireless up and running. After the installation I rebooted into my new Arch system. :) 
I copied and pasted the begginer's guide to a text file in the arch partition (from Ubuntu) so I was all set to setup Arch. The next 2/3 hours I spent setting up config files, installing X and Openbox and applications to get me on my feet. Before installing X I installed alsa-utils and found that it threw an interesting error, but after installing X that error was gone and I could listen to sound, nice. 
I was absolutely amazed as to how many daemons/tasks it initialized, it was so minimal (which I like!). 

In conclusion, Arch is extremely nice and I found that Arch is for me. I found it somewhat 'fun' setting up and configuring my Arch. 

You've found yourselves a new Arch user. :) But I do have a few questions (don't worry nothing big). How can I install Murrina SVN in Arch? I need it because I'm using Shiki-Colors and it needs Murrina SVN to render some things, I know there is a non-Murrina version but I don't really like that version. Thanks. :)

---

### Post by crimesaucer on 2008-10-21
> **OutOfReach said:**
> So yesterday I wanted to try out Arch since I've heard a lot of talk about it. I downloaded the core ISO and booted up from it and I got thrown into a console, I logged in as root and began the installation process. Installation wasn't as hard as I've heard it was. The only part I struggled with is setting up my internet, the installer didn't set it up right but eventually I remembered some commands to get my wireless up and running. After the installation I rebooted into my new Arch system. :) 
I copied and pasted the begginer's guide to a text file in the arch partition (from Ubuntu) so I was all set to setup Arch. The next 2/3 hours I spent setting up config files, installing X and Openbox and applications to get me on my feet. Before installing X I installed alsa-utils and found that it threw an interesting error, but after installing X that error was gone and I could listen to sound, nice. 
I was absolutely amazed as to how many daemons/tasks it initialized, it was so minimal (which I like!). 

In conclusion, Arch is extremely nice and I found that Arch is for me. I found it somewhat 'fun' setting up and configuring my Arch. 

You've found yourselves a new Arch user. :) But I do have a few questions (don't worry nothing big). How can I install Murrina SVN in Arch? I need it because I'm using Shiki-Colors and it needs Murrina SVN to render some things, I know there is a non-Murrina version but I don't really like that version. Thanks. :)

I find Arch is pretty fun to install using the console, I like to use the FTP method because it's much faster for me.


You have to build the murrine-svn from source, there is a PKGBUILD in the AUR: [http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=murrine-svn&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go](http://aur.archlinux.org/packages.php?O=0&L=0&C=0&K=murrine-svn&SeB=nd&SB=n&SO=a&PP=25&do_Search=Go)


I use it, and it works perfectly.


Check out the wiki for AUR and ABS

[http://wiki.archlinux.org/index.php/AUR](http://wiki.archlinux.org/index.php/AUR)
[http://wiki.archlinux.org/index.php/ABS](http://wiki.archlinux.org/index.php/ABS)


..... you will find a lot of packages in the AUR that aren't in the regular repositories.

---

### Post by OutOfReach on 2008-10-21
Hey thanks! That was pretty easy.
While installing my everyday apps I releaized that the repositories have suprisingly up-to-date packages (Geany 0.15, Opera 9.6, etc).
One more quick question, what is the ubuntu-restricted-extras equivalent in Arch? Flash, music/video codecs, etc.

---

### Post by MisfitI38 on 2008-10-21
> **OutOfReach said:**
> 
One more quick question, what is the ubuntu-restricted-extras equivalent in Arch? Flash, music/video codecs, etc.

```
pacman -Sy flashplugin mplayer mplayer-plugin codecs
 libdvdcss
```

---

### Post by chucky chuckaluck on 2008-10-21
[IMG]http://d.imagehost.org/0874/archscr.jpg[/IMG]

the combination of the title and your username threw me off, at first.

i agree, arch is fun to install. it's kind of what i imagine making your own beer would be like.

---

### Post by OutOfReach on 2008-10-21
Lol that is pretty weird.
I am almost done configuring my Arch install. I am glad that I installed Arch because it has also improved my general Linux skills, for example I now know how to manually setup an internet connection, I know how to edit xorg.conf, etc...

[QUOTE=MisfitI38]```
pacman -Sy flashplugin mplayer mplayer-plugin codecs
 libdvdcss
```[/QUOTE]
Thanks. :)

---

### Post by handy on 2008-10-21
Archery really does educate the bowman, err bow-person.

---

### Post by crimesaucer on 2008-10-21
Are you using i686 or x86_64 ?

If you are using x86_64, then I have some other important links for 64bit flash plugin and 64bit openjdk6 icedtea plugin.


If you use i686 then MisfitI38's flashplugin and the regular jre plugin will work for you.

---

### Post by OutOfReach on 2008-10-21
Yes, I'm pure i686.
Would you guys happen to know what package contains HP printer support? And maybe a nice article/tutorial on how to setup a printer in Arch?

---

### Post by handy on 2008-10-22
> **OutOfReach said:**
> Yes, I'm pure i686.
Would you guys happen to know what package contains HP printer support? And maybe a nice article/tutorial on how to setup a printer in Arch?

The [***_CUPS how-to_***]("http://wiki.archlinux.org/index.php/CUPS") is a good place to start, & hopefully finish. :-)

---

### Post by OutOfReach on 2008-10-22
Thanks. I'll get to it tomorrow because I am very tired right now.

---

### Post by SomeGuyDude on 2008-10-22
There are two kinds of people who have used Arch:

1) Those who couldn't get it set up and say it sucks.

2) Those who got it set up and are permanent users now.

I'm willing to bet Arch has the highest retention rate of any distro, if you limit your pool to people who have gotten it working.

---

### Post by handy on 2008-10-22
> **SomeGuyDude said:**
> There are two kinds of people who have used Arch:

1) Those who couldn't get it set up and say it sucks.

2) Those who got it set up and are permanent users now.

I'm willing to bet Arch has the highest retention rate of any distro, if you limit your pool to people who have gotten it working.

You become more intimately acquainted with Arch than most other distro's, & perhaps due to its binary nature as opposed to compiling everything as some do, the intimacy may be a little more appealing. :-)

I spent three or more days battling to get X on a Gentoo install & failed, due to a hardware problem.  I don't think Gentoo sucks though.  I think it is a great distro.  My ISP runs all of their servers on Gentoo with virtual machines on top.

---

### Post by mips on 2008-10-22
> **handy said:**
>   My ISP runs all of their servers on Gentoo with virtual machines on top.

Are they called S&M Internet by any chance? :lolflag:

---

### Post by handy on 2008-10-22
> **mips said:**
> Are they called S&M Internet by any chance? :lolflag:

:lolflag:

No, but I bet they have a lot of identical servers.

---

### Post by OutOfReach on 2008-10-22
Ok, I got my printer (easily) setup thanks to that documentation.
That looks like the last of my questions, any recommendations are welcome. :)

---

### Post by handy on 2008-10-22
> **OutOfReach said:**
> Ok, I got my printer (easily) setup thanks to that documentation.
That looks like the last of my questions, any recommendations are welcome. :)

Did you go through the Arch Wiki [***_Post Installation Tips_***]("http://wiki.archlinux.org/index.php/Post_Installation_Tips")?

It can add some useful polish to the install.

Apart from that, be careful before you do an -Syu , check the Arch home page & the forums to be sure no nasty little bug has managed to get down stream (it has only happened to me once in about 8 months).  Though if you don't, & you do get bit by a bug, you are bound to learn more about Arch than if you didn't get the bite! :lolflag:

Also, it is worth understanding that some times when you do an -Syu .conf files will be affected, the way this happens is pretty cool, in that the files are not overwritten, instead the new files are written into the same directory with a .pacnew suffix.  Now easiest way to deal with this situation is to make a note of the new .pacnew files name & path & then ignore it & just carry on.  

On very rare occasions something will break.  When that happens go through & compare your original .conf with the new .pacnew file. I find the easiest way is by opening two copies of nano, there are other ways & programs like Merge if you run Gnome, or Vim if you know how to use it, that are built for that kind of job. 

Just be careful, if you choose to use the unedited .pacnew file you will loose any changes that you had made to the original, which can certainly be a game breaker.

Apart from that there is nothing I can think of, enjoy, it really is quite a fun distro'.

---

### Post by RiceMonster on 2008-10-23
> **SomeGuyDude said:**
> There are two kinds of people who have used Arch:

1) Those who couldn't get it set up and say it sucks.

2) Those who got it set up and are permanent users now.

I'm willing to bet Arch has the highest retention rate of any distro, if you limit your pool to people who have gotten it working.

Yeah. The first time I installed Arch, I couldn't get anything working right, so in a fit of frustration, I installed Ubuntu (which was a good idea at the time). Then when I got bored of Ubuntu, I decided Arch was the distro I wanted to use, so I tried it again and got it right. Now I'm hooked :D.

---

### Post by heller_barde on 2008-10-23
> **handy said:**
> Apart from that, be careful before you do an -Syu , check the Arch home page & the forums to be sure no nasty little bug has managed to get down stream (it has only happened to me once in about 8 months).  Though if you don't, & you do get bit by a bug, you are bound to learn more about Arch than if you didn't get the bite!
psh. I've been a happy arch user for almost a year now... I never check the wobsite or the news, it's more fun to watch it break on occasion and try to fix it yourself :P you can always go look whether you did it right ;)

nah, you should check the wobsite, but i'm just too lazy

cheers Haller_Berde

---

### Post by handy on 2008-10-23
> **heller_barde said:**
> psh. I've been a happy arch user for almost a year now... I never check the wobsite or the news, it's more fun to watch it break on occasion and try to fix it yourself :P you can always go look whether you did it right ;)

nah, you should check the wobsite, but i'm just too lazy

cheers Haller_Berde

:lolflag:  

Welcome to the Ubuntu forums heller_barde, its good to see you here. :-)

At least after this bug, I now know how to downgrade packages & if I don't keep the the past kernel in my cache I can build a new one with the information that is now a sticky in this forum.  All of that is thanks to the wonderful Arch wiki & forum. :-)

---

### Post by OutOfReach on 2008-10-23
Thanks for the link.
I'm all set (for the time being). But today and yesterday my hard drive started making some weird noises and the system froze for a mili-second, today I was checking my load_cycle_count when I found that at the same time it made those weird noises the load_cycle_count went up by 1. I couldn't find any documentation for solving this in Arch, so I used the Ubuntu fix and it works perfectly. :)

---

### Post by Darkade on 2008-10-25
Arch is the lightest distro I've used, and it's not that hard to configure once you know here everything is. It's superfast! and it does just what I want it to do. 
Just the daemons I need, just the software I need

---

### Post by benerivo on 2008-10-25
I've just got Arch working (after a failed attempt about a year ago). It seemed easier this time round, and i'm impressed with the clean and user controlled installation/setup. I'm not going to say it's easy or hard as it depends entirely on who you are. It seems slightly faster than other distros, although not significantly so. If you want instant speed, then a light desktop environment, such as openbox on any distro will do the trick. I also like the currency of the [packages]("http://distrowatch.com/table.php?distribution=arch"). More and more i get the feeling that all distros are basically the same once you get to know them. For me, it seems that the choice of hardware, desktop environment, and individual packages are important, and that the distro choice is almost insignificant. An example of this is that i could make a youtube video of me doing some work on debian, ubuntu, fedora, mandriva, arch, and each video could be identical. Trying this on significantly different hardware, D.E.'s, and packages, and that's where you notice things. I'm not going to keep arch, but i give it a thumbs up for learning about linux and how it works.

---

### Post by elmer_42 on 2008-10-25
> **heller_barde said:**
> wobsite
I [nearly]("http://xkcd.com/148/") called you on that.
> **RiceMonster said:**
> I couldn't get anything working right, so I installed Ubuntu. When I got bored of Ubuntu, I decided Arch was the distro I wanted to use, so I tried it again. Now I'm hooked :D.
This is almost the exact same thing that happened to me.

---

### Post by chucky chuckaluck on 2008-10-26
i don't understand how someone could not get arch installed. you'd have to have hardware that makes it difficult, is all i can imagine. if not, you either didn't bother to read the guides at all, or you were trying to be too cool in your setup.

---

### Post by elmer_42 on 2008-10-26
When I first tried to install it, the drivers for my WiFi card were rather difficult to deal with. I now use a wireless bridge + ethernet cable, but if I wanted to I could use my WiFi cards; the drivers have come a long way since I initially tried to use them.

And I also didn't follow the Beginner's Guide the first time, while I followed every bit and piece (of course, I modified some things that I *knew* wouldn't hurt) this time. Seriously, it's that good.

---

### Post by SomeGuyDude on 2008-10-26
> **chucky chuckaluck said:**
> i don't understand how someone could not get arch installed. you'd have to have hardware that makes it difficult, is all i can imagine. if not, you either didn't bother to read the guides at all, or you were trying to be too cool in your setup.

Getting the "system" installed is easy.

Getting X/Alsa/WM set up and my wireless? Now that's a completely different monster. You really do need to have the full guide printed out and sitting beside you, and it's easy for a newbie to miss stuff.

---

### Post by Xiong Chiamiov on 2008-10-26
> **OutOfReach said:**
> One more quick question, what is the ubuntu-restricted-extras equivalent in Arch? Flash, music/video codecs, etc.

Yeah, that doesn't really exist...

> **SomeGuyDude said:**
> Getting the "system" installed is easy.

Getting X/Alsa/WM set up and my wireless? Now that's a completely different monster. You really do need to have the full guide printed out and sitting beside you, and it's easy for a newbie to miss stuff.
Or install elinks or its ilk, once you've got your internet working.

In case you haven't, you should install yaourt, which allows you to intergrate the AUR with pacman.  It's pretty awesome.  Pacman-color is also very nice, and I've recently been using [powerpill]("http://bbs.archlinux.org/viewtopic.php?pid=431164").

---

### Post by crimesaucer on 2008-10-26
> **Xiong Chiamiov said:**
> Yeah, that doesn't really exist...

Well, it does, just under a few different names: 

[http://wiki.archlinux.org/index.php/Common_codecs](http://wiki.archlinux.org/index.php/Common_codecs)
[http://wiki.archlinux.org/index.php/Flash_and_Adobe_Acrobat_browser_plugins](http://wiki.archlinux.org/index.php/Flash_and_Adobe_Acrobat_browser_plugins)
[http://wiki.archlinux.org/index.php/DVD](http://wiki.archlinux.org/index.php/DVD)


Since it is i686 and not x86_64..... all you would have to do is install Firefox and your media player of choice (with firefox plugin) then install this for Codecs, flash, java plugin, dvd read/write, and fonts for firefox:



```
pacman -Sy codecs gstreamer0.10-bad gstreamer0.10-ugly gstreamer0.10-ffmpeg gstreamer0.10-ugly-plugins flashplugin jre libdvdread libdvdcss libdvdnav dvd+rw-tools artwiz-fonts ttf-ms-fonts
```

---

### Post by mips on 2008-10-27
> **chucky chuckaluck said:**
> i don't understand how someone could not get arch installed. you'd have to have hardware that makes it difficult, is all i can imagine. if not, you either didn't bother to read the guides at all, or you were trying to be too cool in your setup.

From what I have seen so far it looks like people either cannot read or unwilling to read. All you have to do is follow the Beginners guide step by step. Seen many instances where people are referred back to the guide and then magically it works.

---

### Post by SomeGuyDude on 2008-10-27
> **Xiong Chiamiov said:**
> Yeah, that doesn't really exist...

pacman -S codecs?

> Or install elinks or its ilk, once you've got your internet working.

In case you haven't, you should install yaourt, which allows you to intergrate the AUR with pacman.  It's pretty awesome.  Pacman-color is also very nice, and I've recently been using [powerpill]("http://bbs.archlinux.org/viewtopic.php?pid=431164").

Yaourt is my saviour. I troll the AUR constantly looking for crap to try out.

---

### Post by chucky chuckaluck on 2008-10-27
> **SomeGuyDude said:**
> Getting the "system" installed is easy.

Getting X/Alsa/WM set up and my wireless? Now that's a completely different monster. You really do need to have the full guide printed out and sitting beside you, and it's easy for a newbie to miss stuff.

> **mips said:**
> From what I have seen so far it looks like people either cannot read or unwilling to read. All you have to do is follow the Beginners guide step by step. Seen many instances where people are referred back to the guide and then magically it works.

i'm wondering how many problems are caused by only having one machine available and thus, not having a copy of the guide to use when something goes wrong. i was in that boat and had to use either mrs. chuckaluck's junky old laptop, or a slax cd to get my answers. once you're in though, there are text browsers you can use to get x, etc. working (wireless might be an issue).

---

### Post by mips on 2008-10-27
> **chucky chuckaluck said:**
> i'm wondering how many problems are caused by only having one machine available and thus, not having a copy of the guide to use when something goes wrong. i was in that boat and had to use either mrs. chuckaluck's junky old laptop, or a slax cd to get my answers. once you're in though, there are text browsers you can use to get x, etc. working (wireless might be an issue).

Agreed. I was also in that boat my first time round but I just fired up my laptop so i was lucky. These days however the guide is included on the installation media so it really is not an issue anymore. A printout could also be kept close by if one has access to a printer.

Edit: Just wondering, is there a graphical browser out there that does not require X?

---

### Post by Rumor on 2008-10-27
> **mips said:**
> Edit: Just wondering, is there a graphical browser out there that does not require X?

Sort of . . . Links2 will make use of framebuffer, and display some images. 

There is a good discussion of the nuts and bolts of it here: [http://ubuntuforums.org/showthread.php?t=260946](http://ubuntuforums.org/showthread.php?t=260946)

---

### Post by SomeGuyDude on 2008-10-28
> **chucky chuckaluck said:**
> i'm wondering how many problems are caused by only having one machine available and thus, not having a copy of the guide to use when something goes wrong. i was in that boat and had to use either mrs. chuckaluck's junky old laptop, or a slax cd to get my answers. once you're in though, there are text browsers you can use to get x, etc. working (wireless might be an issue).

I had to use an old machine as well (with a very, very, VERY cluttered XP install that made me wonder how in the world I used it without tearing my hear out), and that's the only reason I was willing to do it, so I could search issues along the way before I got things set up.

There's just no way to "wing it" with the installation unless you're amazingly advanced.

---

### Post by handy on 2008-10-28
> **SomeGuyDude said:**
> I had to use an old machine as well (with a very, very, VERY cluttered XP install that made me wonder how in the world I used it without tearing my hear out), and that's the only reason I was willing to do it, so I could search issues along the way before I got things set up.

There's just no way to "wing it" with the installation unless you're amazingly advanced.

I agree, having a 2nd web reference machine makes things so easy.  Many things I wouldn't even bother attempting without my online e manual.

---

### Post by rsambuca on 2008-10-28
The guide is in the installation CD.  It tells you how to access it during the installation process by opening another terminal.

---

### Post by MisfitI38 on 2008-10-28
> **elmer_42 said:**
> And I also didn't follow the Beginner's Guide the first time, while I followed every bit and piece (of course, I modified some things that I *knew* wouldn't hurt) this time. Seriously, it's that good.

Thank you for your kind words. ;)

---

### Post by Grant A. on 2008-10-28
My problem was that it wouldn't properly install the Nvidia or Nv drivers without breaking the ogl package, which caused the poor rendering of images. Not just that, but it failed to correctly detect my gamma settings as well. I had everything configured properly, it's just the gamma and poor rendering of images that was my problem.

---

### Post by SomeGuyDude on 2008-10-28
> **rsambuca said:**
> The guide is in the installation CD.  It tells you how to access it during the installation process by opening another terminal.

The guide is, in itself, not enough though. To get things working totally right I had to look at the separate articles for some of the components. The beginner's guide is a good launching point, but I'm not sure you can use it by itself in all cases (such as anyone with non-Intel parts).

I was definitely googling on the spare machine.

---

