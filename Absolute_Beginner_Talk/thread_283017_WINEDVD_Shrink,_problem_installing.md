---
title: "WINE/DVD Shrink, problem installing"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-10-23
It's wierd because, I installed DVD Shrink in a previous Ubuntu installation, and now, on this fresh one, I'm having problems installing it w/Wine. 

Wine is installed fine, thanks to AX2. I have the unzipped dvdshrink32.exe file on my desktop, and I've tried several times just dragging that file into the terminal, only to get the message of > Couldn't display "/home/*****/Desktop/dvdshrink32setup.exe".

Followed by > bash: /home/*****/Desktop/dvdshrink32setup.exe: Permission denied after I hit enter again. 

What part of the process am I missing here, please ? And another related question... How do most of you have your "Audio" section set up in Winecfg ? I haven't messed with any of the audio settings since having instaleld Ubuntu again the other day, but I will be installing Amarok, and will use its default engine, if that makes any difference. 

Doug

---

### Post by TooDamFast on 2006-10-24
not a pro here, but I just left click on the .exe and click on open with and pick wine out of the list.  after that, every time I left click on an .exe it shows "open with wine" at the top of the list.

---

### Post by shirilover on 2006-10-24
If you have wine correctly installed, just double-click the setup file to begin installation.
Here's a link with an excellent guide -> [http://www.mrbass.org/linux/ubuntu/dvdshrink/]("http://www.mrbass.org/linux/ubuntu/dvdshrink/")

Using amarok will not have any effect on the audio settings in wine. However, I have setup wine to use ALSA.

---

### Post by Sweet Spot on 2006-10-24
Thanks guys, I think the problem was (logically enough) that I should have re-boot before trying to click on the .exe file. I just did, and it worked as such. At least, I'm pretty sure that's what needed to be done anyway. 

A quick other question... How do you guys have your cfg set up ? Did you select NT 4.0 or XP in the drop down box, and what determines which you pick ? I'll look around for the answer (as in the link you provided above) as well. Thanks again.

Doug

---

### Post by Sweet Spot on 2006-10-24
Have another problem now. This happened before, on my previous installation on WINE.  I tried to access the "audio" tab but then WINE just crashed, and then I got this message:

> ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
Creating link /home/******/.kde/socket-*******-desktop.
can't create mcop directory
******@******-desktop:~$I guess I can uninstall and reinstall, but would love to know why this happens, and what I can do about it. 

Doug

Edit: This is not just an issue of wine crashing. As it is, when I'm backing up a disc, the audio from the DVD is audiable, but is very choppy, thus making it impossible to listen to music on my PC at the same time. Also, if I attempt to listen to music, it affects the rip of the DVD, and may also cause DVD shrink to crash in the process. Not only is the audio from the DVD audiable when backing up, but when I mouse over the GUI in certain spots, I can also hear it popping in as well.

---

### Post by gn2 on 2006-10-24
Have you tried K9Copy yet?

I was a keen DVD Shrink user in Windows, but I find K9Copy does the job in Linux.

---

### Post by Kouki on 2006-10-24
Yes, another vote for k9 copy from me.  You can get it from synaptic package manager, but first you have to add repositories, namely universe.  Click tools, then add repositories, add and tick the two unchecked boxes.  Click reload and search for k9copy.  You shouldn't have any problems using this.

---

### Post by Sweet Spot on 2006-10-24
I did try K9, and found it to be a major pain in the behind. I also read up on "how to" get it to work properly, as in, actually compress the file etc, etc... But there's no way that I have the patience to do all which is required, nor do I want to. 

I don't understand why there isn't a program that just works out of the box for DVD compression/ripping. 

Doug

---

### Post by gn2 on 2006-10-24
> **Sweet Spot said:**
> I did try K9, and found it to be a major pain in the behind. I also read up on "how to" get it to work properly, as in, actually compress the file etc, etc... But there's no way that I have the patience to do all which is required, nor do I want to. 

I don't understand why there isn't a program that just works out of the box for DVD compression/ripping. 

Doug

Did you have k3b installed at the time you were using K9Copy?
(Similar to having Nero with DVD Shrink)

Do you have all the required codecs etc installed (easiest done with Easybuntu or Automatix)

I'm a pity you found K9Copy difficult, a bit more perseverance would have paid off. I have found it does work "out of the box" with k3b.

Other similar tools are available, you can search for them in Synaptic.

Good luck!

---

### Post by Sweet Spot on 2006-10-25
Excuse me, Mr. gn2, I've a question for you. I decided to try K9 again, as it is, out of the box. My first attempt to back up one of my DVD's was successful, in a way, and I'm attempting a second DVD with a different option checked. In the first scenario, the movie copied and burned, but with absolutely no menus or options. 

This time around, I've checked "keep original menus", and hope that's the solution to the problem. However, this wasn't the only little problem which occured. First let me tell you that I have the tab "output device", set to .iso image". I always just right click on my iso's and use Gnome's default burning app, which works a charm for me. 

Why though, is a folder named "dvd" created with "Audio ts" and "video ts" AS WELL as the .ISO file ? Isn't that a bit redundant ? Sorry if that's a dumb question, I just am not very knowledgable regarding these things. 

Secondly, when K9 was finished backing up the DVD, and after it was ejected, I put it back in the drive to see if it had burned correctly. I then got an error message saying that I did not have permission to view this folder. Furthermore, the next couple of DVD's I put in that drive, wouldn't seek correctly, or be read by either K9 or DVD Shrink, and there was an restricted emblem next to the DVD folder as well. I reboot my PC, and it all cleared up, but I'm confused as to why this happened. 

Any reason you can think of ?  At the moment, I've got something ripping, and I think it's doing the menus too, since it's taking MUCH longer this time. Guess I'll see, soon. 

Doug

---

### Post by Sweet Spot on 2006-10-25
And one more problem which is worth a bump: I just ripped the DVD with the "keep original menus" option checked, but this produced a file size of over 5 gigs. So, what gives ? I thought that this program was supposed to automatically compress everything ? What did I do wrong ? 

Help would be greatly appreciated.

Doug

---

### Post by gn2 on 2006-10-25
I followed this simple guide, and it worked. [http://www.pclinuxonline.com/wiki/VideoDVDBackup](http://www.pclinuxonline.com/wiki/VideoDVDBackup)

I had K3b installed and used the option in K9Copy to use K3b to burn the copy.

After K9Copy finished preparing the DVD, K3b opened and burned the disc.

As for removal of menus and extras, for me that's a normally a plus, but that's just my personal preference.

The creation of a folder with audio and video files is the same as you would get with DVD Shrink option to back up to a hard drive folder.

I find it a very simple program to work with, but it isn't what I was used to and some familiarisation had to take place.
The software works, I just had to learn how.

---

### Post by Sweet Spot on 2006-10-25
Well, I looked at that guide, and to be honest, I had already figured out exactly the same thing it said to do, before looking. It's not really very comprehensive, and doesn't cover what to do if it's not working properly. Eg; According to that guide: > It'll automatically calculate how much compression is needed to fit the 9GB DVD on a 4.5GB DVD. You'll see an indication of how much compression you get at the bottom of the window

But in my case, it absolutely did not compress the DVD enough to fit on the 4.7gig disk. The copy came out to be over 5 gigs, in fact. So wouldn't this simply mean that it does not work as intended ?  As for K3b, I doubt that it is necessary to use it, since the default Ubuntu/Gnome burner does the same job. It doesn't expedite the compression methods any, in K9. 

If you happen to have the movie "The Big Labowsky", do me a favour and try copying it WITH the menus in tact. I'm sure there are some movies in which it's ok to not have any menus, but there are some, which I absolutely need/want it. But that guide also says that K9 knows how much to compress..which I don't really see happening. If that excludes the menus, that's not too good IMO.

Doug

---

