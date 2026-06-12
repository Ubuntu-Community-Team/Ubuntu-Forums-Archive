---
title: "XServe G5 Windfarm issue"
date: 2010-07-22
forum: Apple Hardware Users
---

### Post by kokoroexchange on 2010-07-22
Hello,

I've been running Ubuntu (LAMP) on an XServe for a little over 3 years now and have just gone through the process of completely upgrading to 10.04

I'm getting the following error on startup:

Error inserting windfarm_core 

Actually there are 10 errors, the core and then a series of them that appear to coincide with the sensors that exist on the XServe.

After the errors, I am presented with the usual login prompt and the fans on the server are running at a relatively quiet speed. I've noticed when using the server however, that the way the fans throttle is different that it used to be. They used to slowly accelerate as the machine got hot and then slowly decelerate when it cooled. I can hear a little acceleration/deceleration but not as much as before and occasionally it suddenly kicks into full speed (the fans).

Also, the computer suddenly and abruptly shut itself down once after repartitioning a hard drive in one of the bays using parted...

I'm a bit concerned about heat and want to make sure the fans are cooling appropriately (i.e. monitoring temp and adjusting their speed when necessary). 

There must be something going on because the fans default at full speed if there is no controller of any type...

Anyone that has any info/advice? I would be most appreciative.

Jason

---

### Post by kokoroexchange on 2010-07-22
Update,

I'm now noticing that my XServe G5 abruptly shuts down after being on for several hours :-(

Heat issue associated with the fan controllers...?

Jason

---

### Post by imrazor on 2010-07-22
Same here on my Powermac G5 DP 1.8GHz. I'll see several windfarm errors at startup, then the machine appears to boot normally. However, if I put the G5 under heavy CPU load it will sometimes crash. I'm very pleased with Lucid on 64-bit PowerPC, but random shutdowns, no matter how infrequent, really aren't acceptable. I actually thought I might have a hardware problem until I saw this thread.

To the previous posters, did you experience these sort of random shutdowns under previous versions of Ubuntu? Maybe a downgrade is called for...

I did find one hit when googling on the windfarm errors. What I saw was a bug report for Lucid on PS3, where it was regarded as unimportant since the PS3 doesn't have the appropriate hardware.

EDIT: I've also tried inspecting the logs, but didn't really find anything obvious. I suspect the shutdown is so abrupt, no action is recorded. Or it may be that since the OS can't grab fan control, the G5's internal sensors take over and occasionally shut the machine off when it gets too hot too fast....maybe.

---

### Post by kokoroexchange on 2010-07-22
imrazor,

I was running 7.04 for several years prior to upgrading to 10.04 and never had this problem. Thinking maybe I'll have to go back to 7.04 because, as you stated, sudden shutdowns are not acceptable.

I saw the same thread on the web related to the PS3. For my XServe, I know there are windfarm sensors because I remember way back when I first started using Ubuntu that they weren't supported initially and the fans would kick into high speed by default so it sounded like an airplane taking off in my server room.

I stumbled onto the windfarm support somewhere here on a thread in the forums I think but I can't seem to find anything now.

The strange thing for me is that something is obviously throttling the fans but I'm wondering if only certain fans are being controlled and others not...? I don't hear any of them running at full speed though....

Would really be nice to get this resolved.

Jason

P.S. I wonder if the sudden shutdowns could be a result of something completely unrelated to the windfarm errors? I did find a few pages, here and there on the web, about Ubuntu 10.04 suddenly shutting down...

---

### Post by imrazor on 2010-07-22
> **kokoroexchange said:**
> imrazor,

I was running 7.04 for several years prior to upgrading to 10.04 and never had this problem. Thinking maybe I'll have to go back to 7.04 because, as you stated, sudden shutdowns are not acceptable.

I saw the same thread on the web related to the PS3. For my XServe, I know there are windfarm sensors because I remember way back when I first started using Ubuntu that they weren't supported initially and the fans would kick into high speed by default so it sounded like an airplane taking off in my server room.

I stumbled onto the windfarm support somewhere here on a thread in the forums I think but I can't seem to find anything now.

The strange thing for me is that something is obviously throttling the fans but I'm wondering if only certain fans are being controlled and others not...? I don't hear any of them running at full speed though....

Would really be nice to get this resolved.

Jason

P.S. I wonder if the sudden shutdowns could be a result of something completely unrelated to the windfarm errors? I did find a few pages, here and there on the web, about Ubuntu 10.04 suddenly shutting down...

My theory is that there is some internal circuitry on the motherboard that takes over when the OS fails to take control of the fans (is that controlled by the SMU or the PMU?) I was having some hardware issues with my G5 about six months ago, but I thought I had resolved that and OS X has been very stable since. 
This theory doesn't quite mesh with your observation of your G5 going into vacuum cleaner mode under the old Ubuntu. Perhaps Lucid has some fallback mechanism for controlling the fans that is not as efficient as windfarm, and is prone to random shutdowns.

I'm considering going back not to 7.04, but to Karmic. I assume that since you're running an Xserve, you need long term support. But I'm not sure I want to take a casual machine back that far. If someone doesn't resolve the issue soon, I'll probably go ahead and downgrade rather than waiting for a fix.

EDIT: A few more random thoughts...when I try to forcibly load the windfarm_core.ko module with insmod, it reports no such device. I've also tried searching the forum (as opposed to the internet) and found a few Lucid users with windfarm errors. However, some other Lucid users clearly had the windfarm modules loaded. Among those who had errors, some had crashes and some didn't (or at least didn't notice them.) Could our G5's have different fan control hardware? I think I'm going to at least download a Karmic LIve CD and see if any windfarm errors pop up...

---

### Post by kokoroexchange on 2010-07-23
I may have made some progress but am not sure.

I updated all packages and dependencies last night and started up this morning and have been running without any shutdowns so far (about 7.5 hours). Granted, I don't have the server live yet so it's not getting any action but that was the same condition yesterday when it shut down twice.

Also, I'm getting the same "no device" or "device not found" (something like that) error when trying to force the windfarm drivers. I do see that the fans are identified in the kernel log and it seems like they are being controlled but I don't know by what...?

I'd prefer not downgrade back to 7.04 if possible but if that's what it takes then so be it. 

I'm getting ready to put some load on the server and see how it responds. Will post back.

Jason

P.S. My XServe only went into full speed mode a few times immediately after installing 7.04 several years back. I can't remember exactly what it was I did to get the windfarm drivers installed but once I did, it never happened again. Also, never saw the errors that I'm seeing now under 10.04. Also, from what I've read and experienced, if nothing takes over the windfarm control (drivers) the machine is designed (on the board somewhere) to put the fans into full speed. When installing Ubuntu from CD it does this during the install because the drivers are not included on the CD. Loud but I put up with it as the install doesn't take that long. :-)

---

### Post by kokoroexchange on 2010-07-23
Ok, here are my results for the day.

The XServe (with 10.04) stayed on all day without any issues. I did have one very abrupt fan acceleration to what sounded like full speed but it only lasted for a couple of seconds and then throttled back down to a 'normal' speed.

I put a little load on the server during the day by transferring some data (about 15 GB) via lftp and that seemed to heat it up a little and sped up the fans but no shutdown.

BUT, at almost exactly 12 hours after I started it up this morning, it shut down abruptly :-( I wasn't even using it at the time and like I mentioned earlier, the server is not accessible to anyone but me so it wasn't getting any action at all. Damn! I was starting to feel like it was going to be ok :-(

Jason

EDIT - I've just reverted back to 7.04 and in the process I noticed that the command

sudo shutdown -r now

doesn't restart the machine the way it used to. It shuts everything down but doesn't restart. And, when I go to my machine and push the power button to start it, it acts like it's going to start and then stops. That is repeated about three times (each time I push the button) and then on the fourth time (roughly) it starts up as normal.

I did change the motherboard on this machine a while back and haven't used it since then and am now starting to suspect that the battery on the board (PMU battery) might be dead....

Could that also have something to do with the almost exact 12 hour run time today....?

---

### Post by imrazor on 2010-07-23
> **kokoroexchange said:**
> Ok, here are my results for the day.

The XServe (with 10.04) stayed on all day without any issues. I did have one very abrupt fan acceleration to what sounded like full speed but it only lasted for a couple of seconds and then throttled back down to a 'normal' speed.

I put a little load on the server during the day by transferring some data (about 15 GB) via lftp and that seemed to heat it up a little and sped up the fans but no shutdown.

BUT, at almost exactly 12 hours after I started it up this morning, it shut down abruptly :-( I wasn't even using it at the time and like I mentioned earlier, the server is not accessible to anyone but me so it wasn't getting any action at all. Damn! I was starting to feel like it was going to be ok :-(

Jason

EDIT - I've just reverted back to 7.04 and in the process I noticed that the command

sudo shutdown -r now

doesn't restart the machine the way it used to. It shuts everything down but doesn't restart. And, when I go to my machine and push the power button to start it, it acts like it's going to start and then stops. That is repeated about three times (each time I push the button) and then on the fourth time (roughly) it starts up as normal.

I did change the motherboard on this machine a while back and haven't used it since then and am now starting to suspect that the battery on the board (PMU battery) might be dead....

Could that also have something to do with the almost exact 12 hour run time today....?

The bit about the battery is an excellent point. I know for a fact that the battery in my machine is dead or nearly so. However, I wouldn't think that would prevent the OS from taking control of the fans. I let mine sit overnight without any load at all, and in the morning it was still booted up. I've backed up some of the configs (mostly an Xorg.conf and a Greasemonkey script), and I'm going to install Karmic and report back. I'll also try to get a new battery for the machine, but they're hard to find in my town.

EDIT: Encountered a nasty surprise trying to download Karmic. All of the CD images I can track down clock in at over 702MB. I can't burn the images even with overburn enabled. Whose idea was this? I've got a DVD-RW floating around somewhere that I can probably use to burn the image to, but this is annoying. I guess I need to make another post to see if there's anyway to remove an unwanted package from an Ubuntu image.

EDIT2: Excuse my rant above...downloading the Kubuntu 9.10 alt-install CD now @ 679 MB. Still annoying that I can't download the desktop image...

---

### Post by imrazor on 2010-07-23
Update after downgrading to Karmic. No change - still get windfarm errors at boot, and still get random crashes during heavy load. After downgrading, I proceeded to compile on both CPUs and loop some video playback to put a heavy load on the system. It ran that way for about 30 minutes, but then it crashed again. 

Since the battery is the only thing we can find in common, I'm going to try replacing that. However, I won't be able to get a battery until next week. Could it possibly be other hardware causing the problem? I have a flashed PC video card (Radeon 9700 Pro 128MB), a D-Link DBT-120 USB Bluetooth module, an old Apple Pro keyboard (from a G4) and a USB Mighty Mouse attached. Sometimes I will also have a HTC HD2 cell phone attached via USB. I also have desktop effects enabled. I usually experience the crashes during combined compile/transcode runs and simultaneous video playback. I may try compiling without video playback to see if that alleviates the problem.

Please let me know if you have any trouble with 7.04. I may try some other distros to see if they also have problems. Getting them set up will be more difficult, though, since I'm so familiar with Ubuntu on the PC.

---

### Post by kokoroexchange on 2010-07-24
imrazor,

I'm actually back in 10.04. I've been up for a little over ten hours today and it 'seems' like things are the way they used to be. I know that's not very concrete but...

I reset the motherboard (PMU) last night and shutdown/restart commands now function the way I'm used to.

I'm working on getting everything set up so I can test the server via JMeter to make sure it's going to stand up to the load I'm scheduled to throw at it this coming Friday. :-)

I've been running on a Mac Mini for over a year and have never had any problems but I have a test coming up that is going to be taken by almost 400 students in two waves of approximately 200 so I don't want to take any chances. I'm working on setting up my XServe (fully loaded with 8GB of RAM) with the LAMP on one drive, the data directory for Moodle (the system I'm using) on another, and the data directory for MySQL on a third. If I can manage to get everything set up, an the server doesn't suddenly shut down on me :roll: life will be grand.

I'll post later this evening to let you know if my server made it past the 12 hour record :-)

And again on Tuesday after hitting it hard with JMeter.

Jason

---

### Post by imrazor on 2010-07-24
> **kokoroexchange said:**
> imrazor,

I'm actually back in 10.04. I've been up for a little over ten hours today and it 'seems' like things are the way they used to be. I know that's not very concrete but...

I reset the motherboard (PMU) last night and shutdown/restart commands now function the way I'm used to.

I'm working on getting everything set up so I can test the server via JMeter to make sure it's going to stand up to the load I'm scheduled to throw at it this coming Friday. :-)

I've been running on a Mac Mini for over a year and have never had any problems but I have a test coming up that is going to be taken by almost 400 students in two waves of approximately 200 so I don't want to take any chances. I'm working on setting up my XServe (fully loaded with 8GB of RAM) with the LAMP on one drive, the data directory for Moodle (the system I'm using) on another, and the data directory for MySQL on a third. If I can manage to get everything set up, an the server doesn't suddenly shut down on me :roll: life will be grand.

I'll post later this evening to let you know if my server made it past the 12 hour record :-)

And again on Tuesday after hitting it hard with JMeter.

Jason

After yesterday's Karmic failure, I decided to zag instead of zig. I installed Debian Lenny on my G5. I didn't get any FATAL windfarm errors, though I did get some messages about unreferenced symbols. After spending a few hours configuring it, I managed to do about 1-1/2 hours of hard transcoding/compiling. No crashes so far, but more testing is needed.

What is JMeter? Could I use it to stress test my G5?

---

### Post by kokoroexchange on 2010-07-24
Damn! Well I guess I was being overly positive!!!

I went out for a walk with my wife and daughter and just got back and the server was off!!! Just a little shy of 12 hours this time... :-(

This won't do!!!

I guess I'll try and install 7.04 and let it run all day tomorrow and see what happens....  This is really frustrating....

Jason

---

### Post by imrazor on 2010-07-24
Well, poo. Was the Xserve under any sort of load, or was it just idling? Before I left this morning I started Lenny on a transcode run that should last ~1 hour. Oddly, under Lenny ffmpeg doesn't seem to peg both CPUs at 100%. Instead it's about 60% for each CPU. More research is needed on this I guess. When I compiled ffmpeg on Lenny I had to leave out a couple of libraries, so that may be the difference. I may do some research and figure out how to get those two missing libraries on Debian.

When I get home from work, I'll check the G5 and see if it's still up. I may even hear from my fiancee if it survived the transcode run.

---

### Post by kokoroexchange on 2010-07-24
No load, just idling behind my router without even any access from outside my LAN. :-(

I've reverted back to 7.04 and can already tell that the fans are running differently. Much quieter...

The problem is that since 7.04 is no longer supported, it's going to be a royal pain to install packages that I need (libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl). I guess I'm going to have to fish around for them one at a time, download each, and then install them. Yuk!

Or maybe it would be a good idea to try something that is still supported....which would be....8.04...I guess. No guarantee that it's going to work the way 7.04 did for me though...

What a dilemma, spend the time getting 7.04 in the state that I want/need or give 8.04 a shot....?

Jason

---

### Post by imrazor on 2010-07-24
> **kokoroexchange said:**
> No load, just idling behind my router without even any access from outside my LAN. :-(

I've reverted back to 7.04 and can already tell that the fans are running differently. Much quieter...

The problem is that since 7.04 is no longer supported, it's going to be a royal pain to install packages that I need (libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl). I guess I'm going to have to fish around for them one at a time, download each, and then install them. Yuk!

Or maybe it would be a good idea to try something that is still supported....which would be....8.04...I guess. No guarantee that it's going to work the way 7.04 did for me though...

What a dilemma, spend the time getting 7.04 in the state that I want/need or give 8.04 a shot....?

Jason

I found a couple of suggestions for windfarm issues on a Debian PowerPC mailing list. The first is to do as follows with root permissions:

# modprobe windfarm_core

The other suggestion was to add a "windfarm_core" line to /etc/modules (which is a similar solution, just applied at boot.) I won't be home for several hours, so if you get a chance to try either with 10.04 today, let me know if you have any success.

The OP on that thread was also having issues with random shutdowns, so hopefully that will resolve our issues.

You could preserve your new 7.04 install by imaging to an identically sized partition with gparted (I think), dd or a similar tool. I've imaged OS X many, many times but have rarely done so with Linux.

Good luck and thanks...

---

### Post by kokoroexchange on 2010-07-24
Sorry, I missed your question about JMeter.

Here is the link

[http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/)

To be honest, I've never used it but it was recommended by a person on a different forum so I thought I'd give it a try. Haven't gotten that far yet though so unfortunately, I can't tell you much about it.

I'm working on giving 8.04 a shot at the moment. Will let you know how it goes.

Jason

---

### Post by kokoroexchange on 2010-07-24
Ok,

Well it took some time but I got 7.04 back up and running with all the packages and dependencies I wanted and need. Whew!!

I tried 8.04 but the install froze midway through. Right at the partition tool so I gave up on that one.

I contemplated trying adding the trick you found on the Debian forums but couldn't afford to spend any more time on this and had a pretty good feeling I could get 7.04 back up and running so that's where I am. :-)

After I complete the task that is immediately at hand I may spend some more time trying to get up to a newer version but as long as it's as stable as it was in the past, I'm happy with 7.04.

Too bad I had to go through all of this but it looks like I'm in business. Hope it's not too early to say that. I'll let it run for a while now and make sure I don't suffer from a sudden shutdown (fingers crossed). If I do I think it's definitely a hardware issue as I never had shutdown problems with 7.04 in the past.

Jason

---

### Post by imrazor on 2010-07-24
Latest update: Found this old bug report...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/241726](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/241726)

According to the bug report, my model of Powermac (7,3) doesn't have windfarm support. No mention is made of Xserves, unless they're based on one of the Powermac model ID's in the bug report. While those windfarm modules failed to load, one did load: windfarm_pid. On a Lucid PPC Live CD I was successful in removing the windfarm_pid module without the fans going to warp speed. It is possible, but somewhat unlikely, that the windfarm_pid is conflicting with the therm_p72 module, which is used by Powermac7,2 and Powermac7,3 (my model) for thermal control. I'm going to try reloading Ubuntu, then blacklisting all the windfarm modules and see if I still get crashes. Unlikely, but I don't feel like learning my way around Debian.

Eric

EDIT: Additional info; I did an rmmod of therm_pm72 and sure enough my fans ramped up within a couple of minutes. When I reloaded therm_pm72 they instantly shut off. Time for a reload of Ubuntu...

---

### Post by imrazor on 2010-07-24
I've reloaded Lucid and so far things seem promising. I just ran some heavy compiling and transcoding for 4-5 hours and no crash. I accomplished this by doing ```
sudo rmmod windfarm_pid
``` However, no matter what I try I have been unable to blacklist either windfarm_pid, or any of the other windfarm modules. They still give a FATAL error at boot, but don't seem to be crashing the system, at least so far. I've worked around this by adding ```
rmmod windfarm_pid
``` to rc.local. My fingers are crossed...

UPDATE: I left the G5 running overnight with ```
cat /dev/zero > /dev/null
``` running in two separate terminals, and an OpenGL screen saver running. Despite the CPU running at full load for 10-11 hours, it seems to be holding up OK. I may have it licked, but I'll continue stess testing it for another 2-3 days before reaching any conclusions.

---

### Post by imrazor on 2010-07-25
Since I added ```
rmmod windfarm_pid
``` to my /etc/rc.local I haven't seen a single random crash or shutdown. I kept my system on heavy load for about 18 hours without a shutdown. So far the results aren't conclusive, but it does seem as if there's a conflict between the therm_pm72 and windfarm_pid modules. Hopefully Jason or someone else will find the info useful, though it only seems to affect a few models of Mac.

---

### Post by kokoroexchange on 2010-07-25
Thanks for the updated information. Unfortunately I was running out of time and wasn't brave enough to continue working on getting 10.04 up and running in a stable fashion so I moved back to 7.04.

Initially I had trouble getting it all updated but adding a few lines to the sources.list remedied that.

I'm running smoothly and managed to get my load spread across three drives (LAMP on one, application datadir on another, & MySQL datadir on the 3rd). Tweaked MySQL a little and installed APC and I think I'm ready to go.

After I finish the job that this server is going to have to perform and move back to a quieter and more efficient machine (little Mac Mini), I'll work on seeing if I can get 10.04 to work with some of the suggestions provided here by imrazor.  Thanks for your insight and help! :-)

Jason

---

### Post by imrazor on 2010-07-26
> **kokoroexchange said:**
> Thanks for the updated information. Unfortunately I was running out of time and wasn't brave enough to continue working on getting 10.04 up and running in a stable fashion so I moved back to 7.04.

Initially I had trouble getting it all updated but adding a few lines to the sources.list remedied that.

I'm running smoothly and managed to get my load spread across three drives (LAMP on one, application datadir on another, & MySQL datadir on the 3rd). Tweaked MySQL a little and installed APC and I think I'm ready to go.

After I finish the job that this server is going to have to perform and move back to a quieter and more efficient machine (little Mac Mini), I'll work on seeing if I can get 10.04 to work with some of the suggestions provided here by imrazor.  Thanks for your insight and help! :-)

Jason

You're welcome Jason. Unfortunately, my G5 is about to be repurposed as an OS X HTPC. I "need" it for recording TV shows, as we're having to return our DVR after cancelling satellite service and switching back to cable. I"ve really enjoyed my brief foray into PowerPC Linux and may invest in old iBook or Powerbook to continue my mad experiments.

I will say that after removing windfarm_pid from the running modules, the system was far more stable. It ran for about 72 hours, 24 hours of which was under heavy load (99-100% CPU usage) without a single random shutdown. I communicated briefly with the module writer, who claimed that the conflict wasn't possible. My experience seems to contradict that, but I'm no driver coder either. If you find yourself experimenting with 10.04 again, give it a try and let us know if it works.

---

### Post by najeer on 2010-08-25
Hello,

I completed the installation of 10.04 server on a powerpc g5 and received the windfarm_core errors.  The ppc sounds like a plane about to take off and decided to do a re-install.  All appears fine until the installation is completes.  After the post-installation I remove the cd and the powerpc reboots.  It appears the boot up is working fine then bam! Fatal Error Inserting Windfarm . . . :winfarm core no such device.  Now I read all the posts for this issue and many suggest installing winfarm_core separately.  Now can someone navigate me to a post that discuss doing the very such task?

---

### Post by svu on 2010-09-13
[https://bugs.launchpad.net/ubuntu/+bug/631358](https://bugs.launchpad.net/ubuntu/+bug/631358)

---

