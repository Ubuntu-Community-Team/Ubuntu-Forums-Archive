---
title: "Triple Boot Startup Problems"
date: 2010-02-04
forum: Apple Hardware Users
---

### Post by BigMontana on 2010-02-04
I just configured my machine to run Max OS 10.5 (Leopard), Windows 7 64-bit, and Ubuntu 9.10 64-bit.  It took some trial and error, but the process I ended up using was to take a clean install of OS X, use bootcamp to partition and install Windows, then reboot back to OS X and use Disk Utility to split the Mac partition to make room for Ubuntu.  All three operating systems are running pretty well, but it's kind of a hassle to boot to the different operating systems.

If I restart the computer GRUB starts and gives me the following options:

```
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200)
Mac OS X (on /dev/sda2)
Windows 7 (loader) (on /dev/sda4)
```

This works well for both Ubuntu and Windows, but if I select Mac OS X, I get a lot of console output that eventually ends in:

```
AppleIntelCPUPowerManagement: initialization complete
Still waiting for root device
```

If I let it sit longer, it continues to loop on the "Still waiting for root device" message and never boots.  In order to boot to OS X I have to hold the option key during startup where I'm presented with a choice between "Macintosh HD" and "Windows".

I tried rEFIt and didn't see any change to startup.

I would like to get a single boot screen where I can select between Windows, Ubuntu, and OS X.  Something like this:

[IMG]http://refit.sourceforge.net/img/screen2.png[/IMG]

If I could do this in GRUB, that would also be OK.  I would greatly appreciate any help on the matter.

---

### Post by tom4everitt on 2010-02-05
It would be interesting to see what "code" is executed when the mac option is choosen in grub. 

Either find the mac os x entry in /boot/grub/grub.cfg (in your linux system) yourself, or run:

sudo cat /boot/grub/grub.cfg | grep "Mac OS X" -A 10

in linux and paste the output here.

---

### Post by BigMontana on 2010-02-05
Sure.  Here's the entry:

```
menuentry "Mac OS X (on /dev/sda2)" {
	insmod hfsplus
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 51dbbfe84a7d03e3
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 51dbbfe84a7d03e3 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
```

Let me know if there's anything else you need to know.

---

### Post by tom4everitt on 2010-02-06
Thats a lot of code! I believe this OS X entry did it for me (I don't have the same setup anymore, so I can't check):

```

menuentry "MacOSX (verbose mode)" {
  # Set the root device for Mac OS X's loader.
  root=(hd0,2)
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi -v
}

```

Otherwise there are a couple of more alternatives on this site:
[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

(they're all a lot shorter, if nothing else :))

---

### Post by BigMontana on 2010-02-07
Unfortunately both the one that you provided and the ones at the link you sent me give an error ("Invalid signature" for the one you provided and "Unspecified search type" for the one on the other page).

I noticed that both methods refer to "/usr/standalone/i386/boot.efi".  When I checked my file system, there isn't even a /usr/standalone/ dir, let alone a boot.efi file.  Am I missing something?

---

### Post by ahso4271 on 2010-02-08
simply adjust paths and it should work. Im using something like boot_v8 in my linux partiton but dont remember anymore

---

### Post by Odin Overland on 2010-02-08
Double-checking here - has anyone been able to boot Mac OS X in GRUB 2 (1.97 beta) yet?  This is kind of my Holy Grail at the moment.  Then I can worry about cleaning up GRUB to look the way I want.

---

### Post by tom4everitt on 2010-02-09
> **BigMontana said:**
> Unfortunately both the one that you provided and the ones at the link you sent me give an error ("Invalid signature" for the one you provided and "Unspecified search type" for the one on the other page).

I noticed that both methods refer to "/usr/standalone/i386/boot.efi".  When I checked my file system, there isn't even a /usr/standalone/ dir, let alone a boot.efi file.  Am I missing something?


Hmm, interesting. It worked without problems for me (but I don't have that dir either, strange). 

I was using the EFI-boot described at the link I gave you, I guess you were using the MBR variant?

---

### Post by tom4everitt on 2010-02-09
> **Odin Overland said:**
> Double-checking here - has anyone been able to boot Mac OS X in GRUB 2 (1.97 beta) yet?  This is kind of my Holy Grail at the moment.  Then I can worry about cleaning up GRUB to look the way I want.

Only by EFI-booting grub2. But I couldn't boot linux properly that way (graphics problem) so it's not anything I'm using :)

---

### Post by tom4everitt on 2010-02-09
Aah, it just struck me:

It first sets root=(hd0,2), so its in your os x file system you should look for /usr/standalone.

Also you probably need to add insmod hfsplus (and possibly insmod vbe, telling from your old entry). So maybe try something like this:


```

menuentry "MacOSX (verbose mode)" {
  # insert modules:
  insmod hfsplus
  insmod vbe
  # and possibly something more...
  # Set the root device for Mac OS X's loader.
  root=(hd0,2)
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi -v
}

```

I chose the hfsplus module when I compiled grub, thats why I didn't need it.


You've noticed that you can press 'c' and 'e' in the grub menu, quite convenient when experimenting with different options.

---

