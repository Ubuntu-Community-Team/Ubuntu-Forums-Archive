---
title: "LiveCD install problem"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by ndorfn on 2007-03-01
Let me preface this by saying I am a complete Linux noob and am trying to learn since I am fed up with my current XP install and am not very interested in Vista.

I am having problems booting to the LiveCD(6.10) on my system:

MSI MS-7125/nForce4
AMD Athlon 64 4000+
Socket 939
1 Gb PC3200
ATi X850XTPE
2 WD Raptor 36Gb (Raid 0) (SATA channel 3&4) (XP install currently)
1 WD 250Gb (Open Space for Ubuntu install) (SATA channel 1)
Audigy2
PS/2 KB and Mouse

The system will boot to the CD menu but when I try to load either the first choice (Run/Install Ubuntu) or the second choice (graphics compat mode) it ends up giving an error like:

"Buffer I/O error in device sda1"

Any help would be much appreciated. Thank you in advance.

---

### Post by chggr on 2007-03-02
Which liveCD did you download? The correct one for your case (AMD 64bit processor) is:
CD: ubuntu-6.10-desktop-amd64.iso
DVD: ubuntu-6.10-dvd-amd64.iso

After downloading the file, did you calculate the MD5 sum and compared it with the one given on the server? Doing this ensures that the downloaded file is not corrupted.

Finally, if after all that the problem persists, you can try using the alternate CD: ubuntu-6.10-alternate-amd64.iso

---

### Post by Tom Fransson on 2007-03-02
I have nearly the same problems as above, but I dont get any error
Message. My system is Dell latitude pentium 3, 750 processor, with 256 ram.
I choose Ubuntu 6.10-desktop-i386.iso and did md5checksum. That was ok and all the files were there after burning. What happends are after boot and the first alt. run/install the screen get black after a few seconds and the cursor blinking: It gets hanging here, nothing happends. Do I have to use the boot prompt and some special command or what shall I do?

I thanks for all help I can get.

/Tom Fransson

---

### Post by chggr on 2007-03-02
In your case Tom, it's probably a graphics card problem.
Try using the alternate LiveCD, which might correct those problems:
ubuntu-6.10-alternate-i386.iso

In case this doesn't work, you can perform the installation using the command line and not the Graphical User Interface

---

### Post by Tom Fransson on 2007-03-04
With Ubuntu-6.10-alternate-i386.iso I used command line , but in the step identification and mount cd-rom it hangs again. It seems to be the same problem as in the desktop version. Does it exit any solution, not included a new computer order?=)

/Tom

---

### Post by elaich on 2007-03-04
I had a similar problem trying to install Edgy. Solution - I installed Dapper instead. Dapper is fine and is a legacy OS with extended support. I could do an upgrade, but see no reason to.

---

### Post by ecs_pf5 on 2007-03-04
Can someone give the briefest pointers to performing the installation using the command line and not the Graphical User Interface. That's what I have decided to try to resolve my similar problem with a Radeon X700 card, but I have no idea where even to begin researching :(

---

### Post by dexter on 2007-03-04
> **chggr said:**
> Which liveCD did you download? The correct one for your case (AMD 64bit processor) is:
CD: ubuntu-6.10-desktop-amd64.iso
DVD: ubuntu-6.10-dvd-amd64.iso

After downloading the file, did you calculate the MD5 sum and compared it with the one given on the server? Doing this ensures that the downloaded file is not corrupted.

Finally, if after all that the problem persists, you can try using the alternate CD: ubuntu-6.10-alternate-amd64.iso

The Athlon 64 can also run in 32 bit mode, so a i386 version will also work, I would even recommend it, there is a lot more software available for i386 then for AMD64.

---

### Post by Tom Fransson on 2007-03-05
I tried Dapper. When I boot, following happends:

Loading essential file drivers ... OK
Mounting root file system ...
Uncompressing Linux ... OK, booting the Kernel

Then I get several errors similar

[17179828.736001] Bufffer I/O error on device hdc, logical block 357600

and the installation hangs. I guess that hdc is where linux trie to do a partition or something. I have just one disc and one partition 9 Gb where I have Windows XP installed and 4.5 Gb free. If I had to create something wouldn't the installation program let me or must I do this before I start the boot?

---

