---
title: "List of Issues using Linux"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by mrbsee on 2008-02-29
EDIT UPDATE -  This is incredible it seems that all of the problems I've mentioned here have been fixed just by turning off compiz-fusion... my computer is running rock solid stable now.  Truecrypt isn't even throwing IO errors.  I wonder if compiz would work better if I had an ATI card? Or a newer Nvida like a 8800 series..  anyone know?  I hate having to turn off compiz to get stability! /UPDATE




I've been using Ubuntu 7.10  32bit for a little over a month now.  I'm impressed by so many things it can do.. I love the look.. the feel.. the speed.. and a lot of the programs are so much better and free (i.e. hellanzb > newsleecher)  

But I'm having several issues that outweigh the good.

1. Trying to watch Flash movies... I first used the Adobe plug-in and it would cause the computer to lock up completely. Then I was suggested to Gnash.. ok great Youtube videos work for the most part but now the controls do not work.. I can't use slide bar, volume or anything like that.  And most movies that are embeded in blogs do not work at all because it requires you press a play button to watch the video.  Watching streaming videos have always been a big part of my enjoyment of having  the internet.  #SOLVED - downloaded the Hardy flash plugin.  If you're having this problem get the .deb [here]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb")

2. Watching videos in the media players.  After a random point of having my computer on I cannot view movies at all.  You can hear the audio but you get yellow and pink lines for the picture and you cannot fix this without restarting Ubuntu.
#SOLVED?  I'm almost certain this problem stems from using Compiz-Fusion

3. Screen savers lock up my system..  I'll go to work and lock the screen, screen saver comes up.. I come home the screen saver is frozen when I get back and I have to reboot my machine. This is a major annoyance so I just turned the screen saver off.. but why the hell can't I use it?! It's just a bloody screen saver!
#SOLVED?  Compiz-Fusion again

4. Truecrypt 5.0 yes I know people say you should revert to Truecrypt 4.3a right now until 8.04 is released or you can download the newest linux kernel but I'm not willing to go through that trouble.  Why in the heck can't you easily format a drive to use EXT3.. I can only select FAT.  Ok so I encrypt my external My Book Western Digital drive in FAT.. now when I try to copy/cut/move files to the truecrypt drive I get IO errors.  I am assuming that if the drive was ext3 I wouldn't have this problem.  Since i'm using TC 5 I have the sync option set which does make it slower to move files..but i'm not worried about speed. Before the sync option the computer would lock up and require a reboot.. now it just gives me IO errors and I have to unplug my drive and plug it back in.. but I can't get anything copied onto it!!  So my question for this one is.. would making it ext3 fix my problem with IO errors it's a good drive I tried it on a windows machine and files copied just fine.


Ok so those are the only complaints that I have with Ubuntu.. if anyone could tell me how I might get these things working I would be extremely happy. One thing to note. I am using compiz-fusion and some say that turning this off will make it more stable. But that was one of the biggest draws to Ubuntu. I do not want to turn it off.. it is one of the things that make this OS stand out above everything else. 

System specs
Nvida Geforce 6800
Intel Core 2 Duo
4 Gigabytes RAM
2 Internal SATA HDD
2 External USB HDD
Ubuntu 7.10 32 bit

---

### Post by jeffus_il on 2008-02-29
I suggest that if you are interested in staying with Ubuntu, post each problem in a thread and solve them one by one, they are all quite easily solvable.

---

### Post by dca on 2008-02-29
> **mrbsee said:**
> 
3. Screen savers lock up my system..  I'll go to work and lock the screen, screen saver comes up.. I come home the screen saver is frozen when I get back and I have to reboot my machine. This is a major annoyance so I just turned the screen saver off.. but why the hell can't I use it?! It's just a bloody screen saver!

I, too, have this problem.  Apparently if you have your screensavers set for 'Random' a handful of them exhibit this problem, not all of them.  I just found one that I know was working and left it set on that one...

---

### Post by Oldsoldier2003 on 2008-02-29
> **dca said:**
> I, too, have this problem.  Apparently if you have your screensavers set for 'Random' a handful of them exhibit this problem, not all of them.  I just found one that I know was working and left it set on that one...
Blank Screen works fine too :)

---

### Post by owbizi on 2008-02-29
I am been pushed because of three things: games. And games. And, ah, a little games too. But I'm discovering new ones and learning how to use wine, so it's getting fine now.

Look, about flash, I don't know why many of you have this problem. Here, with Firefox, I only need to click on the yellow bar about plugins, when I visit a site which uses Flash (ie Youtube), install the Adobe one, I think, and it's all.

Now, about movies, try to use this: $ sudo apt-get install ubuntu-restricted-extras, and then open the movie you want with totem. Otherwise, two very good players are mplayer and vlc - this has also a Windows version, which is very known and respected.

Screen savers - have you tried to use the blank one, or to choose another one? And, are you using compiz? Here, compiz made my 3d screensaver a little (ok, so much) slower, so I use the blank one.

The fourth question, I can't talk about, because I really don't know...

---

### Post by MONODA on 2008-02-29
you could try linux mint, it is almost exactly like ubuntu and comes preinstalled with flash, mp3 support etc...

---

### Post by kryth on 2008-02-29
2. Try installing and using VLC. No codecs to install. It just works.

---

### Post by kryth on 2008-02-29
[http://ubuntuforums.org/showthread.php?t=711266](http://ubuntuforums.org/showthread.php?t=711266)

---

### Post by owbizi on 2008-02-29
Oh, and about Flash, see this thread too:

[http://ubuntuforums.org/showthread.php?t=711330](http://ubuntuforums.org/showthread.php?t=711330).

---

### Post by piperdown10 on 2008-02-29
> **owbizi said:**
> I am been pushed because of three things: games. And games. And, ah, a little games too....

You should check out Cedega. It's a program written to specifically play windows based games. You can get to their website by clicking [here]("http://www.transgaming.com/").

There's a subscription fee but it's worth it for a gamer, I think.

---

### Post by Tadock on 2008-02-29
> **piperdown10 said:**
> You should check out Cedega. It's a program written to specifically play windows based games. You can get to their website by clicking [here]("http://www.transgaming.com/").

There's a subscription fee but it's worth it for a gamer, I think.

Cedega is decent but there are other programs that are out there that I feel are better like [Wine]("http://www.winehq.org/") and [crossover]("http://www.codeweavers.com/"). Best bet is to try out all three and decide which works best for your particular games.

---

### Post by owbizi on 2008-02-29
Yup, I'm aware of Cedega and CrossOver, but both are paid, so I really can't use them by now. Anyway, I'll be looking forward to these, they got my attention since some time ago.

By the way, I just installed Morrowind now with wine - time to configure!

---

### Post by mrbsee on 2008-02-29
Restricted extras are already installed.  Thanks for all the replys but I haven't got anything fixed yet.. To the poster about the flash.. I did install just by going to a flash site.. it worked fine for some videos, but would eventually lock my computer up especially in youtube.  So neither adobe nor gnash works for me.  =(  Oh and I have VLC installed .. no matter which movie player I use I get the pink and yellow screen with no sound.. this doesn't happen immediately but after having the OS running for a few hours or sooner than that sometimes.. I think it's caused by moving the cube to much... or just switching desktops.

---

### Post by oldos2er on 2008-02-29
The video and screensaver problems sound like an issue with graphics card drivers. If you're using compiz-fusion I'd try turning it off; see if that fixes these problems.

---

### Post by mrbsee on 2008-02-29
> **oldos2er said:**
> The video and screensaver problems sound like an issue with graphics card drivers. If you're using compiz-fusion I'd try turning it off; see if that fixes these problems.

I turned off Compiz and that does seem to be what is causing the lock ups and the video problem.  Maybe it will be fixed in future versions of Compiz?  I hate having to turn it off though =(

---

### Post by owbizi on 2008-02-29
So, the pink-and-yellow-thing is caused by compiz... damn!, it's like when I want to see a full screen movie and have to disable compiz to avoid flickering...

Well, it's not perfect, but... to do this with less effort, you can install libgnome-compiz-manager0 - it's available via via apt-get. The program will put an icon on the notification area, so you'll only need to click on it to enable/disable compiz.

About flash, we'll find a way (I hope), no worries. :)

---

### Post by MONODA on 2008-02-29
yeah i think that it will be fixed soon, i also hate leaving them off. Remember compiz fusion is still 0.52, it is not stable yet (I really cant understand why it is preinstalled and turned on by default.
EDIT: > So, the pink-and-yellow-thing is caused by compiz... damn!, it's like when I want to see a full screen movie and have to disable compiz to avoid flickering...

Well, it's not perfect, but... to do this with less effort, you can install libgnome-compiz-manager0 - it's available via via apt-get. The program will put an icon on the notification area, so you'll only need to click on it to enable/disable compiz.

About flash, we'll find a way (I hope), no worries.

in order to fix flash I installed the hardy flash plugin, you should be able to find a liink easily. you can download it as a .deb just install like you would an .exe

---

### Post by MarkX on 2008-02-29
I'm new to this too but had similar problems. Since I have disabled the restricted drivers to my nvidia card there have been no problems. 
It could also be something to do with the way your monitor is detected. Mine was supposed to be PnP but was starting in wrong resolutions. Selecting "LCD monitor -whatever resolution-" made that go away. HTH

---

### Post by mrbsee on 2008-02-29
> **MONODA said:**
> yeah i think that it will be fixed soon, i also hate leaving them off. Remember compiz fusion is still 0.52, it is not stable yet (I really cant understand why it is preinstalled and turned on by default.
EDIT: 

in order to fix flash I installed the hardy flash plugin, you should be able to find a liink easily. you can download it as a .deb just install like you would an .exe


Flash works now! Thank you a million... 1 problem solved!

---

### Post by MONODA on 2008-02-29
your welcome :D:D i think im happier than you (its my first time to successfully fix someone's problem here :D) youtube doesnt work well for me in firefox so i use [http://www.idesktop.tv/](http://www.idesktop.tv/) it has all the youtube videos but IMO is better than youtube.
EDIT: could you list your problems for me again.

---

### Post by owbizi on 2008-02-29
MarkX, are you sure that disabling the restricted drivers is a good idea? I don't know if it's okay, but I think you'll be losing too much doing this...

With ATI, the driver was way too old - maybe the nvidia one is similar... at least GeForce graphics appears to like Ubuntu more, yup...

ps: iDesktop.tv is in my favs now! :)

---

### Post by mrbsee on 2008-02-29
> **MONODA said:**
> your welcome :D:D i think im happier than you (its my first time to successfully fix someone's problem here :D) youtube doesnt work well for me in firefox so i use [http://www.idesktop.tv/](http://www.idesktop.tv/) it has all the youtube videos but IMO is better than youtube.
EDIT: could you list your problems for me again.

Heh I'd give you a thanks point if I knew how.  Also idesktop.tv is awesome.. it's in my favs now too.

The other problem I'm having is that the ability to play videos .avi .mpg etc.. stops working .. I get pink and yellow lines in the video box.. yet I can still hear the audio.  I'm chalking this up to using compiz-fusion.  as well as my screen saver problem.

As for truecrypt I'd just like to know if using the ext3 file system over the fat system would stop my IO errors when trying to copying files.  I'm trying to move a large collection of files to my truecrypt drive.  I'm using an external USB drive for my truecrypt.  

Again I thank everybody for chiming in on this thread.. this community is truly kick *** bad ***.

---

### Post by MONODA on 2008-02-29
to fix the video problem try another player like vlc. as for the truecrypt, i havent heard of it so i dont know how to fix it sry.
thank button is the yellow start--------------->>>>>>>>>>

---

### Post by .nedberg on 2008-02-29
Number 2 is probably due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/162343")

The driver is updated in Hardy if that helps. I get by it by pressing ctrl+alt+f6 and then ctrl+alt+f7 again if I have the problem.

---

### Post by mrbsee on 2008-02-29
Seems like all my problems are stemming from Compiz-Fusion.  Adobe flash works great when I have compiz turned off.. turn it on and try to watch a youtube video then the computer locks up.  Try to watch a video using any player .. I lose the video to the pink and yellow crap... turn off compiz works forever.  I wonder if it's because my video card isn't powerful enough or if these are just bugs when running compiz.   Sigh... i'm taunted by the beauty that is compiz but when I use it everything goes to hell in a hand basket.

---

### Post by MarkX on 2008-03-01
> **owbizi said:**
> MarkX, are you sure that disabling the restricted drivers is a good idea? I don't know if it's okay, but I think you'll be losing too much doing this...

With ATI, the driver was way too old - maybe the nvidia one is similar... at least GeForce graphics appears to like Ubuntu more, yup...

ps: iDesktop.tv is in my favs now! :)

I don't really have any choice but to disable the nvidia drivers (it's a Ti 4200), they messed things up and even made the computer crash. The most demanding thing it has to do is play vids and DVDs with VLC and surf and it's coping ok without the nvidia. I might get an older card, like a gforce mx440 and see how it works with that.

It might even be the card that has a fault, I'm out in the Azores in the middle of the atlantic at the moment, it's very humid here  and the electricity is pretty ropey.

---

