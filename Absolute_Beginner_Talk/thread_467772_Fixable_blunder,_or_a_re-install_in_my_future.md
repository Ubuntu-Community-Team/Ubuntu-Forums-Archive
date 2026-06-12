---
title: "Fixable blunder, or a re-install in my future?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by detroit/zero on 2007-06-08
Hi all,

I've been [having some trouble with Beryl]("http://ubuntuforums.org/showthread.php?t=466516") on my desktop as of late. It just seems to be running slow and hogging way more resources than it should. I have a 1.73GHz laptop with Intel onboard graphics that runs Beryl and Emerald better than my 3GHz desktop with an NVidia GeForce FX 5500.

All that aside, I was looking around and ran across [a thread about Kiba-Dock]("http://ubuntuforums.org/showthread.php?t=268645&highlight=kiba-dock") and decided to give that a try. The thread states that it may be a broken process (and is quite old), but I found my way to the official site and did things their way. Thing is, after adding the kiba repos to sources.list, a Beryl update came through. I went ahead with the update, but got the following error at the end:
```

E: /var/cache/apt/archives/beryl-settings-simple_0.3.0+git20070320~3v1ubuntu2_i386.deb: trying to overwrite `/usr/share/beryl-settings-simple/level2.Profile', which is also in package beryl-ubuntu
```

It was late and I was tired and I didn't catch it, but the next day I tried to reboot and I was locked out of my desktop. I think it also may have had something to do with the kernel update that came through a few days ago (2.6.20-16).. I didn't realize  I had updated the kernel. I was never prompted for a reboot and never reinstalled my NVidia drivers.. but I know I rebooted once or twice in there somewhere and everything was working as usual.

Having said all that, I decided to go for broke since I was unhappy with how my system was performing; I ran an apt-get autoremove beryl, and decided to try my hand at compiling my first kernel as per the instructions found in [the Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158"). The only things was, since I didn't have access to my desktop (and since I was following the instructions in the browser on my laptop) I performed the compile through SSH in a terminal on my laptop. I was surprised that it all went alright. 

At first.

Reinstalling my NVidia drivers was a failure. At first it seemed to go OK, but then some error came up and it said that it couldn't build the NVidia kernel and aborted the process. (I'm using the NVIDIA-x86-9755 package. System>Administration>Restricted Drivers does not work on this system for whatever reason. I actually end up using a combination of both methods, which I have perfected over 3 or 4 installs since last February.) But that's not even a big deal. I change xorg.conf to use my onboard graphics and comment out the nvidia module loader, undo my blacklists in /etc/hotplug/ and /etc/modprobe.d/, reboot and change my BIOS and all is well.

Only I'm still locked out of my desktop. The new kernel loads, the splash/login screen comes up, but after I login the screen goes blank and sits there.

Like I said, I'm not completely opposed to doing a fresh install - I'd just rather avoid it if at all possible. In case I can't, I'm in the process of backing up all my data onto my laptop via SSH and am preparing for the worst. Is it possible to run the live-cd and copy the original kernel and other things back into my HD? What would I do.. copy everything but my home directory from the CD and have an *almost* fresh install? This is the worst I've messed my system up in a while, and I have more to lose than I did back in Feb/March when I first made the switch to Ubuntu.

At any rate, I'm attaching the nvidia-install.log, Xorg.0.log, and both xorg.conf files I use (clearly labeled to differentiate). I'm hoping one of you gurus can help me make heads or tails out of this mess..

If not, I'll know by the sounds of sighs and laughter that I need to reinstall.

Sorry this is so long-winded and so involved. Thanks for any help.

---

### Post by freebird54 on 2007-06-08
Well - a couple of things I would try first... though I'm still a n00b in some ways myself.

If you have had kernel updates, you will still have the earlier ones around, unless you specifically removed them.  They should be in the /boot directory.  This may lead to a recovery via that method...

As for the copy from Live CD, should also be possible if required.  If you edit your /boot/grub/menu.lst to pick up the version you WANT to use, you should be able to choose on a per boot basis.  (backing up before editing of course, but you know that from the sound of the gyrations you've been through!)  IF you need any help with some of the grub stuff - try here:  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I'll look through the restof the stuff now - and see if I see anything else that'll help - I had my own fun first getting the ATI drivers to work....  :)

---

### Post by detroit/zero on 2007-06-08
Right right.. I realize you can select from the different kernels in GRUB. But if your configuration is messed up bad enough, even the safe-mode kernel won't work - such is the case with me.

I've almost got all my important files copied to my laptop. I think I'm going to go ahead and wipe the drive and start over rather than try to sort through the mess I've made.

You win some, you lose some I supose.

---

### Post by lamalex on 2007-06-08
what happens when you try to go into safe mode? have you tried booting to a livecd, chrooting your hd root partiton and then working from there?

---

### Post by detroit/zero on 2007-06-08
Safe mode works the same as regular - boot/login comes up and after entering my username/password the screen goes blank and it sits there not doing anything. It's just the GUI that's messed up. If I do a CTRL-ALT-F2 from the login screen I have command line access. CTRL-ALT-BACKSPACE from the frozen screen will bring me back to the splash/login, though, so I guess saying it's "frozen" isn't the right choice of words.

I do have a mouse pointer the blank screen, but the sound isn't working (at least the login.wav doesn't play..) and there's no disk activity. 

I can't even login remotely via XDMCP or VNC. I have SSH access but that's it.

One thing I did notice is that between my two xorg.conf files I hadn't changed the PCI address from the NVidia slot to the one for my Intel Onboard Graphics. I thought it was an "Aha!" moment, but no such luck.

---

### Post by detroit/zero on 2007-06-09
Well, I've learned a few things through this experience.

1. I had to have had some settings crossed somewhere inside Beryl and/or Emerald. I'm not sure what would cause the kind of resource-hogging i was seeing, but it's all better now.

2. NVidia drivers will not work with a custom kernel. I tried everything I know of in my limited knowledge-base and no way no how could I use my NVidia card with the kernel I compiled. The kernel itself works great with my Intel onboard graphics controller.. Boot time was decreased by a good 15 to 20 seconds and the performance gains were quite noticable. NVidia has a number of installers available, as anyone with an NVidia card knows all too well. The newest one for the x86 platform (...x86-100.19.09-pkg1.run or some such thing) didn't support my card. Good thing I kept a copy of the older one (...x86-9755-pkg1.run) around. That one worked like a charm. 

3. Copying and pasting 60GB worth of files, music and uncompressed data over an SSH connection is a royal pain and not recommended. Forgetting to hit CTRL-H in Nautilus and copy and paste all those hidden  files in your home folder that contain all the application data (/.mozilla, for example) over your SSH LAN connection is a foolish mistake and will take its toll on your mental health. See lesson #4

4. Having to set up your system to get it back to the way you like it and are used to is a *very* time consuming process. Details, details, details.

I suppose I took the not-so-easy way out of my dilemma, but I managed to make quite a mess out of things and sorting through it was proving to be just as time consuming. I figured I could spend 3 or 4 (or more) days tinkering with this, that, and the other or just start over and kill maybe 2 days. I'm happy (more or less) with the choice I made.

I compiled my first (fully functional) kernel and it ran like a raped ape; I streamlined the ridiculously ridiculous NVidia thing I do; My system runs better even on the generic x86 kernel than it was running before, and the sun is again shining in happy-land.

Yay me.

---

### Post by freebird54 on 2007-06-09
Damn - too late to come in with any sneaky ideas!  I had thought that if you reized your / smaller, created a new partition, copied everything from /home into it, then mounted it as /home (after wiping out the original from CD) you could have avoided some of the reconfiguration....

Than again - maybe that's what worked best about the whole thing! :)

Glad to hear you have it all going - and keep a good hold of that 'legacy' driver...!

---

### Post by detroit/zero on 2007-06-09
> **freebird54 said:**
> 
Glad to hear you have it all going - and keep a good hold of that 'legacy' driver...!

That's the weird part.. I don't think it's actually legacy. My card is a 256MB GeForce FX5500. The list of supported cards on that new installer includes a few from the FX series but for some reason skips the 5500. I don't know when they came out with that particular model, but I bought the thing brand-new in winter 2005.

Oh, yeah. It's a year and a half old.

Legacy.

---

### Post by freebird54 on 2007-06-09
If it's anything like the ATI 9550 that I have - it's a 'budget' model.  Lots of RAM, older chip, misleading model number!  On the other hand it owrks well, and didn't cost much... so fair enough I guess!

(Disclaimer:  I could be wrong about this.  Actually, it has happened before.  Once or twice.  Of course my memory isn't perfect either.  :) )

---

### Post by detroit/zero on 2007-06-09
> **freebird54 said:**
> If it's anything like the ATI 9550 that I have - it's a 'budget' model.  Lots of RAM, older chip, misleading model number!  On the other hand it owrks well, and didn't cost much... so fair enough I guess!

(Disclaimer:  I could be wrong about this.  Actually, it has happened before.  Once or twice.  Of course my memory isn't perfect either.  :) )

I'm thinking that's the case. It doesn't seem to be a *bad* card, but like I said in my original post - I have a 1.73GHz Toshiba laptop with onboard graphics that runs Beryl and Emerald way smoother than this machine does.

I still think I have something set up wrong or that some configuration isn't quite right. Back in my Windows days this same machine would run most modern games with all options maxxed out. Even that resource-hog F.E.A.R. would run at 1024x768 with all the eye-candy - dynamic lighting, DX9 shaders, shadows, etc. Games like Call of duty I & II and Star Wars Battlefront I & II would run at high resolutions and framerates with all video options maxxed right out.

As long as I stay away from the animations in Beryl I do alright. iI fail to see what's so resource heavy about that compared to 3D gaming, but wtf do i know?

---

### Post by freebird54 on 2007-06-09
It is NOT resource heavy - especially compared to  gaming! Almost certainly a config setting or two away from happiness...  Too bad I don't more about the vid settings for nVidia.  Check through back threads here should give some clues though!  I'll checl if there's anything that I *DO* know about them though....

---

### Post by detroit/zero on 2007-06-09
I'm basically back to where I started. I'm finding Beryl to be extremely resource heavy. I can't imagine what would be causing it. It has to have something to do with the settings I'm using.

I uploaded two screenshots. I have sitting in my panel the system-monitor utility. The side on my left is processor activity, while the right side is network activity and can be ignored.

In the processor monitor the color scheme is as follows: Blue=User, Yel=System, Green=Nice, and Red=I/o Wait time.

The first shot is what processor activity is like with a game of Yahoo Pool running in a Swiftfox Java window while in my main window I log into Ubuntu forums and check this post.

The second shot is the post-reply window rendering.

Why is it eating up so much power to do the simplest things? I could upload all the config files, but I don't know where most of them are or which ones someone will need to see to point out the error of my ways.

Anybody have any clues?

---

### Post by detroit/zero on 2007-06-10
Well, OK. I think I have bigger fish to fry than just Beryl. I went ahead and removed that, and even in Metacity simple things like rendering terminal and browser windows are being 75% to 100% processor intensive. Compiz gives the same results as well.

Any ideas why it would act like this?

---

### Post by freebird54 on 2007-06-10
What processor are you running?  Is this from the 3Ghz one?

The only ting I can say is that my charts of the same would look similar, only worse.  But then again this machine is from 2000.....

Do you notice actual 'hitches', glitches, or slowdowns - or is it just the apparent hits on the monitoring?

---

### Post by detroit/zero on 2007-06-10
I'm on my laptop right now and can't do an lspci or get any info off the desktop at the moment, but it's an Intel P4 3.0GHz dual-processor.

Here's a link to the [HP product info page]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00303943&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN") for my system. I can't find any info at the NVidia site for my card. I do notice that they've moved the GeForce FX series to the "Legacy" section, but I still don't see my particular model listed. A quick google search just turns up Amazon pages and the like. The basics off the top of my head, though, are: NVidia GeForce FX5500 - 256MBDDR, 30MHz bus, PCI-E.

---

