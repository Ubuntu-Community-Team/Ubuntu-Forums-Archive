---
title: "Dual boot grub issue"
date: 2014-05-07
forum: Any Other OS
---

### Post by dogma2 on 2014-05-07
Hello everyone,

I installed Kali yesterday as a dual boot with windows 8.

Using Gparted,I made a blank space/unused space of 60GB,then I installed Kali on that space (though I think I din't use the "use the most free space available" option as I saw it was recommended to do so)
I did all my updates yesterday,everything was fine,grub was working.

Today when I started my computter I had a message "Welcome to grub...Grub error:no such device f5s44g5r....>Grub recovery".Plus my mouse and keyboard weren't recognized anymore.I was stuck with that screen with no way to even access the bios or boot option...

hopefully (and for reasons I can't figure out) I found out that,by unplugging the power supply of my computer,waiting 30 seconds that my motherboard turn off,and putting the power back and starting my computer,I was able to access grub and choose to boot windows or Kali without any issues.

So I started kali,everything was fine,restart mycomputer to see if grub still works...No!I had to unplug the power again and stuff and it then works.So it only works one time and I have to redo the thing with power supply and motherboard turning off.

Nom here is a gparted screenshots.One is a 128GB SSD and a 2TB hard drive.[IMG]http://imageshack.com/a/img843/8146/qwnx.png[/IMG]


[IMG]http://imageshack.com/a/img834/7766/4jk1.png[/IMG]


To me what really seems wrong is that 300MB boot partition which make no sense!

I have no idea how to fix that.I dont even know if I dind't totally mess up my Kali installation...

I hope someone could help me out!

Thanks

---

### Post by oldfred on 2014-05-07
Moved to other OS since Kali & Windows.

The 350MB boot partition is typical of Windows 7 or later. But usually it is 100MB. It is a hidden Boot partition for Windows. It is primarily available for you to separately encrypt the main install as the boot files cannot be encrypted. And it also has the recovery (repair) console or f8 to fix things, as it assumes you can boot the boot partition and have issues on main install. Still better to have a Windows Repair CD or flash drive as what if you cannot boot at all?
Grub does not use boot flag, Windows has to have a boot flag on primary NTFS partition with boot files on drive set as boot by BIOS. A few BIOS only boot with a boot flag on boot drive, even if grub, so we still suggest a boot flag on every drive. But that would be a BIOS error not a grub rescue error.

Seems like BIOS on initial setup resets so system works, but something about rebooting it does not. 
Does just powering down normally or cold boot, not warm reboot work? Or without unplugging system.

May be a BIOS setting, or some configuration.
Just to verify configuration, post the link to BootInfo report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Is BIOS the most current version vendor offers?
What computer, model?

---

### Post by dogma2 on 2014-05-07
I don't know how to get the boot info and boot-repair doesn't want to install.I got "could not find a distribution template" when using add-apt-repository ppa:yannubuntu/boot-repair...

WHat should I do?

(I'm still searching to fix that though)

---

### Post by oldfred on 2014-05-07
There is not a trusty ppa yet.
You have to change to the saucy ppa which works. The link shows a command to change that.

 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

### Post by dogma2 on 2014-05-07
I made it work,but really,it was very hard (well...for me it was!)

here's the bootinfo

[http://paste.ubuntu.com/7413080/](http://paste.ubuntu.com/7413080/)

and very interesting,I have this message in the terminal

(glade2script:14657): Gdk-CRITICAL **: gdk_device_get_n_axes: assertion `gdk_device_get_source (device) != GDK_SOURCE_KEYBOARD' failed


Does it mean it can't recognize the keyboard/usb where the keyboard is and it causes the issue?

---

### Post by oldfred on 2014-05-07
Error may be related to not mounting sdb5. It said busy??
I thought Boot-Repair mounted & unmounted partitions.
Or Kali does not have something that Ubuntu normally has and Boot-Repair expects.

Do not run auto fix in Boot-Repair with more than one drive. It just installs grub to the MBR of every drive. You want Windows in sda, and grub in sdb. And BIOS set to boot from sdb, once system is working.

I would see if you can manually mount sdb5 from your live installer. 
And I would try to run e2fsck on sdb5.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb5

You should add a boot flag to sdb1, even if you do not boot from it.
You should reinstall grub to sdb and install a Windows boot loader to sda. Then you can directly boot Windows if need be from one time boot key or BIOS.
But set BIOS to normally boot sdb once you get it working.

What mode is hard drive set in BIOS. AHCI? That is required for SSDs, so it should be your setting.

---

### Post by dogma2 on 2014-05-07
In fact it was  mounted cause I was executing boot-repair from the main installation on the hard drive,not on usb.

Though I rebooted using USB.I launched boot-repair and I did a recommanded reparation.

I restart the computer,and made the 2GB hardrive in first boot position,so now the computer boot on the 2GB and not on the SSD.

I don't have the problem with the grub error anymore,I can reboot as much as I want,I always have access to grub and the choice of selecting the OS.

BUT the keyboard isn't working,I can't choose the OS as I can't move.So I have to wait 10 sec so that it automatically boot on Kali.

Once I have to type my login and password to access  kali,the keyboard now works.

There must be some kind of issue,cause even in boot-repair in the terminal I got this message "(glade2script:14154): Gdk-CRITICAL **: gdk_device_get_n_axes: assertion `gdk_device_get_source (device) != GDK_SOURCE_KEYBOARD' failed"

very strange.

here is the new boot info,I'm still on the main kali installation on the hardrive when performing that

[http://paste.ubuntu.com/7413539/](http://paste.ubuntu.com/7413539/)

---

### Post by oldfred on 2014-05-07
You still are getting already mounted, so it does not show everything. But report would not show anything related to keyboard issues.

You still need to run Boot-Repair and install a Windows boot loader into sda. Use advanced mode not auto fix.
Or you can use your Windows repair CD or flash drive to run fixMBR command.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

May be best to start new thread. Not sure many use Kali. Keyboard is usually hardware related and different distributions may work differently.

Other than BIOS settings I do not know what else to suggest.

---

### Post by dogma2 on 2014-05-08
Ok I was able to fix my keyboard issue,I just set Bios to default settings and now it works.

Now I install MBR in SDA1,but for some reason,it also is installed in SDA2!So in Grub I have 2 options at launch for windows:SDA1 and SDA2 (actually both work,I tried)

But in Gparted I have a a "danger triangle" with and exclamation mark.Did I do something wrong?

[http://paste.ubuntu.com/7415479/](http://paste.ubuntu.com/7415479/)

---

### Post by dogma2 on 2014-05-08
Any ideas?

---

### Post by oldfred on 2014-05-08
Icons in gparted are an issue. Right click and see what it says.
But usually it is running chkdsk from Windows on NTFS partitions or fsck from your Linux on that partition if Linux formatted.

The error in BootInfo report is zenity which is a graphics for bash files. It looks like it expects a gtk device and cannot find it. 
But I do not know if Kali even uses gtk?

---

### Post by dogma2 on 2014-05-08
here is what is says (I can't scroll dwon to see the rest of the text though)

[IMG]http://imagizer.imageshack.us/v2/640x480q90/834/ud44.png[/IMG]

I personally think the issue is that I have 2 boot for windows (sda1 and sda2) so I guess MBR is on both partition.IS it an issue?

edit:I'll try chkdsk

---

### Post by oldfred on 2014-05-08
You only have one MBR per hard drive.
But Windows uses the PBR, or BS or partition boot sector which is like a MBR but the first sector of every partition. Grub does not use PBR normally and system cannot boot from a PBR directly.

---

