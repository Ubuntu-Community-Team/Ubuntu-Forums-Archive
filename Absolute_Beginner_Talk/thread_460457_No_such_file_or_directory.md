---
title: "No such file or directory"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by stevelasvegas on 2007-05-31
During boot it stops with a fail that says:
Loading local filesystem...
/media/host/wubi/disks/usr.virtual.disk
/media/host/wubi/disks/extra.virtual.disk

I do a ctrl+c (I don't know why) and it continues to boot to the login screen.

1. Is this something I need to concern myself with?
2. If not, how can I keep the system from trying to load it? 

Thanks

---

### Post by digitalbenji on 2007-05-31
Hi,
  It sounds to me like the init process is trying to mount a filesystem that is not available.  The list of filesystems mounted at boot, and all filesystems (I think), is kept in this file:
/etc/fstab
If you post the contents of this file, which you can get from doing a cat /etc/fstab , then we can try to see if this is the case.  If it is, you will just have to comment out (or delete) the lines that refer to those 2 file systems.

Thanks, Hope this helps,

---

### Post by steve.horsley on 2007-05-31
Is this a working install that just started doing this? If so, read on...

The latest Feisty kernek update seems to have changed the way the kernel names IDE drives. All previous versions of Linux called IDE drives /dev/hda etc, but Feisty called them /dev/sda. At least, it did until the update 2 days ago which reverted to the hda naming. This doesn't seem to have caused much upset, probably becase the installer uses disk ligical names (UDDI or someting like that). But maybe wubi uses the physical device name, in which case you may need to edit /etc/fstab and correct /dev/sda to /dev/hda etc. Look in /dev first though, to make sure I'm not talking rubbish.

---

### Post by stevelasvegas on 2007-05-31
This is actually a new install (my 3rd in several days). Apparently I have no idea of what I am doing. I used WUBI to install Ubuntu Feisty a couple of weks ago and during my tinkering with installing and un-installing apps, etc other things stopped working or I would get errors. Then I post problems and follow given sugestions and it just seems to get worse, so I am again re-installing. This is a new problem on a fresh install. I don't know what files/folders to back up and restore when things go wrong so I can "go back" so I guess I am just going to have to image the drive or copy the WUBI folder each time I make a change, update, etc. I am sure there is a better way to protect my exisiting working install so as to be able to make changes and revert back if necessary without losing all the additions and configurations (like my firefox profile of add-ons, etc). I would love some suggestions. The way I am doing it now is spending lots of time tweaking and configuring and then wiping out everything when something goes wrong.
Here is what I have:
steven@ubuntu:~$ cat /etc/fstab
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop        0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop        0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw          0   0
/media/host/wubi/disks/usr.virtual.disk       /usr            ext3        loop        0   0
/media/host/wubi/disks/extra.virtual.disk     /media/extra    auto        loop        0   0

When I encounter the 'fail' at boot, I enter ctrl+c (I don't know if that's what I am sujpposed to do) and the boot process contiunes to the Ubuntu login screen, so yes it is a working install.
Thanks for your help and time.

---

### Post by stevelasvegas on 2007-05-31
So I rem'd the last 2 lines
/media/host/wubi/disks/usr.virtual.disk /usr ext3 loop 0 0
/media/host/wubi/disks/extra.virtual.disk /media/extra auto loop 0 0
and now I don't get a 'fail' during boot but it does stop and the screen turns black with the text:
"acitivating swap file".
I do a ctrl+c and it continues to boot to the Ubuntu login screen.
I really like Linux Ubuntu, but I am spending way too much time getting it to work without hitches. Maybe I'll try another install (I'm getting good at that).
I know it's not necessary, but I just don't have a clue what I'm doing. I could fix it if it were Windows, but I hate Windows.
Isn't there a log that has non-cryptic error messages?
Frustrated :(

---

### Post by oiler920 on 2007-05-31
Ah. Wubi is a beta product. Your virtual swap has something wrong with it. It seems Ctrl+C is bypassing the swap and using purely your physical RAM.  Are you running it from the virtual disk that Wubi makes, or did you move it to a real partition on your HD? Try installing Feisty from it's install CD and put it on a real partition. Works for me. If you can't burn the ISO, you can get Feisty from ShipIt, but that takes forever. ;) Feisty didn't install correctly on my computer, so I had to install Edgy then upgrade to Feisty. :( If you ARE running from a real partition, your comp. is messed up. Get Dapper or Edgy and upgrade from there. 8-)  BTW, how'd you come up with Ctrl+C?

---

### Post by stevelasvegas on 2007-05-31
Ctrl+C? If it looks like a DOS screen and it isn't doing anything, Ctrl+C.
Yeah, Its a WUBI install of Ubuntu Feisty, no partition.

---

### Post by digitalbenji on 2007-06-01
I had never heard of WUBI, so I just looked it up.  Is there a need for you to be using WUBI?  I would venture that WUBI is the source of your problems.  I would advice you to allow the Ubuntu installer to resize your Windows partition, and set up dual booting.  I have never had a bad experience with this method.  Of course, you should back up all your criticial files just to be safe.

I'm glad to here that commenting out those 2 lines got rid of those mount errors.

---

### Post by sfenton on 2007-06-03
I am running wubi as well and receive this message. From checking the beta developer forums they say to ignore the message. 

I just let ubuntu finish loading and all is well. I believe you are stoppng the swap file creation and that is causing the error after ubuntu completes loading. 

Sig

---

### Post by KeaponLaffin on 2007-06-12
I used WUBI and had the same problem. But worse ;)
I couldn't get the default Ubuntu to work, I eventually got UbuntuMedia/Studio..whichever to work. Although I still get that Virtual Disk error. I just have to wait a bit and the swap file seems to work.

When installing the Virtual.Disks..when initially installing, it seemed to stop at about 63%, then jump unto the blue screen before starting the next install process.

Previously, it just dropped me into a Maintenance Terminal and told me repeatedly to install apt-get...Lovely help message, use apt-get to install apt-get. It was in my usr/bin but it still wouldn't work for some reason.
It told me to hit Ctrl-D to exit and continue booting. But that just locked me up in the swap file which never started. So, if it happens again, now I know the Ctrl-C trick. Thnx!

One thing I blindly tried that seemed to work a few times(until..I think I installed a Package it didn't like). When in the DOS-like Terminal. I entered 'reboot'..and that re-started the boot process successfully.

Just glad to know I'm not alone. ;)

---

