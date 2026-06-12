---
title: "ubuntu 8.01 update problem"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by shayvasa on 2008-01-11
hey i got a serious problem. i was uptading to the last 8.01 alpha. in the middle of the update my computer got stucked and i had to restart and now i cant get into ubuntu...i gives me a black screen with some lines and next to it it says fail with red letters...what can i do...i tryed typi9ng update-manager -d but it gives me errors...what can i do plz

---

### Post by overdrank on 2008-01-11
> **shayvasa said:**
> hey i got a serious problem. i was uptading to the last 8.01 alpha. in the middle of the update my computer got stucked and i had to restart and now i cant get into ubuntu...i gives me a black screen with some lines and next to it it says fail with red letters...what can i do...i tryed typi9ng update-manager -d but it gives me errors...what can i do plz

HI and you can try and boot into recovery mode and try
```
sudo dpkg --configure -a
``` And hopefully this will continue the upgrade.

---

### Post by shayvasa on 2008-01-11
how do i boot into recovery mode?

---

### Post by overdrank on 2008-01-11
> **shayvasa said:**
> how do i boot into recovery mode?

Hi and from the grub you should see the second choice ( usually) is recovery mode.

---

### Post by Cypher on 2008-01-11
IMHO, testing out the new version of Ubuntu is great to get all the kinks out for the masses, but if you are having a tough time getting into the recovery console, you might be better served sticking with the released version of Ubuntu..

---

### Post by shayvasa on 2008-01-11
ok then how can i go back to the 7.10 withoput reinstalling everything? and i couldnt get into the recovery console...

---

### Post by Cypher on 2008-01-11
Downgrading isn't as graceful as upgrading usually is and in most cases to get a "clean" install of an earlier version of Ubuntu, your best course of action would be a re-install..

---

### Post by shayvasa on 2008-01-11
ok then ill stay with the new ubuntu...now how can i continue the upgrade? i didnt undestand how to enter the recovery mode

---

### Post by Cypher on 2008-01-11
It's the second option in the Grub menu when you boot up your PC.

---

### Post by shayvasa on 2008-01-11
the second option i got in the grub is the failsafe of suse and i tryed the sudo dpkg --configure -a and it didint find dpkg

---

### Post by Cypher on 2008-01-11
Umm..yeah, SuSE != Ubuntu. Look for the entries in the GRUB menu that say "Ubuntu X.XX, kernel 2.6.xx (recovery mode)"..

That's the one you want..

---

### Post by shayvasa on 2008-01-11
im guessing i dont know how to enter the grub menu cause there are only 3 options where i am...suse, failsafe suse and ubuntu

---

### Post by Cypher on 2008-01-11
OK..let's take a step back. Did you have Ubuntu installed first and then install SuSE later on? And did you have SuSE install GRUB? If so, it looks like SuSE found Ubuntu and made it an option for you but got rid of the Recovery option..

But no fear. Choose the "Ubuntu" option in the GRUB menu and hit 'E' to edit the command line, the line might end with "ro quiet splash" or something to that effect, you want to remove the "quiet splash" with "single"..now hit ENTER to boot into that version of Ubuntu..

---

### Post by overdrank on 2008-01-11
> **shayvasa said:**
> im guessing i dont know how to enter the grub menu cause there are only 3 options where i am...suse, failsafe suse and ubuntu

Ok you can enter the recovery mode by  press esp key at the grub line, this will allow you to edit  the kernel line by pressing e and you can remove the quiet splash and single and then hit enter and then  b to boot. This will allow you to boot into recovery mode. Hope this helps. Good luck!
Edit to slow :)

---

### Post by shayvasa on 2008-01-11
i got into recovery mode but it shows me the same screen i described in my first post

---

### Post by macogw on 2008-01-11
it should give you a login prompt.  so the red is when it's still trying to boot?  does it ever finish booting and let you login?  if it's unbootable, you have to reinstall.

---

### Post by shayvasa on 2008-01-11
i dont understand...when it shows the red fail signs it ends there and and its like im in the terminal...it shows me the same line like when i enter the terminal

---

### Post by overdrank on 2008-01-11
> **shayvasa said:**
> i dont understand...when it shows the red fail signs it ends there and and its like im in the terminal...it shows me the same line like when i enter the terminal

Ok and are you able to enter any commands like 
```
sudo apt-get update

``` and can you tell us the error message or fail message. But I would have to agree with macogw the way it's sounds.

---

### Post by shayvasa on 2008-01-11
one more question...if i reinstall will all me data be erased?

---

### Post by shayvasa on 2008-01-11
i tryed typing the other command u gave me and it didint work...the dpkg one...ill try this one

---

### Post by bollix47 on 2008-01-12
Have a look at the Repairing Your Broken Hardy Install section of [this page.]("http://ubuntuforums.org/showthread.php?t=600644")

It's a little over half way down the page.

---

### Post by shayvasa on 2008-01-12
i tryed the what u said bollix but when i put sudo mkdir /media/hardy it says mkdir cant create the directory because its read only. i guess ill have to reinstall...is there a way to not loose all my data?

---

### Post by bollix47 on 2008-01-12
Which live CD did you use?  I just tried it using the Gutsy live CD and didn't get anything about read only.

How much memory do you have on that computer?

Do you have your /home folder on a separate partition?  If so, just make sure you don't reformat that partition when you're doing a fresh install.  If not you will have to somehow back it up on a writeable CD or move it to another partition.  You probably won't be able to do that if you can't get to the disc though.

---

### Post by shayvasa on 2008-01-12
i tryed doing it from the recovery mode...ill try from the live cd now

---

### Post by shayvasa on 2008-01-12
i get this error: ubuntu@ubuntu:~$ sudo mount /dev/hda1/media/hardy
mount: can't find /dev/hda1/media/hardy in /etc/fstab or /etc/mtab

---

### Post by bollix47 on 2008-01-12
Type the following command and paste the output here.
```

sudo fdisk -l
```

That's a small "L", not a one.

Also, you're missing a space between hda1 and /media/hardy.

I want the above output to confirm the /dev/????

It might be sda1 instead of hda1.

---

### Post by shayvasa on 2008-01-12
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21b721b7

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3040    24418768+  83  Linux
/dev/hda2            3041        4870    14699475    f  W95 Ext'd (LBA)
/dev/hda5            3041        3137      779121   82  Linux swap / Solaris
/dev/hda6            3138        3830     5566491   83  Linux
/dev/hda7            3831        4870     8353768+  83  Linux

---

### Post by bollix47 on 2008-01-12
Okay, so you're problem was the missing space between hda1 and /media/hardy.

---

### Post by shayvasa on 2008-01-12
ok i fixed it and i added a space between hda1 and media and it worked but now after i did sudo chroot /media/hardy su i input apt-get uptade and i get this errors:
ubuntu@ubuntu:~$ sudo mount /dev/hda1  /media/hardy
ubuntu@ubuntu:~$ sudo chroot /media/hardy su
root@ubuntu:/# apt-get update
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
/usr/lib/apt/methods/http: error while loading shared libraries: libapt-pkg-libc6.7-6.so.4.6: cannot open shared object file: No such file or directory
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly

---

### Post by bollix47 on 2008-01-12
It doesn't look good but just before the apt-get update try

```
dpkg --configure -a
```

---

### Post by shayvasa on 2008-01-12
dpkg: parse error, in file `/var/lib/dpkg/status' near line 300 package `libdjvulibre15':
 duplicate value for user-defined field `Original-Maintainer'

---

### Post by bollix47 on 2008-01-12
> **shayvasa said:**
> dpkg: parse error, in file `/var/lib/dpkg/status' near line 300 package `libdjvulibre15':
 duplicate value for user-defined field `Original-Maintainer'

Is that the same message you got when you tried the above command while in recovery mode?  Try the recovery mode route again just to check.

Also, while you're in recovery mode try the

```
apt-get update
apt-get upgrade
```

commands again.

If you do decide to re-install have a look at /dev/hda6 and /dev/hda7 to determine if one is your home partition.  
You can use the live cd.

```
sudo mkdir /media/hda6
sudo mount /dev/hda6 /media/hda6
cd /media/hda6
ls -l

```

Repeat for hda7 if necessary.

---

### Post by shayvasa on 2008-01-12
ok but in recovery mode i couldnt do the sudo mkdir /media/hardy or sudo mount /dev/hda1 /media/hardy...should i start off with sudo chroot /media/hardy su?

---

### Post by bollix47 on 2008-01-12
No.  You don't need to do those commands in recovery mode.
i.e. no mkdir or mount or chroot

Just the ones I referred to in my last post.

---

### Post by shayvasa on 2008-01-12
ok both apt-get gives me the same rrors as in the terminal with the live cd and the dpkg it says it cant enter it because its read only

---

### Post by bollix47 on 2008-01-12
Sounds like a re-install may be faster than continuing.

Check those other partitions as I suggested above and if one of them is your home make sure you use it during the install but DON'T format it.

You can check /dev/hda1 similar to above to make sure it in fact is your root filesystem.

Should look something similar to the following if you use the ls command:

bin    dev   initrd      lib32       media  proc  srv  usr
boot   etc   initrd.img  lib64       mnt    root  sys  var
cdrom  home  lib         lost+found  opt    sbin  tmp  vmlinuz


i.e. 
     / **might** be on /dev/hda1 .......... format it
     /home **might** be on /dev/hda6 or /dev/hda7 ......... DON'T format it

Good Luck

---

### Post by shayvasa on 2008-01-12
im kindda confused...the /home is in the hda1..and in the hda1 theres the ubuntu that doesnt work so what should i do? cause i need to delete that partition to install ubuntu again...but how do i do that without deleting my data?

---

### Post by bollix47 on 2008-01-12
The /home in sda1 may just be the mountpoint if your home is in a separate partition.

What's in hda6 and hda7?

---

### Post by shayvasa on 2008-01-12
suse

---

### Post by bollix47 on 2008-01-12
Are you able to run Suse?

I'm not familiar with it so can't give specific instructions but in general you could create a backup folder on Suse then using a routine similar to the one above re mkdir and mount the /dev/hda1 (again not sure how Suse works) then copy the /home from /dev/hda1 to the backup folder.

---

