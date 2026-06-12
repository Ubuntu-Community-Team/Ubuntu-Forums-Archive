---
title: "GRUB issue"
date: 2011-10-07
forum: Any Other OS
---

### Post by Shmook on 2011-10-07
I've been heavy distro-hoppin lately and have 4 installed right now and the only trouble is that using "update-grub" as well as "update-grub2" have both worked fine -- finding all the installed OS's; here's the output:
```
sans@iceblock ~ $ sudo update-grub
Generating grub.cfg ...
Found background image: vlcsnap-2010-12-28-04h29m08s212.jpg
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found openSUSE 11.4 (i586) on /dev/sda5
Found Fuduntu release 14 (Laughin) on /dev/sda6
Found Arch on /dev/sda7
Found memtest86+ image: /boot/memtest86+.bin
done
```
BUT when I restart and GRUB kicks in, the last -- "Arch on /dev/sda7" doesn't show up!

I haven't seen any similar troubles in the forum or in the GRUB wiki, so I'm wondering if anyone has any ideas -- I was thinking of including the 30_os-prober script but wanted to check here first.

---

### Post by amjjawad on 2011-10-07
> **Shmook said:**
> I've been heavy distro-hoppin lately and have 4 installed right now and the only trouble is that using "update-grub" as well as "update-grub2" have both worked fine -- finding all the installed OS's; here's the output:
```
sans@iceblock ~ $ sudo update-grub
Generating grub.cfg ...
Found background image: vlcsnap-2010-12-28-04h29m08s212.jpg
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found openSUSE 11.4 (i586) on /dev/sda5
Found Fuduntu release 14 (Laughin) on /dev/sda6
Found Arch on /dev/sda7
Found memtest86+ image: /boot/memtest86+.bin
done
```BUT when I restart and GRUB kicks in, the last -- "Arch on /dev/sda7" doesn't show up!

I haven't seen any similar troubles in the forum or in the GRUB wiki, so I'm wondering if anyone has any ideas -- I was thinking of including the 30_os-prober script but wanted to check here first.


```
sudo update-grub = sudo update-grub2

```
Usually, we don't put "2".

The entry is there but are you able to login to Arch? what happen when you choose it?

I had 9 installed months ago so 4 isn't too much :)

---

### Post by Shmook on 2011-10-07
Yeah I tried it both ways (update-grub, update-grub2, one at a time, in succession, etc...) and both found them every time, but I'm unable to load it because it doesn't even show up in the GRUB menu when I restart, that's the issue, and it's verrrry strange... :-k

---

### Post by amjjawad on 2011-10-07
> **Shmook said:**
> Yeah I tried it both ways (update-grub, update-grub2, one at a time, in succession, etc...) and both found them every time, but I'm unable to load it because it doesn't even show up in the GRUB menu when I restart, that's the issue, and it's verrrry strange... :-k

Just use "update-grub" and you'll be fine ;)

Hmmm, so basically when you run "sudo update-grub", it shows up but when you restart, it's not there?

---

### Post by ajgreeny on 2011-10-07
I presume you have tried scrolling down the grub menu?  If the menu is long there are often several items hidden at the bottom which you can only see if you scroll down.

However it is also possible if you have an older machine with a newer USB keyboard, that the keyboard may not work to allow scrolling in the grub menu;  I speak from experience here.

I needed to enable legacy USB support for my keyboard in the BIOS, and had to use an older ps2 keyboard to even get to the BIOS; a bit of a catch 22 situation.  That solved my problem completely, and may also help yours.

---

### Post by Shmook on 2011-10-07
@amjjawad: right, exactly

@ajgreeny: I'm quite sure I have tried scrolling down but I'd feel pretty damn stupid if that was the problem...and that's really strange having to adjust BIOS to use GRUB. I am able to get to BIOS I know that -- was considering "flashing" it recently because I can't boot from USB flash drives. But I spose I'll check that out.

---

### Post by ajgreeny on 2011-10-07
OK, fair enough.

Try running the command ```
grep menuentry /boot/grub/grub.cfg
```which will list every OS that is listed in the grub.cfg file of the OS that you are running at the time.

I am just beginning to wonder if the grub that is being used is actually from one of the other OSs on the machine, and though you are updating grub in your running OS, if that is not the one that grub comes from at boot time, it will not show all the OSs unless the other grub systems are also updated.

It seems strange, however, as each OS's grub would automatically put that OS at the top of the grub list, not the ubuntu that I presume always appears at the top of the grub menu you see.

---

### Post by amjjawad on 2011-10-07
> **Shmook said:**
> @amjjawad: right, exactly


IMHO, it's better then to: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

> and that's really strange having to adjust BIOS to use GRUB. I am able to get to BIOS I know that -- **was considering "flashing" it recently because I can't boot from USB flash drives**. But I spose I'll check that out.

I don't think you need all that.

If your BIOS supports booting from USB, you just need to set it as your first device to boot from OR in some BIOS, you just need to change HDD Boot Priority.

[IMG]http://ubuntuforums.org/picture.php?albumid=2145&pictureid=7126[/IMG]

---

### Post by Shmook on 2011-10-07
@ajgreeny -- hmm this is interesting; so it sees it when I'm updating grub, but it's not here when I used the command you asked for:
```

sans@iceblock ~ $ grep menuentry /boot/grub/grub.cfg
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2)" --class linuxmint --class gnu-linux --class gnu --class os {
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) -- recovery mode" --class linuxmint --class gnu-linux --class gnu --class os {
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
menuentry "openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Fuduntu (3.0.3-1.fc14.i686) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

```
oh and yes I'm using mint til 11.10 comes out -- just always used this forum and figured there wouldn't be a difference. Just as a reminder here's what "update-grub" shows:
```
sans@iceblock ~ $ sudo update-grub
[sudo] password for sans: 
Generating grub.cfg ...
Found background image: vlcsnap-2010-12-28-04h29m08s212.jpg
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Microsoft Windows XP Professional on /dev/sda1
Found openSUSE 11.4 (i586) on /dev/sda5
Found Fuduntu release 14 (Laughin) on /dev/sda6
Found Arch on /dev/sda7
Found memtest86+ image: /boot/memtest86+.bin
done

```

@amjjawad: that looks almost identical to my CMOS except "USB Boot" is not an option -- and I have tried altering the order of boot devices to no avail -- and I'm dl'ing that script as we speak
[code

---

### Post by Shmook on 2011-10-07
So is what you think that I should try to make Mint re-write its GRUB output to MBR??

---

### Post by Quackers on 2011-10-07
What OS are you booted into when running those commands? You would need to be in Mint if that system controls grub.

---

### Post by ajgreeny on 2011-10-07
From your Mint installation run command ```
sudo grub-install /dev/sda
``` assuming you always have grub on the MBR of the one main hard disk of the machine.  That will make sure that mint is the grub actually in use,and not one of the other OSs, though as I said before, the OS supplying the grub would always be top of the grub menu, so it seems that Mint is already the grub owner.

---

### Post by Shmook on 2011-10-07
@Quackers -- yeah all of this has been done under Mint katya

@ajgreeny -- just ran that command with no error reported -- I'll restart and see wassap -- thanks a bunch

---

### Post by Shmook on 2011-10-07
D-d-d-d-damn! same output when GRUB boots up; I also ran grub-customizer and it didn't find Arch, so that was no help.

Here's a brief summary of the program from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) that was recommended earlier (sorry it's kind of a lot): 
oh and btw sdb1 is a seperate HD that holds no OS's, just media
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.4 
                       "Celadon" - Kernel ().
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fuduntu release 14 (Laughin) 
                       Kernel on an ()
    Boot files:        /boot/grub/grub.conf /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab 
                       /boot/syslinux/syslinux.cfg

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   153,597,464   153,597,402   7 NTFS / exFAT / HPFS
/dev/sda2         153,597,952   194,545,663    40,947,712  83 Linux
/dev/sda3         194,547,211   310,713,164   116,165,954   f W95 Extended (LBA)
/dev/sda5         194,547,213   258,019,964    63,472,752  83 Linux
/dev/sda6    *    258,020,028   288,736,244    30,716,217  83 Linux
/dev/sda7         288,736,308   310,713,164    21,976,857  83 Linux
/dev/sda4         310,713,165   312,576,704     1,863,540  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   586,072,063   586,070,016   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        6E9852089851CF69                       ntfs       a1 xp
/dev/sda2        5c59838d-daed-405e-b6c7-1eff85362697   ext4       
/dev/sda4        ba6ef235-fa6e-4775-a327-d2a7c2310710   swap       
/dev/sda5        a08d111e-2f78-44b8-9235-e8007f8f9d8b   ext4       
/dev/sda6        790e2123-b3f9-45a9-9d18-9e1821d14992   ext4       _Fuduntu-i386-Li
/dev/sda7        a5f33fe3-f19a-4018-9809-ee7754e8690e   ext4       
/dev/sdb1        2EB43EE1B43EAAEB                       ntfs       

```

---

### Post by amjjawad on 2011-10-07
> **Shmook said:**
> @amjjawad: that looks almost identical to my CMOS except "USB Boot" is not an option -- and I have tried altering the order of boot devices to no avail -- and I'm dl'ing that script as we speak


If I understood your previous post correctly, you are trying to boot from USB Drive but you can't do that, am I right?

Again, if your BIOS does support that feature already, then you just need to check your settings as previously explained. If your BIOS does not support that function then use [Plop]("http://www.plop.at/en/bootmanager.html").

See this post for setting it up: [http://ubuntuforums.org/showpost.php?p=10769333&postcount=8](http://ubuntuforums.org/showpost.php?p=10769333&postcount=8)

---

### Post by amjjawad on 2011-10-07
As for your GRUB issue, as the other friends already explained, you need to be logged in to the OS that owns GRUB2.

The previous post shows how to install GRUB2 to the MBR from Mint so that Mint will be your "main" OS.

---

### Post by Perfect Storm on 2011-10-07
Moved to Other OS/Distro Talk.

---

### Post by Quackers on 2011-10-07
After you ran the grub-install command did you run sudo update-grub and the grep command again?

---

### Post by mhgsys on 2011-10-07
> **amjjawad said:**
> 
 If your BIOS does not support that function then use [Plop]("http://www.plop.at/en/bootmanager.html").

See this post for setting it up: [http://ubuntuforums.org/showpost.php?p=10769333&postcount=8](http://ubuntuforums.org/showpost.php?p=10769333&postcount=8)

Off-topic (a little).. I just adjusted the link in my post to a  new working one...also.. with plop , the entry will not show up in the sudo update-grub2 command, but that's normal (I never seen it, while plop works like a charm, and the plop entry is there when booting into grub)

About the original problem, .. I can only reproduce "losing a grub entry" when trying to update grub from another ubuntu that does not own the grub which I'm trying to boot from, ...also that is normal..)
**ajgreeny **his post will work out for you setting mint to be the OS that owns grub

---

### Post by Shmook on 2011-10-19
Sorry for my absence, I slept for a few weeks, but the problem still exists, with a few minor changes. I installed Ubuntu 11.10, which is where I "grub" from; and still nothing has changed -- that being, ArchBang doesn't show up in the grub boot menu, or in the grep function mentioned above, here's some output:
```
sans@gluebox:~$ sudo grub-install /dev/sda
Installation finished. No error reported.

```
```
sans@gluebox:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Linux Mint 11 Katya (11) on /dev/sda2
Found openSUSE 11.4 (i586) on /dev/sda5
Found Arch on /dev/sda7
done

```
```
sans@gluebox:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) -- recovery mode (on /dev/sda2)" --class gnu-linux --class gnu --class os {
menuentry "openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {

```

very strange where'd Arch on sda7 go?? -- oh and Ubuntu 11.10 is on sda6 if that helps...

Oh and booting from a USB flash drive still won't work for me, even using PLOP, but I'm not too worried about that I'll just continue using CD-RW's.

---

### Post by amjjawad on 2011-10-19
> **Shmook said:**
> Sorry for my absence, I slept for a few weeks, but the problem still exists, with a few minor changes. I installed Ubuntu 11.10, which is where I "grub" from; and still nothing has changed -- that being, ArchBang doesn't show up in the grub boot menu, or in the grep function mentioned above, here's some output:
```
sans@gluebox:~$ sudo grub-install /dev/sda
Installation finished. No error reported.

``````
sans@gluebox:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Linux Mint 11 Katya (11) on /dev/sda2
Found openSUSE 11.4 (i586) on /dev/sda5
Found Arch on /dev/sda7
done

``````
sans@gluebox:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) (on /dev/sda2)" --class gnu-linux --class gnu --class os {
menuentry "Linux Mint 11, 2.6.38-11-generic (/dev/sda2) -- recovery mode (on /dev/sda2)" --class gnu-linux --class gnu --class os {
menuentry "openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {
menuentry "Failsafe -- openSUSE 11.4 - 2.6.37.1-1.2 (on /dev/sda5)" --class gnu-linux --class gnu --class os {

```very strange where'd Arch on sda7 go?? -- oh and Ubuntu 11.10 is on sda6 if that helps...

Oh and booting from a USB flash drive still won't work for me, even using PLOP, but I'm not too worried about that I'll just continue using CD-RW's.

During Ubuntu 11.10 installation, there is a step where you can choose where to install GRUB2. In Systems such as yours, you are Mutli-Booting so you MUST go for "Something Else" Option or "Manual/Advanced" option. Having that said, please check this:

[IMG]http://i52.tinypic.com/6gfmds.jpg[/IMG]

If you decide NOT to install GRUB2 in the MBR during installation but install it instead in the same partition where you'll install that OS (which is sda6 in your case), then you must have another System and GRUB installed and controlling the boot process.
Also, you'll need to run "update-grub" command from THAT OS which is controlling the booting process:

[IMG]http://i56.tinypic.com/28j88qb.jpg[/IMG]

I see in your case (correct me please if I'm wrong) that you have installed Ubuntu in sda6 but decided to install GRUB2 to sda, correct?

Now, for Archbang which is not showing, I have two suggestions here and then I'm totally out of ideas:

Idea 1:
Use GRUB-Customizer to edit GRUB Menu and hope that will fix your issue.
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Idea 2:
Format sda7 (where Archbang is installed now), Run "update-grub from your main system, Re-install Archbang and make sure to install its GRUB to sda7 partition NOT sda and then run "update-grub" from the main system.

I have had a Multi-Booting System before with 9 OS's installed and I haven't had such issue at all. GRUB2 is so smart to find other systems and yes, I can see it's not "showing" yours while it does find it when you run "update-grub".

Hope that will help :)

---

### Post by Shmook on 2011-10-22
Okay, so GRUB'ing from a particular partition is preferred over installing it on the MBR?

> I see in your case (correct me please if I'm wrong) that you have installed Ubuntu in sda6 but decided to install GRUB2 to sda, correct?
Yes, precisely...it might not have been during the Ubuntu installation; I always reinstall GRUB to MBR thinking it will rewrite the previous version with the new, proper one, with whichever distros are then-currently on each partition (being the distro-hopper I am).

I'm guessing that's a poor technique now, eh?

And I've fooled around with grub-customizer before, but tended to prefer using the terminal. I think I got scared off it when I tried several times to make use of that "SuperGrubDisk" OMG what a fright that thing is!...what's the one I found that I prefer now; partition magic? Whatever, one of those. Anyway I'll try GC again.

Or -- and yeah this crossed my mind too -- installing ArchBang took like 6 minutes, I was thinking of just reinstalling it -- and you're saying install GRUB to the particular partition? ok

Just a few more questions if you please:

-Is there ever a situation when it's preferable to have GRUB installed in the MBR rather than a partition?

-If I reinstall and place GRUB on a partition, what will happen to the GRUB on the MBR?

-Have you ever tried BURG? It seems appealing for some reason, and not just for the pretty pictures

-...I think that's it; really appreciate yr help amj, and I'll post this SOLVED when I find what technique works out for me

---

### Post by Shmook on 2011-10-22
One more thing: what program do you recommend for the formatting of a partition. Last time I tried using DBAN and ended up losing ALL my oggs and porn...it was terrible. Or just format it during the OS install process?

---

### Post by amjjawad on 2011-10-22
> **Shmook said:**
> Okay, so GRUB'ing from a particular partition is preferred over installing it on the MBR?

I see you are still confused about that :) never mind, will explain it again.

Whenever you are Dual-Booting or Multi-Booting, it's recommended to have one "main" or "primary" Operating System. The Boot Loader of this Primary/Main OS will take the control over the booting process BUT that will happen ONLY if its Boot-Loader is installed in the MBR. Having that said, if your main OS is Ubutnu 11.10 for example and its Boot-Loader (GRUB2) is installed in the MBR, then it will control the booting process and GRUB Menu that you'll see upon booting is the Ubuntu's GRUB-Menu.

It's totally up to you to install GRUB to the MBR each and every time you install new OS. There is nothing wrong with that. However, there is an extra work that must be done in case you want to get rid of that OS.
You'll need to re-install GRUB to the MBR if you'll format the partition where GRUB Files are stored. You can not install ALL GRUB Files to the MBR because MBR Space is very limited.

Instead, with the concept of one main OS, after each installation of new OS, you just need to run "update-grub" from the terminal of the main OS and that's all. Note that, the boot loader of the new OS that you are installing MUST be installed in the same partition where that OS is being installed. 


> Yes, precisely...it might not have been during the Ubuntu installation; I always reinstall GRUB to MBR thinking it will rewrite the previous version with the new, proper one, with whichever distros are then-currently on each partition (being the distro-hopper I am).

I'm guessing that's a poor technique now, eh?
Please, let's make it simple and short :)

Say you are creating a Multi-Boot System of 5 Operating Systems.
1- Ubuntu
2- Mint
3- Lubutnu
4- Xubuntu
5- Win XP

Main OS = Ubutnu

This is how you do it (the easiest way):
1- Install Windows XP First (sda1)
2- Install Ubuntu and install GRUB to the MBR (sda2)
3- Install Mint and install grub to the same partition where Mint is going to be installed (sda5)
4- Install Lubuntu and install grub to the same partition where Lubuntu is going to be installed (sda6)
5- Install Xubuntu and install grub to the same partition where Xubuntu is going to be installed (sda7)
6- Reboot
7- Login to your main OS (Ubuntu)
8- From Terminal, run:

```
sudo update-grub
```

9- DONE :)


> Or -- and yeah this crossed my mind too -- installing ArchBang took like 6 minutes, I was thinking of just reinstalling it -- and you're saying install GRUB to the particular partition? ok
Re-install Archbang and make sure to install its grub to the same partition where it's going to be installed OR choose not to install GRUB just like Fedora. 



> -Is there ever a situation when it's preferable to have GRUB installed in the MBR rather than a partition?

Already answered :)

> -If I reinstall and place GRUB on a partition, what will happen to the GRUB on the MBR?
Untouched. MBR will not be overwritten as long as you are NOT installing any other boot loader there.

> -Have you ever tried BURG? It seems appealing for some reason, and not just for the pretty pictures
I only use GRUB2 :)

> I think that's it; really appreciate yr help amj, and I'll post this SOLVED when I find what technique works out for me

You most welcome :)

---

### Post by amjjawad on 2011-10-22
> **Shmook said:**
> One more thing: what program do you recommend for the formatting of a partition. Last time I tried using DBAN and ended up losing ALL my oggs and porn...it was terrible. Or just format it during the OS install process?

One word, GParted :)

---

### Post by amjjawad on 2011-10-22
You need to have a look at these links. IMHO, it's very important to have a basic knowledge about these stuff:

[http://en.wikipedia.org/wiki/Booting](http://en.wikipedia.org/wiki/Booting)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
[http://en.wikipedia.org/wiki/GParted](http://en.wikipedia.org/wiki/GParted)

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by utnubuuser on 2011-10-22
two words

Boot Repair

[http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair]("http://sazeit.com/articles/repair-or-reinstall-grub-with-boot-repair")

---

### Post by Shmook on 2011-10-28
Okay, issue resolved, though I still haven't wrapped my head around exactly what the issue was. My best guess is another OS had written its GRUB entries to the MBR while I was updating-grub here in Lubuntu to its respective partition.

IN ANY CASE: I used Grub Customizer, it found every OS, and I wrote THAT to the MBR. Case Closed, and ArchBang is pretty cool afterall.

THANK YOU ALL for yr help!

---

### Post by amjjawad on 2011-10-28
Glad you managed to fix it :)

You most welcome ... enjoy!

---

