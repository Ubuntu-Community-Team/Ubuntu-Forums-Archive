---
title: "ASUS S56CM &amp; Ubuntu"
date: 2012-11-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by snowz on 2012-11-25
Does **Ubuntu** work out of the box on the **ASUS S56CM** Ultrabook?

---

### Post by Amithiel on 2012-11-25
in a day or 2, im going to buy it too. i wonder if it works fine
24gb ssd, and another 1tb hd

---

### Post by snowz on 2012-11-26
The thing that is bothering me is the optical drive. Would be better having the optical drive replaced with a better battery or something more useful.

---

### Post by Amithiel on 2012-11-26
> **snowz said:**
> The thing that is bothering me is the optical drive. Would be better having the optical drive replaced with a better battery or something more useful.

true. anyway, cant wait to get mine :D

---

### Post by Amithiel on 2012-11-26
jesus, just got home with the laptop. can't even format this thing. what the hell. boots only from secure boot, wont let me do anything else. not even installing windows7 ?

---

### Post by Amithiel on 2012-12-10
did you managed to install ubuntu?
since our disk is 1 TB + 24 GB SSD, how should we do the partitioning?
is it possible to disable the secureboot?

---

### Post by Amithiel on 2013-01-15
I just thought it would be nice to leave a last comment here:

I'm now running linuxmint 14 without any issues at all. 

some aditional info:

- first go into BIOS and disable quick/fast boot and also Secure boot (failing this step will block the cd/usb installation)

- install linux and enjoy

- I did a manual partitition: please do NOT delete the "efi partition" , its only 300MB and will save you some headaches if you ever return to windows 8. 
i erase all the left partitions.
Use the 1 TB HDD to install /home , 
and use the 24 GB ssd to install /

everything working out of the box. For the Nvidia driver, use Bumblebee.
There might be some issues with suspending/hibernation, as it freezed on me a couple of times. But i don't care, i rarely use it, so... just disable that and wait for some fix.

---

### Post by donbeo on 2013-01-19
I'm using ubuntu 12.04 on a s56cm. 
Sometimes ubuntu freezes and I do not know why.

Now I'm tryng to use Unity 2d

Do you thing that is nvidia the causes of the freezes?

---

### Post by cobak78 on 2013-01-23
my ASUS have a bunch of partitions 

dev/sda1/ fat32  314MB 
dev/sda2/ ntfs   329MB 
dev/sda3/ unknown 133MB 
dev/sda4/ ntfs   200GB 
dev/sda5/ ntfs   200GB
dev/sda6/ ntfs   20GB

and in the ssd

dev/sdb1/ ntfs 4294MB
dev/sdb2/ unknown 20GB 

wich one is the recovery partition?

---

### Post by jonigual on 2013-01-25
I just installed ubuntu 12.10 along with windows 8 and everything is working fine.
Have to do some twiks thouh.

For installing it I basically followed the steps described here: [http://webent.altervista.org/2012/09/16/how-to-install-ubuntu-linux-12-04-or-newer-on-the-zenbook-ux32vd/](http://webent.altervista.org/2012/09/16/how-to-install-ubuntu-linux-12-04-or-newer-on-the-zenbook-ux32vd/)
Here are the steps I followed (I used SSD disk for installing ubuntu sytem).

- As Amithiel said, to start from an Ubuntu Live CD/USB "first go into BIOS and disable quick/fast boot and also Secure boot".

- I selected to try Ubuntu, and used gparted for partitioning the disk. I had quite a lot of partitions already there. I deleted the DATA partition I had (with 500GB), and used the free space to create a swap partition with 5GB, and the rest for creating an ext4 partition (495GB). I also deleted all the partitions in the ssd disk (sdb), and create another ext4 partition with all of it. I don't really know what all the other partitions are for, so it just felt safer to leave them alone.

- Reboot and install Ubuntu. Select manual partition and use the swap partition for swap, set 495GB partition for ext4 (mounting point /home), and the sdb disk for ext4 (mounting point / ). Follow the rest of the steps and ubuntu should be installed.

AFTER INSTALLATION:

- I couldn't adjust the screen resolution, so I upgraded the kernel to 3.7.4 version following the steps described here: [http://www.upubuntu.com/2013/01/install-linux-kernel-374-in-ubuntulinux.html](http://www.upubuntu.com/2013/01/install-linux-kernel-374-in-ubuntulinux.html)

- After upgrading the kernel edit the file /etc/defaul/grub and change the following line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

with:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

Update grub with the following command: sudo update-grub

- For the nvidia drivers I installed bumblebee ([http://bumblebee-project.org/install.html#Ubuntu](http://bumblebee-project.org/install.html#Ubuntu)).

That's all! Everything is working perfect now.

Hope it helps.

---

### Post by Nesaskewatch on 2013-01-26
I too am having problems. I have done as you described; disabled fast boot and secure boot but it will not give me the option to boot from a usb or a dvd. [N56VJ-SH71-CD]("http://www.staples.ca/ENG/Catalog/cat_sku.asp?CatIds=,4157&webid=100010&affixedcode=WW") here. Which key you are holding down that gives a list of  boot options?

Edit: I found it. One has to enable CSM and disable secure boot and hold the esc key to get the boot options.

---

### Post by coxtor on 2013-02-13
Hey there, I too have managed to successfully install ubuntu, but could somebody please write a step by step tutorial to get bumblebee working? 
I have been trying to get it work for a while and it just wont work, 
optirun glxspheres fails with :
[ERROR] Cannot access secondary GPU - error : [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the

---

### Post by yalç&#305;n can on 2013-02-14
I don't know which fan is constantly running background but very annoying fan noise is always bugging me. Does anybody know how to get rid of that?

---

### Post by sormariano on 2013-02-16
> **Nesaskewatch said:**
> 
Edit: I found it. One has to enable CSM and disable secure boot and hold the esc key to get the boot options.

Thank you very much !!!.
Ok this solution works fine for me. I was already desperate. I bought it yesterday and I was going to give it back to the dealer :)
How did you find it? I've read anything about it on the user's guide

---

### Post by Lurkos on 2013-03-07
I've just bought this laptop, and I'm looking forward to install Ubuntu.

However I cannot find the way to modify EFI configuration.
When I press the power button I see the ASUS logo and after few second the Windows 8 welcome screen.
I tried to press ESC, F2, TAB at boot without success.

How did you access the EFI configuration to disable secure boot and enable boot from CD?

Thank you.

---

### Post by HeraultWan on 2013-03-18
Hello guys i bought a S56cm too and i saw this thread so here am i :)

Concerning the constant fan noise in the background [COLOR=#000000]**yalç&#305;n can** spoke about i upgraded the BIOS from ASUS website ([http://www.asus.com/Notebooks_Ultrabooks/S56CM/](http://www.asus.com/Notebooks_Ultrabooks/S56CM/) > Go to support in the upright corner, then to download tab) which fixed it. It's not constantly blowing out cold air anymore :)
[/COLOR]
To acces the BIOS Lurko try pressing f8 or  f5 aswell on startup i don't remenber quite well which is the one

Some problems i have, maybe you guys know about it :

The battery lasts way longer on Windows than on Ubuntu (Gnome3), 4 hours vs 2h20 (!!) that i brought up to almost 3 hours with *powerertop*. Did you also experience a drop in battery life under Ubuntu? Do you use *powertop* as well and what did you do with it or do you have any battery managing tricks?

I have to go through the BIOS and modify the boot order option to change booting from Windows or Ubuntu (which i find weird although being new to Ubuntu), and after selecting Ubuntu i have to go through a kind of second BIOS where i have to select Ubuntu again to boot but where can also select few other things including a "Windows" option which would however not boot correctly. Do you know a bit about EFI/BIOS configuration so that i could have a straightforward Ubuntu/Windows option a the begining?

Thanks,

HW.

---

### Post by sampo555 on 2013-03-29
I've managed to get the battery life from 2.5 hours to 4.5 hours by completely disabling the NVidia GPU (it's just idling there drawing power if you don't use Bumblebee to run something on it). See [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) for installation instructions (notice the "For advanced users..." part if you only want to save power) and [https://github.com/Bumblebee-Project/bbswitch#usage](https://github.com/Bumblebee-Project/bbswitch#usage) for usage.

---

### Post by Roasted on 2013-04-22
How did you guys manage to get Ubuntu installed on it? I successfully installed 13.04 but each time I try to boot up it just goes right to the BIOS. I disabled CSM, Fast Boot, and Secure Boot, but I'm getting nowhere. I updated the BIOS and that made no change. I contacted ASUS and they don't seem to care (their service can be roughly translated as "pure garbage", and I base that on a dozen situations in the past two years, not just this one).

Does anybody have any insight?

---

### Post by Roasted on 2013-04-22
Somebody suggested to me 3 things:

1) Disable Secure Boot
2) Disable Launch CSM
3) Format drives with MBR partition table

I had done 1 and 2, but not 3. Turns out that's what was needed. I'm super happy to be running Ubuntu on this laptop without any issues now. My function keys seem to work and resume/suspend works without issue. That being said, I can't help but to wonder - what if I needed GPT? What if I had a 5TB 2.5" HDD I wanted to install? With the limitations of MBR, I wouldn't be able to take advantage of the size of that drive, which seems to ultimately come back to Microsoft being to blame (I would think) seeing as though since using MBR is what I needed to do in order to circumvent Secure Boot so I could install the operating system I wanted.

So, would I be absolutely stuck? Is there no hope for GPT partition tables with Secure Boot disabled? (which thereby enables some sort of Legacy Boot, I assume, thereby requiring MBR?) Or am I totally off with my understanding?

---

### Post by yalç&#305;n can on 2013-05-02
> **sampo555 said:**
> I've managed to get the battery life from 2.5 hours to 4.5 hours by completely disabling the NVidia GPU (it's just idling there drawing power if you don't use Bumblebee to run something on it). See [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) for installation instructions (notice the "For advanced users..." part if you only want to save power) and [https://github.com/Bumblebee-Project/bbswitch#usage](https://github.com/Bumblebee-Project/bbswitch#usage) for usage.

Bios updating solved my problem but I had to install windows to install it. Whatever problem solved. Thanks for everything sampo555 =D>

---

