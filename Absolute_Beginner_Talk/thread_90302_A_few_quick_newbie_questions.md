---
title: "A few quick newbie questions"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Aira Rex on 2005-11-14
Hi everyone!

I just tried the Ubuntu live cd a few days ago and liked it so much I installed the os. A few things went wrong while partitioning and XP got deleted. =O oh well, no big deal, I can always reinstall. But I don't want to! My computer is so NOT bloated and full of useless junk for the first time ever. I'm having a blast using Ubuntu but I have a few questions. Sorry if they're stupid!

Where do the programs in the repositories come from? Does someone maintain a server with all the files on it? Is it just magic or witchcraft perhaps?

Could someone direct me to a good linux terminal tutorial for new users? I'd like to learn some of the basics, like changing directories, etc. 

I would like to be windows-free, but I play ALOT of games so I don't know if it's possible. =( I've got all my music and video files working thanks to this forum and a few nice guides I came across, so that's no problem. Let's say I have a Japanese PC CD-ROM game for windows in .iso format. Would it even be possible to install and run it in linux? I'd need to be able to mount the .iso, like a windows user would do with alcohol 120% or daemon tools. I think I saw a package that could do that, but I'm not sure. Then there's the issue of running the .exe.

I've read about wine, tried to install it but I think I'm confused. Obviously there is some command-line stuff I need to do to make it work. How about that Win4Lin program. Is it worth the money? I'm willing to shell out a few bux here and there if it extends my vacation here in Linux Land. Also, that Culdega or whatever...hmm will I need all these progs or just wine to be successful in my quest to run windows programs in ubuntu?

Thanks for taking the time to read my noobish questions. For the first time I actually feel like I have a shot at using Linux, thanks to Ubuntu and the helpful, friendly people here at ubuntuforums.org. 

Ok just one more! [-o< Whenever I use apt-get or the package manager I get a system error message, saying something like this: ```
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
```
Are some of my repository listings outdated? I guess this is where my first question comes from...who maintains the repositories? 

Thanks again! Even if noone has an easy answer for my questions, I'll figure something out...I'm having too much fun with Ubuntu to give it up yet. \\:D/

---

### Post by tonysathre on 2005-11-14
1) repos are maintained on servers by some one
2)[http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)
4) have u enabled extra repos in your sources.list: to do so if u havent, open a konsole and do: sudo kwrite /etc/apt/sources.list and press enter, remove the # symbols from the beginning of the lines

---

### Post by Chayak on 2005-11-14
Well, first off welcome to the world of Linux.

tonysathre covered a bit so I'll cover the games

Games, well you're out of luck there.  There are some ports of good games for linux but they are the exception, not the norm.  Thats the only reason I still keep windows installed on one of my machines.   You might be able to get a few to run in Wine but if they require directx you're pretty much out of luck I know there is a few commercial pograms for getting them to run, but I'm not familiar with them.

---

### Post by tonysathre on 2005-11-14
cedega is supposed to be pretty good for playing windows games but have never needed it since i have an xp dual boot box, the only downfall i have heard is it is not free

---

### Post by Aira Rex on 2005-11-14
Thanks Tony! the link is just what I need. 

Yeah, cedega is like 5 bux or something. I guess if you compile it yourself it's free. Wonder what kind of interface it uses n stuff, I'll have to investigate...

---

### Post by tonysathre on 2005-11-14
good luck

---

### Post by Rackerz on 2005-11-14
Thanks also guys, a few questions i needed answering here were answered. 8)

---

### Post by SSTwinrova on 2005-11-14
[QUOTE=Aira Rex]
Ok just one more! [-o< Whenever I use apt-get or the package manager I get a system error message, saying something like this: **W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages **(/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
Are some of my repository listings outdated? I guess this is where my first question comes from...who maintains the repositories? 
[/QUOTE]

All that means is that your CD isn't in the drive and it's complaining since it thinks it can look there for packages. In Synaptic you can just disable (I'd recommend against removing although it shouldn't hurt anything) the CD-ROM source and that shouldn't come up anymore.

---

### Post by tonysathre on 2005-11-15
u can get cedega for free if u build it yourself? where? i didnt know that

---

### Post by SSTwinrova on 2005-11-15
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

YMMV, but I don't think it can hurt anything to try. Also a search for "cedega cvs" or something of the like may turn up some threads dealing with Ubuntu-specific quirks/tweaks.

---

### Post by Zimmer on 2005-11-15
Hi there Aira Rex
.you said..

*Could someone direct me to a good linux terminal tutorial for new users? I'd like to learn some of the basics, like changing directories, et*c.

Well, you could try this one:
[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)
and
[http://tille.xalasys.com/training/tldp/ch02s02.html](http://tille.xalasys.com/training/tldp/ch02s02.html)

Lots of tips here:
[http://www.brunolinux.com/](http://www.brunolinux.com/)

but the sort of site you would browse to sort a particular problem ,rather than Basic training.

And I assume you have been here..
[http://ubuntuguide.org/](http://ubuntuguide.org/)

I have been trying to use Linux (Fedora and Ubuntu 5.04)  for over a year now, without resorting to XP. It has been an interesting experience. I still have an XP machine but the wife uses that just to play Freecell :D 
And I have used it to download files from a friend's Bluetooth phone.
Other than that, I could have lived without XP.
And I am certainly going to live without the new Vista !!

If it is Games you want, I play Wolfenstein ET (free and without using any Windows emulator software) on Ubuntu.. and I think there is a sticky thread on these forums dedicated to games...

Have fun...

Zimmer

---

### Post by racecat on 2005-11-15
Welcome!

Lets see. I know some of these:

Terminal for beginners. Kyral wrote a good one. Don't think anyone mentioned it, yet:

[HTML]http://www.ubuntuforums.org/showthread.php?t=73885[/HTML]

As was pointed out, the error is wanting to see the distro CD as it's one of the "repos" in /etc/apt/sources.list. You can expand the available repos by uncommenting out the appropriate lines (by deleting the ##) in the sources.list. Note that you will have to do a ```
sudo apt-get update
``` after you save your changes, or you'll get more of the "couldn't stat source package list" type errors. Check out the wiki; I think you have to remove the "us." from the backports lines. I believe that was a change since the release. Sorry, I'm working from memory and at my age, that's a feat.

That about covers my...well...I'll stop short of expertise. Hope that helps.

Bill

---

### Post by racecat on 2005-11-15
One more thing I should mention. It's been recommended by folks who know lots more about this than I do to leave the backport lines commented out unless you need one of them. I believe they are apps that are developed for the next distro and are "backported" to make them available as bleeding edge apps for the current release. There is some potential for problems.

Somebody please correct me if I'm wrong. I have a knack for being wrong (ask my wife!).

Bill

---

### Post by Aira Rex on 2005-11-16
NICE! I finally got rid of the system error. I did the things you guys mentioned and read the scrollback after I did apt-get update, apparenty somewhere along the line I added repositories (maybe when I was trying to get media codecs to work), so I removed 'em. =D Works fine now, I feel better.

Thanks for all the links, got 'em all bookmarked.

Oh yeah and I've been getting quite a few windows games to work with just wine! I'm gonna have to look into that cedega, if it does what it says it does, I might never have to reinstall XP =O

EDIT:oh snap I just found a prog that fakes cd drives, just like daemon tools!  XD Linux i love u. 

[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

---

### Post by chakra_dude on 2005-11-16
[QUOTE=SSTwinrova]All that means is that your CD isn't in the drive and it's complaining since it thinks it can look there for packages. In Synaptic you can just disable (I'd recommend against removing although it shouldn't hurt anything) the CD-ROM source and that shouldn't come up anymore.[/QUOTE]

i also get these errors and i placed my installer cd in the cd-rom but i still get these errors afterwards. what seems to be the problem here? thanks!

---

### Post by SSTwinrova on 2005-11-17
[QUOTE=chakra_dude]i also get these errors and i placed my installer cd in the cd-rom but i still get these errors afterwards. what seems to be the problem here? thanks![/QUOTE]

After you put the CD in, did you try a "sudo apt-get update" before attempting to install whatever program?

---

### Post by chakra_dude on 2005-11-18
yes. i did an apt-get update, but there were still errors. also edited my sources.list...errors still. also tried removing the "us" in sources.list but still not working... 

really appreciate any help i can get. thanks! :)

---

### Post by chakra_dude on 2005-11-21
anyone? :(

---

### Post by aysiu on 2005-11-21
[QUOTE=chakra_dude]yes. i did an apt-get update, but there were still errors. also edited my sources.list...errors still. also tried removing the "us" in sources.list but still not working... 

really appreciate any help i can get. thanks! :)[/QUOTE] See the first link in my sig.

---

