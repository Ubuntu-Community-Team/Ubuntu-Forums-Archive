---
title: "Bluetooth support for MacBookPro6,2 (and maybe other 2010 models)"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by bfroemel on 2010-05-02
This is a minimally modified btusb driver taken from the 2.6.32 kernel. I only tested the PAN aspect on my MBP 15" i7, but it seems to be a standard BCM2043 device that is fully supported by the generic driver(s).

> #lsusb
> Bus 001 Device 009: ID 05ac:8218 Apple, Inc.

output on insmod:
```

[38073.885671] Bluetooth: Generic Bluetooth USB driver ver 0.7
[38073.886642] usbcore: registered new interface driver btusb
[38073.911497] Bluetooth: L2CAP ver 2.14
[38073.911503] Bluetooth: L2CAP socket layer initialized
[38073.941353] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[38073.941357] Bluetooth: BNEP filters: protocol multicast
[38073.951236] Bridge firewalling registered
[38073.955646] Bluetooth: SCO (Voice Link) ver 0.6
[38073.955648] Bluetooth: SCO socket layer initialized
[38074.019858] usb 1-1.1.1: USB disconnect, address 7
[38074.030511] Bluetooth: RFCOMM TTY layer initialized
[38074.030517] Bluetooth: RFCOMM socket layer initialized
[38074.030520] Bluetooth: RFCOMM ver 1.11
[38074.288792] usb 1-1.1.2: USB disconnect, address 8
[38220.936249] bnep0: no IPv6 routers present

```

I just added vendor and product ids, so there is a good chance they are the same across all new MBP 2010 models where bluetooth doesn't work out of the box.
I'll send a patch upstream in a while...

---

### Post by newbie80 on 2010-05-02
bfroemel, looks like you were able to successfully install ubuntu (i am assuming 10.04) on macbook pro 6.2. I have the same machine and I am planning to load ubuntu alongside OSX, if possible can you please be kind enough to post a (quick) instruction guide or at least your experiences with how you got things to work for 6.2 as this is missing in the wiki. Would be of a great help to have some experiences to refer to when I try the installation.

---

### Post by bfroemel on 2010-05-02
it's a little offtopic, but here you go:

- replaced original HDD with a blank OSZ Vertex 120 GB SSD
- installed OSX on it (GUID partition table)
- resized OSX to about 30 GB (partition layout looked like: 200 MB EFI, 30GB OSX, unused space)
- installed refit
- used an Ubuntu netinst ISO (10.4), advanced installation
- custom partitions: 150MB ext2 /boot, 4.5 GB swap, rest ext4 (noatime) /
- selected only a core set of packages (just a very small gnome desktop setup, no themes, no bling bling)
- slected the generic 2.6.32 kernel with a generic initrd
- installed grub-pc on my boot paritition (in my case /dev/sda3)

=> boots via refit into grub2 and from there into Ubuntu without any problems.

I have to admit, I didn't even try to install graphically or follow any Wiki instructions. I come from Debian unstable/experimental so this was pretty smooth :-)

---

### Post by kosumi68 on 2010-05-02
Great work with the DKMS package!

---

### Post by newbie80 on 2010-05-02
Thanks bfroemel, I will try it out pretty soon.

---

### Post by jeroenv on 2010-05-05
Bluetooth works fine with this patch on my MacBookPro6,2.

---

### Post by mari0123 on 2010-05-13
You are a star mate. Works perfectly for me under virtual box.

---

### Post by lael on 2010-05-13
> **bfroemel said:**
> This is a minimally modified btusb driver taken from the 2.6.32 kernel. I only tested the PAN aspect on my MBP 15" i7, but it seems to be a standard BCM2043 device that is fully supported by the generic driver(s).

> #lsusb
> Bus 001 Device 009: ID 05ac:8218 Apple, Inc.

I just added vendor and product ids, so there is a good chance they are the same across all new MBP 2010 models where bluetooth doesn't work out of the box.
I'll send a patch upstream in a while...

Just to confirm my MacBookPro 6,1 (17" i7) works with this with the same deviceID

```
Bus 001 Device 007: ID 05ac:8218 Apple, Inc.
```

I was able to pair a bluetooth mouse with this.  

Thank you!

---

### Post by haopeng on 2010-06-04
Hi I also have MacBookPro6.1(17" i5) but when I installed the btusb-dkms_0.0.1_all.deb.gz and go to System->Preferences->Bluetooth it says "your computer does not have any bluetooth adapters plugged in". And my bluetooth keyboard/mouse still cannot be recognized. Can anyone help? Thank you in advance.

my lsusb show following:
```
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

---

### Post by jonas_t on 2010-06-19
Yay, nice - works fine on my MBP 6,2! Thanks!

---

### Post by ZeroLinux on 2010-06-21
Is it possible to make patch for this Bluetooth?
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

It is for iMac 21.5

---

### Post by jojosmith on 2010-08-11
> **ZeroLinux said:**
> Is it possible to make patch for this Bluetooth?
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

It is for iMac 21.5

Bump ... same issue Macbookpro 7-1 using Lucid

---

### Post by scullez on 2010-08-19
MBP7.1 users, we need usb device ID 05ac:8213
Use this instructions [http://ubuntuforums.org/showthread.php?t=1541357](http://ubuntuforums.org/showthread.php?t=1541357) , just replace 0x8215 to 0x8213 in btusb.patch

---

### Post by Blutack on 2010-09-20
Instructions above do not work for Maverick due to a changed kernel interface in 2.6.35.
Instead, grab the head of btusb.c from kernel.org
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD) .  The deb package won't install properly but it puts the files in the right place.  Put your new kernel.org copy of btusb.c over the top of the existing one (in /usr/src/btusb-0.0.1).  I also changed the version number in btusb.c to 0.6.1 to shut up a complaint from DKMS that the module version was the same.
The changelog indicates it's been patched to support the newer, i7 IMacs but it still didn't support my white Macbook 7,1.
For that, I had to add a line to the file (between the other two entries)
```
    
/* Apple iMac11,1 */
    { USB_DEVICE(0x05ac, 0x8215) },

    /* Apple MB7,1 */
    { USB_DEVICE(0x05ac, 0x8218) },

    /* AVM BlueFRITZ! USB v2.0 */
    { USB_DEVICE(0x057c, 0x3800) },
```
The instructions linked in the post above then worked perfectly.

---

### Post by emanuelgreisen on 2010-09-21
> **haopeng said:**
> Hi I also have MacBookPro6.1(17" i5) but when I installed the btusb-dkms_0.0.1_all.deb.gz and go to System->Preferences->Bluetooth it says "your computer does not have any bluetooth adapters plugged in". And my bluetooth keyboard/mouse still cannot be recognized. Can anyone help? Thank you in advance.

my lsusb show following:
```
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

I have the exact same issue with my MacbookPro6,1 17", other computers can see the machine has bluetooth activated, but it cannot see the name of the PC or anything else. It is just visible as "Apple Bluetooth Device".

```

Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

```

---

### Post by nolsen311 on 2010-09-26
Anyone checked on this bug upstream to see if the vendor IDs will get added to official sources?

...also...maybe get a timeline for official delivery?

> **Blutack said:**
> 
```
    
/* Apple iMac11,1 */
    { USB_DEVICE(0x05ac, 0x8215) },

    /* Apple MB7,1 */
    { USB_DEVICE(0x05ac, 0x8218) },

    /* AVM BlueFRITZ! USB v2.0 */
    { USB_DEVICE(0x057c, 0x3800) },
```


---

### Post by Twiggy794 on 2010-10-10
> **Blutack said:**
> Instructions above do not work for Maverick due to a changed kernel interface in 2.6.35.
Instead, grab the head of btusb.c from kernel.org
[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob_plain;f=drivers/bluetooth/btusb.c;hb=HEAD) .  The deb package won't install properly but it puts the files in the right place.  Put your new kernel.org copy of btusb.c over the top of the existing one (in /usr/src/btusb-0.0.1).  I also changed the version number in btusb.c to 0.6.1 to shut up a complaint from DKMS that the module version was the same.
The changelog indicates it's been patched to support the newer, i7 IMacs but it still didn't support my white Macbook 7,1.
For that, I had to add a line to the file (between the other two entries)
```
    
/* Apple iMac11,1 */
    { USB_DEVICE(0x05ac, 0x8215) },

    /* Apple MB7,1 */
    { USB_DEVICE(0x05ac, 0x8218) },

    /* AVM BlueFRITZ! USB v2.0 */
    { USB_DEVICE(0x057c, 0x3800) },
```
The instructions linked in the post above then worked perfectly.

Has anybody gotten this working on a Macbook Pro 6,2?  I can get the module to build but it never seems to recognize my bluetooth adapter.  Worked great with the OP package in Lucid.

---

### Post by Technoviking on 2010-10-14
This [btusb.c]("http://www.mikesplanet.net/files/apple/btusb.c") works to get bluetooth working under Ubuntu 10.10. . Could a new deb file be built with it.

T-V

---

### Post by Technoviking on 2010-10-14
Howto install by hand.
[https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Bluetooth](https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Bluetooth)

---

### Post by Technoviking on 2010-10-14
Reported a bug to hopefully get this fixed in the kernel for Ubuntu 11.04.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660729](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660729)

---

### Post by pantropik on 2010-10-14
This fix is so trivial, I can't understand why it hasn't been done already. It's kind of sad.

---

### Post by Technoviking on 2010-10-14
> **pantropik said:**
> This fix is so trivial, I can't understand why it hasn't been done already. It's kind of sad.

Probably cause no bug report was filled. Till a bug report is filled, the devs will not know there is  a problem.

T-V

---

### Post by itismike on 2010-10-31
Bluetooth works great, thanks!
but... not in stereo. Does this patch remove A2DP support?

---

### Post by vsh3r on 2010-10-31
Hi,

I tried to install the .deb update and I got the following error.

ERROR:
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

V$H.

---

### Post by kernel_script on 2010-10-31
> **ZeroLinux said:**
> Is it possible to make patch for this Bluetooth?
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

It is for iMac 21.5

> **jojosmith said:**
> Bump ... same issue Macbookpro 7-1 using Lucid

Double-Bump... same here with Macmini4,1

---

### Post by itismike on 2010-10-31
Hi V$H. That's normal. Or at least I saw the same error. Just click through it. It gives the impression that this is a pretty messy fix...

Not sure if this is model-specific, but the [instructions here]("https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Bluetooth") describe how to make the DPKG error go away after you get Bluetooth working.

---

### Post by vsh3r on 2010-10-31
I tried to install the .deb file on my Macbook Pro 6,2 with a fresh install of Ubuntu 10.10 and the patch didn't install.

V$H.

:confused:

---

### Post by itismike on 2010-10-31
@V$H: Be sure to extract the patch first. Just extract it into a new folder, double-click it, and ignore the error. For my 10.10 install it reported "Installed" after the error was dismissed.

---

### Post by vsh3r on 2010-11-01
Hi,

Here is a listing of the error messages i'm seeing after an install...

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 199020 files and directories currently installed.) 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up btusb-dkms (0.0.1) ... 
Loading new btusb-0.0.1 DKMS files... 
 
Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz. 
File does not exist. 
dpkg: error processing btusb-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up gwibber-service (2.32.0.2-0ubuntu1) ... 
No apport report written because MaxReports is reached already
Processing triggers for python-central ... 
Setting up gwibber (2.32.0.2-0ubuntu1) ... 
Processing triggers for python-central ... 
Setting up gwibber-themes (2.32.0.2-0ubuntu1) ... 
Errors were encountered while processing: 
 btusb-dkms 
Setting up btusb-dkms (0.0.1) ... 
Loading new btusb-0.0.1 DKMS files... 
 
Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz. 
File does not exist. 
dpkg: error processing btusb-dkms (--configure): 
 subprocess installed post-installation script returned error exit status 2 

NOTE: I've removed the btusb-dkms using the synaptic package manager but it wont let me reinstall it.

V$H.

:guitar:

---

### Post by itismike on 2010-11-01
I didn't see these specific errors during my install. Seems like something went differently for you.

Try googling the phrase "subprocess installed post-installation script returned error exit status 2" There are many folks posting solutions for that particular error. 

If you get that resolved, return to the link I provided for instructions to resolve the other dpkg error.

Good luck! Let us know how it goes!
:popcorn:

---

### Post by duke9nuke on 2010-11-02
Will this work for 9.10 64bit?

---

### Post by itismike on 2010-11-02
> **Technoviking said:**
> Probably cause no bug report was filled. Till a bug report is filled, the devs will not know there is  a problem.

T-V

reported:
_[bluetooth doesn't work out-of-the-box on a MacBook Pro]("https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/669636")_

If you're affected by this bug, click "This bug affects me too" at the top.

---

### Post by itismike on 2010-11-08
Bluetooth disappeared for me ("no bluetooth adapters present") after what I think was an update this weekend. I looked through `/var/log/apt/term.log` for a mention of something related to bluetooth but found nothing. Is anyone else missing bluetooth also?

---

### Post by vsh3r on 2010-11-08
(see attached screen shot)

Have you tried doing the procedure at:
[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)

?

I haven't yet.  :(

V$H.

---

### Post by vsh3r on 2010-11-08
When I tried out the commands that are posted on the page I got the following...

 sudo dpkg -i btusb-dkms_0.0.1_all.deb
dpkg: error processing btusb-dkms_0.0.1_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 btusb-dkms_0.0.1_all.deb


Does anyone know what the correct name is for the package or how to find out?  Can I get it via apt-get?

V$H.

---

### Post by itismike on 2010-11-08
go back and read between the lines of code. The file you need is provided in a hyperlink within the instructions. Let me know if it still works so I can re-apply the solution.

---

### Post by vsh3r on 2010-11-08
Yes, I understand.  However, the Debian package number 0.0.1 is out of date so I can't compile the code without the rest of the package?

Is there a flag for[FONT=monospace] [/FONT]dpkg that will automaticallly select whatever the latest version number is for example 
sudo dpkg -i btusb-dkms*.deb rather then sudo dpkg -i btusb-dkms_0.0.1_all.deb  ?

Neither works.  I need to get the rest of the btusb package so that I can compile the code.

V$H.

---

### Post by itismike on 2010-11-08
I just ran through all the steps (again) and my bluetooth is working again.
I did see errors during the install (as the page warns,) but after completing all the steps (including the `sudo apt-get install -f`) the system seems fine.

However, when I run an update in Synaptic, it wants to upgrade my btusb-dkms (see attached)

Guess I'll have to restrict this from updating until a more solid solution is found.

---

### Post by Technoviking on 2010-11-09
Added a package to my PPA that should fix the problem, hopefully will be added to mactel ppa soon.

[https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Bluetooth](https://help.ubuntu.com/community/MacBookPro6-2/Maverick#Bluetooth)


Bug report to get change in official PPA:
[https://bugs.launchpad.net/mactel-support/+bug/673125](https://bugs.launchpad.net/mactel-support/+bug/673125)

Cheers,
T-V

---

### Post by itismike on 2010-11-09
Fantastic. Thanks, T-V!

---

### Post by Technoviking on 2010-11-09
Good news, the fix should be in the official Mactel ppa soon.

T-V

---

### Post by vsh3r on 2010-11-10
Hi,

It looks like the bluetooth code made its way into the mainstream update.  I tried to pair it with my Android 2.1 phone and noticed the following error in my /var/log/messages.

bluetooth-apple[1670] general protection ip:XXXXXXXXX sp:XXXXXXXX error:0 in libgobject-2.0.so.0.2600.0[XXXXXXXXXX+49000]

The good news is that it did recognize the device. 

How do I attach a debugger to this?

:P:(

V$H.

---

### Post by denix on 2012-05-19
Hi, I have a Macbook pro 5.1 with the same bluetooth interface and does not work. Is there a package for xubuntu 12.04?

Thanks,
Denis

---

### Post by rab777hp on 2012-07-03
I have a MacBook Pro 7,1 running Lucid Lynx, so far nothing has worked- I have attempted all above suggestions. Is there a fix for this to get bluetooth working? Trackpad pretty much sucks (maximum speed and acceleration and it's still so sluggish, not to mention dragging and right clicking fiascos), I really want to get my bluetooth mouse working.

---

### Post by itismike on 2012-07-03
On a 6,2 from mid 2010 I'm running Precise Pangolin very smoothly. It even enabled multi-touch on my trackpad. Haven't tested bluetooth yet though. Try a live CD and see if it works for you.

---

