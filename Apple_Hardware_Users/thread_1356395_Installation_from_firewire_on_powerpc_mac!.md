---
title: "Installation from firewire on powerpc mac!"
date: 2009-12-16
forum: Apple Hardware Users
---

### Post by andath10 on 2009-12-16
Hello. I installed ubuntu on my Intel Mac and works flawlessly as the only OS of the computer (No dual boot). After a week of usage i decided to do something similar to an older PowerPC Mac. The problem is that there is NO CD-ROM drive in it! Well there is but is ruined after 6 years of usage and the money Apple store asks to fix it here in Greece worth half a new PC:(

I tried boot from the Intel Mac's CD-rom via Firewire but either starting the computer by pressing C or Option or by using Start Up Disk for Mac Os X Control Panel are not working. 

   First option gives me a small icon with a folder and a Mac on it flashing for about 1 minute and then normal boot to Mac Os X, Second option just dont work because even if the Ubuntu cd-rom is mounted by the system there is no choice in Start Up Disk!
   Tried also firewire the other way around and Ubuntu on Intel Mac recognise the disk of PowerPC's flawlessly.

I wondered if i can install PowerPC version of ubuntu from the Intel Mac but then i was like, hey it's a different architecture for the CPU to install it to the other Mac's Disk.
Finally the option im thinking is finding a ready .img of PowerPc Ubuntu and Restore it to the Mac's Disk with Clonezilla

I guess is a special situation but any suggestion or idea or even solution would be much appreciated!

---

### Post by linuxopjemac on 2009-12-16
That last option is not a bad idea...Or you might wanna try a net installation, which is not so easy...(Debian has that option I know), no experience with that though...

if you wanna dd a complete setup, you need to have a working Linux for the same machine. I don't know what kind of PPC machine you are using right now.

---

### Post by batterybaby on 2009-12-16
try something different will be exciting.
 the second thought is worth your trying. donnot be afraid of freshness.;)

---

### Post by linuxopjemac on 2009-12-16
if you have the net install working, post us a detailed howto, for others to repeat...;)

---

### Post by linuxopjemac on 2009-12-16
[http://www.debian.org/releases/stable/powerpc/ch04s05.html.en](http://www.debian.org/releases/stable/powerpc/ch04s05.html.en)

---

### Post by andath10 on 2009-12-16
well it's the last imac g5 isight with powerpc, i tried to learn more about network installation but honestly im using ubuntu and linux generally for 1 week now, dont think my chances are high!:P 

As for the freshnesh, im talking about clean pure ubuntu without dual boot ;). iI am NOT going back to anything like Mac Os X or Windows.

Btw is there any chance to create 2 partitions from x86 ubuntu to the PPC's disk, one to copy the CD image and one to install Ubuntu in?

---

### Post by linuxopjemac on 2009-12-16
I have no experience in that, but you can try to mount the PPC HD from a firewire cable under x86 ubuntu...I am afraid that that only works from within OSX though...

---

### Post by andath10 on 2009-12-16
yes i did this!:) however im a little skeptical to try installation from x86
the code of kernel is to be run in the x86 and since its for ppc?

theoretically speaking since i am installing to a "external firewire disk" in x86 machine code will be running to the x86 CPU so if code is for PPC BOOM!?? 

also i am a bit familiar with cli install (already did a minimal install of gnome-core, xorg, gdm in x86) if this might help tweaking.

---

### Post by andath10 on 2009-12-16
hmm just came up with another idea... Maybe if i can run a PPC virtual machine on my x86 mac and then mount via firewire to the PPC mac disk and start installation? 

The problem is im only familiar with VirtualBox.. installed it in Ubuntu but there isnt support for PPC... anyone familiar with any other virtual machine?

---

### Post by linuxopjemac on 2009-12-16
I must admit that you are creative...

You can make a few partitions on the HD via firewire. Maybe you can clone a PPC Ubuntu LiveCD on one of the partition of the PPC HD via firewire. And then you try to boot that PPC HD with the option key pressed. Hopefully it will recognise a bootable partition. Then you simply install Ubuntu in the other partiton. You then need to tweak later to make a bootloader in another third partition (max 200mb). So start with at least 3 partitions. You get my idea ?

---

### Post by andath10 on 2009-12-16
thanks for the comment!:)

Yes i get it;) so my plan:

1: connect PPC mac to firewire and by pressing T make it act like a firewire disk to the x86 mac

2: from the x86 mac make a partition about 1g with gparted

3: copy/paste (am i right?) contents of ppc ubuntu cd to this partition

4: unplug firewire, restart ppc mac by pressing option (windows) key, select this partition from the menu( really hope this works:)

5: proceed to installation by selecting the rest of the disk as Ubuntu main partition

6: after finishing install boot again as firewire disk to x86 mac

7: delete cd partition in disk with gparted (this way there is no need to make a 3rd partition for bootloader i guess right??)

8: reboot PPC mac in normal mode.. and have automatic load of ubuntu (this way works for me in x86 mac:))

9: happy owner of 2 ubuntu macs:)

just wrote down steps simple in case anyone else will need them for reference!
Also this way i avoid making a 3rd partition for bootloader.. although i think installation make it automatically... (its not that ur idea isnt better.. its just that i dont know how to manually do it;))

---

### Post by linuxopjemac on 2009-12-16
You need to have a bootlaoder partition, otherwise you will never be able to boot from a ppc based Mac (yaboot). Another thing. I don't think that by copy and paste of a CD you will be able to boot. You can try. But to my opinition, a CD consists of several partitions. Am I right here ? You need to clone such a partition scheme to the HD. You might want to try from the Ubuntu x86 computer to burn the PPC CD and to analyse it:
```
fdisk /dev/cdrom
```
and see if a CD indeed consists of several partitions.

---

### Post by andath10 on 2009-12-16
hmm thats why i read about yaboot in so many forums.. in x86 its like i didnt even notice there is a bootloader, thanks for this tip

will give it a try when i get home and ill post results;)

---

### Post by linuxopjemac on 2009-12-16
I am curious how this will go. I did a lot with Linux and MAcs, but I never did this...

---

### Post by linuxopjemac on 2009-12-16
From within the Ubuntu x86 computer, you need to dd the iso of the PPC Ubuntu LiveCd to a partition of the PPC based HD. you need to do something like:

```
dd if=/place/where_the_iso/is/ubuntuppc.iso of=/dev/hda2 bs=512
```

where /dev/hda2 is the partition you want to have the bootable Ubuntu partition

---

### Post by andath10 on 2009-12-16
that was exactly what i was looking now!:) 
i heard about dd when i was looking for partition backup (now using clonezilla) but didnt have a clue how to use it!:)

---

### Post by linuxopjemac on 2009-12-16
I also read about skipping the first 63 block, which contain the partition scheme of a CD

Then, do the following, and REPLACE of=/dev/hda2 by whichever partition you noted down above ! (like, of=/dev/hdb3 or of=/dev/hda3, etc..)
```

 cd /mnt/temp
 dd if=tiger-x86-flat.img of=/dev/hda2 bs=512 skip=63
```

Note : this will skip the first 63 blocks of the disk image. These blocks describe how the disk is partioned. After the 63rd sector, there is the first partition, which in this case is what we want. Most people get that totally wrong !

Wait long... then

---

### Post by linuxopjemac on 2009-12-16
You have to read some stuff about booting in open firmware, otherwise you cannot force your ppc mac to boot from the "liveCD partition".

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

This is from my own website:
> If you don't boot into yaboot, you have to restart again and hold the keys "apple", "alt" "o" and "f" all at the same time. One boots into open firmware then (if you have a NewWorld machine). This is a sort of Apple BIOS. In most cases the only thing to type here is:

setenv boot-device hd: …, \ \: tbxi (followed by)
boot

NB at … you have to give the number of the bootstrap partition. In my case this is partition number 13. The Mac should now boot into yaboot.
You can find this info here:
[http://mac.linux.be/content/installation-linux-ppc-based-macs](http://mac.linux.be/content/installation-linux-ppc-based-macs)

---

### Post by linuxopjemac on 2009-12-16
Write down everything you do. If you succeeded I want to know exactly what you have done. This can be a great tutorial for people installing Linux on PPC based Macs without a CD.

---

### Post by linuxopjemac on 2009-12-16
Out of curiosity, why don't you put a cheap CDROM in the G5? It should not be that difficult to find a second hand one. All you need is an IDE drive.
[http://manuals.info.apple.com/en/PMG5_OpticalDrive_DIY.pdf](http://manuals.info.apple.com/en/PMG5_OpticalDrive_DIY.pdf)

---

### Post by linuxopjemac on 2009-12-16
something as cheap as this will do the trick
[http://link.marktplaats.nl/304907743](http://link.marktplaats.nl/304907743)

or here
[http://eshop.macsales.com/static_pages/Framework.cfm?page=superdrive/sdl_powermac_g5.html](http://eshop.macsales.com/static_pages/Framework.cfm?page=superdrive/sdl_powermac_g5.html)

---

### Post by andath10 on 2009-12-16
well the problem is not the price of slim drives.. its a G5 isight and they are not openable at all.... i tried one time to do a DIY fix (have repaired-built several pc's) but the mainboard is somehow attached to the screen and requires some special tools something.. had seen a guide before some months somewhere and it was like surgery!:P

---

### Post by linuxopjemac on 2009-12-16
ah ok, it's an iMac. I thought you were talking about a PowerMac G5.

---

### Post by andath10 on 2009-12-16
well unfortunately i didnt made it... first the standard ppc iso was 705mbs:S couldnt write it to a spare cd-rw:( i did my test with the minimal installation as a install cd

Secondly gparted managed to delete the partitions of mac os x except a small one (300kb i think) that was marked as sda1. However gparted couldnt create a partition at all in this disk after the deletion of previous partitions:S

Tried also a fresh mac os x install, mostly to check if boot from firewire cd was working as intended, and had success. Tried to boot from minimal ubuntu cd after the installation.. nothing.. option key.. c key.. nothing worked:(

Btw checked from disk utility in mac os x cd if there is any option or something.. tried to partition hole disk as "unix drive" the meter got stuck for about 10 mins:(

Will give it a try again tommorow i guess:S

---

### Post by linuxopjemac on 2009-12-16
try it with a Debian Lenny installer...I'm pretty sure you will have more success.

---

