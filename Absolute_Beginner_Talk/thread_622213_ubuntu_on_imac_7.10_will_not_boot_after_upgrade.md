---
title: "ubuntu on imac 7.10 will not boot after upgrade"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by shill on 2007-11-24
ubuntu on imac 7.10 will not boot after upgrade

Have installed Ubuntu and upgraded from 6.06 one step at a time, after each upgrade ubuntu worked. Restarted after Ubuntu 7.10 completed install,imac will not boot. Does 7.10 not work for imacs?

I typed help at a command prompt. Are there specifics I need to proceed with to get this to boot and work?

Should I start over and stop at 7.04?  

Also, if there are procedures as to what to install ie: plugins and what not for the web, programs/applications for specific tasts,  instructions referenced any where, I would appreciate that.

Busy box - initramfs prompt on the screen - 
do not know what to type to get it to boot

---

### Post by shill on 2007-11-25
**Found these posts on another forum - Will this work????**
[http://ubuntuforums.org/showpost.php?p=3614279&postcount=58](http://ubuntuforums.org/showpost.php?p=3614279&postcount=58)

So... I guess the problem for us was not with the ATI package, but rather just the splash at bootup.

As a review for others in the same black-screen-of-death boat:

1. Use the live CD, at the prompt, I typed:
Code:

live-nosplash-powerpc video=ofonly

This should get you loaded and able to install. Once you've installed, you'll probably still have the black screen. No worries now, let's continue...

2. Repeat step 1. (to get into a working environment)

3. Mount your real installation as follows (in a terminal of course which should be no problem now as you're loaded):
Code:

sudo mount "type the name of your installed system partition here--- mine was /dev/hda5---without these quotes" /mnt

4. Edit the INSTALLATION yaboot.conf file. I used the terminal:
Code:

sudo nano /mnt/etc/yaboot.conf

- remove the words "quiet splash" (or just "splash" - I'm going to try that later) from the append line.

- save the file. in nano, you just hit ctrl-x, and then 'y' for yes to save, and then enter again to confirm the file name save (don't change it)...

5. in the terminal, type:
Code:

sudo /mnt/usr/sbin/ybin -C /mnt/etc/yaboot.conf

That's it! You're done... now just restart without the CD and you should be good to go...
thanks to everyone for the help and research, and thanks to lunalot for the fix.

I have never done anything like this, not sure what drive the installation is mounted on.

**or this post**

 PowerBook G4 15" won't boot live CD 7.10 - white screen or black screen
I have a Powerbook G4 12" that had the same problem with Kubuntu 7.10, and after combining solutions, I've gotten it to work.

1.) At yaboot:

live-nosplash-ppc video=ofonly break=top

2.) At busybox:

modprobe ide_core
modprobe ide_disk
modprobe ide_cd
exit

*NOTE: the busybox commands have to be entered all the first time around before `exit` or else it will fail and you'll have to reboot to try again.

3.) The cd will start to load. Be patient, it took me 3-5 minutes for the full boot, but it booted.
__________________

---

