---
title: "how to move beyond simply working"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Chamith on 2007-02-21
Hi

After two weeks and 7 reinstalls I've finally got Ubuntu 6.06 working on my laptop (including a brief venture to Kubuntu..)... wireless, dvd, ati, etc etc etc

Now I have some questions to move beyond the stage of simply working to actually starting to feel like I want to use Ubuntu on its on merits - rather than being happy for not using windows ;)

1) during my boot up I get an error saying that the filesystem of the boot sector doesn't match the backup.  it doesn't seem to have any effect except to force the boot up process out of the graphical mode to text based.

2) after installing the ATI drivers (envy) I now have to reconfigure the ATI control and restart my X windows to display on a remote monitor. I do lots of presentations and losing the functionality of my Dell FN-F8 key is a major annoyance.
2b) I can not get a resolution higher than 1024X768 on the remote projector (or my laptop screen).
2c) when I close my laptop screen when using a remote monitor the 'lid screen off' feature also turns off the output to the projector.

3) DVD playback (via Ubuntu's default movieplayer and Kafeine) does not seem to be able to read DVDs as well as under windows - i.e. lots more skipping, freezing, and choppy playback <not due to ATI drivers as playback was choppy and I installed the Envy ATI package to update the drivers> --> I had to change the player engine in Kafeine to OpenGL so the movies output to the remote projector.

4) bittornado and Azureus both show up as 'firewalled' although I don't run a software firewall - and the router firewall did not have the same affect in Windows.


haha, ok, these are the issues that have been bugging me.. 

thanks

ps.
(of course, not mentioned are all the many things working perfectly - so its still a balance positve experience)

---

### Post by Chamith on 2007-02-21
oops--

one more I forgot

5) on update I get the following errors with the repository - [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) MD5Sum mismatch

and get 404 errors when trying to upgrade the linux 386 kernal and two related modules.

thanks

---

### Post by Crakie on 2007-02-21
I don't have an ATI-card, so I can't help you there. But point #4 I might have some advice that could be useful.

Ubuntu runs a 'firewall' by default, it's called IPTables. You can install Firestarter, which is basically a graphical frontend for this. If you do, it's easy to punch a hole in the firewall at the required port. You also should forward the same port in your router, if you have one.

---

### Post by lyceum on 2007-02-21
Well, that is a lot of questions I cannot answer :) So I will get the one I can. In some places (the US of A) it is not legal to include the drivers that make DVD's play unless someone pays for it ($$'s). Ubuntu is free, so no one pays for it. I am not really talking about "watching the movie" drivers, but the drivers to get past the restrictions put on the DVD's to stop pirating of movies. So, only the pirates can watch the movies :). There are legal ways around this, though they are questionable backwards engineering feats.

Click [here](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability) to learn more.

---

### Post by mikewhatever on 2007-02-21
[http://ubuntuforums.org/showthread.php?t=331161](http://ubuntuforums.org/showthread.php?t=331161)

It's a thread on opening ports for bittorrent.

---

### Post by Chamith on 2007-02-21
hey

thanks - opening the port worked a bit .. but downloads are still around 5kbs (from 1 kbs before) but still well short of the 40 to 50 kbs in Windows..

Uploading works perfectly though - same speeds as in Windows

thanks again for the help.  the community support is definitely a selling point (THE selling point) for Ubuntu!

---

### Post by Chamith on 2007-02-21
oops

forgot something again!

And firestarter didn't work - it ended up blocking my internet connection completely!

---

### Post by Crakie on 2007-02-23
That's the way it starts out. You have to configure it (open ports). But I think there's an option in the installer to open some common ports such as HTTP, email etc.

---

### Post by tgalati4 on 2007-02-23
The boot sector mismatch is common when performing lots of installs.  Basically you can copy the current to the backup or the backup to the current.  Usually what happens is grub gets copied to the Master Boot Record (MBR) several times so you get a mismatch.  This is not a virus.  Run a live CD and boot into a rescue shell (no graphics) the fsck /dev/hda (or whatever your disk drive is).  Correct the condition (typically copy the current to backup since you are able to boot, so Grub is working OK).  shutown -h now, remove the disk and reboot.  Errors should go away.

To get native resolution on your LCD display, reconfigure xorg.  Search the forum for how to do this. Reboot, you should now be at native resolution.

If this is a Dell Laptop, then I believe there is a BIOS setting that activates the external display.  Turn it on and see if it works.  You will have to edit xorg.conf to get the appropriate resolution.  1024 x 768 is a typical projector resolution.  If you mirror displays, then your LCD screen will look a little fuzzy at 1024 x 768. This is normal.  If you want to set up dual display then you can get native resolution on both the LCD and the projector output.  Search the forum for how to do this.  It can be a pain in the butt.

Keep the faith.  We need you in the fight.  Grab a beret and bandolier and watch your head on the way out.

---

### Post by Chamith on 2007-02-24
Thanks for all the input -

recopying the boot sector did work for the mismatch.  although it was a bit frightening to be copying things from and to the boot sector.

I've got the resolution on the project to go above 1024X768 - but no lack with the laptop.  But I think the laptop might be a DELL hardware issue since it doesn't go above 1024X768 with XP either..

Otherwise, I'm still having the problem that the 'lid switch' on the laptop screen turns off the external projecter.  It may seem like a small problem but during presentations where space is limited it is frustrating.. er.. not that I ever place objects on my laptop.  

There must be a way to turn off the laptop display (even in black it puts out light) while keeping the external display active?

but thanks again for help!

---

