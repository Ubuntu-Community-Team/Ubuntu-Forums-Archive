---
title: "rEFInd failing in El Capitan MacBookPro5,3"
date: 2015-10-01
forum: Apple Hardware Users
---

### Post by Carty_Ellis on 2015-10-01
I am continuing in my quest to dual-boot 10.04.3 Ubuntu.

I am tying to run rEFInd on OSX 10.11 and it is failing.

I am a little rusty on scripts - I did not change ANYTHING in the script.

Here is wha I got in terminal in my Downloads/refind-0.9.2 directory:

elliscmacpro:refind-bin-0.9.2 cartyellis$ ./install.sh
Not running as root; attempting to elevate privileges via sudo....
Password:
ShimSource is none
Installing rEFInd on OS X....
Installing rEFInd to the partition mounted at /Volumes/ESP
Found rEFInd installation in /Volumes/ESP/EFI/refind; upgrading it.
Copied rEFInd binary files


Notice: Backed up existing icons directory as icons-backup.
Existing refind.conf file found; copying sample file as refind.conf-sample
to avoid overwriting your customizations.


Could not set boot device property: 0xe00002bc


WARNING: If you have an Advanced Format disk, *DO NOT* attempt to check the
bless status with 'bless --info', since this is known to cause disk corruption
on some systems!!




ALERT:
Installation has completed, but problems were detected. Review the output for
error messages and take corrective measures as necessary. You may need to
re-run this script or install manually before rEFInd will work.


Unmounting install dir

---

### Post by mjanik on 2015-10-01
I had problems with getting rEFInd to work after upgrading to El Capitan, as well (Mac Pro late 2013).

I wrote my process quickly on how I fixed it here:
[URL="http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/"]http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/
[/URL]
first, get access to your HDD's efi partition:

- find the partition using **diskutil list** in terminal. (usually disk0s1). It'll say EFI.
- Create a mount point using **mkdir /volumes/efi** in terminal.
- Mount the partition to the mount point with this command: **sudo mount -t msdos /dev/disk0s1 /Volumes/efi**

Now you should be able to navigate your efi partition and follow the instructions I posted in the link above. I hope this works for you... did for me!

---

### Post by Carty_Ellis on 2015-10-01
What directory should rrefind-bin-0.9.2 reside in when ./install.sh is executed?

I did set up efi in /Volumes and diskutil list is:

elliscmacpro:Volumes cartyellis$ diskutil list
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *320.1 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:                  Apple_HFS Macintosh HD            319.2 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
elliscmacpro:Volumes cartyellis$ 

and I have:


elliscmacpro:EFI cartyellis$ pwd
/Volumes/EFI
elliscmacpro:EFI cartyellis$ ls -alF
total 5
drwxrwxrwx@ 1 cartyellis  staff  512 Oct  1 11:52 ./
drwxrwxrwt@ 5 root        admin  170 Oct  1 17:02 ../
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 10:49 .Spotlight-V100/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 16:44 .Trashes/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 17:03 .fseventsd/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 10:49 EFI/
elliscmacpro:EFI cartyellis$ 

Also:

elliscmacpro:Volumes cartyellis$ ls -alF
total 9
drwxrwxrwt@  5 root        admin   170 Oct  1 17:02 ./
drwxr-xr-x  39 root        wheel  1394 Oct  1 16:43 ../
lrwxr-xr-x   1 root        admin     1 Oct  1 16:40 Macintosh HD@ -> /
drwxrwxrwx   0 root        wheel     0 Oct  1 17:16 MobileBackups/
drwxrwxrwx@  1 cartyellis  staff   512 Oct  1 11:52 efi/
elliscmacpro:Volumes cartyellis$ 

I ran the ./install.sh from the ./Downloads/refind-bin-.9.2 directory and got the same results.

??

---

### Post by jdg2 on 2015-10-01
> **Carty_Ellis said:**
> What directory should rrefind-bin-0.9.2 reside in when ./install.sh is executed?

elliscmacpro:EFI cartyellis$ ls -alF
total 5
drwxrwxrwx@ 1 cartyellis  staff  512 Oct  1 11:52 ./
drwxrwxrwt@ 5 root        admin  170 Oct  1 17:02 ../
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 10:49 .Spotlight-V100/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 16:44 .Trashes/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 17:03 .fseventsd/
drwxrwxrwx  1 cartyellis  staff  512 Oct  1 10:49 EFI/
elliscmacpro:EFI cartyellis$ 

??

refind lives within the EFI directory.  (An "ls -R" would show this.)

Julian

---

### Post by Carty_Ellis on 2015-10-01
csrutil disable was the trick.  Ran ./install.sh from Downloads/refind-bin-0.9.2 and it worked.  

Thanks

---

### Post by mjanik on 2015-10-01
Ya I figured it had something to do with System Integrity Protection. 
Glad it worked out for you!!

---

### Post by Paulo_Bicudo on 2015-10-02
Hi! 
yesterday I updated OS X to El Capitan, now I can't boot from Ubuntu 14.04 that I have on a partition...It doesn't even appear on disk utility when I select the disk, it used to....

I never had to use rEFInd before because I installed from a specific mac image ubuntu I guess, And it was working fine, I had compiz configured for the first time and was enjoying that cube lol...Oh man I miss my linux

You guys think this solution will work for me too?

EDIT: So I changed system integrity protection disabling it in recovery mode, now - I got to run the install script and it was successful, AND ITS WORKING!!! ITS WORKINGGGGG

---

### Post by mystics on 2015-10-02
> **Carty_Ellis said:**
> I am continuing in my quest to dual-boot 10.04.3 Ubuntu.

Well, it looks like you've gotten rEFInd to work, so that's good.

However, I do want to let you know that 10.04 has reached end-of-life and is no longer supported. The currently supported versions are 12.04, 14.04, and 15.04. 15.10 should release in a couple weeks. Of those four, 12.04 and 14.04 are both long-term support versions and will be supported for 2 years and 4 years more respectively. 15.04 and 15.10 will both reach end-of-life within the next year.

In short, you should look into another version of Ubuntu than 10.04. 14.04 would probably be the best since it will stay supported until 2019, but 12.04 will stay supported until 2017. At the very least, I know 12.04 works with MacBook Pro 5.3 and there is a tutorial on how to get it work well: [https://help.ubuntu.com/community/MacBookPro5-3/Precise](https://help.ubuntu.com/community/MacBookPro5-3/Precise)

I'd imagine 14.04 will also work.

---

### Post by mjanik on 2015-10-02
> [COLOR=#000000]You guys think this solution will work for me too?[/COLOR]
I'm not sure why it's not showing up in disk utility, but your best bet is to try and install rEFInd to see if it solves the problem. Many users use rEFInd to manage their booting. Have you just been holding option when you want to boot into ubuntu?

And if you mean disk utility on El Capitan... it's been totally revamped, and is in the beginning stages of functionality; they chose to make a new disk utility and start fresh with something very weak at the point of first release of El Cap. That might be why you're not seeing your ubuntu partition. 

Hope that helps.

---

### Post by Paulo_Bicudo on 2015-10-02
I edited my post! I got it to work :) thanks for the reply :)

---

### Post by mjanik on 2015-10-02
Glad it's working!!

---

### Post by wmoore on 2015-10-03
When I try and run csrutil disable in recovery, I get this.

```
[FONT=Consolas]dyld: Symbol not found: ___NSDictionary0__[/FONT]    
    Referenced from: /Volumes/Macintosh HD/usr/bin/./csrutil
    Expected in:
    /System/Library/Frameworks/CoreFoundation.framework/Versions/A/CoreFoundation
in /Volumes/Macintosh HD/usr/bin/./csrutil [FONT=Consolas]Trace/BPT trap: 5[/FONT]
```

I saw somebody mention you can switch it off by going to Utilities --> Security Configuration in recovery but that menu doesn't exist for me. Any other suggestions?

Edit: My Mac is an Air 6,2 but I imagine the instructions are the same.

---

### Post by wmoore on 2015-10-03
OK I found something of a temp workaround. Following [this guide]("https://mmanoba.wordpress.com/2013/08/29/howto-install-refind-on-mac-machine-or-usb-stick-hard-drive/"), I installed rEFInd on a USB key. The machine doesn't auto boot from the USB but if I hold ALT on startup, I now get the USB as an option. On selecting this, I see my previous rEFInd options and can boot into Ubuntu. 

And relax :D

---

### Post by Carty_Ellis on 2015-10-03
Currently, rEFInd is "almost" working.  If I put LiveCD for either 14.04.3 or 15.04 in the DVD slot, and try to boot to them, I get "missing operating system".

If I shutdown and start, holding the option key, the DVD (two appear and I select EFI) appears eventually and I can try Ubuntu successfully.  Why can't rEFInd do that?

I have also used Gparted to move my Linux and Linux Swap partitions on my internal HD to the correct places.  I have been hesitant to test, using Gparted,  the EFI partition on the Internal hard drive, which shows as a FAT partition.

Now, if I run install Ubuntu, and get to the "where to install the boot loader" do I pick /dev/sda or /dev/sda5 which is my Linux partition?  

Suggestions?

---

### Post by Carty_Ellis on 2015-10-03
rEFInd is now not working.  I have installed 14.04.3 on my internal HD, along with OSX 10.11.  

I have also got the apple mouse working, and the correct Nvidia driver so the boot works as advertised.

My problem is in how I have to boot.

If I just start the laptop, it boots into Ubuntu.

If I hold the option key down, I can boot into Apple operating system.  If I select the recovery disk, the computer shuts down.  Apple support tells me that I have some corrupted area on my HD and that is why the recovery turns the computer off.

I have not been able to do the "csrutil enable" operation, so it is still disabled.

 If I select the Windows disk (Windows is not installed on the hard drive) nothing happens and the computer just sits there with a blank screen..  

If I use the Command-R hold, intended to boot into Recovery mode - that is the only way I get to Ubuntu.  Yes -- WEIRD!!

rEFInd does not appear to be any place on the computer that I can find in OSX or Ubuntu.

Obviously I have messed up something in the boot process - HELP!

---

### Post by Carty_Ellis on 2015-10-04
> **Carty_Ellis said:**
> rEFInd is now not working.  I have installed 14.04.3 on my internal HD, along with OSX 10.11.  

I have also got the apple mouse working, and the correct Nvidia driver so the boot works as advertised.

My problem is in how I have to boot.

If I just start the laptop, it boots into Ubuntu.

If I hold the option key down, I can boot into Apple operating system.  If I select the recovery disk, the computer shuts down.  Apple support tells me that I have some corrupted area on my HD and that is why the recovery turns the computer off.

I have not been able to do the "csrutil enable" operation, so it is still disabled.

 If I select the Windows disk (Windows is not installed on the hard drive) nothing happens and the computer just sits there with a blank screen..  

If I use the Command-R hold, intended to boot into Recovery mode - that is the only way I get to Ubuntu.  Yes -- WEIRD!!

rEFInd does not appear to be any place on the computer that I can find in OSX or Ubuntu.

Obviously I have messed up something in the boot process - HELP!

I reinstalled rEFInd by simply downloading the package again from SourceForge, going into Terminal in OSX and running ./install.sh

Everything is OK now ( except ability to get into Recovery Mode.  

Guess I panic too easy.  

Thanks everyone for all the comments and advice.

---

### Post by Carty_Ellis on 2015-10-05
Looks like Apple and El Capitan present a major problem for rEFInd and other boot utilities.  I can no longer boot into recovery mode..  

Interesting information on this web site: [http://www.macworld.com/article/2948140/os-x/private-i-el-capitans-system-integrity-protection-will-shift-utilities-functions.html](http://www.macworld.com/article/2948140/os-x/private-i-el-capitans-system-integrity-protection-will-shift-utilities-functions.html)

---

