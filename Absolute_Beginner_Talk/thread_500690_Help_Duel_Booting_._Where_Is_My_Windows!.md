---
title: "Help Duel Booting . Where Is My Windows!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by nikolaig on 2007-07-14
HI
I followed this guide
 [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)
 to installing ubuntu . according to the guide i should now b able to chose on start up! but i cant. windows is not an option! any1 know how to solve this??

---

### Post by LaRoza on 2007-07-14
can Ubuntu see the XP partition? In other words, are you sure Xp is still there?

---

### Post by nikolaig on 2007-07-14
how can i check if it can still see it ?? i sure hope xp is still there (with all my stuff on it :(  ) but i followed the guide to the letter...

---

### Post by LaRoza on 2007-07-14
If you are in ubuntu now, you should be able to see the partition, it will probably be an NTFS partition.

If you are not using that computer boot with the live cd to view your partitions.

-EDIT are you given option, usually three, for Ubuntu and XP is not there or do you not get to choose?

---

### Post by bren on 2007-07-14
open a terminal window (applications - accessories - terminal) and  install gparted

> sudo apt-get install gparted

run gparted via  System / admin / gnome partition editior

take a screenshot Applications / Accessories / Take screenshot 

and post the picture here...

bren

---

### Post by nikolaig on 2007-07-14
im on the laptop now, bt i cant see any partition ill try n boot with the live cd

---

### Post by nikolaig on 2007-07-14
ok ill take the pic n post it in a sec

---

### Post by nikolaig on 2007-07-14
i dont have the gnome partition editor in the system/ admin part....
where can i get it?

---

### Post by LaRoza on 2007-07-14
forget GParted for the moment, just open a terminal, and type 
```

fdisk -l

```
copy the results and post them.

---

### Post by nikolaig on 2007-07-14
how do i insert an image on to here!??!?!
[IMG]file:///home/nikolai/Desktop/Screenshot.png[/IMG]

---

### Post by LaRoza on 2007-07-14
Make it an attachment instead, the paper clip icon.

---

### Post by nikolaig on 2007-07-14
nothing happens if i type disk -l

---

### Post by LaRoza on 2007-07-14
```

fdisk -l

```

copy and paste it.

---

### Post by nikolaig on 2007-07-14
ok this is the attached photo (hopefully)

---

### Post by nikolaig on 2007-07-14
should i insert the live cd ?

---

### Post by LaRoza on 2007-07-14
-edit You don't need to use the live disk, but I believe the disk has Gparted on it might be easier.

Go to system -> computer 

and take a screen shot of that, I don't know why you can't get GParted, but the computer will list all partitions and devices.

---

### Post by nikolaig on 2007-07-14
do u mean places->computer?

---

### Post by 3rdalbum on 2007-07-14
Try:

```
sudo fdisk -l
```

(the "sudo" bit will make sure it lists all drives)

And post the results here. You can copy and paste it from the terminal, as long as you use the Edit menu rather than "control-C".

---

### Post by nikolaig on 2007-07-14
here's the screen shot

---

### Post by nikolaig on 2007-07-14
results from 3rdalbum advice:

nikolai@nikolai-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
nikolai@nikolai-laptop:~$

---

### Post by 3rdalbum on 2007-07-14
Nikolaig,

I'm sorry to be telling you this, but Windows is gone. I don't know why you've lost it (if maybe you took a wrong turn in your instructions), but your hard disk consists entirely of Linux. I do hope you made a backup of everything.

---

### Post by LaRoza on 2007-07-14
bad news, XP was overwritten.

---

### Post by nikolaig on 2007-07-14
wat?!?!!? tsss i knew i shouldnt ave tried this "linux" crap

---

### Post by nikolaig on 2007-07-14
so its impossible to have linux n windows on the same laptop?

---

### Post by LaRoza on 2007-07-14
I understand you are upset, I've made mistakes in the past too. (Thought I lost the computer) don't blame Linux for human error. It is easy to select the wrong option during the partitioning, that is why people say to back up any essential data before altering the partition table.

---

### Post by LaRoza on 2007-07-14
> **nikolaig said:**
> so its impossible to have linux n windows on the same laptop?

No, it is easy. If you resize the existing partion and use the freed space.

---

### Post by nikolaig on 2007-07-14
yeah bt i did EXACTLY wat the guide said n there didnt seem 2 b any problems durin installation

---

### Post by nikolaig on 2007-07-14
hmm how do i resize a partition ?

---

### Post by LaRoza on 2007-07-14
> **nikolaig said:**
> yeah bt i did EXACTLY wat the guide said n there didnt seem 2 b any problems durin installation

There probably was no problem, in fact, you have less installation problems than most (you have internet, good resolution, and everything seems to work). I imagine the wrong radio button was selected when you clicked "next". It would have been easy to to.

---

### Post by LaRoza on 2007-07-14
> **nikolaig said:**
> hmm how do i resize a partition ?

To resize a partition during the installation process, you select the option with the slider bar, and move it to your desired change.

to do it any other time, GParted is used. GParted comes as a live cd also, that is what I use, although you can install it on the os. when it is installed on the OS you can't resize a mounted partition.

---

### Post by nikolaig on 2007-07-14
hmm, i never even got the slider bar durin installation

---

### Post by LaRoza on 2007-07-14
> **nikolaig said:**
> hmm, i never even got the slider bar durin installation

Then how did you follow that guide? It used the slider.

---

### Post by nikolaig on 2007-07-14
yeah bt it said that the first option which comes up is the best , so i chose that 1 (none of them had that sliding bar thing.

---

### Post by LaRoza on 2007-07-14
> 
Now Ubuntu loads the disk partitioner. The first option, to resize the main partition and use the freed space, is pretty much the best one to go with.


the first option on the screen shot is:

"resize IDE1 master partition 1..."

Was that the first option you saw?

that option uses the slider, if you didn't see the slider, the first option would be:
"Erase entire disk..."

so you followed the words, yes, but you didn't follow them in context. 

If there is not enough room, the resize option will not show up.

-edit You selected "erase entire disk"

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

---

### Post by nikolaig on 2007-07-14
well anyway now  ill ave 2 download a pirate windows (since i lost my cd ages ago) n try n get things bak 2 how they were

---

### Post by nikolaig on 2007-07-14
tss linux  is a waste product. it cant even read bloody mp3's!!!

---

### Post by Junixx on 2007-07-14
> **nikolaig said:**
> tss linux  is a waste product. it cant even read bloody mp3's!!!

You have to install the w32codecs... I think you can find them with synaptic, or you could install XMMS, which will also install MP3 codecs and some other things.. (I use XMMS)

---

### Post by thefoolisme on 2007-07-14
You know, it sucks that you didn't back up your stuff or do a little research before attempting the dual-boot, but please don't take your frustrations out on the OS.  It only does what the human running it tells it to do.  Linux will play MP3s, video, etc. with the codecs installed.  If you need help, do a search for it.  Then, if you can't find the answers, just ask.  The people on this forum are amazing with their help.  While you're waiting to download your pirated copy of windows, you might just take the opportunity to explore all that Linux can do.  So step away from the PC, take a deep breath, then come back and start your linux journey.

---

### Post by markusf21 on 2007-07-16
A bit of advice about your pirated windows; MAKE sure you get the student version or windows will not be genuine no matter what u do and die in a month

---

### Post by LaRoza on 2007-07-17
> **nikolaig said:**
> tss linux  is a waste product. it cant even read bloody mp3's!!!

Neither can Windows, you need a media player for that with the codecs, some distros come with them, some don't.

---

### Post by srsairbags on 2007-07-17
> **LaRoza said:**
> Neither can Windows, you need a media player for that with the codecs, some distros come with them, some don't.

dude . . i would generally take crap about windows. . . but not this kind of b*** s*** . Windows can play MP3s out of the box you dont need codecs period.

---

### Post by Outrunner on 2007-07-17
> **srsairbags said:**
> dude . . i would generally take crap about windows. . . but not this kind of b*** s*** . Windows can play MP3s out of the box you dont need codecs period.

LOL. You always need codecs...


Anyway...

For a full codec pack(as far as I know) you can use this command

```
sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll w32codecs
```

---

### Post by srsairbags on 2007-07-17
ya i knwo that you need codecs . . but windows media player (bundled player) can play it rite out of the box . . (thats what i mean to say) . . . . . .

---

### Post by Outrunner on 2007-07-17
Isn't this on a preinstalled Windows copy(that comes with your computer?)? As far as I know, if you install Windows yourself, you do need to find the codecs. But then, most people don't install Windows themselves.

---

### Post by srsairbags on 2007-07-17
dude . .  i understand that this is a linux forum . . and you rent supposed to discuss this . . but please . . . what you are saying is not true . . . . when you install windows, you can play mp3s by using wmp  once the installtion finishes . . and for vista . . .  iam almost 200 % sure that it plays mp3s . . .

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> dude . .  i understand that this is a linux forum . . and you rent supposed to discuss this . . but please . . . what you are saying is not true . . . . when you install windows, you can play mp3s by using wmp  once the installtion finishes . . and for vista . . .  iam almost 200 % sure that it plays mp3s . . .

I know, I am referring to the Operating systems, Windows and Linux. Windows cannot play music or video, the media player does. My point was that the Operating System is not in question, it is the OTHER apps. Some Linux distros come with media players and the codecs and "work out of the box". Windows needs the codecs as much as Linux does.

If I where to say "Windows sucks, you can't write C programs on it", I would be factually correct, but you can't write C programs on Linux either. You need a compiler, Linux often comes with it, although it is missing the headers. (By "write", I mean write, compile, link and run)

---

### Post by srsairbags on 2007-07-17
> **LaRoza said:**
> I know, I am referring to the Operating systems, Windows and Linux. Windows cannot play music or video, the media player does. My point was that the Operating System is not in question, it is the OTHER apps. Some Linux distros come with media players and the codecs and "work out of the box". Windows needs the codecs as much as Linux does.

If I where to say "Windows sucks, you can't write C programs on it", I would be factually correct, but you can't write C programs on Linux either. You need a compiler, Linux often comes with it, although it is missing the headers. (By "write", I mean write, compile, link and run)

dude . . but then are you saying that linux can play mp3s off the console . . once the codecs are installed ? ?  ( as far as i know, its only the players which played stuff) . . . i dont wanaa  be rude but  . . .my fresh install of windows played my mp3 and my frest install of ubuntu  with amarok . . just stood there and crashed . . . ( wrote a bug report . . i guess)

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> dude . . but then are you saying that linux can play mp3s off the console . . once the codecs are installed ? ?  ( as far as i know, its only the players which played stuff) . . . i dont wanaa  be rude but  . . .my fresh install of windows played my mp3 and my frest install of ubuntu  with amarok . . just stood there and crashed . . . ( wrote a bug report . . i guess)

I didn't say Linux can play anything. Try a different distro, some will work fine, I think LinuxMint will, it is almost just like Ubuntu but with all the media stuff added.

As an aside, could you write more coherant sentences and not use an ellipsis for everything? Also, I cringe to think what you're like when you TRY to be rude.

---

### Post by Junixx on 2007-07-17
> **srsairbags said:**
>  my frest install of ubuntu  with amarok . . just stood there and crashed . . . ( wrote a bug report . . i guess)

I shall, once again recommend to download XMMS as an audio player if you have problems... I could never quite get Amarok working right in kubuntu, although I didn't try very hard to get it working

---

### Post by LaRoza on 2007-07-17
> **Junixx said:**
> I shall, once again recommend to download XMMS as an audio player if you have problems... I could never quite get Amarok working right in kubuntu, although I didn't try very hard to get it working

VLC is good too.

---

### Post by srsairbags on 2007-07-17
yep VLC is the best player ever . . . .

---

### Post by Junixx on 2007-07-17
> **LaRoza said:**
> VLC is good too.

Doh how could I forget VLC :-k

---

### Post by LaRoza on 2007-07-17
> **Junixx said:**
> Doh how could I forget VLC :-k

That's what happens when you actually have choices. :D

---

### Post by srsairbags on 2007-07-17
> **LaRoza said:**
> I didn't say Linux can play anything. Try a different distro, some will work fine, I think LinuxMint will, it is almost just like Ubuntu but with all the media stuff added.

As an aside, could you write more coherant sentences and not use an ellipsis for everything? Also, I cringe to think what you're like when you TRY to be rude.

yep . . im gonna try mepis and sabayon after this . . ive almost had it with ubuntu . . .

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> yep . . im gonna try mepis and sabayon after this . . ive almost had it with ubuntu . . .

Let us know how you like them, :), I try all the distros I can.

---

### Post by srsairbags on 2007-07-17
but i know this for certain that ubuntu is the best release among all these . . and the smoothest . . . mepis is the closest to a point and click experience to windows  . . and sabayon is beryle  . . . out of the box  . . .

---

### Post by Old Pink on 2007-07-17
> **nikolaig said:**
> wat?!?!!? tsss i knew i shouldnt ave tried this "linux" crap
> **nikolaig said:**
> tss linux  is a waste product. it cant even read bloody mp3's!!!

You are a waste product. If you'd actually spent time following, reading and understanding the guide, you wouldn't be here complaining now. It was your own impatience and stupidity that brought this on, not Linux. A monkey could understand "Erase Entire Disk" would leave him with nothing left.

And it can read MP3s. Again, if you weren't so impatient you would've noticed a thread at the very top of the forum you're in now, telling you exactly how to play MP3s. 

**_READ_ IT: **[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

You're lucky the people who helped you did, you're so ungrateful and short tempered, and coupled with your constant complaining and slating of what this forum is all about, you don't deserve help, but no, the linux community come through, helping you through your own error, even though you place the blame elsewhere, and helping you get started on your new system, even though most people probably don't want you here.

"Waste product" my ***. Good luck with Windows. I hope you take time to see that in fact Windows doesn't work out of the box and requires alot of setup. And, should you choose to go through with pirating it, I look forward to and codone any and all punishment the law brings to you.

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> but i know this for certain that ubuntu is the best release among all these . . and the smoothest . . . mepis is the closest to a point and click experience to windows  . . and sabayon is beryle  . . . out of the box  . . .

Vector Linux has beryl too, even on the live cd. 

I actually try to make Windows act and look like Linux.

It seems this thread is off topic, or is it just me?

---

### Post by srsairbags on 2007-07-17
yeah, i guess you are right . . . .  also i think sabayon is more popular than victor linux . . . soo popularity = support . . .

---

### Post by srsairbags on 2007-07-17
> **LaRoza said:**
> That's what happens when you actually have choices. :D

hey . . were you referring to the  . . . VLC on windows oe linux . . . . ? ?

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> hey . . were you referring to the  . . . VLC on windows oe linux . . . . ? ?

I was referring to the one on Linux. The Windows version is just as good, I recommend them both.

---

### Post by srsairbags on 2007-07-17
i was  . . talking bout the one in windows . . .  but hey vlc is vlc . . .

---

### Post by LaRoza on 2007-07-17
> **srsairbags said:**
> i was  . . talking bout the one in windows . . .  but hey vlc is vlc . . .

They seem to be the same.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
Sorry if this is a horrible place to ask this, but I came here looking for an less scary dual booting guide, and found this searching  "dual booting." I probably should have found it frightening that the first guy I heard of using this wiped his drive, but I'm actually happy to see how easy this guide looks. I was holding off only because most of the guides scared me, and I really didn't feel comfortable manually repartitioning everything. Can I really just follow the installer like that? If so, why are all the other guides so complicated? 

Also (sorry, this is stupid,  I'm pretty new at this, and have no idea what I'm doing), I have two hard drives. One (my SATA, which is the C drive ) has my system and whatever else it is we accumulate on it, and the other has mostly video files (you can guess) and a few important backups. I don't want to run the system off the second, because it's slower, so I just plan on doing this like most people. It's my understanding this won't effect my second drive? It seems like there's no way it should, but then again I have no idea. Thanks, and sorry for the timid, stupid, apologetic noobish feel of this post, I'm sure if this Ubuntu thing works out I'll be here a lot, because I'm a bit of a message board geek.

Thanks, 

Cyril.

---

### Post by LaRoza on 2007-07-24
> **InflammatoryWin.Apologist said:**
> Sorry if this is a horrible place to ask this, but I came here looking for an less scary dual booting guide, and found this searching  "dual booting." I probably should have found it frightening that the first guy I heard of using this wiped his drive, but I'm actually happy to see how easy this guide looks. I was holding off only because most of the guides scared me, and I really didn't feel comfortable manually repartitioning everything. Can I really just follow the installer like that? If so, why are all the other guides so complicated? 

Also (sorry, this is stupid,  I'm pretty new at this, and have no idea what I'm doing), I have two hard drives. One (my SATA, which is the C drive ) has my system and whatever else it is we accumulate on it, and the other has mostly video files (you can guess) and a few important backups. I don't want to run the system off the second, because it's slower, so I just plan on doing this like most people. It's my understanding this won't effect my second drive? It seems like there's no way it should, but then again I have no idea. Thanks, and sorry for the timid, stupid, apologetic noobish feel of this post, I'm sure if this Ubuntu thing works out I'll be here a lot, because I'm a bit of a message board geek.

Thanks, 

Cyril.
Hi, you  probably should have started your own thread, but here are the answers.

The Ubuntu installer is extremely easy, and yes, it is that simple to dual boot.

Other guides probably focus on other installation schemes, there are many options, sometimes people don't want the simplest.

If you install to your drive that you called "C:", your second drive will not be affected. However, you should know that Windows is calling it a "C:" drive, Linux doesn't use drive letters, it will be called "/dev/sda". 

Your post is perfectly stated, except, you should focus on the issue instead of being timid :D, your question is perfectly valid for this forum.

Have fun!

-EDIT The poster overwrote his hard drive because he selected "Overwrite harddrive", a perfectly logical outcome of his action.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
> **LaRoza said:**
> Hi, you  probably should have started your own thread, but here are the answers.

The Ubuntu installer is extremely easy, and yes, it is that simple to dual boot.

Other guides probably focus on other installation schemes, there are many options, sometimes people don't want the simplest.

If you install to your drive that you called "C:", your second drive will not be affected. However, you should know that Windows is calling it a "C:" drive, Linux doesn't use drive letters, it will be called "/dev/sda". 

Your post is perfectly stated, except, you should focus on the issue instead of being timid :D, your question is perfectly valid for this forum.

Have fun!

Thanks, and your "/dev/sda" point is well-taken. I'm glad I know that going in. In fact, I just wrote that down. I plan on using [this guide ]("http://www.pcmech.com/show/os/917/") to help me with the latter part of the setup, unless there's a better one or some other reason why I shouldn't. Otherwise, I hope to be back on here tonight, yelling at you guys for tricking me into using some gay operating system that doesn't even have a paperclip to tell me what to do.

Thanks.

---

### Post by Mornedhel on 2007-07-24
> **InflammatoryWin.Apologist said:**
> some gay operating system that doesn't even have a paperclip to tell me what to do.

No worries, I hear OOo has its own ridiculous assistant somewhere now, or am I mistaken ? Edit : OK, so it's not a paperclip, it's a bulb. (With hands.) So it's less ridiculous, and apparently less annoying, but I'm sure the OOo devs can fix that.

---

### Post by InflammatoryWin.Apologist on 2007-07-24
> **Mornedhel said:**
> No worries, I hear OOo has its own ridiculous assistant somewhere now, or am I mistaken ?

If they do it's pretty new, or maybe you have to turn it on somehow. My one and only leg-up here is that I already use and love OO.

---

