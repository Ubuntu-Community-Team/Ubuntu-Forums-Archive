---
title: "Oss-linux... problems."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by FirewolfX-7 on 2008-02-03
Yes, I have a problem typical.  I installed oss-linux, it recognized my sound drivers but then it couldn't install the rest of the stuff because something was using the drivers or such and such, and now I'm stuck with a broken install that I can't get rid of. I tried a few uninstall and remove commands but in  all cases this is what I got:

firewolf@X-7:~$ sudo dpkg --remove --force-depends --force-remove-reinstreq oss-linux
(Reading database ... 138795 files and directories currently installed.)
Removing oss-linux ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing oss-linux (--remove):
 subprocess pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
 oss-linux


Yes I have another thread with a little more details on what went wrong under the name "oss installation help needed" yes this is a cmi sound card and I doubt I understand anything in the readme along with the driver they provided. Oh and for more information, yeah when I hit ossinfo:

firewolf@X-7:~$ ossinfo
Version info:   (0x00000000) 
Platform: Linux/i686 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 (X-7)

Number of audio devices:        0
Number of audio engines:        0
Number of mixer devices:        0


Device objects


Mixer devices

Audio devices




... nothing... can some one just help me?  I really need it.

---

### Post by spiderbatdad on 2008-02-03
have you tried the installation as root?  It might be helpful if you posted the result of an installation attempt, rather than the result of a failed removal attempt.

---

### Post by FirewolfX-7 on 2008-02-03
Um... I couldn't remember the result as I said I have a another topic on this and there is a link tot the instructions I followed: [http://ubuntuforums.org/showpost.php?p=3768914&postcount=60](http://ubuntuforums.org/showpost.php?p=3768914&postcount=60)  It said something was being already used or unavailable so 'soundon' could not be completed.  I need a reinstall first before getting anywhere... looking at the error message it seems that my installation has major holes. :(

Oh... here is my old topic... not much help though: [http://ubuntuforums.org/showthread.php?t=686149&highlight=oss+uninstall](http://ubuntuforums.org/showthread.php?t=686149&highlight=oss+uninstall)

---

### Post by spiderbatdad on 2008-02-03
is it possible the message was that the package management utility was in use? If so then you failed to download and of the dependencies. It seems like you should go back to square one.

---

### Post by FirewolfX-7 on 2008-02-09
Right, I did and I reinstalled from the start... and I copied the error.  The next day was weird cause my computer reverted to Graphics Safe mode but reverted back to normal graphics on the day after.

Here you go, riddle me this:

ERROR: Module snd_pcm is in use by cx88-alsa
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd_page_alloc is in use by snd_pcm

this happens after the computer installs all the drivers... and it recognizes the hardware I have and then it happens right after it says

starting Open Sound System

well... I plan on having a sound system in the future... should I plan on replacing my cards or can this error be repaired?

---

