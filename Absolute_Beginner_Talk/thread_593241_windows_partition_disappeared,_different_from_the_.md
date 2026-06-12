---
title: "windows partition disappeared, different from the post from a day ago, i think"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by dimethylsulfoxide on 2007-10-27
so i started using ubuntu a few days ago. everything has been working fine...

except now my windows partition has disappeared from the boot list.

i clicked places->computer and the windows partition (sda2) was not listed.

i rebooted, the grub menu was still missing windows but now sda2 is listed when i go to places->computer.

the only thing i thought to do was try...

sudo mount /dev/sda2 
> fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()


...the last time i used vista i shut down normally.

any thoughts? sorry if any of the above was irrelevant...

is this good to include?

cat /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fec4015d-4e12-4848-a86d-b708b7f754e0 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FC7407EB7407A80A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=78DE4714DE46C9D8 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


---

### Post by mridkash on 2007-10-27
This thing happened with me and was solved after I did a chkdsk /f in windows. Try checking the windows drive for errors.

---

### Post by dimethylsulfoxide on 2007-10-27
im sorry if this is a stupid question... but how do i do that if i cant boot into windows?

---

### Post by dukejib on 2007-10-27
Hmm, It seems your windows shutdown has corrupted your windows Install, that is why , your Ubuntu is not able to see it.
Try to use your Windows CD/DVD to repair the windows, then reboot in Ubuntu.
That will do it, hopefully! :)

---

### Post by mridkash on 2007-10-28
he he :-P . Now I'm with you too! My ubuntu gutsy cannot see windows partition, but I get a different error message and I can boot into windows. All I did was opening a virus loaded pen drive in windows. It even kinda tried to ruin ubuntu, I use ext2fs in windows to see my linux partition, and after virus infection, ubuntu stopped loading and I had to manually run fsck on linux partition to correct it. Thank god ubuntu is so good, it even told me that to correct filesystem you have to run fsck manually. 

Error message,

```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0

```

And regarding your problem, what is the error message that you get when booting to windows?

---

### Post by dimethylsulfoxide on 2007-10-29
i got that same exact error message at one point!!


> And regarding your problem, what is the error message that you get when booting to windows?

...sorry if this is a silly question, but how do you boot to windows if windows isnt listed in the boot menu?

---

### Post by Maestro23 on 2007-10-29
> **dimethylsulfoxide said:**
> i got that same exact error message at one point!!




...sorry if this is a silly question, but how do you boot to windows if windows isnt listed in the boot menu?

Try to use your Windows CD/DVD to repair the windows, then reboot in Ubuntu.

---

### Post by dimethylsulfoxide on 2007-10-29
my laptop did not come with an installation disc. instead, it came with a recovery partition. there really isnt anything useful on the recovery partition, (the four options im given are to use: restore points (tried), system diagnostics (checked), reinstall vista, and data recovery) but im thinking ill get my hands on an installation disc and use the "startup recovery" feature. 

do you think thats a good idea? someone in a vista forum told me it "might wreck the partition tables" and ill "have to start from scratch." im thinking theyre being a little paranoid, but just to be sure id like some other opinions.

---

### Post by mridkash on 2007-10-30
The windows option disappeared from my laptop too! Actually, I got to know it happens when there is some error on windows partition and you run update-grub on ubuntu, it tries to find the windows partition but couldn't so it just removes the option from menu. update-grub can run sometimes after kernel updates etc.
For me, it was a simple solution. 

Follow: open a terminal and write ```
sudo gedit /boot/grub/menu.lst
```enter your password and a file called menu.lst will open. This is a system file that is why you need that sudo command to open it. You'll notice lot of instructions etc. lines starting with # are comments.

At the end of the file you'll see a list of options that are displayed when computer starts.

Now you have to manually add an entry for windows here.
If you know that the windows partition is first on the disk then  copy and paste exact code given here

```

title        Windows XP Home Edition
root        (hd0,0)
makeactive
chainloader    +1
```Make sure that you insert this code in the list.

For your reference, I'm pasting the end of menu.lst file here. your boot options should look like this, DOnt copy and paste this text as it may be different for your pc.
```
## ## End Default Options ##

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a885b544-b341-49ed-8747-35c57fcad9f2 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Windows XP Home Edition
root        (hd0,0)
makeactive
chainloader    +1

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=a885b544-b341-49ed-8747-35c57fcad9f2 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
```

If you don't know if your windows is on first partition then write back.

---

### Post by dimethylsulfoxide on 2007-10-30
aha!!!


vista's back on the boot menu and im using it right now. im so relieved!

thanks so much, mridkash!!

---

### Post by mridkash on 2007-10-31
All the best!

---

