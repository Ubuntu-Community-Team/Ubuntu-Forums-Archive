---
title: "Ubuntu Crash -- Need help"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by johnnyboy on 2006-06-02
I am an absolute newbie to linux, so if I show a disgusting amount of ignorance, I apologize, but I am somewhat lost (okay, I'm lying, I am REALLY lost).

My system started acting up the other day for what seemed to be no apparent reason.  I am running ubuntu 5.10 Breezy Badger (or was).  I am using a Dell Inspiron 600m w/ 512 RAM, ATI Radeon vid card, Intel Pentium M processor w/ speed of 1.4 gigs.

I typically use the GUI, w/ some use applied through terminal, however I rarely, if ever, solely use command line.  I also rarely use root, unless it is to use the chmod command in order to configure some basic config files for specific proggies.

After the com started acting really slow, I checked the top command, with no unusual finds.  The system then refused to boot to the GUI, and would only run command line, the errors came up with the following:

*checking root file system...
 /contains a file system with errors, check forced
/:
 Inode 2523454 has illegal block(s)
/:unexpected inconsistency; run fsck manually -- NOTE: i did not run fsck manually as I recieved a warning saying that it could seriously damage the hard drive
                                                                 [FAIL]
*fsck failed, Please repair manually and reboot.  Please note that the root file system is currently mounted read-only.  To remount it read-write:
  #mount -n -o remount, rw /
*bash:lesspipe: command not found
*bash:dircolors:command not found

I have had 3 different op systems crash on me for what I found to be no reason.  I am getting tired of it, since I had just recently installed ubuntu I decided to clean the hard disk and reinstall from scratch.  However the ubuntu disk will not reinstall, it will give me errors saying that it cannot reinstall the base system as there are files left on there after the erasure process.  Any help is appreciated, I am very lost.

Thanks

---

### Post by learning on 2006-06-02
I am a newbie too, so take this for what it is worth...

I had the same problem one time during one of my many re-installs.  I used the partitioner to re-format the petition, then ran the install.  

That got it to work.

---

### Post by johnnyboy on 2006-06-02
Thx for the reply.  I will attempt to do that.  I don't know if it will work though as the hard drive cannot be booted and therefore I don't know if I even have access to command line.  I'll give it a go and reply in a bit.

---

### Post by Iowan on 2006-06-02
[QUOTE=johnnyboy]
I have had 3 different op systems crash on me for what I found to be no reason.  .  [/QUOTE]I'd hate to breathe gloom and doom, but it certainly sounds like something on that machine is unhealthy.

---

