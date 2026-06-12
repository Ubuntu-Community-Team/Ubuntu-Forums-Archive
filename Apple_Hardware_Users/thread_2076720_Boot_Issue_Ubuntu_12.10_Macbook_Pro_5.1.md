---
title: "Boot Issue Ubuntu 12.10 Macbook Pro 5.1"
date: 2012-10-26
forum: Apple Hardware Users
---

### Post by gatias on 2012-10-26
Hi,

I'd like to boot Ubuntu 12.10 on my Macbook Pro 5.1 (Mountain Lion) and set up a dual boot.

I tried:
1. Ubuntu 12.10 (32 bit) USB Stick through Terminal (on OSX) ([http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx"))
=> Is not bootable (does not show any other boot device after holding Alt)

2. Ubuntu 12.10 (32 bit) USB Stick through Disk Tool on another Ubuntu machine
=> Is not bootable as well (does not show any other boot device after holding Alt)

3. Ubuntu 12.10 (32 bit) internal boot partition 
used the commands form (1.) but copied the content of the image to an empty partition of my internal harddrive (i'm not sure about the format of the partition, any suggestions?)
=> partition does not appear as a boot device

4. Installed refit through Package Installer
=> refit doesn't show up  

5. Installed refit through command line
=> refit dosen't show up

6. disabled Filefault2 and tried step 4 and 5 again
=> still no refit menu

(I tried more than 2 reboots after each fresh install of refit)


Some other facts:
- Internal OCZ 120gb SSD (Mountain Lion) with a 15gb partition for Ubuntu
- Replaced my cd drive with a 250gb hdd => so can't boot from cd
- Macbook Pro 5.1

I hope some of you have any ideas how to get a working dual boot or at least how to boot an ubuntu on my machine.

Thanks for your help!

---

### Post by risidoro on 2012-10-29
Hi, I have a macbook 5.1 (13" unibody late 2008 ), ML 10.8.2, and was recently able to install ubuntu 12.10 with EFI quite easily (for the first time ever).
No bootcamp required (bootcamp is for BIOS emulation AFAIK, I wanted pure EFI)

The only difference with your setup: I used the 64bit version (the normal 64bit image, not the mac-specific).

This is what I did:

- Download 64bit Ubuntu image from main download page
- Create a USB stick on windows with pendrivelinux's Universal USB installer (maybe the terminal under OSX will do the same)
- Boot Ubuntu USB keeping ALT pressed during boot (I was quite surprised to see the ubuntu usb showing in the ALT menu, It had never worked with previous versions of Ubuntu - but I had only tried 32bit versions until now, ths time it was 64bit)
- Open Gparted, I had sda1: EFI partition, fat 32; sda2: Macbook partition, hfs+; sda3: ML recovery partition, hfs+

- Reduce sda2 (the main osx partition, the biggest) to free up space for Ubuntu (I left 30gb)  [Suggestion: I think it's better if you reduce the sda2 partition using disk utilities under OS X, I used gparted with no problems but i think disk utilities is safer]
- Leave the space you just freed up unpartitioned
- Start the Ubuntu installer and choose: Automatic installation OSX AND Ubuntu  (i don't remember the exact wording, but it was something like that) No manual partitioning.
- Ubuntu will proceed automatically and install inside the empty space you left for him (and install grub efi too)
 - at the end, power off the pc, sorry, the macbook :)

- On the restart, I saw the grub bootloader menu listing Ubuntu, OS X 32bit and OS X 64bit. Choosing Ubuntu will start, well, Ubuntu! Choosing the other two OS X options instead, will crash the pc (will solve this problem later).

- On Ubuntu you will have to follow one on the many guides to correctly install the wifi card (not too difficult. I havent time now to give you some links, just google them)

- To start OS X, instead, keep pressed ALT during boot (you will see only OS X and OS X Recovery, No Ubuntu)

- In OS X, install reFind (a fork of ReFit, more up to date). To install it: download it, unzip, and run one script with sudo from the terminal (documented on refind site). No further configuration required.

- Power off (no restart) the mac and power on again: This time you'll see a nice graphic boot menu with only two icons: Ubuntu and OS X. Both Icons will work perfectly. So no more ALT pressing at start.

That's all! This time it was very easy installing EFI ubuntu on my mac! But remember: 64bit version!

Have fun,
bye

Isidoro

---

### Post by elctro on 2012-10-31
Tips:

1. Resize partion from Mac with FAT, to be in the safe side.
2. Install rEfIt.
3. With Mac devices you should check "nonodeset" box. In the main screen of livecd press F6 then check "nomodeset". After finishing installtion, choose linux in the rEFIt screen after that press key e in the command line screen to edit it and add the word "nomodeset" before two spaces before "quitsplash" word then press F10 to start temporary. Finally edit the file grub.cfg and add the word "nomodeset" before two spaces before "quitsplash" word to make it official^^ then save it.

```
sudo gedit /boot/grub/grub.cfg
```

---

### Post by gatias on 2012-11-05
Thanks for your reply!

@risidoro:
Using Ubuntu 64Bit and Windows to create an usb drive worked pretty well. I was able to see the screen where I can choose "Try ubuntu" or "Install ubuntu". Unfortunatley, neither try nor install worked. The only thing I got, was weird graphic artifacts on the screen and nothing happend. 
Any ideas? I would replace OSX with ubuntu, if i could...

@elctro:
I do not have a cd drive, but thanks anyway!

---

### Post by risidoro on 2012-11-06
Hi,
I had similar problem recently with a Kubuntu 64bit MAC-specific image. DOn't know why though.
The image that worked with me (late 2003 macbook 5.1, nvidia 9400m) was Ubuntu 12.10 64bit NON-MAC-specific (the one you download from the main download page on ubuntu.com).

Also, after choosing Try Ubuntu, try to wait for a few minutes for X to start completely or try to switch to another console ALT+CTRL+1 (... up to 6) and from there cat a few logs (in /var/logs/) to see what's going on...

---

### Post by gatias on 2012-11-06
I used the same Ubuntu version and waited a few minutes. I couldn't switch to console :(.
Maybe I'll try other images.

Thanks.

---

### Post by jjmajava on 2012-11-15
I'm having exactly the same issue as gatias, with only these graphic artifacts showing up. Is there any way to do the install without the graphical interface?

---

### Post by quentinl on 2012-11-15
are you using 32 or 64-bit?
32 has worked better for me
also you could try burning the iso to a disk and the run a disk boot and take it from there (thats what i did)
p.s that was on a PC but i don't see why it wont work on mac

---

### Post by fulopattila122 on 2012-11-16
> **quentinl said:**
> 
also you could try burning the iso to a disk and the run a disk boot and take it from there (thats what i did)
the guy has stated clearly that he doesn't have a CD, so it's not really  good option.
> **quentinl said:**
> 
p.s that was on a PC but i don't see why it wont work on mac
you didn't yet try to install OS on a mac did you? :)

---

### Post by fulopattila122 on 2012-11-16
I neither could make the USB stick appear in OSX's boot menu. I tried the stick with a PC and it worked well, so I realized the problem isn't with the stick but with the Mac EFI loader.

I've installed [rEFIt]("http://refit.sourceforge.net/"), restarted (twice) the mac, and finally the USB stick has appeared in it's menu and I could start installing from that my brand new Ubuntu 12.10. It is a late 2009 iMac, with OSX 10.6 and the ubuntu image I was using was the 64bit+mac one.

---

