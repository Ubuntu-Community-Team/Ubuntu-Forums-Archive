---
title: "Ubuntu on Toshiba Qosmio G20"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Mahon on 2007-09-15
I've successfully installed Ubuntu on my Toshiba Qosmio G20 laptop, and set it up to dual boot with Windows XP. There are certain problems however. I've installed Ubuntu on a separate hard disk from windows, and this seems to slow down the boot process. Windows boots normally, but Ubuntu takes for ever to get going, and when it finally does it's pretty slow. It takes some time for it to open even Firefox.
I would guess I have a problem with my drivers. I've checked, and Ubuntu is using the correct nvidia driver, and I think OpenGL is activated (how can check this to be absolutely sure?). Also I'm getting a whole lot of boot choices on the GRUB screen, but only one of the Ubuntu options are bootable, that is "...12 Generic". The "...16 Generic", "...10 Generic" and "386" options do not work. Why are they there, and what is the difference between them?
I am now running Feisty Faun, but I was unable to install Feisty Faun, and had to install the Edgy Eft and upgrade from there. Feisty didn't find my hard disks.
I'm sick and tired of having to wait for ten full minutes for Ubuntu to boot every single time. What can I do?

---

### Post by Mahon on 2007-09-15
Oh, and of course my wireless connection isn't working. It's all set up. All the correct parameters are in place, and the WEP key is correct. It's sending packages, but it's not receiving. What can I do?

---

### Post by Akre on 2007-09-16
Fiesty will find harddrives if you modprobe ahci.

However after instaling it it is possible that ubuntu will not boot correctly.
ata_piix module may couse some troubles during boot. You need to blacklist it in initram filesystem. Latter will be loaded from root file system, where it is not blacklisted.

I've just dealt with this problem.If you have more questions or how to do this in detail just ask!

It seems it is already in bugzilla:
[https://bugs.launchpad.net/ubuntu/+bug/133892](https://bugs.launchpad.net/ubuntu/+bug/133892)

---

### Post by Mahon on 2007-09-17
Thanks for your reply. I am extremely new to linux. Started using Ubuntu because of its user friendly-ness. So I don't have any idea how to blacklist, and I don't really know what the initram filesystem is, so a detailed run-through would be great. :???:

---

### Post by Akre on 2007-09-19
Ok, here we go. I do not have access to machine so all I write, I write from memory, and this could lead to some mistakes. This is my first how-to (really)
So forgive me :))

Also, machine have disabled raid support in bios, and i was using kubuntu 7.04
[B]
Installing ubuntu:[/B]

Fiesty install will not detect Hard Drives (this could be the same with gutsy)
open terminal and:
switch to root interactive mode
load module for intel sata controller, this should be enough
```
sudo -i             
modprobe ahci    
```

Start instalation as normal. If in any case hdd will not be detected modprobe following modules:
```
modprobe libata
modprobe ata_piix
modprobe scsi_mod
modprobe sg
modprobe sd_mod
```

I've modprobed all modules and hdd was detected. Then install ubuntu as normal.

After instalation and reboot, in my case chances were: 2% successful boot, 98 %: failure

When in grub, press e, edit kernel line (vmlinuz, press e once again), append at the end:
rootdelay=10 and remove quiet and splash
This should look like:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1d85dd0d-78e6-4000-84d1-3c104d134c7f ro quiet splash
```

you make:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=1d85dd0d-78e6-4000-84d1-3c104d134c7f ro rootdelay=10

```
On my machine this made sure that i was able to get to shell. So when finished with editing press enter, then b to boot.

#Machine hangs with sth like:
Cannot find rootfs
Job tty control...
(bla bla)

(initramfs-shell)
Then you go with:
```
rmmod ata_piix
rmmod ahci
modprobe ahci
exit
```

Machine boots normally. I would suggest going with upgrade so you will have two kernel installed - one of thous is your backup. 2.6.20.-15 - old kernel
2.6.20.-15 - old kernel
2.6.20.-16 - new kernel, you will have this after update. You need to go with this procedure with every kernel you have, but i suggest trying only one at first.

So when on desktop you go to console, go to dir where you are going to store unpacked initrd image:
```
sudo -i
cd /root
mkdir initrd-image
cd initrd-image
```
then unpack it:
```
gzip -dc /boot/initrd.img-2.6.20-16-generic |cpio -i
```
No go with you favorite text editor and change file in this folder:
gedit, kate, mc, whatever, remember, only as root
kdesu kate, or gksu gedit or sudo mc
```
/root/initrd-image/etc/modules/modprobe.d/blacklist
```
append line at the end of file:
```
blacklist ata_piix
```

No we pack initrd **Ignore any error output you may encounter**:
```
find . | cpio --create --format='newc' > ../initrd-image-file
cd ..
gzip -9 initrd-image-file /root/initrd.img-2.6.20-16-generic
```

and copy /root/initrd.img-2.6.20-16-generic file to /boot dir and overwrite your old image (did I say to backup it? if not: make backup!!!!)

Then reboot, and this should work... if not... repeat until successful.

If you want I'll send yuou my images that are already done so you only have to overwrite thouse. They are big (few MBytes) so just send me yours e-mail and i will post it to you.
But first try to make this yourself, you will be happier :)
And remember to backup!!

---

### Post by e.saed on 2007-10-20
Please my friend 
I'm still new in using Linux 
So please send it to me by this e-mail 
[email]e.saed@hotmail.com[/email]

Thanks a lot

---

### Post by Akre on 2007-10-22
Problem is still present in Gutsy (yep - that is sad), 
new initrd are on the way. I will post them here soon.

**EDIT:**
I've got initrds, but they are far to big to attach them here.
Please give me your mails or follow this how to, it worked for me perfectly

Anyway, how to install gutsy on toshiba g20:

in boot choice: choose f6 and append to kernel options line:

```
break=mount 
```

remove splash and quiet.

Computer will boot to initramfs, then:
```

rmmod ata_piix
rmmod ahci
modprobe ahci
modprobe ata_piix
exit
```

Then just follow fiesty instructions.
Anyway, it is strange as in feisty it was enough to modprobe ahci in graphical mode, in gutsy in is no longer possible.
I call this bug regression :))

Anyway, on this toshiba g20 i was unable to get Nvidia card working (tried everthing, everyversion, from pkg, from source :/), while in feisty it was easy as cake. Another regression i would say.

---

### Post by shoha2108 on 2007-11-15
after the stroke gzip -9 initrd-image-file /root/initrd.img-2.6.20-16-generic, terminal says that there is no such a file or directory, although all the above codes worked without mistakes.
if possible, can you please send those images to my mail  [email]shoha2108@yahoo.com[/email] 
thank you very much.

---

### Post by Akre on 2007-11-17
that was the case in my example. But inits worked fine. Your repairead inits should be okay. If not please PM me and I will send inits.
---
Also, from other sources I thnik that command initramfs-update fetches it config from system files.
So perhaps blacklisting offending module in /etc/modprobe.d and then running initramfs-update -k all -c should be enough?
I will not be able to try this on machine in question (it is production machine:) but perhaps anyone else could try this and report result?

another problem is that ata_piix is responsible for cd device so blacklisting it in initramfs and in real root is bad idea as cd will not be detected.
Patching initramfs manualy couses this module to be loaded latter when system already chrooted (from what i can understand)

---

### Post by SharkP on 2007-11-21
Ehm...I didn't understand! What shall I do? Shall I blacklist ata_piix in initrd or not? I'm beginning crazy...Can't I use the cd drive if I blacklist ata_piix?

---

### Post by Akre on 2007-12-24
What i think the current solution to the problem is:
```

blacklist ata_piix in /etc/modprobe.d/blacklist
```

run:```
 sudo update-initramfs -u -k all
```

then reboot and check if this runs machine okay, if it does then you unblacklist ata_piix but do not run update-initramfs

That way ata_piix is blacklisted in initram and is not blacklisted in the real filesystem. So the sdhci modules takes hdd and ata_piix takes cd, which is correct behavior.

If this solution does not work please patch initram manualy, as outlined in this thread. I've done this few times and this work perfectly.

---

### Post by localhost44112 on 2008-06-14
Same problem on Ubuntu 8.04 but that did the trick ;)

---

