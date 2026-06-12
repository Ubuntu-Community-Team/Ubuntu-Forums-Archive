---
title: "Giving up?!?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Red David on 2007-11-02
Dear Friends: I am very close to giving up on (generic, here) Linux after 7.10 hell. Initially, I had very good results and experiences (with really great terminal help from this forum) with kubuntu 7.04, which I installed from the .iso cd I had burned. I installed on a separate drive, which I made the master in accordance with instructions and the original drive with XP shows up as an option in the Grub bootloader. Everything went very smoothly and I hardly ever booted XP. Fine until 7.10 arrived and I very rashly decided to upgrade, over the web after getting directions, on day one ( I also ordered an official cd, in case, yet to arrive). Things seemed to go well, although what should have been a 1+ hour process was obviously going to be 10 or 12 due to server overload, when a <2 second power outage rebooted my machine and it's been downhill ever since. Without going into all the details, I ended up with an obviously crippled Kubuntu 7.04 installation.

I could boot but not install from my original live cd, same for the official Ubuntu 7.04 cd and the Ubuntu live 7.10 cd I burned. Last night, after any kind of booting was getting problematic, I replaced the drive and tried installing from all 3 disks. About half way through installing, the 7.10 bailed, with a message suggesting a defective cd and/or drive. Both the official Ubuntu 7.04 and the original Kubuntu 7.04 claimed to have installed succesfuly, but upon reboot w/o cd would stall with the progress bar barely started. I've tried safe and generic modes, no go. If I persist I get the following, in text (safe mode):

Alert!/dev/disk/by-uuid/bfa78818-4b8a-44c7-a2b8-1814d01bf3b2 does not exist. Dr opping to a shell!

The shell apparently being:

Busybox V1.1.3 (Debian 1: 1.1.3-3 ubuntu3) built-in shell (ash)

Enter 'help' for a list of built in commands

/bin/sh: can't access tty i job control turned off

(initramfs) blinkin cursor


Help is no help at all.


I've never had this much trouble in Windows, even. Let alone os X.

I'm reasonably certain it isn't a motherboard problem because I can still boot my xp drive and use it.
Both linux drives bad? I'm stumped but also linux free. A live cd is not really very practical or fun.

Any and all suggestions welcome and appreciated.

d

---

### Post by rudeboyskunk on 2007-11-02
Read the article in my signature.

---

### Post by Red David on 2007-11-02
Rudeboyskunk. I merely mentioned that I'd not ever had this much trouble in windows. I thought I made it fairly clear that I was using the linux much more than the xp and enjoying it more. And trying to learn it. I can't learn it if I can't install and/or boot it, can I?

Right now, I'm using a distribution that actually works. It's called Tiger.

---

### Post by fatso on 2007-11-02
> **rudeboyskunk said:**
> Read the article in my signature.

I've read it...but I just don't go along with the assumption that different must mean less user friendly (user friendly is a term that by the way is defined like idiots like me, not experts like you. get used to it). Mac computers manage to be different but still usable for idiots like me.

---

### Post by rsambuca on 2007-11-02
It could be a dirty lens on the CD drive is causing problems, both with writing and reading.  That error message is from a mismatched UUID for the drive and what is recorded in the /etc/fstab file, which definitely shouldn't be occuring with a fresh install.

Did you check the md5sums of the iso's, burn them at a very slow rate to help prevent single bit errors, and run the cd integrity check?

---

### Post by Red David on 2007-11-02
Right up through 2 days ago both drives were reading and writing music cds with no problems, so I'm reasonably certain that the drives are not at fault for being dirty. However, when I'm back from vacation I am going to try the very slow burn route. I also have a copy due in the mail. I would hope that it is clean and error free. Thanks.

---

### Post by mdpalow on 2007-11-03
Make sure your disk is free of smudge marks.

I went to install my 7.10 disk and the system just crashed on me. I was like ... WTH! I finally thought the disk had to be bad or something. I turned it over and sure enough, 4 smudge marks on it. 

I cleaned it off and had a perfect install.

Just an idea...

Good luck...

---

### Post by sailor2001 on 2007-11-03
out of habit, I always wipe an install disk with alcohol before using.

---

### Post by ByteJuggler on 2007-11-03
> **Red David said:**
> 
Alert!/dev/disk/by-uuid/bfa78818-4b8a-44c7-a2b8-1814d01bf3b2 does not exist. Dr opping to a shell!


OK, this message means the boot loader isn't finding the partition that it's expecting to mount (probably as the root partition.) 

Basically I'd say you've got a boot-loader/GRUB problem.  I would imagine that what's going on is that the fstab file/boot loader is possibly still trying to use/mount your Linux partition, and trying to identify it with it's previous UUID identifier, which has now been changed one way or another, whether due to the reinstall or something else, and so it's not finding it and bailing during bootup.

You could try the "[SuperGrub]("http://supergrub.forjamari.linex.org/")" disk, although I've never tried this myself, so cannot know whether it will help in your situation.  Worth a try probably.

Anyway, I'll/we'll try our best to get you going again.  Can you please boot from a LiveCD, try to make sure all your partitions is mounted under /media (they should hopefully be mounted by default and should be visible on your desktop and under the "Places" menu. Ideally you should browse around and confirm you can (for example) find your Linux user's home folder, to confirm your root partition is indeed mounted.)  Then proceed as follows:

1.) Open a terminal (Applications->Accesories->Terminal)
2.) Enter the following command(s) into the terminal exactly as shown:

```
{ 
  echo "====Disks by-id====" 
  ls -lah /dev/disk/by-id
  echo "====Disks by-uuid====" 
  ls -lah /dev/disk/by-uuid
  for name in $(find /media -name fstab); do 
    echo =====File: $name=====; 
    cat $name;  
  done; 
} 2>/dev/null >~/Desktop/log.txt 

gedit ~/Desktop/log.txt 
```

Note you can copy and paste all the command(s) into the terminal all at once by marking them in the browser with your mouse, then left clicking on the terminal, followed by middle clicking in the terminal (middle button/mouse wheel click, or alternatively by clicking both left and right buttons together.)  Make sure to press enter after the last line, to execute it also.  This will prevent manual copying errors causing further trouble.

3.) You should end up with an editor open with a bunch of information in it.  Please copy and paste the contents and post it back to the forum.  This should help us to figure out what's going on in your system.

---

