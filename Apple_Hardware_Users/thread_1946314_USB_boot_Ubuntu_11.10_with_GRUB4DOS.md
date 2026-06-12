---
title: "USB boot Ubuntu 11.10 with GRUB4DOS ?"
date: 2012-03-24
forum: Apple Hardware Users
---

### Post by Obelisk Do on 2012-03-24
Hi everyone,
I'm not a newbie in term of using Ubuntu but still a chick when it come to working with command-line system.

Right now I'm trying to create a multiboot USB, in detail I want a USB that contains 3 common OSes (Window, Ubuntu, and Mac) using GRUB4DOS. Firstly I 've try it with Ubuntu 11.10 and 11.04 (iso file got from the official Ubuntu website).

The main and maybe toughest task - it seem - is writing the "menu.lst" file (I guess that anyone who used GRUB4DOS knew it). After hours learn from the Internet I 've come up with some configures as follow:

```

title Ubuntu 11.10 - 1
find --set-root /OS/Ubuntu_11_10.iso
map --mem /OS/Ubuntu_11_10.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Ubuntu 11.10 - 2
find --set-root /OS/Ubuntu_11_10.iso
map /OS/Ubuntu_11_10.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz boot=casper iso-scan/filename=/OS/Ubuntu_11_10.iso quiet splash locale=zh_CN.UTF-8 --
initrd /casper/initrd.gz
boot

title Ubuntu 11.04 - 1
find --set-root /OS/Ubuntu_11_04.iso
map --mem /OS/Ubuntu_11_04.iso (hd32)
map --hook
root (hd32)
chainloader (hd32)

title Ubuntu 11.04 - 2
find --set-root /OS/Ubuntu_11_04.iso
map /OS/Ubuntu_11_04.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz boot=casper iso-scan/filename=/OS/Ubuntu_11_04.iso quiet splash locale=zh_CN.UTF-8 --
initrd /casper/initrd.gz
boot

```

Though all of them've just lead to the installer's splash screen (well-know to Ubuntu users), and after that the following error occured (see attached file).

Would you like to give me some tips about that ? And how can I write commands that can boot any bootable iso file on my USB stick ? (I use a Transcend 4GB).

Thank you for even viewing this thread ^^

And finally, sorry for my bad Enlish.

---

### Post by oldfred on 2012-03-24
Booting any type of proprietary operating system without a license is against forum rules. You also cannot boot Windows except from the system it is licensed to. It will not install into anything other than a internal hard drive. You can install the Windows installer to a USB but have to do that from a Windows machine.

Hackintosh/Apple EULA violation. 
We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalized with infractions and warnings.

For more information, please see the forum policy: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy). If you believe this was made in error, please post in the Resolution Center, which you can find in the previous link.

I used grub2 to multi-boot ISO.
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

### Post by Obelisk Do on 2012-03-25
Maybe there's a mistake of mine in writing.

I'm trying to say that I want a USB that *contains* those OSes - not *run them inside*. It mean when I'm insert the USB to my iMac, I can choose to *install* any of them, and after that, *booting them from my iMac* is a certain thing...

Does that still against the law ? >"<

I'm so sorry about that, but... I don't want to be an out-law here :|

And, thank you for your support ^^

---

### Post by oldfred on 2012-03-25
If you have a Mac and a full license to Windows then that is fine & we have no issue. 

But you may be better in the Apple subforum. As USB booting in a Mac is a lot different and I know nothing about that.

Moved to Apple sub-Forum.

---

### Post by Obelisk Do on 2012-03-25
Yeah, thanks again to your fully-support, my problem is now solved :p.
It was a little mistake of mine in expecting file name. From Karmic Koala on, the file "initrd.gz" was changed to "initrd.lz". Boot to Ubuntu perfectly with these line in menu.lst:

title Ubuntu 11.10 (OK!)
find --set-root /OS/Ubuntu/Ubuntu_11_10.iso
map /OS/Ubuntu/Ubuntu_11_10.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz boot=casper iso-scan/filename=/OS/Ubuntu/Ubuntu_11_10.iso quiet splash locale=zh_EN.UTF-8 --
initrd /casper/**initrd.lz**
boot

Hope this helps many others ! ):P

---

### Post by nazar2nirvana on 2012-07-25
ok all this is about loading the iso file from grub4dos

how can i load the installed ubuntu 12.04 from grub4dos of my 3rd partition of my harddisk

previously it was like
title find and boot Linux with menu.lst already installed
fallback 5
find --set-root /sbin/init
savedefault --wait=2
configfile /boot/grub/menu.lst


now menu.lst no longer exit

what is the solution??

---

### Post by oldfred on 2012-07-25
@nazar2nirvana
This is a solved thread, so posting a new question in it will not get much response.
You also have same question in your own thread, Please do not post duplicate posts with the same question as we all all volunteers and you dilute the efforts of all the volunteers.

Thread closed.

---

