---
title: "Linux and FreeBSD in 2019"
date: 2019-07-20
forum: BSD
---

### Post by lammert-nijhof on 2019-07-20
I am using ZFS on Linux and I'm very pleased with its performance. I even boot two different flavours of Ubuntu from two ZFS datasets in the same datapool. I had an old Pentium that I wanted to use once a week as backup server. I still had a 250GB and a 320GB IDE disks and a spare 320 GB laptop SATA disk (2,5" and 5400 rpm). Fortunately the Pentium motherboard had SATA-1 support. I could not use Linux, due to the lacking ZFS support for my ancient  Pentium 4 HT. Basically 32-bits support is fading from Ubuntu and Linux.

So I looked at FreeNAS and FreeBSD. I first tried FreeBSD in Virtualbox to check its facilities and performance. I was happily surprised by FreeBSD, it needed somewhat more work in updating e.g. rc.conf, but everything worked reliably. I now use FreeBSD 12 on my Pentium 4 HT with 3.0 GHz and 1280 MB of memory. The system is installed on those 3 striped disk and I have added some additional datasets to contain my backups. I use XFCE, because I like GUIs and I use XRDP as remote display server. The Pentium is connected with the world by two cables one for the power and one for 1 Gbps Ethernet.

Today I did the second backup. For normal files I use Samba and rsync, while for my VMs I use ZFS send/receive function, because of the huge VDI files often only change partly. I detected that some of the ZFS release 8 functionality, like the fast sequential scrub, is already available in FreeBSD's ZFS, 

FreeBSD impressed me, supporting ZFS in its installer and boot loader, I could even choose the Raid configuration to use. The system makes a reliable and effective impression, its implementation of ZFS is at least 3 months ahead of Ubuntu, but its GUI is very basic compared to e.g. Xubuntu. It is surely a system to watch in the coming years, because their priorities seems to be performance and functionality instead of bling-bling. Unfortunately too often in Linux distros it seems to be the other way around.

---

### Post by kevdog on 2019-09-27
FreeNAS is great.  I also like FreeBSD a lot and am a huge fan of ZFS.  The FreeBSD community is rather small but extremely technical.  Very very knowledgable about their distribution.  I'm a big fan of BSD servers ran through command line.  BSD repositories however are limited in terms of software compared to a general Linux repository and sometimes there isn't as much information on the web when you run into a jam as compared to a similar problem with Linux.

---

### Post by lammert-nijhof on 2019-10-14
Still using that ZFS system every week, no problems.

---

### Post by Artim on 2019-10-14
Just for giggles and grins I'm trying out GhostBSD (it's a kinda front-end for FreeBSD, easier installation, Xfce desktop).  In Live mode it's extreeemely fast on a very modest old machine.  Quite sparse compared to just about every Linux distro I've ever tried, and my favorite Internet suite (Seamonkey) is no longer maintained in FreeBSD's repositories.  Hopefully I'll find a way to get it anyway.  So far so good!

The reason I wanted to venture into BSD to begin with has to do with two things that seem to worry a lot of bloggers I read:

**One is systemd** and what it "could become" over time.  Some people write about it like it's the advent of hostile Robotic Overlords ruling over humanity.

**The other is Microsoft**, jumping into Linux with both feet, buying out GitHub and basically taking over the Linux Foundation.  Not that I begrudge any private company using Linux to increase profits, but there's a lot of that "embrace, extend, extinguish" talk still going around.

Trying BSD out feels like putting some extra distance between myself and these two "great evils."

I'm really *not* worried about either one, but it's fun to go where I've never explored before.

---

### Post by lammert-nijhof on 2020-04-19
Still using FreeBSD, but now version 12.1p3. I have added another spare laptop disk, so the configuration is now:
- 3.5"; IDE 250GB + 320GB
- 2.5"; SATA-1; 2 x 320GB
Every week I power on that old Pentium and backup all my changes during that week in 0.5 - 1 Hour. I stopped using rsync, since ZFS is much faster, since:
- it only copies the changed physical records, which is very useful for large files, like ISO files and virtual disk files (vdi, qcow2);
- if both sides use the same compression, it will send the compressed physical records.

I'm not afraid for Raid-0 on those old disk, since they age one working week during a whole year :) And I also have a second backup on a new 1 TB SSHD in my laptop. A third monthly copy of photos, music and family videos are also stored on my 64 GB SD Card in my phone.

---

### Post by O)9(yo&amp;# on 2020-06-27
I checked out True and Ghost awhile back, pretty much liked both (although on Ghost I got hacked somehow; somebody was on the terminal and attempting to chroot. Almost certainly not the operating system's fault, but it did "spook" me - pardon the pun.) What really impressed me was that I could use them on an old hard drive that had been red-flagged on Crystal Disc for years, and when Windows was on it, it sounded like somebody getting fried in the electric chair while it booted up. but the BSD systems ran cool and quit. ZFS I guess was the reason, plus nice lean systems. 

Now of course True, which changed its name to Trident, is not even BSD anymore. It's now based on Void Linux. Haven't given it a try lately but I'll get bored no doubt and try it at some point.

---

