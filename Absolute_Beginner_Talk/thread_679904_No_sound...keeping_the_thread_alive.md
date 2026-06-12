---
title: "No sound...keeping the thread alive"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by jtbrookreson on 2008-01-27
Hello all

The short....I'm a total linix Noob running ubuntu 6.10 on a G3 500 ibook with 256 Ram. Everything is fine except I have no sound. I had a thread going earlier

[http://ubuntuforums.org/showthread.php?t=679804](http://ubuntuforums.org/showthread.php?t=679804)

but it has seemed to died. When I was running 6.06 (something tells me I should not have switched), the sound worked fine,

any Ideas?

Thanks for all of your help.

-JTB

---

### Post by Cubby on 2008-01-27
Hi,

I just reinstalled ubuntu feisty fawn, and wondered why I had no system sound, either.

I then went to the upper right hand corner icon of a speaker, right clicked on it and it showed "mute" was ticked.  I unticked it and that solved the problem for me.

Hope others can be of help if it isn't this simple a problem.

Lisa  Marie

---

### Post by jtbrookreson on 2008-01-27
I was hoping it would be that simple...but when I went to unmute it, I got the following:

***The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.***

Now if this gives anymore clues, Totem won't run...won't even start up...but VLR does (without sound obviously).

Any other suggestions?

-JTB

Thanks for looking.

---

### Post by Cubby on 2008-01-27
one newb helping another newb *grin*

check to see if gstreamer plug ins for alsa is installed,

---

### Post by jtbrookreson on 2008-01-27
Riiiiggghttttt....

I think I understand the giist of what you are suggesting....

But I have no clue how to do that....

-JTB

---

### Post by Cubby on 2008-01-27
you can go to system > admin > and open up Synaptic Package Manager and type in search > gstreamer >  and look to see if it shows it as installed.

---

### Post by jtbrookreson on 2008-01-27
Its looks as if gstreamer0.10-alsa is installed...

---

### Post by Cubby on 2008-01-27
just another added note, that if you can't install gstreamer via synaptic, such as it gives you error  (such as "failed to fetch" )then you'll probably have to enable the multiverse and universe repositories 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

after enabling all the repositories 

sudo apt-get install gstreamer0.10-alsa

should install the package along with the dependencies

My system has both gstreamer0.10-alsa and gstreamer0.10-esd installed, plus the documentation and manuals.

---

### Post by Cubby on 2008-01-27
well, scratch that...:(  but, hang on. Hopefully you'll get some seasoned help with this problem.

---

### Post by Cubby on 2008-01-27
to show what's in your system, try opening terminal and typing in

dmesg 

and then hit enter and paste the output here.  It could give a clue for others to help you with.

If you want to read  about the command dmesg before implementing it, then here is some info on it:

[http://linuxgazette.net/issue59/nazario.html](http://linuxgazette.net/issue59/nazario.html)

---

### Post by DMK62 on 2008-01-27
Hi

I did some searching through google and the forums and maybe this link will help with the problem or point you in the right direction to resolve the sound problems on your G3.

[http://ubuntuforums.org/showthread.php?t=309494](http://ubuntuforums.org/showthread.php?t=309494)

Dale

---

### Post by DMK62 on 2008-01-27
I should have added that if it does work and you want to add it to /etc/modules

from the terminal ( If you want to make a backup of the file )

sudo cp /etc/modules   /etc/modules.backup 

To edit the file

sudo gedit  /etc/modules


Dale

---

### Post by jtbrookreson on 2008-01-27
does this help at all?

snd_aoa_i2sbus 24516 0 
snd_pcm_oss 54048 0 
snd_mixer_oss 22144 1 snd_pcm_oss
snd_pcm 95556 2 snd_aoa_i2sbus,snd_pcm_oss
snd_timer 26980 1 snd_pcm
snd_page_alloc 11368 1 snd_pcm
snd 69940 5 snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,s nd_timer
soundcore 11396 1 snd
snd_aoa_soundbus 7972 1 snd_aoa_i2sbus

-JTB

---

### Post by DMK62 on 2008-01-27
Hi

Really wish I could help more with this problem at this point. I am not familiar enough with the particulars of Apple hardware ( pc user here ). I did notice that snd-aoa was loaded ( Apple Onboard Audio ) and I read on one webpage that snd-aoa replaced snd-powermac but the page did not indicate if it worked properly with all G3 ibooks. 

I have your post bookmarked and if I can find any additional information for you I will post it here for you.

Dale

Also if you go to System>Preferences>Sound is there any other option than Auto ?

---

### Post by jtbrookreson on 2008-01-27
> **DMK62 said:**
> Hi

I did some searching through google and the forums and maybe this link will help with the problem or point you in the right direction to resolve the sound problems on your G3.

[http://ubuntuforums.org/showthread.php?t=309494](http://ubuntuforums.org/showthread.php?t=309494)

Dale

I looked at the thread you posted, and I thin I understand half of it....the other half I have no clue what I am looking at, or at least the application of the information. I feel very wierd being a grown man and asking someone to hold my hand step by step...

in an earlier post, someone suggested that I type "dmesg" in terminal, and it looks like all of my specs came up on screen. The thing is, I don't know what I am looking for, so I'm not sure if it is there or not.

All I do know is that 6.04 had working sound, and 6.10 doesn't....

Again, thanks for all of the support...

-JTB

---

### Post by DMK62 on 2008-01-27
The dmesg command is useful in getting information about the hardware on your system. It can be somewhat cryptic for the new user. As mentioned previously I will try and do some more research on this problem. 

Have you tried any versions after 6.06 ? Feisty Fawn seemed to fix a lot of bugs that were in Dapper. However Feisty Fawn is not a long term support release. The latest Gutsy Gibbon 7.10 might be too resource hungry for the ibook. Having gone through several versions of Ubuntu I have found that some versions hated some of my hardware no matter what I tried and the last 2 releases have been problem free. Sometimes it's a matter of finding a release that is stable and works well with your configuration and sticking with it as long as it's supported. 

I feel very wierd being a grown man and asking someone to hold my hand step by step... .... Myself and others are here to help you step by step if need be. All of us have needed assistance along the way. And having it step by step can help other newcomers to linux reading the post see how the problem is solved. 

Dale

This may be a long shot but worth seeing if it helps. Double click on the volume control by the clock in the upper right hand corner. The title bar should say Volume Control : device name ( AlsaMixer ). What does it say on the Title bar ? I have a soundblaster audigy card that will not produce sound unless I go to the Switches tab and remove the digital output option. See if disabling / enabling some of the options resolves the problem.

---

### Post by jtbrookreson on 2008-01-27
as posted earlier in this thread, this is what I got on volume control...
 
> **jtbrookreson said:**
> I was hoping it would be that simple...but when I went to unmute it, I got the following:

***The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.***

.

In a previous thread that died, I was asked to type a few commands in terminal, and these are what the results were...

for "lsmod|grep snd"

snd_aoa_i2sbus 24516 0
snd_pcm_oss 54048 0
snd_mixer_oss 22144 1 snd_pcm_oss
snd_pcm 95556 2 snd_aoa_i2sbus,snd_pcm_oss
snd_timer 26980 1 snd_pcm
snd_page_alloc 11368 1 snd_pcm
snd 69940 5 snd_aoa_i2sbus,snd_pcm_oss,snd_mixer_oss,snd_pcm,s nd_timer
soundcore 11396 1 snd
snd_aoa_soundbus 7972 1 snd_aoa_i2sbus

for "ls -la /dev/snd"

total 0
drwxr-xr-x 2 root root 60 1904-01-01 00:01 .
drwxr-xr-x 12 root root 13340 2008-01-27 11:23 ..
crw-rw---- 1 root audio 116, 2 1904-01-01 00:01 timer

and then after following the instructions on a trouble shooting page, I got this:

joshtyler@ubuntu:~$ aplay -l
aplay: device_list:222: no soundcards found...
joshtyler@ubuntu:~$ lspci -v
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea AGP
Flags: bus master, 66MHz, medium devsel, latency 16
Capabilities: <access denied>

0000:00:10.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) (prog-if 00 [VGA])
Subsystem: ATI Technologies Inc Rage Mobility M3 AGP 2x
Flags: bus master, stepping, 66MHz, medium devsel, latency 255, IRQ 48
Memory at 94000000 (32-bit, prefetchable) [size=64M]
I/O ports at f0000400 [size=256]
Memory at 90000000 (32-bit, non-prefetchable) [size=16K]
Expansion ROM at f1000000 [disabled] [size=128K]
Capabilities: <access denied>

0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea PCI
Flags: bus master, 66MHz, medium devsel, latency 16

0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Pangea Mac I/O
Flags: bus master, medium devsel, latency 16
Memory at 80000000 (32-bit, non-prefetchable) [size=512K]

0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB (prog-if 10 [OHCI])
Flags: bus master, medium devsel, latency 16, IRQ 27
Memory at 80081000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Pangea USB (prog-if 10 [OHCI])
Flags: bus master, medium devsel, latency 16, IRQ 28
Memory at 80080000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth/Pangea Internal PCI
Flags: bus master, 66MHz, medium devsel, latency 16

0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth/Pangea FireWire (prog-if 10 [OHCI])
Subsystem: Apple Computer Inc. UniNorth/Pangea FireWire
Flags: bus master, 66MHz, medium devsel, latency 16, IRQ 40
Memory at f5000000 (32-bit, non-prefetchable) [size=4K]
Capabilities: <access denied>

0002:20:0f.0 Class ffff: Illegal Vendor ID Unknown device ffff (rev ff) (prog-if ff)
!!! Unknown header type 7f

to be honest, I can figue out what some of this might mean, but only abstractly and have no idea how to use the information...

Thanks again for all the support. It has been keeping me sane...

BTW, I am using the Xubuntu interface now, and things seem to be moving a bit quicker, but still no sound. I am wondering if I should go back to 6.04...I was wondering how I could do that without having to reinstall everything and loose all of the data I now have? or is that not possible?

-JTB

---

### Post by DMK62 on 2008-01-28
Hi

A few questions before I get some sleep here.

Was it a clean install of your current version of Ubuntu ? Or did you upgrade it from a previous version ? I have seen lots of whacked out issues when doing upgrades as opposed to clean installs. It could also be that you had a bad install to begin with and the hardware detection did not work properly.  

If you have a separate home partition you may be able to reinstall and leave the home partition alone. Are you using a live cd or alternate cd to install ? I think the support for 6.04 must be running out soon so myself I would recommend trying to get it to work with Dapper or higher.

The gstreamer error you are getting can be caused by several different things ranging from permissions to kernel versions etc etc.  Finding which one it is may take time.

If you have an external drive or dvd drive I would make sure to back up any data that is important before trying a reinstall or anything beyond editing a config file ( always best to be on the safe side ). 

Dale

---

### Post by Cubby on 2008-01-28
> **jtbrookreson said:**
>  I feel very wierd being a grown man and asking someone to hold my hand step by step...

in an earlier post, someone suggested that I type "dmesg" in terminal, and it looks like all of my specs came up on screen. The thing is, I don't know what I am looking for, so I'm not sure if it is there or not.



-JTB
Hi you two,

JTB, I too need hand holding with my LINUX problems as I'm having a mount issue I have been working on in both kubuntu and ubuntu.  

When I typed in the error message you received after pointing to your speaker icon, I googled it and one person said to see if your sound card is being recognized, and to use dmesg in terminal.  

I did mine and looked down the long list for my sound card and this is what it shows, but I don't know what it means, either. :)  I guess this means it's detected.

 76.360480] [drm] Initialized drm 1.1.0 20060810
[   76.374582] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[   76.378836] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   77.144470] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   77.144827] agpgart: Device is in legacy mode, falling back to 2.x
[   77.145034] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   77.145277] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode

I understand the pain this can be.  I had to go outside and stack firewood just to give myself a break from trying to figure out my OS problem, though not as bad as yours and reinstalling is not a problem for me as I've just started using these os's.  I just haven't figured out which one I prefer yet, kubuntu or ubuntu.

Lisa Marie

---

### Post by iris-n on 2008-01-28
When I got this message: > The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
, the problem was that i didn't had sound permissions.

To fix that:

```
sudo adduser <your_name> audio
```

Hope that helps =)

---

### Post by DMK62 on 2008-01-28
Thanks for the additioal advice iris-n. When searching for info on this problem there were several sites that indicated problems with permissions. Unfortunately from the terminal in this case there is no sound card found. Using the process of elimination will probably be the only way to get this working as it stands now. Making sure he is has sound permissions is a good thing to check.

Lisa Marie ... feel free to start a new post concerning the mount issues. From experience it's much easier to do in Ubuntu than Kubuntu. Keep trying both Ubuntu and Kubuntu and see which you prefer. I use both but that's my personal preference. Walking away is often the best thing you can do. It clears the mind and regains one's sanity at times. I hope you stay with linux as you will see the rewards as time goes by and you will be surprised how much you learn.

Dale

---

### Post by jtbrookreson on 2008-01-28
**The Saga of JTB and Ubuntu**

I just got my hands on this iBook G3, and I needed an operating system. I always wanted to try Ubuntu, and it seemed like a perfect opportunity.

Installed 6.04, and I was happier than a pig in Paris. Except until I found out about the clock errors (ibooks hardware clock would sometimes reset to 1904, causing Ubuntu not to work). The orignial instrall was a complet install, alternate CD, with no other OS on the drive.

After looking for a solutioon to the date problem, I thought I found some simple code to fix the problem. I typed it in, and turned my machine into a bithering idiot, not able to boot up except to a blue shell that was always on safety mode. After hours that felt like years, I decided to reinstall, but the 6.10 version instead (alternate CD) thinking that the bug might be fixed in that version (have yet to have the pronlem). When I went to install, it would not let me to a total install, but a partition disk. I don't know how or why...

6.10 works fine now, except I have no sound, totem won't work, or Movie player, but VLR works greatr (sans audio of course). Korganize wouldn't load after installing, no the chess game either...but that was just a small price.

To further my exploration of Ubuntu, last night I installed Xubuntu as well, trying the different desk top eviroments to see what I like.

I am going to see if the solution offerened above, giving permission, helps. But I am open to any and all ideas.

Thanks again. I really appreciate not feeling alone here.

-JTB

BTW...Xubuntu is faster on my machine, smoother...I can see that it is a stripped down version. But some of me likes the extra bells and wistles of gnome...I have not come up with a final conclusion yet.

---

### Post by jtbrookreson on 2008-01-28
making a copy of all my files (its not that much, I have only has this thing for two weeks now) would be very easy.

Would it be best if I just reinstalled 6.04? Can I do it so that it wipes everything clean, and starts as if I never had Ubuntu at all?

-JTB

Oh yeah, I do have an external 40 gig HD that came with this iBook, but it seems to be read only, with about 8 gigs of data from the previous owners MAC crap...how can I fix that (quick fix only....I'll start a new thread if I need to).

---

### Post by jtbrookreson on 2008-01-28
> **iris-n said:**
> When I got this message: , the problem was that i didn't had sound permissions.

To fix that:

```
sudo adduser <your_name> audio
```

Hope that helps =)

uhmmm that got me a "no such file or directory"

OK....

---

### Post by DMK62 on 2008-01-28
Hi

Adding and mounting the external drive may not be a quick fix. Try posting in the Apple forum on Ubuntu forums  for that.

Xubuntu shares  the same Ubuntu base as the other versions. It is not so much stripped down as it is geared towards lower spec computers or those that want a really fast system and have no need for Open Office etc.

As far as reverting back to 6.04 you should be able to do that. Just delete the partitions and create new ones using the alternate cd. Make sure you have absolutely everything you need backed up. One thing I would take into consideration is what the computer will be used for. If it is just to tinker with and security is not a major issue then go with 6.04 as you know it works. Security updates to the best of  my knowledge are no longer available for 6.04.

Here comes the tricky part when it comes to Dapper. The Desktop or Live CD ( both are the same ) may not work on the G3. It requires 256mb of ram and can run into problems with some graphic adapters ( there may be a safe graphics mode when the cd boots up and choose that if the regular one cannot boot to start the setup ). One advantage of the Live CD is that you can test to see if your hardware works. It will be slow so be patient. Check if your sound card works or at least the volume control is not X'ed out. I did read on some of the sites that G3 owners who did an alternate cd install ran into the problem you have and when using the Live CD instead it worked.

We have an ice storm headed up our way to Ottawa over the next 24 to 36 hours so I am not sure when I will be around the next day or so. However, I will check to see if any progress has been made on your part. 

Good Luck

Dale

---

### Post by jtbrookreson on 2008-01-28
Thanks buddy...

When I first tried installing, I used a Live CD, and it wouldn't work. The forums suggested that use the alternate CD, and everything worked fine with that (1 hour and 30 minutes later that is).

I am just hoping that the install will let me wipe the whole drive clean, and not make me partitian it like it did when I installed 6.10. I think that might be the root of my problem. I think that there is 6.10 code is somehow getting mixed signals from the old 6.04 code.

Once I get 6.04 back up and running, I plan on installing Xubuntu through the back door like I have now. I think I like Xubuntu better, despite the fact that it looks like a 2nd cousin to windows 3.1...A better looking, faster and more stable cousin, but a cousin just the same.

This somputer is going to be my sole computer for the most part, using it for Office application, and internet fun. I am not that concerned with secuirty at the moment, and will burn that bridge when it gets closer.

So for the next 18 hours I am going to sleep on it and see what other advice others can offer. But if you can do me one last favor, I would apprecaite it...Please saty warm and safe up there during this winter storm. I know you Kanucks are used to wintery blasts, but try to stay in, have an extra Molson, maybe some Crown Royal, and enjoy the wit and wisdom of Bob & Doug McKenzie until it gets a bit nicer out there.

Thanks again. You have been a great help.

-JTB

---

### Post by DMK62 on 2008-01-28
Thanks for your concerns about the weather up here. It's almost tropical compared to my hometown in western Canada where it is currently experiencing windchills close to - 60 f and a blizzard on top of that has reduced visibility to under 20 ft. Nothing like a snowbank to chill beer lol. 

Xubuntu can be customized using themes etc so it can be made more visually appealing. I have done several installs using the alternate cd's and I prefer them over the Live CD's.

There is a forum staff member ( Aysiu ) here that has a page on Ubuntu/Linux basics and I would recommend you take a look, if you haven't already.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

A great site for information on installs and partitions is

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

Cheers

Dale

---

### Post by jtbrookreson on 2008-01-29
Ubunto 6.04 or 6.10...let's split the difference and go with 6.06

I decieded to reinstall, or actually install for the first time 6.06. The reason is that it sitll has LTS, and I hope that the audio will work....

I burned the alternate install CD, backed up all my files on a flash drive, and began installation with my external 40 gig HD connected.

It then asked me what HD do I want to partition. I first said the internal one, because that is wher I plan on installing everything. When it asked for my username, I though...wait a minute...and I went back to disc partitioning screen, and then chose the external HD, and proceeded to wipe th puppy dog clean (it was used and had old MAC files on it, formatted to "Read Only") I figured that will fix that problem. I then went back again and re-partitioned the internal HD a second time, and continued with the installation (I removed the external HD, so that the computer would not be tempted to put anything on it).

So far everything is working like a charm, but then again, itiisn't done installing. I figure I have another hour wait. I will give an update when all is said and done. Hopefully my sound issue will be resolved, and I'll buy drinks for everybody.

Thanks again for your help and support.

-JTB

---

### Post by DMK62 on 2008-01-29
Storm is currently south of here....woohoo

I seem to have gotten versions mixed up in my head...gets that way after using too many versions. 6.04 was originally supposed to be released in April but was delayed until June and hence the 6.06 version. 

Hope the install goes well.

Will check back later.

Dale

---

### Post by jtbrookreson on 2008-01-29
an hour and a half later....

according to my screen it says 75% complete

storing language...

Its said that for about 20 minutes now.

Now the last time I installed, I remember things taking a bit, and lasting on one process for quite some time. I also remember it taking about an hour and a half total...

I don't know if it has stalled, taking its sweet old time, or just froze....

I don't hear the CD buzzing....

why can't life be simple....

-JTB

---

### Post by jtbrookreson on 2008-01-29
Something didn't work...

Re download...re-burn...reinstall.

---

### Post by jtbrookreson on 2008-01-29
I am happy to report that everything is working quite well. I have sound. I have video, I have wireless...I have Xubuntu....

The solution was to wipe clean and reinstall 6.06. The get all the updates (192 of them), plus the gstreamer packages. In all, including transfering files back onto this little beast, and restarting the whole process due to a faulty disc...5 hours.

to each and every one of those who offered hekp, insight, advice, and didn't leave me hanging....Thanks!!!! I owe you each a case of beer of your choice!

Thanks again.

JTB

---

### Post by DMK62 on 2008-01-29
That's awesome news !!!

It's been a pleasure helping you over the last few days. You persisted and did not give up and were always open to advice given here on the forums. I am sure you are feeling a sense of accomplishment upon getting a fully functional system. Let your journey into Linux and Ubuntu now begin ..... 

Feel free to pm me if you have any questions or just to say hi.

Cheers

Dale

---

### Post by Cubby on 2008-02-01
is it my turn to keep the thread alive...:)

I'm so glad that it all worked well for you, JTB.  Well, guess what, I'm having the same problem. Oh, I should first mention that I'm trying to get kubuntu 7.10 Gutsy working on my desktop machine.  Firstly, I messed up my repository list while I was using ubuntu feisty fawn, and decided, gee, I like the KDE desktop better than gnome, so I'm going to try reinstalling kubuntu.  I did a clean reinstall using my entire second hd, which is 40G.  After restarting, I didn't get any system sound like I had while using the live kubuntu cd.  So, I booted back in with the live cd, and checked what the settings were in KMix, and I clicked on the speaker icon in the lower right hand kicker panel, and it showed the volume at 0%.  Right clicking icon, I bring up "show mixer window", and it shows "current mixer" as CA0106, The pull down menu shows the other option is VIA8237.  

So, I then boot into the installed kubuntu, and I get no sound, put my cursor over the speaker icon, and it shows volume 80%, and I bring up "show mixer window" and it shows "current mixer" as VIA8237.  I see that the other option in the menu is CA0106, and so I select this, thinking this will solve my problem as this is what works for my card.  But I still get no sound when I do a sound test under system settings > sound system > test.  And, when I reboot, KMix defaults back to VIA8237.  I have an external AGP slot audio card, as shown in my signature.  It is listed as an Audigy line, and this is what some of the commands show:

```
aplay -l outputs:
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I can bring up alsamixer when I type in the command alsamixer.

and this command shows:
```

$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9761A+ at 0x1000, irq 18
 1 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0410] at 0xd000 irq 19
```

and this lspci -v command gives me this:
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Subsystem: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: e0000000-e00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <access denied>

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs SB0410 SBLive! 24-bit
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d000 [size=32]
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: VIA Technologies, Inc. VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
        Flags: bus master, medium devsel, latency 32, IRQ 16
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at d400 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: VIA Technologies, Inc. USB 2.0
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at e0100000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: VIA Technologies, Inc. DFI KT600-AL / Soltek SL-B9D-FGR Motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Flags: medium devsel, IRQ 18
        I/O ports at 1000 [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device c00a
        Flags: bus master, stepping, 66MHz, medium devsel, latency 32, IRQ 20
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at e0020000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at e0000000 [disabled] [size=128K]
        Capabilities: <access denied>
```

Someone said I could add  some entries at the bottom of my etc/modprobe.d/alsa-base text, but I don't know what to add.  Here's my current alsa-base text
 
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

If all else fails, I may end up following this suggestion.
 
[http://www.mail-archive.com/alsa-user%40lists.sourceforge.net/msg21618.html](http://www.mail-archive.com/alsa-user%40lists.sourceforge.net/msg21618.html)
 
The tar file is on my desktop ;)

Alsa home page says they haven't completely made a working driver for my particular audio card, but why does it work in ubuntu feisty fawn,  Does ubuntu feisty fawn use alsa,  and why do I get sound in the kubuntu live cd?  And how can I set CA0106 as default mixer, if this is where my problem lies. I  hope I have given enough clues.  

Thanks to anyone that checks this out.  I do appreciate it.

Lisa  Marie

---

### Post by Cubby on 2008-02-02
Well, well, well,

got up this morning, turned the compooter on, and I heard the wonderful "la la la la" system sound after the desktop showed its beautiful face.  I moved the cursor over the speaker icon, and it shows the pleasing number of "volume at 0%" as well as mixer being set as CA0106.  Odd, because yesterday when I'd reset it via Kmix to this by clicking on it in "current mixer" pull-down menu ( the other being the Via one, which is the default one that was chosen during installation), and then restart the system, it would revert back to Via8237 and no sound.  This time my choice stuck.  Maybe it was because I did a cold boot, and maybe it was because it was long enough time for the on board audio, Via, to have a talk with my AGP audio card by Creative Labs, and they came to an understanding that said human, me, wanted things different.  

Oh, just to let you know that when I install LINUX, in BIOS I have PNP turned off, as well as disable the on board video card.  

I'm happy now.  I hope this is a lasting effect. :)

P.S.  I was wondering if doing some of those commands I listed above in code had anything to do with things working out now.  Just curious as Holmes.
For now I'll leave the current ALSA driver version installed, which is 1.0.14-1.  I also notice kubuntu 7.10 has libstreamer and libstreamer plugs-ins installed, and that is it from the long list of gstreamer stuff.
Regards, Lisa Marie

---

### Post by DMK62 on 2008-02-02
Hi

Computers can have a mind of their own at times, things sometimes seem to automagically work.

Even though you have pnp disabled it doesn't necessarily mean the hardware doesn't get polled during installation. You said you have on board video disabled...was that supposed to be onboard audio ? If not, try disabling that in bios if the problem comes back again.

I don't think any of the commands had any effect on things working. They were just showing the hardware that the OS can see.

To the best of my knowledge most KDE apps like kaffeine use xine by default instead of gstreamer. On kubuntu I use some apps like Totem with the gstreamer plugin. You will find a lot of debate over which is better. Some videos I watch don't work in kaffeine but will work great in Totem ( gstreamer ).

In case you want to know which ones I use, here are the terminal commands to install them...

sudo apt-get install gstreamer0.10-ffmpeg

sudo apt-get install gstreamer0.10-pitfdll 

sudo apt-get install gstreamer0.10-plugins-bad 

sudo apt-get install gstreamer0.10-plugins-bad-multiverse 

sudo apt-get install gstreamer0.10-plugins-ugly 

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

Also if you notice a lot of hard drive activity and your system seems to slow down it can be caused by an indexer named Strigi. They have fixed some of the bugs since last fall but some prefer to remove it and use Kfind instead.

sudo apt-get remove strigi-*

If you run into proprietary formats needing the win32 codecs the package for them can be downloaded from [http://www.medibuntu.org](http://www.medibuntu.org) . You can add them to your repository list or just directly download.

I still have this thread bookmarked and will check it from time to time. If you have any additional questions about the audio, kubuntu, or the additional info I gave let me know and I will try to get back to you asap.

Dale

---

### Post by DanielTJ on 2008-02-03
**The situation: **
[LIST]
[*]5.1 mother-board integrated audio card, Intel ICH7 family, Asus motherboard
[*]audio panel on front of the case
[*]2.1 logitec ssound system (1 woofer and 2 speakers)
[*]snd-hda-intel module loaded
[/LIST]



I have a little problem also. After following several howto's I managed to get sound in the front 3mm Jack, but it is mono!
The Jack on the back still does not work. But if i plug the green audio cable, in some other other output, one of the speakers work. 
Alsa mixer settings does not help. I tried every single possiblity. so it is not the volume or anything.
I have the Idea, that the kernel thinks I have 3.1 audio card, and sends the signal to a wrong output. I also added the option with stack=3 at the end of /etc/modprobe.d/alsa-base file.

Please help me!

---

### Post by Cubby on 2008-02-03
> **DMK62 said:**
> Hi

Computers can have a mind of their own at times, things sometimes seem to automagically work.

Even though you have pnp disabled it doesn't necessarily mean the hardware doesn't get polled during installation. You said you have on board video disabled...was that supposed to be onboard audio ? If not, try disabling that in bios if the problem comes back again.

Hi Dale,

And thanks for the additional information.  You're terrif!

I booted my system up this morning and guess what? No sound.  Kmix shows it is using Via8237 and if I change it back to CA0106 and then test the sound in system settings > sound system I get nothing.  I restart the computer and Kmix shows it reverts back to Via8237.  My husband always says to give a new OS a week before  proclaiming it to be stable.  I guess I spoke to soon.  It was nice to be able to use Amarok for the day.  I really like that player!

Anyway, I'll be searching for a solution to this as many others are having a similar problem.  

Oh, and I did mean on board audio.   Thanks for the noticing this and letting me know about PNP.  

It seems to me more of a Kmix problem than an ALSA base driver problem.  I'll look into how to force Kmix to use the CA0106 mixer by default.  Just a guess.  If anything, I can experiment with using the latest alsa driver 1.0.15 just to see if this solves my problem.  I've just reinstalled kubuntu, so it's not a loss if I have to do another reinstall, or switch back to ubuntu feisty fawn.

Thanks again!
Kind regards,
Lisa Marie  

[COLOR="DarkGreen"]Hey DanielTJ, what ubuntu version are you using?[/COLOR]

---

### Post by DMK62 on 2008-02-03
Hi 

Out of curiosity did you ever try installing Ubuntu Gutsy Gibbon 7.10 ( gnome version of Ubuntu ). If so, did the sound work ? KDE differs from gnome in that it has an additional layer in the sound system called aRts. Unfortunately with linux when it comes to hardware it is a case of doesn't work, works some of the time but is not predictable, or just works. 

You can run amarok in Ubuntu ( Gnome ). It takes a couple more seconds to load and might have a few small quirks but nothing that really impedes on its function. 

If you look back on my posts to JTB you will see that it can come down to finding a version of ubuntu / linux that works with as much of your hardware as possible. Some will debate my opinion but when it comes to the current releases of ubuntu and kubuntu I would recommend ubuntu. It's on a much more predictable release cycle ( Gnome vs KDE DE's ) and has more devs working on it whereas kubuntu and kde is sort of a mixed bag with a foot in kde 3.5.x and slowly working towards 4.x. From my experience you have to put more effort into kubuntu as it stands now.

Have you looked at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)  ?

It's a very lengthy post but a solution may be hidden somewhere in the 80 + pages.

Dale

---

### Post by Cubby on 2008-02-03
Hi again, Dale,

I did try ubuntu feisty fawn, and only recently did I switch back to kubuntu gutsy gibbon.  Sound worked fine in ubuntu ff.  

Yes, I knew I could install amarok in ubuntu, but for now, I'm trying to give kubuntu a chance, as I am more comfortable with the kde desktop.  I've even heard of many folks that run the kde desktop in ubuntu, but I'm trying to keep the processor free from doing any extra work than it has to, as well as RAM.  

I will agree with you on ubuntu being more stable.  I think maybe that is because there is more work being done, than say kubuntu and kde desktop as ubuntu, to my knowledge, has always been a gnome first os.  I'm glad the folks at ubuntu  have put out a kde version, though, and they've done a fine job with it.  One thing I notice when I run kubuntu is when it first boots up,  my LCD screen will have the autoconf window pop- up and say, "input not supported", then the pop-up will switch to "auto config please wait", (the normal auto config window that pops up when Windows boots up, or when ubuntu feisty fawn booted up), and then it changes to a window that says, "signal not found", and that goes away and the system comes up as normal.  So this tells me ubuntu is more stable.  If I was more LINUX knowledgable, I could probably alter the grub config file, but for now, I don't mind these "hesitations" at boot up;

I came in here to let you know I decided to take the alsa-base driver 1.0.15 installation plunge, (the link I posted above) and I just did a cold boot and I have sound!  Kmix is showing mixer default as CA0106.  I will definitely let you know in a week if this is stable and keeps working, whether I restart the 'pooter or boot it up.  If it works, then this solved my problem.  The alsa home page has a section where you can look up your audio card and see if it is supported.  Mine was iffy, by Creative Labs of the Audigy line, and maybe this is what did the trick as the fine folks at the alsa team have been trying to support more and more audio cards.  

Again, thanks again Dale for all the excellent help.  Again, I'll poke back in here after a week to  let you know how it goes.

Oh, I installed automake 1.7 before I installed the .tar file.  I also followed the instructions by installing "build-essential" via terminal, via the kubuntu installation disc.

Take care,
Lisa  Marie

---

### Post by Cubby on 2008-02-03
nope, that didn't do the trick...

I just did a cold boot and no sound, and Kmix was back to the via8237 mixer.  Just to mention this so other folks won't think this was the answer to my problem and switch to the newer alsa-base driver.  

In Kmix, I did reset it back to CA0106 mixer, and restarted and I got sound.  Obviously, this is a random problem and has nothing to do with changing alsa-base driver.  

Back to the drawing board, and I'll probably swich back to ubuntu feisty fawn after I do a bit more searching on the problem.

---

### Post by DMK62 on 2008-02-03
Hi

I found this on a Mandriva forum on how to specify the sound card to be used. It can be used when there is more than one sound card. Maybe it will stop the AC97 from loading and with a little luck the sound will work. 

Here are the instructions on the page ( note: you can get to sound system via kcontrol or system settings )

 Open a terminal and execute:

$ cat /proc/asound/cards

You'll see something like this:

0 [V8237 ]: VIA8237 - VIA 8237
VIA 8237 with CMI9761 at 0xe400, irq 18
1 [Phone ]: USB-Audio - VoIPvoice USB Phone
PDT VoIPvoice USB Phone at usb-0000:00:10.0-1, full speed


The sound device names are in the square brackets.

In KDE Control Centre -> Sound and Multimedia -> Sound System -> Select the
audio device: "Advanced Linux Sound Architecture".


Activate the "Override device location:" and insert e.g. hw:V8237 (use the
name of the device you want KDE to use) into the corresponding text field.


Re-start KDE.

KDE apps should now use the selected device. For non-KDE apps, I think you'll
have to use the app's own configuration tools.

---

### Post by Cubby on 2008-02-03
Hi,

I want to experiment and try that. 

I'll tell you what I did try.  Since Kmix keeps defaulting back to the Via8247 card, I found a bug report where installing asoundconf-gtk would work.  I selected it via adept and it installed it with some other required python packages.  I went to my kde pull down menu, found it listed under settings and selected CA0106.  I did a cold boot and got sound, and did a restart and got sound.  Kmix is showing mixer as the correct CA0106 for default card both times.  I'm still holding my breath that this won't hold, or maybe this is just a patch to a bug, but so far so good.  I'm going to uninstall it and try your found method just to experiment and let you know how it works.  I don't mind doing this.  I'm curious to try.

This fellow had the same problem, as he exclaimed, "How do I force it to use the right one please, i.e. the CA0106?" 
[http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-no-wireless-ubuntu-studio-578533/](http://www.linuxquestions.org/questions/linux-newbie-8/no-sound-no-wireless-ubuntu-studio-578533/)

---

### Post by DMK62 on 2008-02-03
Hi

Thanks for the link. Great to see you jump in with both feet and not afraid to try different solutions. I have found that you learn a lot that way and even if you end up hosing the system you learn along the way.

I can understand your preference for kubuntu and kde. I run both ( separate installs ) and when in gnome I often find myself thinking of features in kde that would really come in handy. The current version of Ubuntu would prob run well with your cpu but you have an older Radeon that could end up not working well. Ubuntu runs ok on my system but nowhere near as fast as kubuntu.

If adept gets on your nerves ( it crashes off and on ) you can always install synaptic. It works well under kubuntu. I use synaptic for installing packages and use adept or the terminal for system updates and upgrades.

Dale

---

### Post by Cubby on 2008-02-03
Hi Dale,

That worked!

I wanted to make sure I was doing your suggestion under a basic installation of kubuntu, without the latest alsa-base I installed, and any other things I may (or should that be might?) have changed.  So, I did a clean install of kubuntu, did my usual using gnome partition editor live cd to halve my 40G hardrive, extended the swap and extension a wee bit, created a 18 G fat32 partition and logged into the new install.  No sound. Tested it to see if I got sound by restarting.  No sound.  Set Kmix to mixer CA0106 instead of the default VIA 8237, and got the usual - reverted back to VIA - no sound.  That satisfied me that there was a true problem.  

I then went to terminal and did the command and got:

$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with CMI9761A+ at 0x1000, irq 18
 1 [CA0106         ]: CA0106 - CA0106
                      Live! 7.1 24bit [SB0410] at 0xd000 irq 19


Then I did as you instructed and went to KDE > system settings > sound system > hardware > I selected Adv. Li. Sound Arch. Then ticked "override device location" and entered:

hw:CA0106

the card I want to use, then clicked "apply".  Closed that window.  I don't know if I needed to do this next step, but I right clicked on the KDE icon in kicker, and clicked on menu editor, then clicked the save icon and it said it "updating system configuration" (an old habit from when I used Simply Mepis KDE desktop).  Then restarted the computer.  Got sound.  I smiled.  I then laughed because when I right clicked on the speaker icon in the panel and clicked on "show mixer window" it shows as "current mixer" VIA 8237.  Ha!  And I get sound in spite of it.

I did a cold boot.  Got sound.  Did another restart or two and got sound.  I think I can leave you alone.  You've been such a tremendous help for me and it turned out to be a solution where I didn't have to add more packages, like the one I did with the package asoundconf-gtk, or installing another alsa-base driver.  This was a straightforward, simple solution.  Oh, you'll hear from me if it doesn't last. *grin*.

Yeah, I like ubuntu, but now I get to stick with kubuntu for a while.  At least we kubuntians get to select our gamma in "monitor and display", whereas ubuntians have to edit their xorg.conf file, according to this gentleman's page:

[http://www.antoinegirbal.com/?page_id=13](http://www.antoinegirbal.com/?page_id=13)

Have a great evening and week, Dale.  Again, thank you so much!  I appreciate your help!

Lisa Marie

---

### Post by DMK62 on 2008-02-03
You are very welcome.

See how it works over the next while and if you run into any issues let me know. I've enjoyed helping out both JTB and you with the sound problems. From his last communication his ubuntu / xubuntu system is running smoothly and the sound is working properly with all installed programs.

Funny that you mention the gamma as it's one of the features that I miss not having in gnome. 

I just noticed that as far as irq assignments go that the via 8237 is at irq 18 and the audigy at irq 19. Just wondering if a lower irq gets selected first during boot. But, as long as it continues to work that can be left alone for now.

Hope you also have a great week. Kick up your feet and listen to some tunes on amarok. I will be taking it easy this week as I sprained my wrist while falling on ice ( over a foot of snow on top of ice ) on Friday and then managed to wipe out another 3 times yesterday and injured my shoulder. 

Dale

p.s. I just noticed something that you can check if it doesn't resolve the problem use hw:SB0410 instead of hw:CA0106 and see how that works.

---

### Post by Cubby on 2008-02-04
"la la la la la"

Yep, I have sweet sound.  I just booted up the computer after a long day.  Gustav Mahler Symphony No. 5 playing in Amarok, while our cat jumps at the window saying he wants out.

Yes, when I was usuing ubuntu the contrast was too high so I set mine at 0.6.  

The irq assignment order does make sense.  I have the BIOS set to auto set the irq's.  I'll look into this as it is something that I do not know much about, but would like to learn.  There's lots of info. at my disposal via the internet.  What would I do without internet access - it always amazes me at the information out there, some not so good, but some that can really make a difference in solving a problem.  I'm always thankful for folks that are of help.  Like you!

Ice storms.  Something I've lived through three times since moving east of the Rockies.  
I like snow.  Give that wrist a decent rest.  

Oh, some folks mention something about putting in manual settings in monprobe.conf file, but I don't see one on my system, even with hidden files showing.  I only have monprobe.d folder which includes the text file alsa-base.  Anyway, I've heard of some people adding a line at bottom of the monprobe.conf to manipulate which cards are selected first.  I wish I had the link about it, but anyway, I'm happy to say that sound is working well so for, and in kde devices such as amarok.  I'll see how sound works when I someday install mplayer.  I need to install that player when I install k9copy, as it uses mplayer.  I'll let you know how things go when I get to that point.  I'm just enjoying things as they are, no problems.  Even my mount issues are not an issue any longer.  When I stick a disc in, whether it is audio cd or data, it shows it as mounted while it is in the optical device.   (don't mean to go on tangent)

Thanks so much, and take care,
Lisa Marie

---

### Post by Cubby on 2008-04-06
Hi,


After recently reinstalling kubuntu gutsy gibbon I managed to come across the how-to to edit the modprobe.d file here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

as I was having a problem with the disabled on board sound (via) reverting back to default, in spite of attempts to get my installed sound card (Sound Blaster Audigy) to be the default.  
In the
kdesu kate /etc/modprobe.d/alsa-base 
file I added the two lines which gave the card I wanted to use the index zero, so it is read first.

options snd-ca0106 index=0
options snd-via82xx index=1

and hit "save".  Now I get system and media sound whether I cold boot or restart the system, each and every time and the kmix soundmixer stays at ca0106.

I was also having this same problem in ubuntu feisty fawn, and did this fix 
[http://ubuntuforums.org/showthread.php?t=712908](http://ubuntuforums.org/showthread.php?t=712908)

but it only worked at cold boot, but not on restart.

Regards!

---

