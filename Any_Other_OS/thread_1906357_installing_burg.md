---
title: "installing burg"
date: 2012-01-08
forum: Any Other OS
---

### Post by RastaCalavera on 2012-01-08
Hello!

I am trying to install burg on a 500gb hd that is partitioned into two drives with linux installed on a 80gb partition (mint --> I know its not Ubuntu but I have gotten more help from these forums than the mint ones, I use to use 10.4 and they use the same dependicies so I don't think it matters much..) so here is a list of my hds


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   154296319    77147136    7  HPFS/NTFS/exFAT
/dev/sdb2       154298366   156299263     1000449    5  Extended
/dev/sdb5       154298368   156299263     1000448   82  Linux swap / Solaris


question is where is my mbr? is it on the sdb1 that has the * under boot? would I install it using hd0 or hd0,1 or hd1? I don't want to screw it up. The process I am following is located [here]("http://www.unixmen.com/how-to-install-burg-in-ubuntu-/") and the process I don't want to screw up is this:
sudo burg-install "(hd0)"
Remember to substitute ‘hd0&#8242;  with the drive on which your MBR is installed.

any advice would be very much appreciated. Thanks!!!:D

---

### Post by bluexrider on 2012-01-08
The MBR should be on your Windows Partition sdb1.

How are you currently booting into Ubuntu? Meaning, are you using windows boot selection?

---

### Post by RastaCalavera on 2012-01-09
> **bluexrider said:**
> The MBR should be on your Windows Partition sdb1.

How are you currently booting into Ubuntu? Meaning, are you using windows boot selection?

I don't quite understand your question...I installed windows first then used g parted to set aside the Linux space. When i boot up, it is going to grub and lets me choose what to boot from. In terminal would I write the sdb1 or hd1?

Thanks for the reply!!!!

---

### Post by cortman on 2012-01-09
I had burg on my laptop for a while before I upgraded. Nice little piece of software. Use this command to install it on your MBR-

```
sudo burg-install /dev/sdb1
```

---

### Post by Perfect Storm on 2012-01-09
Moved to Other OS/Distro Talk.

---

### Post by bluexrider on 2012-01-10
> **RastaCalavera said:**
> I don't quite understand your question...I installed windows first then used g parted to set aside the Linux space. When i boot up, it is going to grub and lets me choose what to boot from. In terminal would I write the sdb1 or hd1?

Thanks for the reply!!!!

If you are trying to dual boot follow the instructions at the bottom of my post. (signature)


   > Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   154296319    77147136    7  HPFS/NTFS/exFAT
/dev/sdb2       154298366   156299263     1000449    5  Extended
/dev/sdb5       154298368   156299263     1000448   82  Linux swap / Solaris


If you are trying to install Burg you want it on your partition which contains Ubuntu sdb2

---

### Post by RastaCalavera on 2012-01-10
If you are trying to install Burg you want it on your partition which contains Ubuntu sdb2[/QUOTE]


so the mbr is on the larger linux partition? When I turn on my machine it takes me to the grub menu. . would there be any harm in installing it two different locations? like say db1 and db2?

---

### Post by RastaCalavera on 2012-01-10
> **cortman said:**
> I had burg on my laptop for a while before I upgraded. Nice little piece of software. Use this command to install it on your MBR-

```
sudo burg-install /dev/sdb1
```

sdb1 because that is where the asterisk (*) is? That was my first assumption as well but wanted to make sure.. . there is also a 300gb hard drive in my machine that does not have an os on it but i don't think that was listed. . .also, would it be bad if i just installed it on two different drives? it would only work with the one with the mbr and just kind of sit there doing nothing on the others right? 

Thanks for the reply

---

### Post by cortman on 2012-01-11
> **RastaCalavera said:**
> sdb1 because that is where the asterisk (*) is? That was my first assumption as well but wanted to make sure.. . there is also a 300gb hard drive in my machine that does not have an os on it but i don't think that was listed. . .also, would it be bad if i just installed it on two different drives? it would only work with the one with the mbr and just kind of sit there doing nothing on the others right? 

Thanks for the reply

MY understanding is that the MBR is located at the front of the HD, ergo, on the first partition. I don't think it'd make any difference at all if you installed it on different drives, so long as you can boot and run update-grub to make sure you get all possible OS's.

---

### Post by RastaCalavera on 2012-01-13
So, I tried sdb1 and this is what I got


/usr/sbin/burg-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/burg-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/burg-setup: error: if you really want blocklists, use --force.


so I am a little scared to use the force command.....any other ideas?

---

### Post by cortman on 2012-01-13
Hm... I'd be a little hesitant to force it too. And I've been known to be wrong before.

How about you download and run [Boot Info Script]("http://bootinfoscript.sourceforge.net/") and paste the results here? Then we'll know for certain where your system is booting from.

---

