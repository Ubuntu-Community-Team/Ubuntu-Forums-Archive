---
title: "Any solution for the problem of how to read VCDs in Ubuntu?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-15
For those who may not be aware, VCDs are videos discs with the video on CDs rather than on DVDs. It is a recognized problem that Linux does not recognize VCDs as it should. I am pasting a brief description of the problem here below, from the referenced website. Has anyone figured out how to get Ubuntu to successfully play VCDs? My Ubuntu 7.04 doesn't even recognize that there is a disc (VCD) in the drive.

Here is the brief article (and its website address) for reference info:

[http://www.mpegtv.com/faq.html#vcdtech](http://www.mpegtv.com/faq.html#vcdtech)


                                                        What is the problem with VCD's ?

        The source of the problem with VCD's is that the MPEG bitstreams, unlike normal CD-ROM files, are stored on special mode-2 form-2 sectors (also called CDROM-XA sectors). Those sectors have less error protection but hold more data). 
        
        Although the MPEG files are visible in the directory structure when you mount the Video CD filesystem (the avseqXX.dat files in the mpegav directory), you may get garbage if you try to read those files as if they were normal files (depending on the Operating System you use).
        
        Ideally reading VCD tracks should be handled by the Operating System and it should be totally transparent to the applications, but it is not always the case.
        
        This is the case under Windows95 (Microsoft sometimes does a good job!), but unfortunately Unix-type Operating Systems do not (yet) give transparent access to the video tracks from VCD's. Some systems give access through some low-level driver calls (this is the case with Linux and Solaris) but some don't have any support for reading video tracks from VCD's.
        
        With Linux and Solaris it is possible to read data from those mode-2 form-2 sectors using some special ioctl() calls, but those calls are very system dependent (not the same with Linux and Solaris), and whether those calls work may depend on the type of drive itself.
        
        In general, on Unix-type systems, when an application reads those files with the normal read() routine, the system does not return the correct data because it is not aware (or does not care) that these mode-2 form-2 sectors are organized differently than regular CD-ROM sectors.
        
        This is why applications that try to read VCD tracks as if they were regular CD-ROM files get what looks like corrupted data with missing chunks.

---

### Post by AAM on 2007-06-15
Vlc.

---

### Post by swarup on 2007-06-15
Can anyone offer a solution to this knotty problem? I've been searching for a solution to this problem for a month now, and haven't got success.

---

### Post by zek725 on 2007-06-15
open with a multimedia player (right click): vlc, totem, mplayer, gxine, etc.

---

### Post by swarup on 2007-06-15
> **zek725 said:**
> open with a multimedia player (right click): vlc, totem, mplayer, gxine, etc.

Have you ever tried doing that?

I have tried all those players. None of them can even begin to try to work, because Ubuntu 7.04 does not even recognize that there is a VCD disk in the drive. You know, when you put a disc in the drive, it mounts and shows up on your desktop with a picture of a disc. Well, with VCDs at least on my computer, that doesn't happen. And if you open "computer" under "places" and click on the DVD drive, Ubuntu will reply that "there is no disc in the drive". 

So first it needs to recognize the disc. Then perhaps one of those multimedia players may work. Question is, how to get it to recognize a VCD disc? It recognizes DVDs and also regular CDs fine. But not VCDs. What's the Solution???

---

### Post by swarup on 2007-06-15
And I just tried to play a VCD on a completely new Dell computer on which Ubuntu has been loaded along with all the AUD-DVD codecs and multimedia players. On that computer the VCD actually does mount and appears on the desktop. But none of the multimedia players will play it. Anyone have a solution?

---

### Post by carloslosgrande on 2007-06-15
I initially thought to give you the same answer, as I've not had any difficulty previously in playing VCDs, but haven't tried for a while, since I had Dapper actually.
So I just tried it.

VLC won't play it, Totem won't and neither will MPlayer.

Sometime ago, (in Feisty) I noticed that Gnomebaker would no longer rip/copy VCDs as it had before, in Dapper.
I had to change to K3b to do this.

I have all the codecs (to my knowledge). and yes, the VCD isn't being recognised as even in the player.

I can view the contents as files.
There's a problem with kernel version 16 regarding the cdrom drives. I've been waiting for the fix to come. I'm assuming that this is where its stuck as these apps played VCDs before.

The guts of it is - I don't have a solution, sorry.

---

### Post by swarup on 2007-06-15
> **carloslosgrande said:**
> I initially thought to give you the same answer, as I've not had any difficulty previously in playing VCDs, but haven't tried for a while, since I had Dapper actually.
So I just tried it.

VLC won't play it, Totem won't and neither will MPlayer.

Sometime ago, (in Feisty) I noticed that Gnomebaker would no longer rip/copy VCDs as it had before, in Dapper.
I had to change to K3b to do this.

I have all the codecs (to my knowledge). and yes, the VCD isn't being recognised as even in the player.

I can view the contents as files.
There's a problem with kernel version 16 regarding the cdrom drives. I've been waiting for the fix to come. I'm assuming that this is where its stuck as these apps played VCDs before.

The guts of it is - I don't have a solution, sorry.

Yes. I've been looking further into the matter, and there definitely is a bug. Here is the reference to the bug site where this has been discussed and reported in full detail:


[https://bugs.launchpad.net/ubuntu/+s...20/+bug/106786](https://bugs.launchpad.net/ubuntu/+s...20/+bug/106786)

And here is a reference to another Ubuntu Support page where this very matter was discussed. One person on the page reported three ways in which he had been able to successfully play VCDs. But I tried his first way, and it did not work for me. Anyway, here is that reference:

[http://ubuntuforums.org/showthread.php?p=2847505&highlight=VCD#post2847505](http://ubuntuforums.org/showthread.php?p=2847505&highlight=VCD#post2847505)

The way it seems to me at this point, is we'll just have to wait until the bug is fixed.

---

### Post by klytu on 2007-06-15
> **swarup said:**
> Yes. I've been looking further into the matter, and there definitely is a bug. Here is the reference to the bug site where this has been discussed and reported in full detail:


[https://bugs.launchpad.net/ubuntu/+s...20/+bug/106786](https://bugs.launchpad.net/ubuntu/+s...20/+bug/106786)

And here is a reference to another Ubuntu Support page where this very matter was discussed. One person on the page reported three ways in which he had been able to successfully play VCDs. But I tried his first way, and it did not work for me. Anyway, here is that reference:

[http://ubuntuforums.org/showthread.php?p=2847505&highlight=VCD#post2847505](http://ubuntuforums.org/showthread.php?p=2847505&highlight=VCD#post2847505)

The way it seems to me at this point, is we'll just have to wait until the bug is fixed.

I haven't found a solution either. 

I remember noticing this bug when I first installed Feisty on my spare hard drive; it's one of the reasons I still use Dapper as my main workhorse OS. On my machine in Feisty VCDs mount and are recognized, but I have to go through contortions to get some to play and some won't play at all. For example, I can get some to play using mplayer in a manner similar to the one described in your second link above. 

In Dapper I can play all VCDs I have tried easily with Xine or using the same method with mplayer.

---

### Post by swarup on 2007-06-15
Do does that mean I should change my OS to dapper? When I was looking into what OS to load, everyone said "Go with Ubuntu 7.04". So I did. But now I am finding that the time of official support for Dapper is much longer than that for Feisty, and seemingly there are still a lot of problems with Feisty. So which OS do you think is better to go with?

---

### Post by klytu on 2007-06-15
> **swarup said:**
> Do does that mean I should change my OS to dapper? When I was looking into what OS to load, everyone said "Go with Ubuntu 7.04". So I did. But now I am finding that the time of official support for Dapper is much longer than that for Feisty, and seemingly there are still a lot of problems with Feisty. So which OS do you think is better to go with?

In my experience Dapper has been rock-solid to work with once I got everything tweaked; and at this point I really only have one really minor issue in Dapper.  When I installed Feisty, most things just worked without much tweaking at all, but since then I encountered some unexpected issues. VCD playback is one. The fact that Feisty won´t power off my computer on shutdown is another.  And there are a couple more issues on top of those. However,  my hardware is eight years old, I am not into video games, and I have no need of restricted graphics card drivers. 

MANY people who had difficulty with proprietary drivers running Dapper, have had little or no trouble with Feisty. I also think Feisty generally handles embedded video and multimedia a bit better than Dapper. Dapper also uses older versions than Feisty for a lot of software. 

So, on balance I think if you don´t need any proprietary drivers and you have older hardware - you may get better results with Dapper for now. Otherwise, I think you should probably stick with Feisty and await bug fixes and improvements in the newer kernel it uses. Just my opinion ....

---

### Post by swarup on 2007-06-15
> **klytu said:**
> In my experience Dapper has been rock-solid to work with once I got everything tweaked; and at this point I really only have one really minor issue in Dapper.  When I installed Feisty, most things just worked without much tweaking at all, but since then I encountered some unexpected issues. VCD playback is one. The fact that Feisty won´t power off my computer on shutdown is another.  And there are a couple more issues on top of those. However,  my hardware is eight years old, I am not into video games, and I have no need of restricted graphics card drivers. 

MANY people who had difficulty with proprietary drivers running Dapper, have had little or no trouble with Feisty. I also think Feisty generally handles embedded video and multimedia a bit better than Dapper. Dapper also uses older versions than Feisty for a lot of software. 

So, on balance I think if you don´t need any proprietary drivers and you have older hardware - you may get better results with Dapper for now. Otherwise, I think you should probably stick with Feisty and await bug fixes and improvements in the newer kernel it uses. Just my opinion ....

Your experience is quite helpful to hear-- thank you. Actually my computer is old as well. It is a 1999 laptop (celeron 433 mhz, 288 Ram). I did install all the latest video codecs and restricted drivers, but I'm not sure whether I really need them or not. DVD-type video only seems to run stutteringly on my computer so I don't watch it much. I mainly use the computer for word-processing and e-mail. And I would like to be able to see VCDs. 

As for powering off the computer, I have the same problem. Sometimes it powers off completely normally. I'd say that's around 40% of the time. The other 60% of the time, the desktop goes away and the screen goes black, or turns all kinds of multicolors-- and the computer never turns off no matter how long I wait. So in that case I have to hold the power button down until the computer goes off. I don't know what to make of that.

If Ubuntu is going to be investing its main efforts in Feisty from now on, perhaps it may still be worth sticking with Feisty. But if as some have said, that the support and efforts in Feisty are going to be short-lived, then perhaps I should just get rid of Feisty in favor of Dapper which sounds like it is more solid and better established.

---

### Post by carloslosgrande on 2007-06-15
Until recently I had dual boot of Dapper and Feisty as I was concerned with reliability of Feisty, but now I just have Feisty. I don't usually watch VCDs, so this isn't really a problem for me.
I've never had any luck with getting Edgy to run on my system, my recommendation is go for Dapper as its very dependable.

---

### Post by zek725 on 2007-06-16
> **swarup said:**
> Have you ever tried doing that?

I have tried all those players. None of them can even begin to try to work, because Ubuntu 7.04 does not even recognize that there is a VCD disk in the drive. You know, when you put a disc in the drive, it mounts and shows up on your desktop with a picture of a disc. Well, with VCDs at least on my computer, that doesn't happen. And if you open "computer" under "places" and click on the DVD drive, Ubuntu will reply that "there is no disc in the drive". 

So first it needs to recognize the disc. Then perhaps one of those multimedia players may work. Question is, how to get it to recognize a VCD disc? It recognizes DVDs and also regular CDs fine. But not VCDs. What's the Solution???

You're right. None of them works even with complete multimedia codecs. 

**Gxine** crashes. An error dialog appears with no message in it. 
**Totem Movieplayer** output: > Totem could not play this media (Video CD) although a plugin is present to handle it. You might want to check that a disc is present in the drive and that it is correctly configured.
**RealPlayer 10** crashes.

---

### Post by swarup on 2007-06-17
> **zek725 said:**
> You're right. None of them works even with complete multimedia codecs. 

**Gxine** crashes. An error dialog appears with no message in it. 
**Totem Movieplayer** output: 
**RealPlayer 10** crashes.

Yes, that is true. This is what happens. And it is a recognized bug, which has been reported in detail. 

Does anyone know how long it usually takes for Ubuntu to fix recognized and reported bugs? Is it something that we can expect a fix on? Or will it probably remain like this until the next version of Ubuntu comes out?

---

### Post by zek725 on 2007-06-17
> **swarup said:**
> Yes, that is true. This is what happens. And it is a recognized bug, which has been reported in detail. 

Does anyone know how long it usually takes for Ubuntu to fix recognized and reported bugs? Is it something that we can expect a fix on? Or will it probably remain like this until the next version of Ubuntu comes out?

We should expect a fix on this. Sometimes there are temporary fixes posted by some users in the Launchpad Bug filed. We should check it out.

---

### Post by swarup on 2007-06-17
> **zek725 said:**
> We should expect a fix on this. Sometimes there are temporary fixes posted by some users in the Launchpad Bug filed. We should check it out.

I see. That's very good news. If anyone comes across a temporary fix, plse let me know. I'll do the same.

---

### Post by scyleung on 2007-06-19
I can get it to work, but it isn't playing very well.

Firstly you need to get mplayer by entering this in the Terminal, it is about 14.5MB
```
sudo apt-get install mplayer
```
then
> **Kingsley said:**
> Open up your terminal and type
```
mplayer -zoom vcd://2
```

The "2" at the end of the code is the file you want to play, so you can change it to the file you want to play.(In windows XP, when you open a VCD, under a folder, there is a few video file, if you enter "1" at the end of the code, it will open the first file, if you enter "2", it will play the second file, etc) sometime it may not work, if it doesn't, try to restart the terminal.

There is no CP so here are some shoutcut:
```

<, >=Seek backward/forward 10 seconds
up and down=Seek forward/backward 1 minute
pgup and pgdown=Seek forward/backward 10 minutes
[, ]=Decrease/increase current playback speed by 10%.
q=quit
backspace=Reset playback speed to normal.
-= A-V delay less
+= A-V delay more
d= flame dropping
f= fullscreen
space bar, p= pause
m= mute
mouse scroll up= fast-forward 
mouse scroll down= fast-backward

```

There is more but these is the most important few.:KS

> **klytu said:**
> Actually there are quite a lot of controls - those are just off the top of my head. See ```
man mplayer
``` for full info.

---

### Post by klytu on 2007-06-20
I have done a lot of experimenting in Feisty with this situation and something bizarre happened. I figured out a few weeks ago that VCDs are recognized and mount in one of my optical drives, but the other drive can´t seem to read them (it reads and mounts other formats without a problem - and actually it might just be the brand of discs blanks and not VCDs per se that this drive is choking on ...  all the VCDs I have were burned by a friend who uses a different brand of CD-R blanks than I use). I had success in getting them to play automatically when inserted in the working drive by using ```
gconf-editor
``` then navigating to desktop>gnome>volume_manager and changing the autoplay_vcd_command key from > totem %m to > mplayer vcd://2 This worked well for weeks, but stopped working and I can´t figure out why. The first time the autoplay feature stopped working was after I did a reboot into Feisty and had accidently left a VCD in the problem drive that couldn´t read VCDs (I have a tri-boot setup. I had booted WindowsXP to see if I the problem drive could read VCDs when Windows XP was running. It wouldn´t read them there either ....) Since this reboot, I can´t get VCDs to autoplay in Feisty anymore. They still will mount properly in the working drive and I can get playback by invoking mplayer from the commandline. I can still get automatic VCD playback in Dapper with a variety of players including mplayer, xine, and VLC. Seems strange but maybe this is a clue to help solve the puzzle?

EDIT: I got automatic VCD playback working in Feisty again by changing the autoplay_vcd_command key to, explicitly: > mplayer vcd://2 -cdrom-device /dev/hda No help here in solving the problem for others ....

---

### Post by manmath on 2007-11-27
Dear All,

Copying VCDs in Linux has always been a Herculean task. However, here are some trick you might apply to get the files off your VCD.

I copy the disc to the hard disk as a raw/iso (dd if=/dev/cdrom of=/tmp/image.iso) then I use vcdgear to extract the dat to mpg:

vcdgear -raw2mpg /tmp/image.iso movie.mpg


This is pretty much the method I would recommend as well, the one change I would add is that I use readcd as it handles copying from the CD medium much better than dd, IMHO.

"vcdgear -fix -cue2mpg" has been reliable in extracting a working mpg from a standard image file set.

Just tried with DD and had an issue. readcd is a good tool, I prefer cdrdao myself and this command line should get you a lovelly bin/cue to use vcdgear on:

cdrdao read-cd --device ATA:1,1,0 --driver generic-mmc-raw --read-raw image.cue

Change the device for whatever is your reader!

OR

install readvcd and then 

# readvcd 2 > mv.mpg

OR

Install vcdimager
# vcdxrip

OR

install cdfs
mount -t cdfs /dev/cdrom (or whatever your drive is) /home/movie (or whatever your destination)

---

### Post by pyan on 2008-02-09
hello,
I faced the same problem but now I can play vcd file using Kaffiene,gxine and xine movie player after installing 'vcdtools' from Synaptic.
Open the player and click for vcd.
and you can try this link:
[https://answers.launchpad.net/ubuntu/+question/22214](https://answers.launchpad.net/ubuntu/+question/22214)
hope this help...:)

---

