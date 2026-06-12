---
title: "installing 12.04 on macbookair1,1"
date: 2012-10-12
forum: Apple Hardware Users
---

### Post by nicolo.p on 2012-10-12
Hello,
I want to install ubuntu 12.04.1 on a macbookair1,1 (Apple MacBook Air "Core 2 Duo" 1.6 13" (Original) according to [http://www.everymac.com/systems/apple/macbook-air/specs/macbook-air-core-2-duo-1.6-13-specs.html](http://www.everymac.com/systems/apple/macbook-air/specs/macbook-air-core-2-duo-1.6-13-specs.html) ). And I have some questions.

1. Reading this post
[http://ubuntuforums.org/showthread.php?t=1799460](http://ubuntuforums.org/showthread.php?t=1799460)
is it safe to put linux? particularly, how close to rumors are the claims that os x is far better than linux in 'micromanaging' this particular device, and using linux can lead to potential problems in the cpu voltage handling?
2. grub vs efi: how's the story? is that correct that in any case I will have to maintain let's call it 'apple bootloader', and ony in a second part of the boot process give control to grub->linux?
3. reading
[http://ubuntuforums.org/showthread.php?t=2039799](http://ubuntuforums.org/showthread.php?t=2039799)
I don't know how to produce a bootable usb stick, namely when I do what he says with a usb stick in mrb or guid with ms-dos (fat) partition in both cases (is this correct?)
I get the message "the inserted disk is not readable by this computer" (translation from Italian, but this is the meaning) after the dd process is completed (see the post), and when I restart pressing alt it only sees the hd-drive, and not the usb.

4. is that correct to select the mac 64 bit version for this model? is there any other particular suitable version?

Can anyone help me? in particular, anyone with (hopefully positive) experience with similar macbook and ubuntu versions?
Thanks, N

---

### Post by litiform on 2012-10-12
Ive read in several places that installing ubuntu on Macs is a lot of trouble. You need to know a lot.

---

### Post by Caltac on 2012-10-13
Alright, here we go.

1. It is definitely safe to install linux on a Mac. I have been running linux on my Macbook Pro 7,1 for around two years, and nothing has gone wrong regarding the CPU, etc. However, it is crucial to remember that Linux was not written for apple computers, and there will always be some configuring to do. For example, your macbook running linux will have probably only around ~70% of the battery power compared to your macbook running OS X, simply because Apple optimized their operating system for those particular Macintosh laptops and the developers of Ubuntu did not.

2. On my macbook pro, I kept the apple bootloader and installed grub on my linux partition. That way, when I boot up my laptop I can just hold down the option/alt key and I can choose which operating system to boot into. When I choose linux, I am then taken to the bootloader installed on my linux partition (in this case GRUB). I would recommend this method; however, you can install rEFIt while in OS X, which is a third party bootloader. That method works well, too.

3. This link should be helpful to you.
[https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick")

4. I checked the specs of your laptop, and it looks like you only have 2 GB of RAM. Therefore you should run a 32-bit installation, not 64-bit. A 64-bit installation is best for computers with 4+ GB RAM.

I hope this information helped.

Cheers,
Thomas

---

### Post by nicolo.p on 2012-10-14
Hi Thomas, thanks for your reply.
about 3. my problem is that when I do 
```
sudo dd if=/path/to/downloaded.img of=/dev/diskN bs=1m
```
I get that error at the end of the process.
about 4. I know it is 32bit, but I was thinking that maybe the 64bit-mac was somehow optimized for mac.

Best, Nicolo'

---

### Post by iGeekiHackiMatt on 2012-10-14
3:
  [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx)
4:
  You should be able to use 64 bit.

---

### Post by nicolo.p on 2012-10-14
I've seen that page too, but it's basically the same as above; also, the error I get is not listed in the possible errors one could get (actually I get it when os x tries to mount the usb, and reads it as corrupt or something, I don't know if this is normal), while at reboot pressing alt just shows me the hdd

---

### Post by nicolo.p on 2012-11-23
at this stage, i'm not even able to boot, with or without refit. refit says basically 'the hardware refuses to boot': does anybody know a way to boot linux on this specific model from usb, without making new partitions and without the use of external usb dvd drive?

---

### Post by zaebo on 2012-11-23
I don't know if this is working with your mba, but it worked for my mb.
Maybe, if the normal ubuntu 12.04.1 image is not booting for you, you should check out the amd64+mac image.

For me, it works out this way:
I make a bootable USB-stick with unetbootin and the Ubuntu 12.04.1 amd64 image. When I reboot the macbook, I press alt (before rEFIt shows up). Sometimes I need to to pull the USB stick and insert it again, while being in the "mac boot screen" (that grey screen where I can choose to boot Mac).
Than there appears a new bootable device, called "EFI boot". By booting from that, I can boot Ubuntu and install it.

I can't tell you if this is the perfect way to do it, and if it is working with your mba (since I'm not so familiar with the EFI and legacy boot). But this way how I installed Ubuntu 10.04 months ago on my mb6.1, and now Xubuntu 12.04.

---

