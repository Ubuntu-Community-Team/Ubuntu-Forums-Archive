---
title: "Reinstalling -- what should I save?"
date: 2005-08-01
forum: Absolute Beginner Talk
---

### Post by mikeb on 2005-08-01
Ubuntu was working great for a couple of weeks, then, all of a sudden, digital audio output was downgraded to stereo only. I have no idea what happened, but I can't seem to fix it. As the only connection between the computer and audio amplifier is via the digital audio cable and it works, the problem is only getting the computer to output AC3.

So, I'm hoping to get everything back with the reinstall. I'm planning on saving the sources.list for apt as that will speed up the restoral.

Considering that I'm using the machine only for multimedia, are they any other files I should save or other tips on how to do the reinstall?

Thanks.

---

### Post by heimo on 2005-08-01
All the files you have touched. I'd at least backup /etc and /home directories, and on those computers where I have any server software running (probably doesn't concern you) I'd definitely backup parts of /var too (/var/www, /var/spool). Maybe /root -directory, too. I'd burn a DVD of these, reinstall and then use the backups to copy back my home directory and those services that I've tweaked most (Apache, postfix, network settings, firewall config, xorg.conf).

Be sure that all the hidden directories (beginning with dot '.') on those directories you backup will be included. If storage space is not an issue, just copy the files - otherwise use tar with gzip or bzip compression - it's the best single backup solution. :)

---

### Post by mikeb on 2005-08-01
Many thanks for your helpful response, heimo. I'll do as you suggest.

---

### Post by Footer on 2005-08-01
[QUOTE=heimo]All the files you have touched. I'd at least backup /etc and /home directories, and on those computers where I have any server software running (probably doesn't concern you) I'd definitely backup parts of /var too (/var/www, /var/spool). Maybe /root -directory, too. I'd burn a DVD of these, reinstall and then use the backups to copy back my home directory and those services that I've tweaked most (Apache, postfix, network settings, firewall config, xorg.conf).

Be sure that all the hidden directories (beginning with dot '.') on those directories you backup will be included. If storage space is not an issue, just copy the files - otherwise use tar with gzip or bzip compression - it's the best single backup solution. :)[/QUOTE]

Does a reinstall touch /home directories or can those be left alone?  I'm thinking ahead to October when Breezy comes out final and I do a reinstall of the OS.  Better to be safe than sorry and make a backup of them as you suggest?

---

### Post by heimo on 2005-08-01
Of course I can't recommend anything else than to _do_ backups before any major changes to system. If you're going to apt-get dist-upgrade, home should be safe. Keeping important stuff on their own partitions or disks can make reinstalling lot easier. I've done dist-upgrades from different versions of Debian and Ubuntu several times, sometimes you get package conflicts, which are solvable with some work, but may put your system to almost unworkable condition (at least for a newbie). What I'd try to do when Breezy is released, is to download install CD, burn it, make backups of your important stuff, edit sources.list, use apt-get update && apt-get upgrade && apt-get dist-upgrade to upgrade from Hoary to Breezy. If you get problems, you can always reinstall.

---

### Post by Footer on 2005-08-02
What's the difference between doing:

     apt-get update && apt-get upgrade && apt-get dist-upgrade

or:

     download install CD, burn it, install it

for Breezy when it comes out final?  Or is there no difference?  I believe you've answered my question though:  /home directories are safe from upgrades but it's good practice to back them up before any major updates ... and just plain good practice to back them up often regardless!

---

### Post by heimo on 2005-08-02
If you dist-upgrade, all the stuff that you have installed using package management, will be upgraded and old configuration will be used as far as possible. If you download CD, boot and install, even if you won't format partitions, no smart upgrading is done and you will end up with default set of packages and original configuration files.

Now, there's plus and minus sides on this story. If you dist-upgrade, you really want to make sure that important metapackages (actually only one comes to my mind) like ubuntu-desktop (or if you're KDE friend, kubuntu-desktop) is installed so you get new software that's included on desktop. You will have your old configuration and possibly miss some enhancements. You may want to try creating new user and check how his desktop looks.

Even if you download CD, you can still use it to dist-upgrade. That'd probably be smart move to minimize bandwidth. You can probably add CD to sources using Synaptic. But don't forget to update && upgrade after that either - it's possible that release CD is already old.

I'm probably going to do reinstall. I have /home on its own disk and I've been using Breezy for ... months. But I'm going to do it mainly to see the new graphical installer and test hardware autodetection.

---

### Post by Footer on 2005-08-02
Thanks heimo!  Good explanation ... I understand completely.

 :)

---

