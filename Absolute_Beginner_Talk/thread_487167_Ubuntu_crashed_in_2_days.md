---
title: "Ubuntu crashed in 2 days"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by JAmerican on 2007-06-28
I posted the information below in this thread...

[http://ubuntuforums.org/showthread.php?t=486945](http://ubuntuforums.org/showthread.php?t=486945)

My issue pertained to 64-bit so I posted it there. Realizing that no one was helping me, I decided to post this here...

--------------------------------------------------------------------------------

Hey all,

I am a new comer to Ubuntu and Linux. I've been a Windows guru and fanboy for some time. I have also purchased a PowerBook G4 to better understand Mac OS X. Having come to like the stability of Mac OS X (being that its really just Unix under the hood), I decided to do the same to my PC. Having installed Ubuntu AMD64 Feisty Fawn on my PC, I came into some problems. I didn't want to have to deal with the terminal and it seems like you need to in order to install an application. In any regard, I installed the NVidia drivers by enabling the Graphics Acclerator.

The problem started when I tried to install the RealTek HD Audio drivers. My PC didn't take them and I started having libasound.so.2 shared library missing errors. I read on the forums to try something and now I cannot see my Ubuntu GUI login screen. I just seen the command prompt. I also think that the Firefox 32 Flash Fix contributed to the problem greatly. I am going to reinstall Ubuntu again but I have a few questions:

Is it better to partition the drive for the OS and regular storage?

If so how do you make the storage partition the default for applications so that the OS partition does not fill up?

Where can I find RealTek High Definition drivers for Linux that won't crash my PC?

What can I do to prevent such a catastrophic problem as this one from happening again?

I thought Ubuntu would have been easier to use and start with but it seems way harder with the constant Terminal codes? Is there a guide that relates Windows commands or actions with Ubuntu commands or actions?

As for my hardware, I have a Shuttle SN27P2. Can I get some suggestions as to where I can get drivers for my hardware?

Also is there a recovery mode or repair mode of some kind? I tried using a guide that told me to use the Live CD but with every command, the terminal windows replied with 0 changes, 0 updates, 0 etc...

Please help. After this experience, I felt like going back to Windows but I am willing to live though this and make Ubuntu or just Linux in general work for me. 

To get an idea of my background. I am a person who likes to program in Visual Basic .NET 8, uses Windows Mobile 6 Smarthpone (T-Mobile Dash), uses Macromedia Fireworks MX 2004 to create images and logos, used to play games on my PC until I got a 360. If anyone has had better luck with another distro with my kind of personality, please suggest it. I just want to leave the headache that is Windows XP. As for my Dash, its my first Windows Mobile device. I used to be a Palm OS person. So I am not a M$ fanboy throughout. It just looks that way.

BTW, my Ubuntu Linux install is on a 120 GB HDD by itself and I partitioned the drive to have 8GB for Ubuntu OS and the rest for storage.

Could someone also tell me how much swap is necessary?

Thanks all. Looking forward to replies. Here is my site as well where I posted basically what I said above...

[http://www.jamerican.net/?p=39](http://www.jamerican.net/?p=39)

JAmerican

---

### Post by JAmerican on 2007-06-28
I'm going to try Kubuntu this time since KDE is more like Windows and has one taskbar instead of two. I hope this one doesn't crash on me :(. I may have to consider going back to Windows if this doesn't work out for me.

JAmerican

---

### Post by p_quarles on 2007-06-28
I have a RealTek sound card myself, and it works just fine with the default drivers. No advanced graphical equalizer, unfortunately, but the sound is (with a few exceptions) always great. I don't know if they even have drivers designed for Linux. 

You don't have to use the command line to install the vast majority of applications. There are two GUI tools that will do this for: Add/Remove under the Applications menu, and the Synaptic Package Manager under System >> Administration. 

You'll have a much better time in the long run, though, if you do try to learn the command line. I highly recommend Scott Granneman's _Linux Phrasebook_. 

Your partitions sound fine. I'm thinking 1 GB should do it for a swap, but I'll defer to anyone who contradicts me. 

Hope this helps.

---

### Post by p_quarles on 2007-06-28
> **JAmerican said:**
> I'm going to try Kubuntu this time since KDE is more like Windows and has one taskbar instead of two. I hope this one doesn't crash on me :(. I may have to consider going back to Windows if this doesn't work out for me.

JAmerican
Kubuntu's slightly different, but just as good. FYI, I was a lifelong Windows user as well, and it only took me a few days to get used to the Gnome interface. If you find you don't like Kubuntu, but still don't like the start menu at the top of the screen, you can right-click on it and move it to the bottom of the screen.

---

### Post by silverglade00 on 2007-06-28
You might want to create a partition for /home. This will let you reinstall without losing your settings and personal files. As for Kubuntu, I love KDE, but I have nothing but problems with Kubuntu on 3 laptops. It seems like Kubuntu is just an afterthought. You might get better luck with installing Ubuntu and then installing the kubuntu-desktop package in it to use KDE. If you want to try a very easy KDE distro, I would highly suggest PCLinuxOS. It is my favorite distro, but I am using Ubuntu because it has an updated kernel with features that I need to run my hardware.

Your swap should be twice as large as your RAM. Most drivers are in the kernel, so there is no need to run off to multiple websites spanning 15 countries in search of a particular driver like in Windows. It looks like you are having sound troubles, in which case you will want to research snd-hda-intel in the forums. I had a realtek sound chip before and it couldn't be used in Linux for a while. Now most of them are supported, but you might have one of the problem ones.

Good luck!

---

### Post by cogadh on 2007-06-28
I think you aren't getting fast answers because that is way too much information. Next time try to deal with this one problem at a time instead of a huge shotgun blast of questions. These kinds of posts tend to overwhelm.

Partitioning - It is often recommended that you create three partitions minimum for your install; one for swap, one fore your /home and one for / (root). By default, Ubuntu will only create the swap and / partitions. By creating a seperate /home partition, you can protect you documents in settings in the event you need to do a reinstall of the OS.

Installations - Someone smarter than I will have to take the bulk of this one, but I believe that the software package determines the install location by default. You may be able to specify an install location on a per-package basis, but I don't believe you can change that globally. Many applications will already install in your /home directory by default

RealTek drivers - The only ones I know of are available from [RealTek website]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false"), if those are the same ones you already tried, then I don't know what else to suggest.

Catastrophic problems - Well, if we are able to come up with solutions for your other questions, you won't have catastrophic problems. But the advice above on partitioning will limit the impact of any new problems.

Terminal Codes - I use [this website]("http://www.onlamp.com/linux/cmd/") for referencing basic Linux terminal commands. However, almost everything that you can do with the terminal can now be done with a GUI. Is there a particular task that you were having a problem with?

General drivers - Nearly all of the mobo drivers are already part of the Linux kernel, there are no additional drivers to get. Is there a particular piece of hardware you need to find drivers for (i.e. network card, video, etc)?

Recovery mode - When you boot Ubuntu, the boot loader should present you with at least three boot choices (more if you dual boot or update your kernel). The first one is standard boot, the second is a console boot (i.e. no GUI) that is generally used like the Windows Recovery Console. The third is a memtest boot, for testing the status of your system memory.

Swap - Same as Windows 1.5 to 2 times your system RAM.

I think that is about all I can cover for now, hopefully this helped some.

---

### Post by p_quarles on 2007-06-28
> **cogadh said:**
> Recovery mode - When you boot Ubuntu, the boot loader should present you with at least three boot choices (more if you dual boot or update your kernel). The first one is standard boot, the second is a console boot (i.e. no GUI) that is generally used like the Windows Recovery Console. The third is a memtest boot, for testing the status of your system memory.

The boot options actually ONLY come up if you're dual-booting. If you only have a single OS installed, the GRUB screen comes up for about 3 seconds and you need to hit escape for the options.

---

### Post by JAmerican on 2007-06-28
OMG thanks for the replies guys. I was getting discouraged by no one responding to me. Next time I have to look for the Beginner's forum. LOL. 

I love the way Kubuntu looks so I am going to install it. It feels more buggy than Ubuntu though but I hope thats just because of the Live CD. 

Thanks for the swap tip. I have 2GB of RAM and was using 2GB of Swap. I'll increase that. :)

As for /home, I was using /media/hdb5. I'll rename it with the new install.

@p_quarles: How did you get your sound to be louder? My sound is way too low. Even with everything turned up. 

Thanks. 

JA

---

### Post by JAmerican on 2007-06-28
So this is my set up...

10GB root ext3 filesystem
4GB swap
remaineder /home ext3 filesystem

I have a SATA drive with Windows XP on it and I installed a Ext2 filesystem library to read/write to ext3. That way I don't have to make my Linux partition depend on M$ Fat32.

It is installing now and I'll let you all know how it goes. I'll definately be posting more here for help in setting up and so on. 

Thanks again :) Kubuntu is so quick and looks great.

JAmerican

---

### Post by p_quarles on 2007-06-28
> **JAmerican said:**
> @p_quarles: How did you get your sound to be louder? My sound is way too low. Even with everything turned up.

I didn't have to do anything, actually. Are you using a laptop? My RealTek card is on a desktop with external speakers, and 40% volume works fine for me. If you're also on a desktop, I'd just buy some cheap, used amplified speakers. With a laptop, obviously, there's less you can do.

---

### Post by swoll1980 on 2007-06-28
You can switch to kubuntu with out doing a install just put this command in the terninal

sudo aptitude install kubuntu-desktop

---

### Post by Josey on 2007-06-28
If you use this command you can switch between ubuntu's default gnome desktop and kubuntu's kde desktop environment at will from the login window.
```
sudo aptitude install ubuntu-desktop
```
or just find ubuntu-desktop in synaptic package manager if the terminal isn't your cup of tea.

---

### Post by JAmerican on 2007-06-29
Hey guys,

I installed Kubuntu but I can't get the nVidia drivers to work correctly. I tried Envy, Automatix, Nvidia-glx-new, nvidia-glx. what else is there to try because all these just give me a blinking cursor and a black screen.

My card is an nVidia GeForce 7600GT. Please help. I was able to get back the original crappy quality by configuring the xorg.conf from nvidia to nv. Anyone know how I can get this to work. I got it to work fine in Ubuntu by turning on Nvidia 3D accelerator and Desktop Effects. 

JAmerican

---

### Post by JAmerican on 2007-06-29
Going to reinstall Ubuntu. Yes I know I can do a command line prompt but I tried that and I don't see the Nvidia graphics option anymore. So I am going to just reinstall Ubuntu. seems like there is more support for it anyway. I'll let you all know how it goes.

Kubuntu was just not working out with the NVidia drivers.

JAmerican

---

### Post by JAmerican on 2007-06-29
I love how fast it reinstalls :). I am back on Ubuntu and got Nvidia working great :). Kubuntu needs more work IMHO. 

I still need help increasing my volume. I need RealTek HD Audio drivers.

JAmerican

---

### Post by cogadh on 2007-06-29
Go to the RealTek website, they have Linux drivers, believe it or not.

---

### Post by JAmerican on 2007-06-29
> **cogadh said:**
> Go to the RealTek website, they have Linux drivers, believe it or not.

Last time I tried installing those, I think I lost my UI. But I am not sure if it was because of the drivers or the steps I took to get Firefox 32 with Flash working.

How do I insure that I won't end up without a UI again?

JAmerican

---

### Post by JAmerican on 2007-06-29
Ok I installed their drivers and while I still have my UI. I get an error saying that my session was terminated in less than 10 seconds. When I press OK. I am returned to the login screen. Any way to fix this.

I think this is one of the deterrents to moving to Linux is because its so hard to start with and almost anything can break it. :( There should be a safe guard in place so that if something does cause such an error, there is a way to restore your previous settings like Windows has. Just a thought for the devs.

JA

---

### Post by JAmerican on 2007-06-29
anyone?

JA

---

### Post by sci-fi guy on 2007-06-29
I am in much the same boat as you when it comes to installing the RealTek drivers. I lost my GUI when I tried, and had to reinstall.  It sounds though as if you have a problem with extremely low volume, whereas I have no audio whatsoever. I hope that someone figures this out soon!

---

### Post by p_quarles on 2007-06-29
If you installed the 32-bit version of Firefox, I'm guessing that you're running the 64-bit version of Ubuntu? 

A lot of people have had problems with that. You might try going for the 32-bit OS. It won't be much slower, and it will be more stable with certain components and applications. I think the 64-bit version is more for people who are very comfortable looking under the hood, which is why I haven't bothered with it.

---

### Post by sci-fi guy on 2007-06-29
You are probably right about him being on 64-bit. But I don't think the architecture has anything to do with this. When I lost my GUI I was on a 32-bit system.

---

### Post by p_quarles on 2007-06-29
I just looked around on Realtek's site, and noticed something pertinent: the Realtek HD drivers seem to be available only kernel versions 2.2 and 2.4. That could be the problem.

---

### Post by sci-fi guy on 2007-06-29
That did concern me, but I figured that if it worked then, it should work now.

---

### Post by JAmerican on 2007-06-29
> **JAmerican said:**
> Ok I installed their drivers and while I still have my UI. I get an error saying that my session was terminated in less than 10 seconds. When I press OK. I am returned to the login screen. Any way to fix this.

I think this is one of the deterrents to moving to Linux is because its so hard to start with and almost anything can break it. :( There should be a safe guard in place so that if something does cause such an error, there is a way to restore your previous settings like Windows has. Just a thought for the devs.

JA


Fixed it thanks to this poster...

[http://ubuntuforums.org/showpost.php?p=2850542&postcount=7](http://ubuntuforums.org/showpost.php?p=2850542&postcount=7)

**apt-get install --reinstall libasound2**

This only allowed me to see my desktop again. I tried removing alsa drivers and other audio drivers. Now I have no audio even though I reinstalled them all.

JAmerican :)

---

### Post by sci-fi guy on 2007-06-30
Thanks for posting that line... I will likely be more willing to experiment if I know I can get my desktop back.

---

### Post by sci-fi guy on 2007-06-30
> **Josey said:**
> If you use this command you can switch between ubuntu's default gnome desktop and kubuntu's kde desktop environment at will from the login window.
```
sudo aptitude install ubuntu-desktop
```
or just find ubuntu-desktop in synaptic package manager if the terminal isn't your cup of tea.

Could you please explain this in a little more detail? I already have ubuntu-desktop installed but don't know what to do next.

---

### Post by JAmerican on 2007-06-30
OMG!!! MAJOR BREAKTHROUGH!!! :)

MY AUDIO IS LOUD AND CLEAR except Flash  :(. Still working on that.

Thanks to this poster: [http://ubuntuforums.org/showpost.php?p=2823123&postcount=2](http://ubuntuforums.org/showpost.php?p=2823123&postcount=2)

If you need a High Definition Audio (HDA) Driver, this is the best way that I got my Realtek ALC882 HD Audio to work and sound great. 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Don't worry about the fact that you have to type intel or intel is there. I did it and I have nothing dealing with Intel in my machine. I believe the HDA drivers are pretty generic and companies just put their names on it. 

Oh well it works. That's what matters.

Use the alsamixer and alsamixergui from the Synaptic Package Manager to increase the sound. I increased the Subwoofer, Center and LFE and my music became much louder and clearer.

As I said, now I am off to fix Flash. I have it working smoothly (moreso than in Windows and Mac OS X) just no audio. So I hope to get it working in Firefox with Sound. Opera is weird IMHO. ;)

This Ubuntu thing was annoying at first but it becomes so much fun when you find what your looking for :).

JAmerican

---

### Post by p_quarles on 2007-06-30
Glad you got it working.

A word of warning, though: based just on reading the posts in this forum, Flash seems to be one of the most difficult things to get working on a 64-bit system. I've seen some workarounds suggested, but they seem to be hit-or-miss for different people's machines. Just keep in mind that you CAN switch to 32-bit Ubuntu if you ever find you've had enough. 

Best,
p_quarles

---

### Post by sci-fi guy on 2007-06-30
For flash, I recommend Gnash.  Look for it in Symantic, and restart Firefox. It works perfectly for me with the singular exception that I don't know how sound is (I am about to try that fix you posted about).

---

### Post by JAmerican on 2007-06-30
Reinstalling Ubuntu again. Lets see if I can get Flash to work after a clean install.

JAmericane

---

### Post by JAmerican on 2007-06-30
OMG UBUNTU IS AMAZING!!

This partition thing is doing wonders for me. I reinstalled Ubuntu on my root partition which removed some audio and video libraries but my desktop, theme and even mouse were the same as before. Its the best way to reformat your OS and it works great :). 

So I installed the NVidia graphics accelerator that comes with Ubuntu and it worked great.

My audio was low so I just enabled the Surround, Center, LFE controls in my Volume control and max them out. My sound was loud and clear. No additional drivers or installs needed. (This is for a HDA ALC882 HD audio and possibly other High Definition Audio chipsets)

I then installed the nspluginwrapper and started Firefox-64bit and watched Family Guy with no problems :).

I love this forum and I love this OS. Thanks guys. Next challenge is TV tuner application. I tried MythTV before but was having issues. I'll let you all know how it goes :popcorn::p:D

Thanks Kilz for the late night help.

JAmerican

---

### Post by sci-fi guy on 2007-06-30
No luck for me in HDA.  Is there any reason that Gutsy will solve this problem when it becomes a full release?

---

### Post by JAmerican on 2007-07-01
> **sci-fi guy said:**
> No luck for me in HDA.  Is there any reason that Gutsy will solve this problem when it becomes a full version?

What is exactly your chipset. Mine is RealTek ALC882 HD Audio. When you install Ubuntu, is your volume low or do you not hear anything at all? If your volume is low, don't install anything else. You just need to increase the volume. I just need more info like what card you have. I know you have a HD Audio card so hopefully its a similar fix.

JAmerican

---

### Post by sci-fi guy on 2007-07-01
Not sure how to find out what chipset I have. Is it under Hardware Information? If so, it is:
82801G (ICH7 Family) High Definition Audio Controller

No, I do not have any sound whatsoever.

---

### Post by dfreer on 2007-07-01
Also, check out your alsamixer and make sure that the volumes on everything is turned up to 100, and then adjust the volume in the OS. See if that helps. It may just be a bug.

---

### Post by Raineer on 2007-07-01
> I love the way Kubuntu looks so I am going to install it. It feels more buggy than Ubuntu though but I hope thats just because of the Live CD.
I'm in the same boat, I went back to Gnome just because I can't stand how buggy KDE is. I constantly had "kdeinit" issues, especially if I had a lot of windows open.

I love the interface though, and I'm excited when KDE 4.0 comes out later this year. I'm better for the experience, it was a good chance to really learn KDE and how to manage it..hopefully it will help me once 4.0 is released.

---

### Post by sci-fi guy on 2007-07-01
alsamixer and OS volume are turned up fully already.

---

### Post by cleverselfreferentialname on 2007-07-05
Everyone, at least read the paragraph on swap. I rant a couple times, I apologize.

KDE is not more like Windows, it's very different from it. I personally think it's a lot nicer than gnome, but my opinion doesn't count, I use fluxbox. See: [http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

If you're not comfortable with the UNIX/linux CLI or generally with Linux, I do suggest running 32-bit K/X/Ubuntu.

> Is it better to partition the drive for the OS and regular storage?

Yes, it is better to partition the disk with the OS and storage separate. If you have to reinstall, you don't lose your /home, if you have it mounted as such.

> If so how do you make the storage partition the default for applications so that the OS partition does not fill up?

It is highly improbable that it will fill up. Programs in Linux are dynamically linked, making them all much smaller. You would have to link /usr to something beneath wherever you mounted the storage partition (should be /home).

> Where can I find RealTek High Definition drivers for Linux that won't crash my PC?

The reason that the RealTek HD audio drivers broke your install probably has to do with the fact that they were probably compiled for 32-bit linux. If they're open source, there is probably a workaround for 64-bit. If they're closed and open drivers don't existed, you're screwed.

> What can I do to prevent such a catastrophic problem as this one from happening again?

Well, learn the command line, and it won't be as catastrophic. Whoa. Deja-vu. I've told somebody this before.

> I thought Ubuntu would have been easier to use and start with but it seems way harder with the constant Terminal codes? Is there a guide that relates Windows commands or actions with Ubuntu commands or actions?

Well, they aren't codes, using bash briefly not really full-fledged coding, and they're not terribly cryptic or related to cryptography for the most part. It's really not harder, not at all, it's just way different. You expect a GUI, but it is not there for all actions. But that's okay. The CLI offers more control, because the people who author this webserver or this clustering software do not have time to write a GUI, and learning the CLI is very good for you if you intend to break into the higher arts of computing. Please see:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

and it will be easier when it gets more familiar to you. No viruses or spyware and never having to pirate software is a nice touch :)

> As for my hardware, I have a Shuttle SN27P2. Can I get some suggestions as to where I can get drivers for my hardware?

The distro or the kernel will package the vast majority, it is unlikely that you'll need other things, but we need more detail than the in regard to the hardware. The output of 'sudo lshw' would help, and list your graphics card, sound card, and any hardware that is not working. Might want to detail those problems in a separate thread once the general issues here are resolved.

> 
Also is there a recovery mode or repair mode of some kind? I tried using a guide that told me to use the Live CD but with every command, the terminal windows replied with 0 changes, 0 updates, 0 etc...

There is a recovery mode, but if you're not used to the CLI, you're not going to like it. I am not sure what you mean by the second part of the paragraph. If you mean that apt-get did that, then the guide you were following is apparently quite unrelated to what your problems are.

> Please help. After this experience, I felt like going back to Windows but I am willing to live though this and make Ubuntu or just Linux in general work for me.

It helps here to ask yourself why you're coming to linux in the first place. If you're here for ideological reasons (software freedom as the beginning of social freedom) then you have a great reason to be on linux. If you're looking for linux to be easier or more maintenance free than windows, it'll take a month to get used to it to the point where you're more productive than you were in Windows. If you're looking to learn for the sake of learning, you're certainly in the right place. If you're looking to get into unix because you work in a tech field, you might want to start learning the CLI right now, and get a good book on UNIX.

> To get an idea of my background. I am a person who likes to program in Visual Basic .NET 8, uses Windows Mobile 6 Smarthpone (T-Mobile Dash), uses Macromedia Fireworks MX 2004 to create images and logos, used to play games on my PC until I got a 360. If anyone has had better luck with another distro with my kind of personality, please suggest it. I just want to leave the headache that is Windows XP. As for my Dash, its my first Windows Mobile device. I used to be a Palm OS person. So I am not a M$ fanboy throughout. It just looks that way.

There is an implementation of .NET called mono. I have no idea if there are good IDEs for it or anything. I have no idea whether your code from windows will run in Mono under Linux. Visual Basic is generally not portable off windows and so it's generally not a good language on which to be dependent.

Fireworks 2004 MX will not run under Wine acceptably at this point, so I would start looking for a replacement. Look at Gimp, possibly with photogimp/gimpshop (I don't like to give the impression that Gimp is a cheap replacement for photoshop, because IMO it blows photoshop out of the water), and inkscape, and krita.

> BTW, my Ubuntu Linux install is on a 120 GB HDD by itself and I partitioned the drive to have 8GB for Ubuntu OS and the rest for storage.

Good man, this is a very sane method of partitioning your disk, just be sure to mount the storage partition as your /home. Very nice, I personally would chose 8GBs myself if I had just / and /home. If you're still very concerned about filling it up, making it 16GBs would not be a bad idea, but that's only if you intend to play with a lot of different desktop environments.

> Could someone also tell me how much swap is necessary?
Less than 1GB. 'Three times your RAM' is an outdated rule. If you have 1GB, make it 256MBs, if you have 512, make it 512. You probably won't use that, even. I have 512MBs of RAM and 512MBs of swap and my swap has never reached 50% usage. It really varies with system load and other factors. The 'three times your ram' or 'two times your ram' metrics come from the age of DOS. Avoid that thinking, it's not necessary anymore. 4GBs of swap with 2GBs of RAM is really absurd. I just asked some buddies on IRC, the metric predates systems with even 256MBs of RAM, and it won't scale past 512MBs of swap.

I can see absolutely no reason that KDE wouldn't work with your nvidia drivers. Don't get the drivers from nvidia.com, do the nvidia-glx method, and make sure your xserver is configured properly for your screen and graphics card. sudo dpkg-reconfigure xserver-xorg, select the nvidia driver, enter proper identifiers for both the card and monitor (exact, it'll produce the sync rates for your monitor, which can be a lifesaver.)

> Ok I installed their drivers and while I still have my UI. I get an error saying that my session was terminated in less than 10 seconds. When I press OK. I am returned to the login screen. Any way to fix this.

I think this is one of the deterrents to moving to Linux is because its so hard to start with and almost anything can break it. There should be a safe guard in place so that if something does cause such an error, there is a way to restore your previous settings like Windows has. Just a thought for the devs.

Not 'almost anything' can break linux. 'Linux' in it of itself, the Linux Kernel, is not being broken. It's functioning absolutely fine. The reason why your UI keeps breaking is because of retarded proprietary companies not opening up their drivers or documentation. Nvidia and ATI both infringe on the copyrights of many open source and closed source projects, and that is why they do not have open drivers, because every hardware manufacturer refuses to admit that it steals intellectual property, and it refuses to fix it's own crappy code, for that matter. (I have an ATI card....I had to rant. Sorry.)

---

### Post by dfreer on 2007-07-05
.... except you need at least 1 x the amount of RAM (I believe 1.25 x the amount of RAM is recommended nowadays) to use hibernation correctly. It's true that swap was used back in DOS days to "make up for" not having very much RAM, but you still need swap if you want to hibernate your laptop.

you may not need 4 GB's of swap on a 2 GB system (simply because you'd be hard pressed to use that much RAM on a normal desktop/laptop), but recommending only 256 MB's of swap for a 1 GB RAM system is NOT a good idea. Of course I could be wrong about the way hibernation works, but I'm *fairly* confident.

---

### Post by JAmerican on 2007-07-05
> **cleverselfreferentialname said:**
> Everyone, at least read the paragraph on swap. I rant a couple times, I apologize.

KDE is not more like Windows, it's very different from it. I personally think it's a lot nicer than gnome, but my opinion doesn't count, I use fluxbox. See: [http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

If you're not comfortable with the UNIX/linux CLI or generally with Linux, I do suggest running 32-bit K/X/Ubuntu.



Yes, it is better to partition the disk with the OS and storage separate. If you have to reinstall, you don't lose your /home, if you have it mounted as such.



It is highly improbable that it will fill up. Programs in Linux are dynamically linked, making them all much smaller. You would have to link /usr to something beneath wherever you mounted the storage partition (should be /home).



The reason that the RealTek HD audio drivers broke your install probably has to do with the fact that they were probably compiled for 32-bit linux. If they're open source, there is probably a workaround for 64-bit. If they're closed and open drivers don't existed, you're screwed.



Well, learn the command line, and it won't be as catastrophic. Whoa. Deja-vu. I've told somebody this before.



Well, they aren't codes, using bash briefly not really full-fledged coding, and they're not terribly cryptic or related to cryptography for the most part. It's really not harder, not at all, it's just way different. You expect a GUI, but it is not there for all actions. But that's okay. The CLI offers more control, because the people who author this webserver or this clustering software do not have time to write a GUI, and learning the CLI is very good for you if you intend to break into the higher arts of computing. Please see:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

and it will be easier when it gets more familiar to you. No viruses or spyware and never having to pirate software is a nice touch :)



The distro or the kernel will package the vast majority, it is unlikely that you'll need other things, but we need more detail than the in regard to the hardware. The output of 'sudo lshw' would help, and list your graphics card, sound card, and any hardware that is not working. Might want to detail those problems in a separate thread once the general issues here are resolved.



There is a recovery mode, but if you're not used to the CLI, you're not going to like it. I am not sure what you mean by the second part of the paragraph. If you mean that apt-get did that, then the guide you were following is apparently quite unrelated to what your problems are.



It helps here to ask yourself why you're coming to linux in the first place. If you're here for ideological reasons (software freedom as the beginning of social freedom) then you have a great reason to be on linux. If you're looking for linux to be easier or more maintenance free than windows, it'll take a month to get used to it to the point where you're more productive than you were in Windows. If you're looking to learn for the sake of learning, you're certainly in the right place. If you're looking to get into unix because you work in a tech field, you might want to start learning the CLI right now, and get a good book on UNIX.



There is an implementation of .NET called mono. I have no idea if there are good IDEs for it or anything. I have no idea whether your code from windows will run in Mono under Linux. Visual Basic is generally not portable off windows and so it's generally not a good language on which to be dependent.

Fireworks 2004 MX will not run under Wine acceptably at this point, so I would start looking for a replacement. Look at Gimp, possibly with photogimp/gimpshop (I don't like to give the impression that Gimp is a cheap replacement for photoshop, because IMO it blows photoshop out of the water), and inkscape, and krita.



Good man, this is a very sane method of partitioning your disk, just be sure to mount the storage partition as your /home. Very nice, I personally would chose 8GBs myself if I had just / and /home. If you're still very concerned about filling it up, making it 16GBs would not be a bad idea, but that's only if you intend to play with a lot of different desktop environments.


Less than 1GB. 'Three times your RAM' is an outdated rule. If you have 1GB, make it 256MBs, if you have 512, make it 512. You probably won't use that, even. I have 512MBs of RAM and 512MBs of swap and my swap has never reached 50% usage. It really varies with system load and other factors. The 'three times your ram' or 'two times your ram' metrics come from the age of DOS. Avoid that thinking, it's not necessary anymore. 4GBs of swap with 2GBs of RAM is really absurd. I just asked some buddies on IRC, the metric predates systems with even 256MBs of RAM, and it won't scale past 512MBs of swap.

I can see absolutely no reason that KDE wouldn't work with your nvidia drivers. Don't get the drivers from nvidia.com, do the nvidia-glx method, and make sure your xserver is configured properly for your screen and graphics card. sudo dpkg-reconfigure xserver-xorg, select the nvidia driver, enter proper identifiers for both the card and monitor (exact, it'll produce the sync rates for your monitor, which can be a lifesaver.)



Not 'almost anything' can break linux. 'Linux' in it of itself, the Linux Kernel, is not being broken. It's functioning absolutely fine. The reason why your UI keeps breaking is because of retarded proprietary companies not opening up their drivers or documentation. Nvidia and ATI both infringe on the copyrights of many open source and closed source projects, and that is why they do not have open drivers, because every hardware manufacturer refuses to admit that it steals intellectual property, and it refuses to fix it's own crappy code, for that matter. (I have an ATI card....I had to rant. Sorry.)

OMG THANKS cleverselfreferentialname.

I didn't think anyone would answer all my questions in one go. This place has been very helpful to me as a beginner. I've come a far way. I now use my Linux OS more so than Windows. I only boot in Windows when I leave my PC so I can Remote Desktop. I know its not secure as it should be. So, I am now looking into Remote Desktoping that's similar to M$ version on Windows for Linux. I heard of FreeNX but being that I have 64-bit, I read that it was not a good idea to use it. 

If you guys want to see where I am now and where I was, I wrote an article about my Ubuntu Switch experience on my site...

[http://www.jamerican.net//?page_id=43](http://www.jamerican.net//?page_id=43)

JAmerican

---

### Post by JAmerican on 2007-07-06
I was able to get NX Remote Desktop to work (not FreeNX). NoMachine offers Free NX server and client with 64-bit and it works great. I really wonder why do people struggle with FreeNX?

I'll do a little guide if people think its necessary. Let me know :) :popcorn:

JAmerican

---

### Post by JAmerican on 2007-07-06
Here's the guide: 

[http://ubuntuforums.org/showthread.php?t=493983](http://ubuntuforums.org/showthread.php?t=493983)

Wouldn't have been able to do it without everyone's help

JA

---

