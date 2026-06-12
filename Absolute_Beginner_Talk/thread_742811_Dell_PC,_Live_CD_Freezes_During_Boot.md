---
title: "Dell PC, Live CD Freezes During Boot"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by gplauche on 2008-04-02
Hello,

I'm new to Linux and Ubuntu. I just got the latest Ubuntu 7.10 cd in the mail today. I tried booting the live cd but it keeps freezing up on me. After I select the Start or Install option the Ubuntu logo and a progress bar show up. The orange bar goes back and forth for a little while before the progress bar starts but it always freezes up when there are 4 squares left.

My computer is a Dell Dimension 2400 desktop pc with Intel Pentium 4 2.8 GHz, 512 MB of RAM and 14 GB of HD space left. I'm currently running Windows XP Home Edition with SP2.

What can I do to get this thing to finish booting?

Geoffrey

---

### Post by Rocket2DMn on 2008-04-02
Did you check the md5sum on the iso file?
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Once those check out, you should burn the disc at a slow speed like 4x to prevent write errors (I tend to find that the disc check built into the cd doesn't work very well).

If all that fails to get your CD booting up properly, you may need to try the alternate install cd available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate disc.  The alternate install cd doesn't have a live sessions, just a text based installer, but it is very easy to use.

---

### Post by gplauche on 2008-04-02
Thanks. I checked the disk for errors and it came out clean. I can try downloading the alternate cd for installing but I'd like to be able to run the Live CD to try out Ubuntu first.

Other things I've tried to get the Live  CD to boot:

Defraging the HD (because I read somewhere that a severely fragmented HD could mess up installation).

Adding acpi=off and aic7xxx.aic7xxx=no_probe to the boot command as recommended by the Help file on the disk.

I tried booting it in safe graphics mode.

I also tried changing the monitor setting from VGA to 640X480 (?).

The boot always freezes when the progress bar is almost finished with 4 boxes left.

---

### Post by Rocket2DMn on 2008-04-02
Then I would go check the md5sum on the iso image you downloaded under windows, then reburn the disc if the md5sum checks out, at 4x speed.  Like I said, that error checker doesn't work very well.

---

