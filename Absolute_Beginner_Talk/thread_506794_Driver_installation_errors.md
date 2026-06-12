---
title: "Driver installation errors"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by Githlar on 2007-07-22
I downloaded the recent Linux drivers for my wireless receiver and my PCI video card. But, when I try to run the installers for them (or tar to unzip a package) I get an error similar to "Operation not permitted." I looked up permission problem and people said to use "sudo [command]," but that doesn't work for me either. I even used "sudo su" to enter an elevated terminal window, but that had no effect either. I am trying to run these files from a USB flash drive if that's any help.

I did read something about the /etc/fstab file. Might this be my problem?

This is my first installation of Ubuntu (or Linux for that matter...) so I guess you could call me a Super n00b. So, please, go easy on me... I really don't understand anything yet.

---

### Post by tomcheng76 on 2007-07-22
you better copy the tar.gz or bz2 from your flash drive to your home directory
then using this command should works 

tar xvf nameofyourfile.tar.gz

---

### Post by Githlar on 2007-07-22
Well thank you. That *did* work. However, doesn't having to copy over all my files to my home directory kind of destroy the purpose of a flash drive? Is there any way to bypass that behavior?

PS: Got my wireless adapter installed, but my ATI graphics card is a pain in the butt to install. Any suggestions? I tried the guide [here](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide), but to no avail. X keeps giving me a configuration error saying fglrx doesn't exist or something like that. That's when I'm using onboard video. When I'm using PCI video, Ubuntu gets three bars into loading and just sticks.

---

### Post by 56seeker on 2007-07-22
> **Githlar said:**
> Well thank you. That *did* work. However, doesn't having to copy over all my files to my home directory kind of destroy the purpose of a flash drive? Is there any way to bypass that behavior?


Well; a *.tar.gz is a Linux "zip" file.

The command "tar xvf <filename> unzips it; so if you've enough room on your USB drive you could unzip and run the drivers from there.

---

### Post by Githlar on 2007-07-22
I do have enough space and that's what I tried doing, but it gave me that permission error. Odd.

PS: Still no luck on those ATI Radeon 9250 drivers... However, I did manage, by some miracle, to figure out how to bring my computer back from the dead (when the drivers screwed up). It took about 5 installations, but I figured it out all on my own =D

---

### Post by 56seeker on 2007-07-23
> **Githlar said:**
> I do have enough space and that's what I tried doing, but it gave me that permission error. Odd.


Then it's probably formatted with NTFS. Linux has problems writing to an NTFS as standard; although it's easily fixable. I can't remember the name of the program but there's a program in Synaptic whiives you read permission on NTFS drives (there's probably a few, actualy).

Or you coSB drive as FAT.

---

### Post by Githlar on 2007-07-24
The drive is FAT32. I knew Linux had issues with NTFS by default, so I formatted with FAT32.

---

