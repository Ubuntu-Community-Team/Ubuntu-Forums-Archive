---
title: "ubuntu doesn't boot"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by civic on 2007-09-03
Hello everyone,
At first I am sorry for my poor english. Secondly I do not know how to use frums, so I have type only the plain text.  And thirdly, I want to ask someone for some help, if I could. I have been trying all day to install ubuntu feisty fawn, but I do not know why, I failed. I am absolute newbie to linux. I know nothing about it, but I want to learn it. So that's what I have done, while installing linux:
[LIST]
[*] Downloaded and burned so file to acme cd-rw.
[*] Shutted down my pc, inserted that cd, turned on the power and the disc booted the menu from the cd.
[*] Then I pressed install or boot from the menu (the top one).
[*] The linux had booted from the cd.
[*] Pressed the install icon on the desktop (or how it is called in linux)
[*] Chosen English language, my place (lithuania), keyboard layout
[*] Then the partition manager showed up. I already have XP installed in the C: (~5 Gb). I also have other partitions with NTFS format for XP: D: (~25 Gb) and F: (~30 Gb). So I have left about 10 Gb for linux.
[*] I know, that I have to make two partions for linux - with Swap and Ext3 file format. So I have made one partiton with 2 Gb for Swap (logical) and the other one for Ext3 file format, where the linux will be instaled. 
[*] I checked the format button under the Ext3 format and pressed next.
[*] Chosen no accounts, because I do not need it (I think :))
[*] pressed Advanced. There I have found field with name Boot Options or something like that with "(hd0)" in it. I left it as it was. Also I have checked the button under "popularity contest" or something like that, which was also in there.
[*] Clicked next and it started instaling.
[*] After that it showed me a message where I was asked if I want to continue using the live cd or boot linux from the hard disc. I chosen to restart to boot from the HDD.
[*] I have started to feel so smart, but when the pc shutted down and started up again, the Windows XP had booted. I can boot linux, but only with the cd.
[/LIST]
So, what do I need to do to boot linux from the hdd? I have tried to install linux all this day - at least 20 times, but always got the same. I have googled for the problem, but found nothing. Only I know I need something like grub (do not know what it is). In wikipedia I found, that this is a program, which bots up firstly to boot up other OS. So I think I need to instal this program, but maybe I am wrong. So could anyone write me step-by-step instructions what do I need to to do make my ubuntu boot up together with my XP.

---

### Post by splintercellguy on 2007-09-03
Strange, the installer should have installed GRUB on the disk. Is the XP/Ubuntu installs on separate hard disks?

---

### Post by civic on 2007-09-04
I have only one 80 Gb Fujistu hard disc.
> **civic said:**
> I already have XP installed in the C: (~5 Gb). I also have other partitions with NTFS format for XP: D: (~25 Gb) and F: (~30 Gb). So I have left about 10 Gb for linux.
So I think it means, that ubuntu should have been installed in to these 10 Gb, because when I boot up windows everything seems to be all right.
And was that right to leave (hd0) in the setup, when I clicked advanced options in the last step of install?

---

### Post by logos34 on 2007-09-04
> **civic said:**
> I have only one 80 Gb Fujistu hard disc.

So I think it means, that ubuntu should have been installed in to these 10 Gb, because when I boot up windows everything seems to be all right.
And was that right to leave (hd0) in the setup, when I clicked advanced options in the last step of install?

According to my calculations you should have a total of ~74 GB space (at least that's how the OS's see it).  Minus the ~60 GB windows partitions = ~14 GB for linux.  

Here's some step-by-step guides w/screenshots you might want to take a look at. (Unfortunately they don't discuss extended partitions):

[http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html](http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html)
(*partitioning section)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by civic on 2007-09-04
I did everything as it was shown in these links. But now I have noticied one little difference, which may be important. As you can see in this picture their devices are /dev/hda and /dev/sda, but when I install linux I see only five /dev/sda with different nubers at the end. Can it be the reason, why my ubuntu doesn't install?

---

### Post by phoochka on 2007-09-04
Hmm I'm a newbie myself and I have broken GRUB a lot (dont ask!  :oops:) and find the Super Grub Disk very helpful! This is the website: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) 

I am sure there is a proper answer to your problem but in the meantime super grub should get you through.

---

### Post by civic on 2007-09-05
Well it did not helped to me. I can't boot linux from the hard disc, only from the live cd. And I even do not know if get it installed in to my hard disc. I use program Explore2fs to see, what is in linux partitions. I was said, that I should have menu.lst file in /boot directory, but I don't have it. What did I wrong, installing the linux?

---

### Post by jw5801 on 2007-09-05
That's very odd indeed. Did you try booting up from the supergrub disk to see if it could find your Ubuntu partition? You should be able to reinstall grub using it as well. There should also be a fix or recover (or something like that) in the Ubuntu LiveCD menu, so that might be able to find your Ubuntu partition as well. When you boot up into the LiveCD can you see your 4 partitions? It should automount the 3 NTFS partitions as well as your EXT3 linux partition. So you should be able to see them all on your desktop in the LiveCD.

---

