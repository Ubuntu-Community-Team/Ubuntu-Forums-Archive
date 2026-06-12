---
title: "[ubuntu] Macbook Pro 11,1 (2013 Haswell Retina)"
date: 2013-10-30
forum: Apple Hardware Users
---

### Post by conan.jen on 2013-10-30
Creating this thread to start listing things that are working / not working so others don't have to scour the Internet to confirm things.

OS: Ubuntu 13.10

Doesn't work:

- Speakers
- iSight
- Suspend / Resume (resumes to black screen)

Works:

- Wifi
- Keyboard backlight / LCD backlight function keys
- Touchpad
- Headphones
- SD Card
- Thunderbolt (for displayport)

Installation process very smooth, deleted all other partitions, created efi boot partition + ext4 partition, installed onto ext4 partition and everything* just works.

Make sure to add libata.force=noncq to your grub configuration, otherwise SSD will lock up from time to time.

---

### Post by mpereira1 on 2013-10-31
Have you noticed a different battery discharge rate on Ubuntu?

Thanks for posting your experiences!

---

### Post by conan.jen on 2013-10-31
Not an OSX person, so I can't speak to what the "normal" battery life in Mavericks is supposed to be. Based on my own experiences, after I added in a bunch of the kernel level powersaving options (whether they helped or not, have not determined yet), I generally tend to average around 6-8 hours on battery (i7 4558u).

My usual computer usage generally tends towards web browsing + 1-2 dev vm environments + local travis CI / testing. To be quite honest, I'm plugged in during the day at the office, and it lasts me from when I get home until I go to sleep, so I'm not too worried about battery.

---

### Post by vic.jang on 2013-11-01
Hey Conan,
I just got my 15" RMBP with Retina yesterday and I am trying to install ubuntu in it. I didn't find an tutorial so I followed one for the previous model, and installed 13.04.

After the installation, I am able to use Refind to boot, but it then entered verbose mode, kept running and would never boot into Linux.

Anyway, I am just hoping if you can provide a simple instruction on what I should do to install Ubuntu(which version doesn't matter to me)

I read you post but I don't really understand the partition part. What do I need to do exactly in DiskUtility to create both the EFI partition and the ext4 partition?

Also, do I need Refind as the boot manager? Or is Grub working without any problem?

Thank you so much!

---

### Post by vic.jang on 2013-11-01
I tried again using 13.10.
I select to boot into Ubuntu from Grub, it starts booting, and stopped at a blank purple screen, with fan running at highest speed.
I shut it down after around 8 minutes.
Any idea?

---

### Post by conan.jen on 2013-11-01
> **vic.jang said:**
> I tried again using 13.10.
I select to boot into Ubuntu from Grub, it starts booting, and stopped at a blank purple screen, with fan running at highest speed.
I shut it down after around 8 minutes.
Any idea?

Here's what I did:

1. Downloaded 13.10 NON-MAC iso.
2. Put it onto flash drive via unetbootin.
3. Boot up with option held at startup, and select the usb drive.
4. Upon installer bootup, went into advanced section and deleted all partitions.
5. Created an efi boot partition at 200mb. Installer should auto set the mount point on that partition to /boot/efi, but make sure.
6. Created a normal ext4 partition mounted to /, for the system installation point.
7. Continued on setup.

Again, not sure if this is generally the "accepted" way to do this, but everything works fine, and ubuntu boots into EFI mode.

---

### Post by vic.jang on 2013-11-01
Thanks for the reply, Conan!

I have two questions:
1. Why did you use the NON-MAC iso instead of the Mac one?
2. Do you still have the Mac OS and is able to dual boot? It seem to me that you only have Ubuntu on your MacBook Pro?

---

### Post by conan.jen on 2013-11-01
> **vic.jang said:**
> Thanks for the reply, Conan!

I have two questions:
1. Why did you use the NON-MAC iso instead of the Mac one?
2. Do you still have the Mac OS and is able to dual boot? It seem to me that you only have Ubuntu on your MacBook Pro?

AFAIK (someone correct me if I'm wrong) the Mac iso is forced to boot in BIOS mode, since earlier versions of mac hardware will not boot a hybrid EFI / BIOS image. Since the end goal is to get Ubuntu running in EFI mode, it seems the new haswell machines can boot hybrid images, and therefore the normal iso will boot fine.

No, I do not have OSX running. I'm sure you can get dual boot working, but I have no desire to run OSX so it made more sense for me to just wipe it.

---

### Post by kjano on 2013-11-01
I just installed Ubuntu 13.10 on the new Macbook Pro 15 Retina/Haswell without any issues. I am using Refind. Wifi works, the keys for display brightness etc work. I will have to play around more to see what is missing. What I already noticed is that there is no sound and suspend does not work (see also the first posting). I hope to get the sound working soon.

---

### Post by vic.jang on 2013-11-01
kjano,

Can you share some information about your install?
Did you install grub or you only have Refind?
Which ubuntu image did you use? Did you have to convert it to .img to put it into a USB stick?
 
Thanks!

---

### Post by conan.jen on 2013-11-01
> **kjano said:**
> I just installed Ubuntu 13.10 on the new Macbook Pro 15 Retina/Haswell without any issues. I am using Refind. Wifi works, the keys for display brightness etc work. I will have to play around more to see what is missing. What I already noticed is that there is no sound and suspend does not work (see also the first posting). I hope to get the sound working soon.

I'm currently looking into sound as well. My current suspicion is that the speakers are default muted (as evidenced by looking at alsamixer), but I haven't figure out quite yet if that's necessarily the root cause for them not working, since unmuting and setting them as the only active device hasn't worked.

---

### Post by kjano on 2013-11-01
> **vic.jang said:**
> 
Can you share some information about your install?
Did you install grub or you only have Refind?
Which ubuntu image did you use? Did you have to convert it to .img to put it into a USB stick?
 

Frankly speaking I had a lot of work to do and thus was very lazy with the installation. All I did was installing Refind, using Mac's DiskUtility to free 450GB on the SSD, create an bootable USB stick under OSX, and then simply boot it. I did not had to change anyting or play with any config files.

I used an external ALFA USB wifi card during installation but after that the internal Macbook wifi is working just great. Sound is not working and I can neither restart the machine nor put it to sleep. Shutting it down is the only option. For some reason booting takes nearly a minute.

I am also only using the Nvidia card which is not good for the battery. I tried to install Bumblebee but this turns out to be a very bad idea and I ended up removing it for like 30 minutes running into multiple errors. Now I am using Nvidia's driver in version 319. 

If anybody would know how to completely disable the external card and just use the Intel card, that would be great. Of course I want to use a mixed mode in the future (that is why I got the card) but for the moment I prefer 9 hours of battery over the ~5:30 that I would be getting with the Nvidia card running all the time (according to the power notification in Gnome). 

I installed Gnome and increased the font scaling for the Retina display -- works great. 

**Offtopic:** I hate the fact that I had to buy a Macbook Pro but it has the best hardware, best build quality, and since last weak is also the  cheapest slim laptop on the market. Very sad... I initially wanted the Lenovo T440S or Yoga 2 Pro but the Yoga cannot show the color yellow (no kidding) and the T440s has a delivery time of nearly 4 weeks, the (by far) weaker hardware, and costs more....

---

### Post by kjano on 2013-11-02
Btw, looks like there is a tutorial here: [http://randomtutor.blogspot.co.uk/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.co.uk/2013/02/installing-ubuntu-1304-on-retina.html)

---

### Post by kjano on 2013-11-02
@conan.jen: From what I see we both installed via Grub und without going via the ubiquity -b route. I guess this may be the reason why the graphics card switching does not work. I re-installed using the tutorial linked above today but this is a real pain. I do not want to do this with every new kernel update and will go back to the regular grub version:

Sound: 
This is what I found on the Web to fix that issue but it does not work for me:
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

---

### Post by mpereira1 on 2013-11-02
> **kjano said:**
> **Offtopic:** I hate the fact that I had to buy a Macbook Pro but it has the best hardware, best build quality, and since last weak is also the  cheapest slim laptop on the market. Very sad... I initially wanted the Lenovo T440S or Yoga 2 Pro but the Yoga cannot show the color yellow (no kidding) and the T440s has a delivery time of nearly 4 weeks, the (by far) weaker hardware, and costs more....

Same. I was gonna get the Lenovo T440S as well, but considering its price/specs ratio it doesn't make a lot of sense getting it over the new Macbook Pro.

---

### Post by kjano on 2013-11-02
Exactly. The Macbook is just soooo much better.

---

### Post by kjano on 2013-11-02
**Update:**

I reinstalled Ubuntu now with grub-efi boot and without any refind or related software. I really do not want to play around with this every kernel update. System now boots in less than 10 seconds and with the noncq setting in grub (libata.force=1:noncq )it does not freeze. I still cannot get the webcam working despite installing isight-firmware-tools and selecting the right macOs file by hand (the default will not work). Sound (i.e., speakers) are still not working but I can use my headset (neither changes to alsa-base.conf nor the alsa-daily ppa help). I am back to the open source drivers for nvidia getting about 4 hours battery with full screen brightness, surfing, and using (PDF)latex. Using the original nvidia drivers I got like 5:30. Please not that I never really tried this up to the point where the battery wasa really empty. I am just reporting the estimates from the notification app after working without the power supply for about 2 hours each time. xsensors works and reports the temperature and fan speed correctly (I hope). Fan speed is between 1999 and 6000 (using the stress tool for 100 sec). I hope this is helpful to somebody. Please feel free to ask questions if you have any. At this point, while many aspects (e.g., using the intel graphics as well) do not work, all the major parts are fine and I am enjoying the Macbook.

---

### Post by vic.jang on 2013-11-03
I still cannot boot into Linux.
I tried the following few methods:

1. Use Disk Utility to create 100GB Free Space, and reboot with Option key held to boot using a USB stick with 13.10 in it.
installation was fine, but when restarted computer and selected Ubuntu in Grub, the screen would stay purple and never proceed.

2. Create 100G Free Space, installed Refind, reboot, and select to boot from USB, and installed Ubuntu(with Grub)
the first reboot after installation, it went into Ubuntu successfully.
However, if I restart again, it would hang at the purple screen.

3. Followed the tutorial kjano posted, and it went into verbose mode after installation during boot, never finished.
(this is the first method I tried. And this tutorial is actually for last year's model btw..)


do you guys have any idea what I might have done wrong?
thanks :-/

---

### Post by kjano on 2013-11-03
Hi,

so here is what I did: I freed up space with the Mac DiskUtility. I created a USB boot stick from within Mac OS (you cannot just do it the regular way). I pressed alt during reboot to boot the stick. I used the live mode and then clicked on install 13.10. I created a ext4 partition (mounted as /) and a swap partition, in my case an EFI partition was already there so I did not had to create it. During the installation it found my wifi card and thus was able to get all updates. At times the installation was freezing so you have to be patient. After that I added noncq to the grub conf. Next, I used boot repair to switch to grub-efi (not bios emulation) and that was it. Are you sure you are really using grub-efi and not just the bios compatibility mode?

---

### Post by bmerlover on 2013-11-03
> **vic.jang said:**
> I still cannot boot into Linux.
I tried the following few methods:

1. Use Disk Utility to create 100GB Free Space, and reboot with Option key held to boot using a USB stick with 13.10 in it.
installation was fine, but when restarted computer and selected Ubuntu in Grub, the screen would stay purple and never proceed.

2. Create 100G Free Space, installed Refind, reboot, and select to boot from USB, and installed Ubuntu(with Grub)
the first reboot after installation, it went into Ubuntu successfully.
However, if I restart again, it would hang at the purple screen.

3. Followed the tutorial kjano posted, and it went into verbose mode after installation during boot, never finished.
(this is the first method I tried. And this tutorial is actually for last year's model btw..)


do you guys have any idea what I might have done wrong?
thanks :-/


A general note: I don't think the intel iris pro 5200 is ready for Ubuntu. I originally purchased the standard 15" Retina and the screen would show up with lines all over the place. Horrible resolution.

Now I got the MBPr with the Nvidia card and that one seems to work fine. Although no sound like everyone else is what I've noticed.

To answer your question, I tried everything 100 times and now I know what to do, I had the same exact problem as you.

I followed this guide: [http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html) (Please use this as reference, but I will try to explain the part that is relevant to you)

I installed Ubuntu 13.10 with GRUB but after I would select Ubuntu, it would just stay on the purple screen and looks like the GPU would just get really hot, so this is the solution again taken from the link above:

Load a live USB stick and select the try ubuntu option
Go to the partition where you installed Ubuntu (in my case /dev/sda5)
You should see it as one of the hard drives in the task bar in the left or you can mount it through the terminal.
Inside the /dev/sda5, go to your boot directory and copy/paste the **vmlinuz-3.11.0-12-generic** and** initrd.img-3.11.0-12-generic** files to a usb stick or upload it online.
Type 

**sudo blkid /dev/sda5  **

in the terminal and store that long list of characters next to /dev/sda5 in my case because you will need to type it in refind.conf in MacOS X later.

For example: As an example if you see *27c9a93d-6cc8-2395-9a97-d105353e5c07 as your number next to sda5, then write that down* (every computer has a unique number)

Once you have those 2 files and the hex characters, reboot into Mac OS X

Now create a folder called ubuntu in the /EFI directory, store the 2 files (vmlinuz... and initrd....) to that folder

Open up the refind.conf file (i used "sudo nano refind.conf") and go to the section where you see the  "menuentry Linux {"

  menuentry Linux {  
     icon EFI/refind/icons/os_ubuntu.icns  
     volume **5**:  
     loader **EFI/ubuntu/vmlinuz-3.11.0-12-generic  **
     initrd **EFI/ubuntu/initrd.img-3.11.0-12-generic  **
     options "ro root=UUID=***27c9a93d-6cc8-2395-9a97-d105353e5c07***"  
    **#**disabled  
} 

Now edit that part of the file to point it to your files which I have done above if you paste the files in /EFI/ubuntu
Volume must point to the sdaX you installed it on, in my case sda5
and type in your hexadecimal characters after UUID=
Comment out disabled with a #

Save and close the file

Note: if you use the nano command to edit refind.conf then
          ctrl+o is to save the file
          ctrl+x is to exit


Restart from OS X and you will see a new Penguin during boot, mine was the one all the way at the end. Now click on that penguin and it should load Ubuntu, although once in a while it takes some time to load but it does work.
Another thing I noticed is that once in a while it gets laggy.

Hope this helps

---

### Post by bmerlover on 2013-11-03
> **kjano said:**
> Frankly speaking I had a lot of work to do and thus was very lazy with the installation. All I did was installing Refind, using Mac's DiskUtility to free 450GB on the SSD, create an bootable USB stick under OSX, and then simply boot it. I did not had to change anyting or play with any config files.

I used an external ALFA USB wifi card during installation but after that the internal Macbook wifi is working just great. Sound is not working and I can neither restart the machine nor put it to sleep. Shutting it down is the only option. For some reason booting takes nearly a minute.

I am also only using the Nvidia card which is not good for the battery. I tried to install Bumblebee but this turns out to be a very bad idea and I ended up removing it for like 30 minutes running into multiple errors. Now I am using Nvidia's driver in version 319. 

If anybody would know how to completely disable the external card and just use the Intel card, that would be great. Of course I want to use a mixed mode in the future (that is why I got the card) but for the moment I prefer 9 hours of battery over the ~5:30 that I would be getting with the Nvidia card running all the time (according to the power notification in Gnome). 

I installed Gnome and increased the font scaling for the Retina display -- works great. 

**Offtopic:** I hate the fact that I had to buy a Macbook Pro but it has the best hardware, best build quality, and since last weak is also the  cheapest slim laptop on the market. Very sad... I initially wanted the Lenovo T440S or Yoga 2 Pro but the Yoga cannot show the color yellow (no kidding) and the T440s has a delivery time of nearly 4 weeks, the (by far) weaker hardware, and costs more....


Hi,

What commands did you type or where did you go to install nvidias 319 drivers? I've had way too many problems in the past with installing nvidia drivers on my previous pc's with it just showing a blank screen and having to reinstall ubuntu again.

I'm assuming 319 drivers work for your 15" haswell MBPr?

If so, can you tell me what I need to do to install it? I don't want to guess and reinstall ubuntu cause of it.

Thank you.

---

### Post by bmerlover on 2013-11-03
Is anyone else experiencing the computer freezing for a few seconds intermittently?

It looks like every 10 to 15 mins or so my computer freezes for about 10 seconds then it comes back.

Is there a fix for this? Does it have anything to do with me using the default graphics driver that was installed during ubuntu's installation?

---

### Post by kjano on 2013-11-03
> **bmerlover said:**
> Is anyone else experiencing the computer freezing for a few seconds intermittently?

It looks like every 10 to 15 mins or so my computer freezes for about 10 seconds then it comes back.

Is there a fix for this? Does it have anything to do with me using the default graphics driver that was installed during ubuntu's installation?

You have to add libata.force=noncq to your grub configuration file in etc to fix this.

---

### Post by kjano on 2013-11-03
@bmerlover: I followed this long blog post as well but you would have to redo this for every new kernel update. Thus, I removed ubuntu again and  just went for the super simple grub-efi install with the boot repair tool (see above). You do not even need refind. You can see that others did so as well by reading the comment section of the blog post. 

Nvidia: This will not work with the EFI install -- you will just get a black screen. I used the nvidia drivers when I did the grub bios mode install. In fact, there are many reasons why the bios compatibility mode may be the better way to go as the nvidia drivers give you clearly more battery runtime and the system does not run hot. On the grub bios mode my GPU temperature was about 55-60 while browsing, watching videos, and using pdflatex. Now with the EFI install and the open source drivers I get 70-75 degree celsius on my GPU doing the same tasks and the battery runs only for about 4 hours will full display brightness and regular workload. Unfortunately switching graphic cards only works in the EFI mode but as this feature does not work at all for now, it probably does not make a difference. Installing Bumblebee did not work in bios mode nor EFI mode (in my case).

---

### Post by kjano on 2013-11-04
Hmm, any idea how to get a projector connected (or any external VGA device)? I got a mini Displayport to VGA adapter from Apple a few days ago but putting it into the Thunderbolt port freezes Ubuntu?

---

### Post by bmerlover on 2013-11-04
> **kjano said:**
> @bmerlover: I followed this long blog post as well but you would have to redo this for every new kernel update. Thus, I removed ubuntu again and  just went for the super simple grub-efi install with the boot repair tool (see above). You do not even need refind. You can see that others did so as well by reading the comment section of the blog post. 

Nvidia: This will not work with the EFI install -- you will just get a black screen. I used the nvidia drivers when I did the grub bios mode install. In fact, there are many reasons why the bios compatibility mode may be the better way to go as the nvidia drivers give you clearly more battery runtime and the system does not run hot. On the grub bios mode my GPU temperature was about 55-60 while browsing, watching videos, and using pdflatex. Now with the EFI install and the open source drivers I get 70-75 degree celsius on my GPU doing the same tasks and the battery runs only for about 4 hours will full display brightness and regular workload. Unfortunately switching graphic cards only works in the EFI mode but as this feature does not work at all for now, it probably does not make a difference. Installing Bumblebee did not work in bios mode nor EFI mode (in my case).

I installed the boot repair tool and clicked on the recommended fix but that doesn't seem to help. What options do I need to select to actually do a grub-efi install? I'm assuming I have to go into the advanced options correct?

I also added "libata.force=noncq" without the quotes at the end of the file after #GRUB_INIT_TUNE="480 4401 1" in GRUB configuration file. I opened the GRUB config file from "Edit GRUB configuration file" from boot-loader just to be safe that was the one I was updating. After I added those lines at the end and typed in sudo update-grub in the terminal, I got some sort of error.

Can you please be more specific on how to do the above 2 steps (installing grub-efi and where exactly in the file to add libata.force=noncq? Thank you

---

### Post by vic.jang on 2013-11-04
bmerlover,

I have the same model as yours.
That tutorial is the first thing I tried and it wasn't able to boot. (repeatedly trying to kill some process but kept failing)
And then I found this post and started trying other things.

Yesterday I searched a bit more about hanging at purple screen and found that it's not unique to the Haswell model.
I saw this post [http://askubuntu.com/questions/363234/purple-screen-on-boot-imac](http://askubuntu.com/questions/363234/purple-screen-on-boot-imac)
and were able to successfully boot adding the option "nolapic".
I installed 13.10 using Refind, with grub.

Btw, my wifi doesn't work for some reason...


> **bmerlover said:**
> A general note: I don't think the intel iris pro 5200 is ready for Ubuntu. I originally purchased the standard 15" Retina and the screen would show up with lines all over the place. Horrible resolution.

Now I got the MBPr with the Nvidia card and that one seems to work fine. Although no sound like everyone else is what I've noticed.

To answer your question, I tried everything 100 times and now I know what to do, I had the same exact problem as you.

I followed this guide: [http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html) (Please use this as reference, but I will try to explain the part that is relevant to you)

(neglected)

Hope this helps

---

### Post by vic.jang on 2013-11-04
The temperature of the machine feels very high...

Does this look normal or should I worry?

[IMG]http://i.imgur.com/QTVpmNp.png[/IMG]

---

### Post by kjano on 2013-11-04
**Temperature**, **graphics** (!) and a lot of other details: Kernel 3.12 was just released and it addresses exactly those issues as well as better Thunderbolt [not for Mac :-(] and Haswell support. It clearly saves battery and keeps the temperature lower in my case (MacBookPro11,3). Just takes 3 min to install:

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb 

sudo dpkg -i linux-headers-3.12*.deb linux-image-3.12*.deb

(thanks to [http://linuxg.net/how-to-install-kernel-3-12-on-ubuntu-linux-mint-pear-os-elementary-os-debian-wheezy-and-kwheezy/](http://linuxg.net/how-to-install-kernel-3-12-on-ubuntu-linux-mint-pear-os-elementary-os-debian-wheezy-and-kwheezy/)).

Btw, 70-90 degree Celsius is abolutely fine for the CPU, just dont get it up to 105. Btw, I would suggest xsensors instead of psensor, there is no real need to monitor this constanty.

**Conan**? Can you help me with the external display as you got **Thunderbolt** working?

---

### Post by conan.jen on 2013-11-04
> **kjano said:**
> **Temperature**, **graphics** (!) and a lot of other details: Kernel 3.12 was just released and it addresses exactly those issues as well as better Thunderbolt [not for Mac :-(] and Haswell support. It clearly saves battery and keeps the temperature lower in my case (MacBookPro11,3). Just takes 3 min to install:

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb

wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb 

sudo dpkg -i linux-headers-3.12*.deb linux-image-3.12*.deb

(thanks to [http://linuxg.net/how-to-install-kernel-3-12-on-ubuntu-linux-mint-pear-os-elementary-os-debian-wheezy-and-kwheezy/](http://linuxg.net/how-to-install-kernel-3-12-on-ubuntu-linux-mint-pear-os-elementary-os-debian-wheezy-and-kwheezy/)).

Btw, 70-90 degree Celsius is abolutely fine for the CPU, just dont get it up to 105. Btw, I would suggest xsensors instead of psensor, there is no real need to monitor this constanty.

**Conan**? Can you help me with the external display as you got **Thunderbolt** working?

Hm... I haven't tried to do minidisplayport => vga. I've only attempted to do minidisplayport => minidisplayport / thunderbolt. In my case, it just works when you plug it in. Can you elaborate on what happens when you plug in the monitor? I'll see if I can find a minidisplayport => vga adapter at work today to test against.

---

### Post by kjano on 2013-11-04
I am at the airport right now, will check logs later. I often have to connect to a projector via VGA. unfortunately gnome freezes as soon as I put the mini display port to VGA adapter into one of the two thunderbolt ports. this happens no matter whether a VGA cable and device is attached or just the adapter. if I shutdown the macbook pro 11.3  and reboot with the adapter already attached it will boot to a black screen with blinking cursor but I will not be able to go to another terminal and have to shutdown the machine. maybe an issue with the  open source nvidia driver?

---

### Post by bmerlover on 2013-11-05
First of all, thank you kjano and vic.jang

You were right, you don't need refind. When I boot the computer, I just hold the alt option and select "windows" which loads ubuntu grub and I select ubuntu from that menu and ubuntu loads.

I found this site based on the libata.force=noncq , [http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade](http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade)

This a summary of what I did to fix the install.

Removed refind (optional) from OS X
Temporary solution to login to Ubuntu from GRUB (fixes purple screen freeze after selecting Ubuntu):
    Logged in Ubuntu by modifying the file directly from grub by pressing 'e' while 'ubuntu' was highlighted and added "nolapic" next to "quiet splash".
    So it looked like this " quiet splash nolapic " 
or you can just load the live usb stick and modify grub directly.

Once you get into Ubuntu, this is the permanent fix:
Open up the terminal and type "sudo gedit /etc/default/grub"
Type your password

When the GRUB configuration file opens, look for the line:
GRUB_CMDLINE_LINUX=""
and add libata.force=noncq nolapic inside the quotes
so it should look like: 

GRUB_CMDLINE_LINUX="libata.force=noncq nolapic"

Save and close the file

Type in terminal: sudo update-grub

Now your Ubuntu GRUB configuration should be fixed, next time you turn on the computer, hold "alt" during boot and select "Windows" then select "Ubuntu" and it should load fine and not freeze intermittently.

Hope this helps others that have the same problem, again thanks to kjano and vic.jang

---

### Post by bmerlover on 2013-11-05
vic.jang

The wifi drivers worked for me out of the box. When I load the live usb stick and click on try ubuntu or install ubuntu. Check to install the 3rd party software on the bottom. On the next page, if you wait a few seconds, broadcom drivers will get loaded and it will show you the nearby networks. At that point, my wifi drivers work. Hope this helps.

---

### Post by vic.jang on 2013-11-05
bmerlover,
Thanks for the summary, that would help many users like us save a lot of time.


I still have two questions though.


1. Doing it your way, are you booting using grub-efi like kjano said?
Or is it maybe still grub in bios compatibility mode? (Is there even such thing? I never actually understand this efi/bios thing)


2. What is the advantage of using grub only over Refind+grub?
I read some post and saw something related to Intel / nvidia graphics.
but again I don't know the answer and don't really understand why efi/bios would affect those...


kjano, can you help clarify these?
I guess you might know the answers, cuz you know much more about this than I do :P


> **bmerlover said:**
> First of all, thank you kjano and vic.jang

You were right, you don't need refind. When I boot the computer, I just hold the alt option and select "windows" which loads ubuntu grub and I select ubuntu from that menu and ubuntu loads.

I found this site based on the libata.force=noncq , [http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade](http://www.howtoeverything.net/linux/hardware/ubuntu-freeze-issue-after-ssd-upgrade)

This a summary of what I did to fix the install.

Removed refind (optional) from OS X
Temporary solution to login to Ubuntu from GRUB (fixes purple screen freeze after selecting Ubuntu):
    Logged in Ubuntu by modifying the file directly from grub by pressing 'e' while 'ubuntu' was highlighted and added "nolapic" next to "quiet splash".
    So it looked like this " quiet splash nolapic " 
or you can just load the live usb stick and modify grub directly.

Once you get into Ubuntu, this is the permanent fix:
Open up the terminal and type "sudo gedit /etc/default/grub"
Type your password

When the GRUB configuration file opens, look for the line:
GRUB_CMDLINE_LINUX=""
and add libata.force=noncq nolapic inside the quotes
so it should look like: 

GRUB_CMDLINE_LINUX="libata.force=noncq nolapic"

Save and close the file

Type in terminal: sudo update-grub

Now your Ubuntu GRUB configuration should be fixed, next time you turn on the computer, hold "alt" during boot and select "Windows" then select "Ubuntu" and it should load fine and not freeze intermittently.

Hope this helps others that have the same problem, again thanks to kjano and vic.jang

---

### Post by kjano on 2013-11-05
FYI: this is supposed to fix the sound: [https://bugs.launchpad.net/ubuntu/+bug/1247475](https://bugs.launchpad.net/ubuntu/+bug/1247475) but it does not work for me.

---

### Post by conan.jen on 2013-11-05
> **kjano said:**
> FYI: this is supposed to fix the sound: [https://bugs.launchpad.net/ubuntu/+bug/1247475](https://bugs.launchpad.net/ubuntu/+bug/1247475) but it does not work for me.

Huh. I wonder how much of this stems from the discrete gpu vs integrated. Just tried this and it fixed my speakers, but I'm assuming it doesn't work on your end because of the hardware discrepancy.

---

### Post by kjano on 2013-11-05
yes, that may well be the case. So you have the integrated graphics. anyway, great that your speakers work now.

---

### Post by lichun1668 on 2013-11-06
Thank you Conan for your lead!  I have successfully installed Ubuntu 13.10 on a MacBookPro11,1 (Retina, 13-inch, Late 2013).  The installation went smoothly but I could not boot into Ubuntu.  After hours of trying, I finally figured it out.  The following are what I did (same steps as Conan's except Step 5):

1. Download 13.10 NON-MAC iso and put it onto flash drive via Startup Disk Creator (or unetbootin).
2. Boot up with OPTION key held, and select the EFI icon to boot the flash drive.
3. Enter live mode (i.e. "Try Ubuntu").
4. Install.  Wipe out existing partitions and create new ones: i) 200MiB efi, bootable, mounted to /boot/efi; ii) 20GiB ext4, mounted to /; iii) 8GiB swap; iv) rest ext4, mounted to /home.
5. After installation, fix the EFI boot order (The EFI BootOrder was 0080 but ubuntu was listed as Boot0000*).

sudo apt-get install efibootmgr
sudo efibootmgr  ## display boot order information
sudo efibootmgr -o 0  ## set boot order to 0000 first
sudo shutdown -r now

6. Edit grub configuration file /etc/default/grub (one line): GRUB_CMDLINE_LINUX="libata.force=noncq" and then 'sudo update-grub'
7. Install kernel 3.12. Thanks, kjano!
8. Fix speakers (following [https://bugs.launchpad.net/ubuntu/+bug/1247475](https://bugs.launchpad.net/ubuntu/+bug/1247475)). Thanks, kjano!

(There is no need of rEFIt or rEFInd or boot-repair.  I wasted hours trying various options of boot-repair to no avail.)

---

### Post by diggory-hardy on 2013-11-06
Can anyone comment on whether standby (suspend-to-RAM) works on any of the new Pros?

---

### Post by lichun1668 on 2013-11-06
> **diggory-hardy said:**
> Can anyone comment on whether standby (suspend-to-RAM) works on any of the new Pros?

Mine does not  work. Mine suspends immediately when lid is closed. When I open the lid, the keyboard light is on immediately, but sometimes it took about 10 seconds for the screen to light up to show to the password/unlock interface.  Sometimes the screen is never back and I have to do hard shutdown by pressing the power button for a few seconds.

---

### Post by bmerlover on 2013-11-06
> **vic.jang said:**
> bmerlover,
Thanks for the summary, that would help many users like us save a lot of time.


I still have two questions though.


1. Doing it your way, are you booting using grub-efi like kjano said?
Or is it maybe still grub in bios compatibility mode? (Is there even such thing? I never actually understand this efi/bios thing)


2. What is the advantage of using grub only over Refind+grub?
I read some post and saw something related to Intel / nvidia graphics.
but again I don't know the answer and don't really understand why efi/bios would affect those...


kjano, can you help clarify these?
I guess you might know the answers, cuz you know much more about this than I do :P


1. I don't know which one I am using, I installed ubuntu and the GRUB that came is the one I used. I didn't actually do a grub-efi install so I'm assuming I'm using the bios compatibility mode. Please correct me if I'm wrong. I just deleted Refind from OS X and edited the grub configuration file to add the nolapic and the libata.force=noncq, and it started working.

2. From what I see, you don't really need Refind because you can just hold the alt option when you're turning on your computer if you want to boot into Ubuntu. So from my perspective, it's one less thing installed and one less thing to worry about.

General thought, it looks like some of the people are completely wiping Mac OS X and just installing Ubuntu directly. I actually need to use both operating systems so I'm afraid to touch that 200MB EFI partition that came by default from OS X. So it looks like people are using EFI mode cause I guess Macs don't use BIOS, instead they use EFI.

Some of the other users will answer your question better, I'm just guessing. I've always had a PC and installed Ubuntu with no problems whatsoever (besides the nvidia drivers and only on laptops that had both integrated and dedicated graphics), so I've never really needed to search so much just to get Ubuntu to install.

---

### Post by conan.jen on 2013-11-06
For those of you that aren't sure if you've installed / are running Ubuntu in EFI mode: check to see that /sys/firmware/efi exists. In BIOS mode it doesn't exist.

---

### Post by eindgebruiker on 2013-11-06
Thanks to all here for guidance to install Ubuntu on my MBP. Here is some experience with a MBP 11,3 (with discrete graphics). I have:
- dual boot
- Refind
- Ubuntu 13.10 non-Mac
- grub-efi
- 3.12 kernel
- nouveau

- Neither VGA, DVI nor ethernet work when hot-plugged. Ethernet and DVI do work when plugged at boot time, VGA does not work at all (screen freezes).

- MacOSX does not start from grub. I have two MacOSX entries. The 32-bit entry says "Mach-0 doesn't contain suitable 32-bit architecture", the 64-bit entry will result in a purple screen.

- When starting Ubuntu, just after grub I see "i8042: No controller found"

Does anyone know how to change the resolution of the login screen?

---

### Post by vic.jang on 2013-11-06
eindgebruiker,

How did you get grub-efi installed?
I managed to switch from grub-pc(bios mode) to grub-efi by using boot-repair after ubuntu is installed.
But I wonder if there is a more elegant way, maybe during the installation process?

Thanks.

---

### Post by lichun1668 on 2013-11-06
[FONT=arial]There is a  loud chime sound whenever the laptop boots. The setting for this is in the NVRAM on motherboard and it can be modified using a MacOS program nvram. Now that I have wiped out MacOS, I found this a very annoying issue. Fortunately I found a webpage [https://plus.google.com/111049168280159033135/posts/6GAix9cuyiq](https://plus.google.com/111049168280159033135/posts/6GAix9cuyiq)

The solution is to boot into an EFI shell and modify EFI variables in that shell.  To install the shell:

wget [https://edk2.svn.sourceforge.net/svnroot/edk2/trunk/edk2/EdkShellBinPkg/FullShell/X64/Shell_Full.efi](https://edk2.svn.sourceforge.net/svnroot/edk2/trunk/edk2/EdkShellBinPkg/FullShell/X64/Shell_Full.efi)
sudo cp Shell_Full.efi /boot/efi/EFI/
[FONT=arial]## Create a boot record for the EFI shell
[/FONT]sudo efibootmgr -c -l \\EFI\\Shell_Full.efi -L EFIShell
[FONT=arial]                                          ## Find boot number (You can also assign a boot number.)
[/FONT]sudo efibootmgr
[FONT=arial]                                     ## Set Nextboot to the EFI Shell boot number (1 in my case)
[/FONT]sudo efibootmgr -n 1

Restart to boot into the EFI shell.  Do the following to modify the setting for EFI variable SystemAudioVolume:

[FONT=arial]                                  ## Go into the EFI partition
[/FONT]fs0:
[FONT=arial]## Save variable value to a file called volume
[/FONT]dmpstore -s volume SystemAudioVolume
[FONT=arial]                        ## Edit the file to change the very last byte to "80", save and exit
[/FONT]hexedit volume
[FONT=arial]  ## Save the value back to the EFI variable
[/FONT]dmpstore -l volume SystemAudioVolume
[FONT=arial]                                  ## Reboot
[/FONT]exit

[/FONT]

---

### Post by kjano on 2013-11-06
> **eindgebruiker said:**
> 

- Neither VGA, DVI nor ethernet work when hot-plugged. Ethernet and DVI do work when plugged at boot time, VGA does not work at all (screen freezes).

- When starting Ubuntu, just after grub I see "i8042: No controller found"



I have the 11,3 as well. I am also getting the no controller message (which just points to a missing PS2 controller :-)) and the VGA freeze. Have you tested the HDMI interface? I really need to get a VGA projector connected. Hopefully at least via the HDMI. I am still trying to get the speakers working and also suspend mode.

---

### Post by eindgebruiker on 2013-11-07
> **vic.jang said:**
> eindgebruiker,

How did you get grub-efi installed?
I managed to switch from grub-pc(bios mode) to grub-efi by using boot-repair after ubuntu is installed.
But I wonder if there is a more elegant way, maybe during the installation process?

Thanks.

In MacOSX I decreased the OSX partition size (without any further partitioning) and installed Refind.
Then I booted into Ubuntu from USB and clicked "Install Ubuntu", and chose "Install alongside MacOSX".
That's all.
Now I have two options in Refind (besides MacOSX): EFI/ubuntu/grubx64.efi and EFI/ubuntu/shimx64.efi. I don't know if there's any difference, they both boot into Ubuntu in efi mode.

@kjano: I just tried HDMI. Works both at boot time and with hot pluging.

---

### Post by vic.jang on 2013-11-07
Does anyone know how to check which graphics chip is being used?
As you know, there are Iris Pro and Nvidia 750M.
I wonder which one is being used in ubuntu.

---

### Post by eindgebruiker on 2013-11-08
Check "Settings > Details".
Mine says: "Graphics: Gallium 0.4 on NVE7", which is the Nvidia.

Under "Software & Updates > Additional Drivers" I just see the wifi driver, no graphics. On my old MBP the graphics driver is displayed there as well, and I can choose several nividia drivers. Why is that? Does it have something to do with the 3.12 kernel? How can I install the nvidia driver on my new MBP?

---

### Post by kjano on 2013-11-08
If you use EFI you will not be able to use the nvidia drivers (at least not 304, 310, and 319). Theoretically kernel 3.12 makes sure the unused intel card is powered down and also should make switching between them simpler. To do so you probably have to install Bumblebee (without the nvidia drivers!): sudo apt-get install --no-install-recommends bumblebee. I tried that with kernel 3.11 and it resulted in a black screen so that I had to remove the driver again. I have not tested it with 3.12 so be careful. In fact, I am not even sure what the relation between the modifications made in 3.12 and bumblebee is [1]. Anyway 3.12 will save you about 5W. I hope this helps.

[1] [http://4x.reddit.com/r/linux/comments/1q6dan/do_i_still_need_bumblebee_with_kernel_312/](http://4x.reddit.com/r/linux/comments/1q6dan/do_i_still_need_bumblebee_with_kernel_312/)

Just as update: it looks like they are still working on the speakers for 11.3, see [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401)

---

### Post by premal-j-shah on 2013-11-09
> **kjano said:**
> You have to add libata.force=noncq to your grub configuration file in etc to fix this.

Can you explain how to  to update grub configuration?

Is it in 
1) /etc/default/grub 
2) one of these in /etc/grub.d - 00_header  05_debian_theme  10_linux  20_linux_xen  20_memtest86+  30_os-prober  30_uefi-firmware  40_custom  41_custom

---

### Post by kjano on 2013-11-09
**Speakers**: fixed now also for Macbook Pro 11.3 using mba6 setting (see: [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401))

**VGA/external displays **: HDMI to HDMI works, HDMI to VGA requires and active adapter (that uses USB). Was anybody successful with an passive adapter as well?

**iSight/Webcam**: still not working

**Suspend**: still not working

---

### Post by kjano on 2013-11-09
> **premal-j-shah said:**
> Can you explain how to  to update grub configuration?

Is it in 
1) /etc/default/grub 
2) one of these in /etc/grub.d - 00_header  05_debian_theme  10_linux  20_linux_xen  20_memtest86+  30_os-prober  30_uefi-firmware  40_custom  41_custom

1.) sudo nano /etc/default/grub 
2.) Change GRUB_CMDLINE_LINUX_DEFAULT....  to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=1:noncq" 
3.) sudo update-grub
4.) Restart

Let me know if you need help.

---

### Post by patrick.ling on 2013-11-11
Could you please explain how to apply the patch?

Thanks.

---

### Post by Quackers on 2013-11-11
> **patrick.ling said:**
> Could you please explain how to apply the patch?

Thanks.
Edit the file as above.
Save the file.
In a terminal run ```
sudo update-grub
``` and it's done.

---

### Post by kjano on 2013-11-11
Some good news. Nvidia-331 works with kernel 3.12 and EFI. I have problems getting the scaled resolution working with nvidia-settings but other than that the new driver works fine.

---

### Post by lichun1668 on 2013-11-12
Except for the network,  suspension has been working my MacBookPro 11,1 and everything comes back after resume.  I found a way to make network come back as well.  All I did was to create a file under /etc/pm/sleep.d/

 $ ll /etc/pm/sleep.d/99_myfix
-rwxr-xr-x 1 root root 186 Nov 12 21:44 /etc/pm/sleep.d/99_myfix*

$ cat /etc/pm/sleep.d/99_myfix
#!/bin/sh
## Network after resume
case "$1" in
      resume|thaw)
             service network-manager stop
             rm /var/lib/NetworkManager/NetworkManager.state
             service network-manager start
             ;;
esac

---

### Post by diggory-hardy on 2013-11-13
> **kjano said:**
> **Speakers**: fixed now also for Macbook Pro 11.3 using mba6 setting (see: [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401))

**VGA/external displays **: HDMI to HDMI works, HDMI to VGA requires and active adapter (that uses USB). Was anybody successful with an passive adapter as well?

**iSight/Webcam**: still not working

**Suspend**: still not working

Thanks for the update. Did you try a mini-DP to VGA adaptor? As I understand it the thunderbolt ports are also mini DisplayPort ports.

---

### Post by ckankiewicz on 2013-11-13
> **kjano said:**
> Some good news. Nvidia-331 works with kernel 3.12 and EFI. I have problems getting the scaled resolution working with nvidia-settings but other than that the new driver works fine.

Do you have multiple resolution choices with the 331 drivers or are you stuck with 2880x1800?

---

### Post by conan.jen on 2013-11-13
> **lichun1668 said:**
> Except for the network,  suspension has been working my MacBookPro 11,1 and everything comes back after resume.  I found a way to make network come back as well.  All I did was to create a file under /etc/pm/sleep.d/

 $ ll /etc/pm/sleep.d/99_myfix
-rwxr-xr-x 1 root root 186 Nov 12 21:44 /etc/pm/sleep.d/99_myfix*

$ cat /etc/pm/sleep.d/99_myfix
#!/bin/sh
## Network after resume
case "$1" in
      resume|thaw)
             service network-manager stop
             rm /var/lib/NetworkManager/NetworkManager.state
             service network-manager start
             ;;
esac

Are you running in bios or efi? Suspend doesn't seem to work for me, it resumes to an entirely black (but backlit) screen, and will not respond to keyboard input.

---

### Post by lichun1668 on 2013-11-13
> **conan.jen said:**
> Are you running in bios or efi? Suspend doesn't seem to work for me, it resumes to an entirely black (but backlit) screen, and will not respond to keyboard input.

I am runing in EFI.  Resuming from suspend takes a few (but less than 10) seconds.  (Suspend does not bring the sound back, which I am still researching how to get it back.)

---

### Post by Rockmaninoff on 2013-11-13
Hi all, I've successfully got Ubuntu booting on an 11,3 MacBook Pro.  As expected, speakers don't work.  I haven't tried the webcam or suspend yet.  My issue is that my Wi-Fi is not working.  I've seen reports of it "just working" via the Live CD, but I've got nothing.  I do have a Thunderbolt-to-Ethernet adapter, and it's picking up a wired connection OK.

Any advice?  Thanks!

---

### Post by lichun1668 on 2013-11-13
lspci shows my Macbook Pro 11,1 has BCM4360 wireless chipset.  Installing Broadcom's official driver package bcmwl-kernel-source works for me.

---

### Post by otognan on 2013-11-13
Here is a compilation of instructions that worked out for my MacBook Pro 11,3. Thanks everybody for all the pieces! (I spend quite some time with ubuntu 12.04, nolapic and REFind, but I don't really like using only one processor (lscpu) that nolapic forces you to do:)

  
[LIST]
[*]Download Ubuntu 13.10 non-mac iso and put it onto flash drive ([http://blog.lewan.com/2012/02/10/making-a-bootable-usb-stick-on-an-apple-mac-os-x-from-an-iso](http://blog.lewan.com/2012/02/10/making-a-bootable-usb-stick-on-an-apple-mac-os-x-from-an-iso)) 
[*]Free up a good amount of space on your hard drive, and start disk  utility. Make a new partition and set it to "Free Space", this will be  the partition on which ubuntu will be installed. 
[*]Boot up with OPTION key held, and select the EFI icon to boot the  flash drive. If you have multiple EFI icons, select the first one.  Enter live mode (i.e. "Try Ubuntu"). 
[*]On the desktop click "Install Ubuntu"-> "Alongside with MacOS" and follow the installation  steps, do not install updates to save time. !!Do not restart after  installation!! 
[*]After installation, fix the EFI boot order (The EFI BootOrder was 0080 but ubuntu was listed as Boot0000*). 
[/LIST]
[INDENT] sudo apt-get install efibootmgr
sudo efibootmgr ## display boot order information
sudo efibootmgr -o 0 ## set boot order to 0000 first
sudo reboot

 [/INDENT]

[LIST]
[*](Optional: people recommend it and its related to SSD issues, but I  couldn't see the difference. I didn't experience any hanging or other  issues for 2 hours. After that I decided to do it just in case:) 
[/LIST]
[INDENT] sudo gedit /etc/default/grub
change GRUB_CMDLINE_LINUX="" to GRUB_CMDLINE_LINUX="libata.force=noncq" and save file
sudo update-grub
 [/INDENT]

[LIST]
[*]If WIFI doesn't work, go to "Software and Updates" -> "Additional Drivers" and propriotary enable WIFI card driver. 
[*]Update linux kernel to 3.12 (I'm still not sure what did I get with updating kernel from 11 to 12 - hardware seemed to work fine for few hours) 
[/LIST]
[INDENT] wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb
wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-image-3.12.0-031200-generic_3.12.0-031200.201311031935_amd64.deb
wget -c kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-saucy/linux-headers-3.12.0-031200_3.12.0-031200.201311031935_all.deb 
sudo dpkg -i linux-headers-3.12*.deb linux-image-3.12*.deb

[/INDENT]

[LIST]
[*] Fix GPU. I have MacBook Pro 11,3 with external Nvidia GPU. When I ran  glxgears or glmark2 (proper benchmarking for gpu), I got screwed up  rendering with black patches on the textures. So I decided to get the  most recent driver from NVidia instead of using opensource nouveau  drivers. The following steps helped me to fix rendering issues and bump  performance in glmark2 from 223 points (Nouveau) to 3851 (NVidia).  Prepare another laptop or printout these instructions as you GUI will  not going to work in between the steps.
[LIST]
[*]Go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and download Linux x86_64/AMD64/EM64T Latest Long Lived Branch version: 331.20. 
[*]Go to console mode (Fn+Ctrl+Alt+F1) and kill xserver: sudo service lightdm stop 
[*]chmod a+x NVIDIA-Linux-x86_64-331.20.run 
[*]sudo ./NVIDIA-Linux-x86_64-331.20.run 
[*]accept licence, ignore failing of pre_install script, agree to disable nouveau drivers by adding modprobe config, reboot 
[*]here you should not get to GUI and just see some failures from boot.  Press (Fn+Ctrl+Alt+F1) and run sudo ./NVIDIA-Linux-x86_64-331.20.run  again, finish the installation, reboot. 
[*]here you should get to GUI and be able to run glxgears 
[/LIST]
  
[*](Optional, but extremely useful on Retina  display) Increase borders  of your windows since its quite a challenge to  work with windows with huge  retina resolution. I also prefer to work  with lower resolution  1920x1200 to save my eyes: sudo nvidia-settings,  change resolution,  "Apply", "Save to XConfig". 
[/LIST]
 sudo gedit  /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml    In the  section starting <frame_geometry  name="frame_geometry_normal" change  left_width, right_width and  bottom_height from 1 to 8.
[LIST]
[*]After these steps you can boot to your MacOSX holding "option" during boot and choosing "EFI" disk to boot from. 
[*] Issues I couldn't fix:
[LIST]
[*]I haven't try to fix speakers do not work (apparently you can fix it with [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401) but I don't know how to apply patch to linux kernel:). I will be gratefull if someone post step-by-step instructions for dummies. 
[*]Changing display brightness with F1, F2 doesn't work 
[*]Suspend doesn't work (closing laptop leads to black screen) 
[/LIST]
    
[/LIST]

---

### Post by ckankiewicz on 2013-11-13
> **otognan said:**
> 

[LIST]
[*] Fix GPU. I have MacBook Pro 11,3 with external Nvidia GPU. When I ran  glxgears or glmark2 (proper benchmarking for gpu), I got screwed up  rendering with black patches on the textures. So I decided to get the  most recent driver from NVidia instead of using opensource nouveau  drivers. The following steps helped me to fix rendering issues and bump  performance in glmark2 from 223 points (Nouveau) to 3851 (NVidia).  Prepare another laptop or printout these instructions as you GUI will  not going to work in between the steps.
[LIST]
[*]Go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and download Linux x86_64/AMD64/EM64T Latest Long Lived Branch version: 331.20.
[*]Go to console mode (Fn+Ctrl+Alt+F1) and kill xserver: sudo service lightdm stop
[*]chmod a+x NVIDIA-Linux-x86_64-331.20.run
[*]sudo ./NVIDIA-Linux-x86_64-331.20.run
[*]accept licence, ignore failing of pre_install script, agree to disable nouveau drivers by adding modprobe config, reboot
[*]here you should not get to GUI and just see some failures from boot.  Press (Fn+Ctrl+Alt+F1) and run sudo ./NVIDIA-Linux-x86_64-331.20.run  again, finish the installation, reboot.
[*]here you should get to GUI and be able to run glxgears
[/LIST]
[/LIST]


This seems straight forward, but I can't seem to disable nouveau.  The nvidia install script offered to add the modprobe file (and it IS there) but even after reboot nouveau is still enabled.  Any ideas?

---

### Post by otognan on 2013-11-13
> **ckankiewicz said:**
> This seems straight forward, but I can't seem to disable nouveau.  The nvidia install script offered to add the modprobe file (and it IS there) but even after reboot nouveau is still enabled.  Any ideas?


Here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) you can find instructions how to remove nouveau completely. Do you have 11,3 laptop?

---

### Post by Rockmaninoff on 2013-11-13
Thanks all, the bcmwl-kernel-source install worked for me.  This page specifically helped: [http://askubuntu.com/questions/315950/drivers-for-wireless-card-asus-pce-ac66](http://askubuntu.com/questions/315950/drivers-for-wireless-card-asus-pce-ac66)

---

### Post by lichun1668 on 2013-11-13
Otognan: Thanks for sharing the information on border size.  I found changing the numbers to 4 is good enough to me.  Instead of changing the display resolution, you may want to set the text scaling factor.  This way you still get the crisp native resolution.  You can change the text scaling factor in dconf-editor or on the command line:

gsettings set org.gnome.desktop.interface text-scaling-factor 2

By the way, it is great to install Ubuntu the native EFI way without rEFIt or rEFInd, isn't it? ;)

---

### Post by otognan on 2013-11-13
> **lichun1668 said:**
> 
By the way, it is great to install Ubuntu the native EFI way without rEFIt or rEFInd, isn't it? ;)

Well, I would prefer to have fully working gpu support from Parallels or Virtual Box than rebooting my mac every now and then:)
I got dual boot working in 2 days, before I played with VB and Parallels for 5 days until I realized that there is no way to fix all GPU issues..

---

### Post by Rockmaninoff on 2013-11-14
otognan: I'm following your instructions because I didn't like only having one CPU available :P I'm at the point where I'm trying to enable the Wi-Fi driver.  Unfortunately my "Additional Drivers" section doesn't show anything there.  How did you get around that?

EDIT: After connecting an Ethernet-to-USB adapter and running a system update, I'm seeing "Broadcom Corporation" in the "Additional Drivers" section.  Enabling this and applying fixed my Wi-Fi issues.

---

### Post by lichun1668 on 2013-11-14
On MacbooPro 11,1, sound does not work after boot and after resume.  The former has been addressed by adding the following line to /etc/rc.local

hda-verb /dev/snd/hwC1D0 0x1 set_gpio_data 1

The latter can be solved by setting GPIO mask, direction, and data in /etc/pm/sleep.d/.  Here is my code (including the solution for network after resume, which I posted earlier in this thread):

$ ll /etc/pm/sleep.d/99_myfix
-rwxr-xr-x 1 root root 186 Nov 12 21:44 /etc/pm/sleep.d/99_myfix*

$ cat /etc/pm/sleep.d/99_myfix
#!/bin/sh
## Network after resume
case "$1" in
    resume|thaw)
        service network-manager stop
        rm /var/lib/NetworkManager/NetworkManager.state
        service network-manager start
                hda-verb /dev/snd/hwC1D0 0x1 set_gpio_mask 1
                sleep 1
                hda-verb /dev/snd/hwC1D0 0x1 set_gpio_direction 1
                sleep 1
                hda-verb /dev/snd/hwC1D0 0x1 set_gpio_data 1
        ;;
esac

The sleep commands are here because without them sometimes not all three are set.

---

### Post by kjano on 2013-11-14
> **ckankiewicz said:**
> Do you have multiple resolution choices with the 331 drivers or are you stuck with 2880x1800?

I was stuck with 2880x1800 because the scaling (via nvidia-settings) only ended up changing the viewport. Thus, I am back to the open source drivers.

---

### Post by kjano on 2013-11-14
> **Rockmaninoff said:**
> Hi all, I've successfully got Ubuntu booting on an 11,3 MacBook Pro.  As expected, speakers don't work.  I haven't tried the webcam or suspend yet.  My issue is that my Wi-Fi is not working.  I've seen reports of it "just working" via the Live CD, but I've got nothing.  I do have a Thunderbolt-to-Ethernet adapter, and it's picking up a wired connection OK.

Any advice?  Thanks!

Hmm, I have  11,3 and sound works. Have you tried the tips postet some days ago? 

Wifi should start working during the live cd installation. If not you can use another external wifi or ethernet and then install the bcmwl-kernel-source package by hand. 

**Have you updated to kernel 3.12 yet? Have you checked the saucy-backports repository?**

---

### Post by kjano on 2013-11-14
> **conan.jen said:**
> Are you running in bios or efi? Suspend doesn't seem to work for me, it resumes to an entirely black (but backlit) screen, and will not respond to keyboard input.

I am running a 11,3 on EFI and suspend does not work. It will suspend but not come back until I restart the machine completely. Which graphics drivers are you using?

Leaving suspend mode and the webcam aside everything works great now and I am getting more than 6 hours out of my battery using the open source nvidia driver. I would love to use the intel card as well. Was anybody here able to get it working? Also, I am using an active (usb powered) hdmi to vga adapter. Are there adapters that do not require usb and will work?

---

### Post by lichun1668 on 2013-11-14
Conan, kjano, and those who have the suspend problem: I wonder if the features you added to the kernel have caused the problem.  I saw Conan wrote earlier that he "added in a bunch of the kernel level powersaving options (whether  they helped or not, have not determined yet)."  For me, I only added libata=noncp.

---

### Post by conan.jen on 2013-11-14
For reference, here's the other options I'm running:

```
libata.force=noncq pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1 drm.vblankoffdelay=1
```

---

### Post by kjano on 2013-11-14
I am only using noncq. conan can you explain the other options?

---

### Post by kjano on 2013-11-14
lichun1668, conan: got it! stupid me :-). The suspend will take like 15 sec but the screen already turns black after like 2-3 sec and thus I did not wait long enough. My trick now is to have the keyboard light on. This way I can see whether the suspend process really finished (light goes off). Recovering works now but without network etc. I will try lichun1668's patches now. thanks guys! Only the webcam problem is left. Great to see that everybody can make some part work and together we can make it all function.

Some you may want to subscribe to this bug report: [https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/1247476](https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/1247476)

---

### Post by conan.jen on 2013-11-14
All of these were pulled from here: [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

The i915 options are related to the intel embedded video hardware, as is the drm.vblankoffdelay option. The PCIe ASPM may not be needed (internet seems to say that it got included after 12.04), but I've been to busy to test whether that is still the case. Ideally, when I have more time I'll get rid of all of the options, and rerun my power consumption tests to see what actually affects my battery (if any of them).

---

### Post by david.richards39 on 2013-11-16
Hey everyone, first off thanks for the guides, I've finally managed to get my Ubuntu install working (to an extent), however I still have a couple unresolved issues.
First issue: when trying to boot OS X from GRUB doesn't seem to work. I am selecting the "Mac OS X (64-bit) (on /dev/sda2)" option, and it gets stuck on a blank screen. Any ideas on how I can fix this? 
Additionally how can I change the GRUB boot order to boot to OS X by default (preferably with a reduced automatic launch time)? I am still able to boot to OS X, however it requires me holding the Option button on boot up which is a bit of an annoyance.

Second issue: I can't seem to get my WiFi working. My "Additional Drivers" section does not list anything, and I do not have any adapters to connect to the internet through Ethernet. Any suggestions?

---

### Post by lichun1668 on 2013-11-16
> **david.richards39 said:**
> Second issue: I can't seem to get my WiFi working. My "Additional Drivers" section does not list anything, and I do not have any adapters to connect to the internet through Ethernet. Any suggestions?

If  your Ubuntu is 64-bit 13.10, download the deb file 
[http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu1_amd64.deb)

and put it to a location that you can read from within Ubuntu.  Then inside Ubuntu, open a terminal and type

sudo dpkg -i <path/name of this deb file>

For other versions of Ubuntu, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and scroll down to search bcmwl-kernel-source for your version and on the next page to select your architecture (amd64 or i386).

---

### Post by lichun1668 on 2013-11-16
> **kjano said:**
> lichun1668, conan: got it! stupid me :-). The suspend will take like 15 sec but the screen already turns black after like 2-3 sec and thus I did not wait long enough. My trick now is to have the keyboard light on. This way I can see whether the suspend process really finished (light goes off). Recovering works now but without network etc. I will try lichun1668's patches now. thanks guys! Only the webcam problem is left. Great to see that everybody can make some part work and together we can make it all function.

Some you may want to subscribe to this bug report: [https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/1247476](https://bugs.launchpad.net/ubuntu/+source/isight-firmware-tools/+bug/1247476)

Thanks for reporting the problem with camera.  I hope the network after resume works for you now.

---

### Post by lichun1668 on 2013-11-16
> **conan.jen said:**
> All of these were pulled from here: [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

The i915 options are related to the intel embedded video hardware, as is the drm.vblankoffdelay option. The PCIe ASPM may not be needed (internet seems to say that it got included after 12.04), but I've been to busy to test whether that is still the case. Ideally, when I have more time I'll get rid of all of the options, and rerun my power consumption tests to see what actually affects my battery (if any of them).

Interesting tweaks.  But how much practical impact do these tweaks bring?  On my laptop, I installed laptop-mode-tools and set the screen and keyboard backlight to comfortably low values in /etc/rc.local:

## Brightness (max is 100)
echo 40 > /sys/class/backlight/acpi_video0/brightness
## Keyboard backlight brightness (max is 255)
echo 36 > /sys/class/leds/smc\:\:kbd_backlight/brightness

---

### Post by lichun1668 on 2013-11-16
I just went to an Apple Store to test out external displays. Ubuntu on my MBP11,1 can work with the older "cinema display" but not the new "thunderbolt display". It also works with an HDMI monitor. At work I already tested that it works with a DVI monitor through a minidisplay to DVI adaptor. All were hot plugged during testing.  Those of you who have a NVIDIA card (MBP11,3) might be able to drive a thunderbolt display through a nvidia driver.

Apple confuses people by using the same port interface for "thunderbolt" and "mini display" while thunderbolt is not full backward compatible with mini display. Thunderbolt monitors require "thunderbolt-enabled" sources and won't even show up if the computer is not thunderbolt enabled.

---

### Post by eindgebruiker on 2013-11-18
> **david.richards39 said:**
> First issue: when trying to boot OS X from GRUB doesn't seem to work. I am selecting the "Mac OS X (64-bit) (on /dev/sda2)" option, and it gets stuck on a blank screen. Any ideas on how I can fix this? 

I have the same problem, on an 11,3: booting OSX from GRUB doesn't work. Booting from Refind does work, though.

---

### Post by david.richards39 on 2013-11-18
> **eindgebruiker said:**
> I have the same problem, on an 11,3: booting OSX from GRUB doesn't work. Booting from Refind does work, though.

It seems that exiting GRUB (Esc, then entering exit command) will boot OSX properly.
Is there a way to boot to OSX by default, and then only boot to Ubuntu through a boot selection screen (via holding some key on startup)?

---

### Post by david.richards39 on 2013-11-18
As an aside, I'm looking into enabling OSX-like multi-touch gesture  support for the trackpad. I'm currently giving Touchegg a go, after not  being very impressed with xf86-input-mtrack (scrolling felt sloppy and  resting thumb was finicky).
Does anyone have any other suggestions?

---

### Post by Rockmaninoff on 2013-11-20
I run multiple monitors frequently from an 11,3.  Both off of DisplayPort to DVI adapters, which work great and are hot-pluggable.

Can I change things like text resolution and window borders _only_ for the laptop display?  As you can imagine, increasing the text scaling across the system creates poor results on external displays.

Thanks!

---

### Post by kjano on 2013-11-20
Was anybody able to get the internal intel graphics working and to disable the nvidia card?

---

### Post by lichun1668 on 2013-11-22
I had a chance to put my hands on another Macbook Pro 11,1 (i.e., 13-inch Late 2013 Haswell Retina) and this time I set it to dual boot without rEFIt or rEFInd, and to boot to MacOS by default.

After installation, the EFI boot order looks like this (output from 'sudo efibootmgr -v'):

```
BootOrder: 0080
Boot0000* ubuntu  HD(...)File(\EFI\ubuntu\shimx64.efi)
Boot0080*         ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)...HD(...)File(\System\Library\CoreServices\boot.efi)
BootFFFF*         ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)...HD(...)File(\System\Library\CoreServices\boot.efi)

```

This will let the laptop boot to MacOS.  To boot to grub, we need to fix the EFI boot order before reboot.

```

sudo apt-get install efibootmgr
sudo efibootmgr  ## check boot order information
sudo efibootmgr -o 0,80  ## set boot order to 0 first and 80 second
sudo shutdown -r now

```

Now the laptop boots to Grub and then Ubuntu by default.  On my laptop, there are 4 grub entries, two for MacOS, which don't work.

To boot into MacOS from grub, we can take advantage of the EFI boot order feature.  Make sure the EFI boot order is 0,80 (first ubuntu and second MacOS).  If the boot order has 80 as its first value, the laptop boots to MacOS.  If the boot order has 0 as its first value, the laptop boots to Grub, and when we exit grub, the laptop boots to the second in line, the MacOS.  So the trick is to exit grub.  (This is quite neat although it is not a real grub solution.)

Note that EFI boot order and Grub boot order are different things.

a) Edit /etc/grub.d/40_custom, add to the end:

```

menuentry "MacOS" {
     exit
}

```

b) Edit /etc/default/grub, change GRUB_DEFAULT=4.  This sets the default to the 5th entry, the one we just added.  The first one is 0.

c) 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

Then reboot to see if it works.

A side note:  The initially installed Ubuntu kernel is not "efi.signed" yet.  If there is a newer version of the kernel in the repository, 'sudo apt-get dist-upgrade' will install a "efi.signed" version and update the EFI boot files in /boot/efi/EFI/ubuntu/.

---

### Post by bmerlover on 2013-11-26
> **otognan said:**
> 
[/INDENT]

[LIST]
[*] Fix GPU. I have MacBook Pro 11,3 with external Nvidia GPU. When I ran  glxgears or glmark2 (proper benchmarking for gpu), I got screwed up  rendering with black patches on the textures. So I decided to get the  most recent driver from NVidia instead of using opensource nouveau  drivers. The following steps helped me to fix rendering issues and bump  performance in glmark2 from 223 points (Nouveau) to 3851 (NVidia).  Prepare another laptop or printout these instructions as you GUI will  not going to work in between the steps.
[LIST]
[*]Go to [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) and download Linux x86_64/AMD64/EM64T Latest Long Lived Branch version: 331.20.
[*]Go to console mode (Fn+Ctrl+Alt+F1) and kill xserver: sudo service lightdm stop
[*]chmod a+x NVIDIA-Linux-x86_64-331.20.run
[*]sudo ./NVIDIA-Linux-x86_64-331.20.run
[*]accept licence, ignore failing of pre_install script, agree to disable nouveau drivers by adding modprobe config, reboot
[*]here you should not get to GUI and just see some failures from boot.  Press (Fn+Ctrl+Alt+F1) and run sudo ./NVIDIA-Linux-x86_64-331.20.run  again, finish the installation, reboot.
[*]here you should get to GUI and be able to run glxgears
[/LIST]
[/LIST]

[LIST]
[*]
[LIST]
[/LIST]
    
[/LIST]


Thanks for the detailed write-up otognan.

Just want to add something to this, when I got to the reboot portion after disabling nouveau drivers. After the restart, ubuntu loaded fine with a GUI, however the screen resolution was low. I actually tried installing the Nvidia drivers from the terminal but that didn't work. **When I tried to go to console mode again, I just saw a black screen (no prompt, nothing)**. So here is what I did to fix that issue:

I restarted and in grub2 I went to advanced menu. I selected the ubuntu 13.10 (recovery mode) and then I selected "root" from the menu. This is essentially getting to console mode. Then I continued from there following the instructions. Seems to work fine now.

---

### Post by bmerlover on 2013-11-26
> **kjano said:**
> I was stuck with 2880x1800 because the scaling (via nvidia-settings) only ended up changing the viewport. Thus, I am back to the open source drivers.

otognan explains how to change resolution, it worked for me:

Terminal: sudo nvidia-settings
Select "X Server Display Configuration" on the top left
Change the **Resolution **to any desired resolution
Click "**Apply**"
Click "**Save to X Configuration File**"

---

### Post by bmerlover on 2013-11-26
> **ckankiewicz said:**
> Do you have multiple resolution choices with the 331 drivers or are you stuck with 2880x1800?

otognan explains how to change resolution with the nvidia drivers installed, it worked for me:

Terminal: sudo nvidia-settings
Select "X Server Display Configuration" on the top left
Change the **Resolution **to any desired resolution
Click "**Apply**"
Click "**Save to X Configuration File**"

---

### Post by Meizirkki on 2013-12-02
Hello. I'm waiting for my Macbook Pro 11,2 (15" base model, Iris Pro graphics) to arrive as I'm typing this.

It's my first Macbook and I'm planning to install Ubuntu or other Linux distribution alongside the OS X. I'll give up using OS X once major annoyances are fixed (if any).

My question is, since I have no previous Mac experience, what are the most common pitfalls I should be aware of? Especially the booting is a complete mystery to me, I having only ever used traditional BIOS computers and GRUB as the bootloader. Are installation instructions for previous MBP generations still relevant, or should I just carefully follow the steps posted to this thread?

Thanks.

---

### Post by premal-j-shah on 2013-12-02
Is there a fix for the thunderbolt ethernet port? If I restart the computer with the thunderbolt adapter plugged in, the ethernet works. But resume from suspend does not wake up the ethernet connection.

---

### Post by lichun1668 on 2013-12-02
> **premal-j-shah said:**
> Is there a fix for the thunderbolt  ethernet port? If I restart the computer with the thunderbolt adapter  plugged in, the ethernet works. But resume from suspend does not wake up  the ethernet connection.
I hope post #57 in this thread would help.

---

### Post by lichun1668 on 2013-12-02
> **Meizirkki said:**
> 
My question is, since I have no previous Mac experience, what are the most common pitfalls I should be aware of? Especially the booting is a complete mystery to me, I having only ever used traditional BIOS computers and GRUB as the bootloader. Are installation instructions for previous MBP generations still relevant, or should I just carefully follow the steps posted to this thread?


The old instructions are for previous hardward configuration, which were EFI based but did not recognize multi-boot CD images.  To support Mac, Ubuntu had to provide a BIOS-boot only CD image but unfortunately named it "mac".  The old Macs would recognize the BIOS-boot image and enters a BIOS emulation mode to install Ubuntu.  Ubuntu installed this way "thinks" the hardware is BIOS-based instead of EFI-based and needed to be fixed to boot under a EFI mode.  The new Haswell Macs (and probably the Macs in 2012) already recognize multi-boot images and can choose the EFI boot image automatically. So, you probably will get a better luck if you follow this thread for your installation.

---

### Post by premal-j-shah on 2013-12-02
Here's the contents of /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

I was already restarting the network to enable WiFi. It still does not enable the Ethernet via the Thunderbolt adapter.

---

### Post by premal-j-shah on 2013-12-02
> **lichun1668 said:**
> I hope post #57 in this thread would help.

Here's the contents of /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

I was already restarting the network to enable WiFi. It still does not enable the Ethernet via the Thunderbolt adapter. Does it need a line for the Ethernet adapter?

---

### Post by lael on 2013-12-03
I'm getting considerable wait time when installing packages or anything requiring disk access.  When I boot, the system acts incredibly sluggish.  indicator-multiload shows me some cpu wait time.  So does top.

I've installed Ubuntu 13.10
```
$ sudo dmidecode -s system-product-name
MacBookPro11,3
Invalid entry length (0). DMI table is broken! Stop.
```

1) Install rEFInd, Dual boot (and more later)
2) unetbootin -> Stock Ubuntu 13.10 64 bit -> USB stick
3) boot the USB stick & install 
4) No special copying kernel modules to rEFInd, it detects Ubuntu
5) Update Kernel to 3.12
```
$ uname -r
3.12.2-031202-generic
```
 
Added libata.force=noncq to /etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash libata.force=noncq"
GRUB_CMDLINE_LINUX="quiet splash libata.force=noncq"
```

Yes I updated Grub after this.

I assume I'm booted in EFI mode for 2 reasons:
[LIST=1]
[*]There is a /sys/firmware/efi folder
[*]It loads grub64.efi (or something like that) from rEFInd
[/LIST]

Otherwise, most things work, Nvidia 331, Wifi, keyboard backlight, display backlight.
Audio works but is mediocre with the 'options snd-hda-intel model=mba6' added to /etc/modules.d/alsa-base.conf apparently there is a subwoofer - the Audio is really tinny without it.


**How do I go about diagnosing and fixing the wait time issue?**
This is a blocker for me.

---

### Post by Meizirkki on 2013-12-03
> **lichun1668 said:**
> The old instructions are for previous hardward configuration, which were EFI based but did not recognize multi-boot CD images.  To support Mac, Ubuntu had to provide a BIOS-boot only CD image but unfortunately named it "mac".  The old Macs would recognize the BIOS-boot image and enters a BIOS emulation mode to install Ubuntu.  Ubuntu installed this way "thinks" the hardware is BIOS-based instead of EFI-based and needed to be fixed to boot under a EFI mode.  The new Haswell Macs (and probably the Macs in 2012) already recognize multi-boot images and can choose the EFI boot image automatically. So, you probably will get a better luck if you follow this thread for your installation.

Okay thanks :)

I might just try Arch, they have a decent wiki page up already [https://wiki.archlinux.org/index.php/MacBookPro11,x](https://wiki.archlinux.org/index.php/MacBookPro11,x)
Gotta try and see if I can make the switch from X to Wayland with Enlightenment's E18 release :)

---

### Post by lichun1668 on 2013-12-03
> **premal-j-shah said:**
> Here's the contents of /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

I was already restarting the network to enable WiFi. It still does not enable the Ethernet via the Thunderbolt adapter. Does it need a line for the Ethernet adapter?

I am sorry that I had misunderstood your question.  I have the same problem that the thunderbolt ethernet works only when it is plugged in at boot. The  network controller is inside the adapter, and the adapter is effectively a PCIe network card. My understanding is that the current version of Linux kernel does not support PCIe plug-and-play (or at least no support for PCIe PnP through thunderbolt). This is why the adapter is recognized only when it is already plugged in at boot.

---

### Post by lichun1668 on 2013-12-05
> **lichun1668 said:**
> I am sorry that I had misunderstood your question.  I have the same problem that the thunderbolt ethernet works only when it is plugged in at boot. The  network controller is inside the adapter, and the adapter is effectively a PCIe network card. My understanding is that the current version of Linux kernel does not support PCIe plug-and-play (or at least no support for PCIe PnP through thunderbolt). This is why the adapter is recognized only when it is already plugged in at boot.

I wonder if a USB ethernet adapter would work.  Can someone test it out?

---

### Post by huggie9876 on 2013-12-05
I have a new Macbook Pro Retina, 15" screen, 16GB RAM, NVIDIA GT750M, Intel Core i7 Haswell.

Ubuntu is successfully installed on a second partition created from iOS. (~300GB for iOS, ~200GB for Ubuntu 13.10 on the SSD partitions, plus like ~15GB set up for Linux swap).

Both boot from rEFInd boot manager.  I want to use Ubuntu more as this is my first ever Linux installation, however there are major bugs and I need "completely new to Linux" help to fix them:

[B]1)  In Ubuntu the screen turns grey and just freezes for like 10-15 seconds every 5 minutes or so.  Not critical but extremely annoying.

2)  No Sound from the on board speakers.  I have tried the fix described but because it assigned me open source NVIDIA drivers I don't think it is working (I am not using Intel integrated graphics and I do not know how to switch).

3)  No Bluetooth.

4)  The laptop gets warm.[/B]

[B]5)  The proprietary NVIDIA drivers will not work.

6)  There is no sound over HDMI output, although image is great.[/B]

I have read I should update my kernel - I have no clue how to do this safely - and also if I understand at all how rEFInd is working updating the kernel could really screw up my EFI boot.

If you can ELI5 on how to fix any of numbers 1-6 (or all of them!) above I would be eternally grateful.  My long term objective is to remove iOS and only use Linux, but I have a lot of learning to do.  Frankly I was surprised I even got it installed and booting consistently.

any help appreciated, remember we were all new to something at one time so go easy, TIA.

---

### Post by huggie9876 on 2013-12-06
If someone could just explain a fix for the 15-20 second freezes and applications graying out randomly on EFI boot 13.10 - it would be a huge step in allowing me to migrate over and get more used to Linux.

---

### Post by kjano on 2013-12-07
> **huggie9876 said:**
> If someone could just explain a fix for the 15-20 second freezes and applications graying out randomly on EFI boot 13.10 - it would be a huge step in allowing me to migrate over and get more used to Linux.

Did you add libata.force=noncq to your grub configuration and updated grub?

---

### Post by kjano on 2013-12-07
> **huggie9876 said:**
> I have a new Macbook Pro Retina, 15" screen, 16GB RAM, NVIDIA GT750M, Intel Core i7 Haswell.


I have the same machine as you and none of these problems. Are you sure you followed my instruction versus the other instructions that may or may not work for the 11.3? Don't give up, the webcam aside you will get everything working.

---

### Post by bmerlover on 2013-12-07
> **Meizirkki said:**
> Hello. I'm waiting for my Macbook Pro 11,2 (15" base model, Iris Pro graphics) to arrive as I'm typing this.

It's my first Macbook and I'm planning to install Ubuntu or other Linux distribution alongside the OS X. I'll give up using OS X once major annoyances are fixed (if any).

My question is, since I have no previous Mac experience, what are the most common pitfalls I should be aware of? Especially the booting is a complete mystery to me, I having only ever used traditional BIOS computers and GRUB as the bootloader. Are installation instructions for previous MBP generations still relevant, or should I just carefully follow the steps posted to this thread?

Thanks.

I actually originally bought this version but when I tried loading Ubuntu. The graphics were all over the place, very hard to make out the image on the screen. Just an FYI, a month ago, whatever I tried on Ubuntu 13.10 and 13.04, nothing worked. The only Ubuntu that loaded with the graphics was 12.04.1 which I had used before. I think Intel's site is still working on the drivers for the 5200. Hopefully it's resolved by now.

---

### Post by Meizirkki on 2013-12-08
> **bmerlover said:**
> I actually originally bought this version but when I tried loading Ubuntu. The graphics were all over the place, very hard to make out the image on the screen. Just an FYI, a month ago, whatever I tried on Ubuntu 13.10 and 13.04, nothing worked. The only Ubuntu that loaded with the graphics was 12.04.1 which I had used before. I think Intel's site is still working on the drivers for the 5200. Hopefully it's resolved by now.

Thanks for the heads up. Did you try adding nomodeset in your kernel boot arguments?

I'm still waiting for mine btw. Looks like the store is in no hurry even tho they assured me the laptop's in stock.. :(

---

### Post by kjano on 2013-12-08
some good news to share **suspend** mode seems to work out-of-the-box now with kernel 3.13 RC3.

---

### Post by huggie9876 on 2013-12-08
> **kjano said:**
> Did you add libata.force=noncq to your grub configuration and updated grub?

I will try this but to be clear, I do not think this is using GRUB at all.

I am booting from EFI only using rEFInd.  GRUB is not my boot loader.

Would you suggest a total re-install using GRUB to boot instead of rEFInd to boot?  And emulate a BIOS with GRUB?

---

### Post by kjano on 2013-12-10
you can also use grub-efi but you will need noncq to prevent your system from freezing up for like 15-30 seconds.

---

### Post by mattholl82 on 2013-12-10
Heys guys I installed 13.10 on a 10,1 macbook pro the other day and fouled up my windows 7 bootcamp partition.  In refind when I boot windows I get a "operating system not found" error or something like that.  I'm assuming the ubuntu install fouled up the boot sequence for the windows install.  I have been searching a ton a read through this thread that has a bunch of good stuff in it.  I guess my question is it best to install ubuntu before installing a bootcamp partition??

---

### Post by mahtin360 on 2013-12-10
Hi Everyone, I managed to get Ubuntu running on my MBP 11,1. Seems the only issue I encounter is the sound, I have tried the wo ([https://bugs.launchpad.net/ubuntu/+bug/1247475](https://bugs.launchpad.net/ubuntu/+bug/1247475))  but that fixed it only until suspend or reboot. Now i've tried applying  this patch ([https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401)) but that  does not seem to do anything for me. As described in this thread, I'm  running kernel 3.12 but I'm also using rEFInd. Has anyone experienced  something similar? I'm new to ubuntu, or any linux distribution actually so once i get the sound running i would be sorted for now.

---

### Post by premal-j-shah on 2013-12-10
thanx for ur response.

---

### Post by lichun1668 on 2013-12-10
> **mahtin360 said:**
> Hi Everyone, I managed to get Ubuntu running on my MBP 11,1. Seems the only issue I encounter is the sound, I have tried the wo ([https://bugs.launchpad.net/ubuntu/+bug/1247475](https://bugs.launchpad.net/ubuntu/+bug/1247475))  but that fixed it only until suspend or reboot. Now i've tried applying  this patch ([https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401)) but that  does not seem to do anything for me. As described in this thread, I'm  running kernel 3.12 but I'm also using rEFInd. Has anyone experienced  something similar? I'm new to ubuntu, or any linux distribution actually so once i get the sound running i would be sorted for now.

Have you tried the solution in #71?

---

### Post by mahtin360 on 2013-12-11
> **lichun1668 said:**
> Have you tried the solution in #71?

Not yet, I'm only two days into using Ubuntu and the instructions are not very clear to me at this point. The sound from headphones still works though.

---

### Post by aaBlueDragon on 2013-12-13
There should really be a an organized guide for this in [https://help.ubuntu.com/community/MacBookPro]("https://help.ubuntu.com/community/MacBookPro") .

---

### Post by lichun1668 on 2013-12-15
> **aaBlueDragon said:**
> There should really be a an organized guide for this in [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro) .

I have added an entry in that page for MacBookPro 11,1 with Ubuntu 13.10.  The direct link is

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

The 15-inch Haswell retina MacBook Pros (11,2 and 11,3) seem to have a few problems specific to their hardware configuration.  You 15-inch users may want to create a separate page to address those issues.

---

### Post by oskar22m on 2013-12-15
My problem is that I've installed both Linux Mint and Ubuntu on my MacBookPro 11,3 but my laptop is really heating up . Is anybody else experiencing this problem ?

Thank you

---

### Post by mattholl82 on 2013-12-15
> **oskar22m said:**
> My problem is that I've installed both Linux Mint and Ubuntu on my MacBookPro 11,3 but my laptop is really heating up . Is anybody else experiencing this problem ?

Thank you


Yeah there are a couple things you can do.  Quick google search will tell you a bunch.  Start here, install macfanctld:

[http://ubuntuhandbook.org/index.php/2013/11/ppa-install-fan-control-ubuntu-macbook/](http://ubuntuhandbook.org/index.php/2013/11/ppa-install-fan-control-ubuntu-macbook/)

You can play with the config file to change the fan speeds and min and max temps.  You can also use this to log temps which is pretty cool.

---

### Post by oskar22m on 2013-12-15
Is there anybody here that has successfully installed Ubuntu on a MacBook Pro 11,3 and fixed sound and suspend on it ?

If so, I would really appreciate if he could explain me as detaild as possible the way he did it. I'm struggling with this MacBook for the past week and can't go on like this anymore. 


My problems with the installation are :

If I install Ubuntu 13.10 with grub, after reboot only MacOS boots. I've tried using efibootmgr but my [COLOR=#333333][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]EFI BootOrder is 0000 and not 0080 so I don't really know how to do this. On the other hand, if I install REFIND it detects my Ubuntu installation and let's me boot it but instead of showing me one Ubuntu boot option it shows me two. This is very annoying .[/FONT]

[FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]I've tried to put the computer to sleep but once I woke it up it only showed me a black screen.[/FONT]

[FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]I have also tried to install Ubuntu 13.10 MAC version but can't manage to boot to the new installed system without pressing e at GRUB and adding "nolapic" .[/FONT][/COLOR]

---

### Post by Meizirkki on 2013-12-16
> **oskar22m said:**
> If I install Ubuntu 13.10 with grub, after reboot only MacOS boots. I've tried using efibootmgr but my [COLOR=#333333][FONT=Ubuntu, Ubuntu Beta, Bitstream Vera Sans, DejaVu Sans, Tahoma, sans-serif]EFI BootOrder is 0000 and not 0080 so I don't really know how to do this. On the other hand, if I install REFIND it detects my Ubuntu installation and let's me boot it but instead of showing me one Ubuntu boot option it shows me two. This is very annoying .[/FONT]

Install non-mac Ubuntu with GRUB and do the following after installation

```

#mount your installation partition
sudo mount /dev/sdaX /mnt 
#bind important directories
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo mount --bind /proc /mnt/proc
#create a mountpoint for EFI partition and mount it
sudo mkdir /mnt/efi
sudo mount /dev/sda1 /mnt/efi
#chroot into installed Ubuntu
sudo chroot /mnt /bin/bash
#Edit your /etc/default/grub, if necessary add libata.force=noncq to kernel boot line right after "splash"
nano /etc/default/grub
#update grub
update-grub
#goto root dir
cd /
#create a directory named boot into you EFI partition (if not already there)
mkdir /efi/EFI/boot
#Create a standalone GRUB EFI image into the boot directory in EFI partition.
grub-mkstandalone -o /efi/EFI/boot/bootx64.efi -d usr/lib/grub/x86_64-efi -O x86_64-efi -C xz boot/grub/grub.cfg
#exit chroot
exit
#umount all
sudo umount /mnt/*
sudo umount /mnt

```

What the above does is install GRUB into the EFI partition in the place Macbook looks for it during startup. You should now be able to boot Ubuntu when pressing alt at startup.

---

### Post by mahtin360 on 2013-12-16
> **lichun1668 said:**
> I have added an entry in that page for MacBookPro 11,1 with Ubuntu 13.10.  The direct link is

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

The 15-inch Haswell retina MacBook Pros (11,2 and 11,3) seem to have a few problems specific to their hardware configuration.  You 15-inch users may want to create a separate page to address those issues.

thank you very much, everything is working for me now. Thanks also for putting all the information together, that should help a lot.

---

### Post by oskar22m on 2013-12-16
Thank you very much. I shall do this today and update here. Thanks again and merry christmas!

---

### Post by kjano on 2013-12-18
> **oskar22m said:**
> Thank you very much. I shall do this today and update here. Thanks again and merry christmas!

I have the 11.3 and everything works great including sound, suspend, the laptop remains cool, etc. If you have specific problems, I am happy to give you a hand.

---

### Post by oskar22m on 2013-12-18
I just sent you a private message tried to explain my problem as details as possible. Thank you

---

### Post by oskar22m on 2013-12-19
Could someone please tell me what is it that I'm doing wrong here ? I have a macbook pro retina 11,3

1. I've downloaded Ubuntu 13.10 desktop 64 bit and not the MAC version.I've written it on a USB stick using the Ubuntu for Mac os tutorial with the "dd" command .
2. I've used Disk Utility in Mac os X to shring my partition and provided 256 GB of free space for the Ubuntu installation.
3. I've booted it by pressing ALT at boot. I've installed Ubuntu with grub Allongside Mac os .
4. After this I rebooted and when I press ALT at boot only the Mac os X shows up and the Mac recovery HD .

After seeing that this is not working I tried again only this time I did step 1.,2. and 3. and did step 4. a little bit different:
4. After insallation finished, I didn't reboot. I did
sudo apt-get install efibootmgr
sudo efibootmgr
sudo efibootmgr -o 0

[B]ubuntu@ubuntu:~$ sudo efibootmgr 
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000,0080
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0082* 
BootFFFF* 
ubuntu@ubuntu:~$ [/B]



(I've also done different installations with sudo efibootmgr -o 0.80 and 0.82) and all ended up in Ubuntu not showing up at boot when I was pressing the ALT key.


On the other hand, I encounter some problems that I don't know what they mean and if this might be the cause.,

Every time I boot the live installation USB , if I try to open gparted in terminal , I see this error:
The primary GPT table is corrupt, but the backup appears OK, so that will be used.

And, while I'm installing Ubuntu 13,10, when I get to the step where it asks me for Full name, Login user id, the COMPUTER NAME autofills with "**oskar-MacBookPro-Invalid-entry-length-DMI-table-is-broken-Stop**"

I've installed Ubuntu at least 1 few houndread times to know that this shouldn't be here but never done it on a Mac before.

I've also done at least 30 different Mac OS x complete reinstallations on this laptop the last week trying disperately to find a solution to this problem.

If I install ubuntu with REFIND then it shows up but I can't boot it up without the "nolapic" option .I don't like having only one procession so this isn't a solution for me.

I've also tried to install ubuntu without GRUB and that works out well for me but i can't add the "liberta.force=noncq" since I don't have a grub file.

Sorry for my bad english. It's not my first language.

---

### Post by lichun1668 on 2013-12-19
> **oskar22m said:**
> 
(I've also done different installations with sudo efibootmgr -o 0.80 and 0.82) and all ended up in Ubuntu not showing up at boot when I was pressing the ALT key.


After you have fixed the EFI boot order information, there is no need to press the option key at startup.  The system will boot the first in the EFI boot order, which is 'ubuntu' in your case.  I have not see that GPT table error and strange autofilled computer name.  Sounds something has been messed up.

---

### Post by oskar22m on 2013-12-19
Ok, so I tried something else that I think worked for some reason. I went on Mac os X and mounted the EFI boot partition and inside I deleted the folder Ubuntu and left only the folder called Apple. I then deleted all my previous linux partitions and freed up space and did another Ubuntu install. As soon as the install finished, I restarted and presto changeo my laptop boots in GRUB directly now. I added libata to my grub file to stop the ssd freezing and I'm updating my system as I'm writing this reply.

Question, About my GPT table error, how could I do a check on that and see if everything is OK now ? I still have a feeling that something might be broken. I've been trying to install Ubuntu like this for the past two weeks and this almost seems too good to be true, haha

This is the way my EFI boot order looks now:

oskar@oskar-MacBookPro:~$ sudo efibootmgr
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0082* 
BootFFFF* 
oskar@oskar-MacBookPro:~$

---

### Post by lichun1668 on 2013-12-19
> **oskar22m said:**
> This is the way my EFI boot order looks now:

oskar@oskar-MacBookPro:~$ sudo efibootmgr
BootCurrent: 0000
Timeout: 5 seconds
BootOrder: 0000
Boot0000* ubuntu
Boot0080* Mac OS X
Boot0082* 
BootFFFF* 
oskar@oskar-MacBookPro:~$

Congratulations.  If you want to dual boot via grub, you can follow the trick I found.  It is in a post in this thread and also summaried in this page: [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

---

### Post by oskar22m on 2013-12-19
Already did that and it works just fine, now a new entry called MacOs shows up in my grub and I can boot with it. But what about the other two MacOs entries: MacOs 32bit and MacOs64bit .How could I remove them ? They don't even work. The screen just stays blank.


What should I do about the graphic card ? Do you have a suggestion ?

---

### Post by lichun1668 on 2013-12-19
> **oskar22m said:**
> Already did that and it works just fine, now a new entry called MacOs shows up in my grub and I can boot with it. But what about the other two MacOs entries: MacOs 32bit and MacOs64bit .How could I remove them ? They don't even work. The screen just stays blank.


What should I do about the graphic card ? Do you have a suggestion ?

When you do "update-grub", it will go through the programs in /etc/grub.d/ to update /boot/grub/grub.cfg .  The file 30_os-prober is responsible for probing other OSes.  Try to add to /etc/default/grub this line:

GRUB_DISABLE_OS_PROBER=true

And then "sudo update-grub".  If you had set default OS, you should change it accordingly.  I have not tested this but let us know if this works.

I don't have the 11,3, which has a nVidia card.  So I don't know how to address issues with it.

---

### Post by oskar22m on 2013-12-20
[FONT=Times][SIZE=2]lichun1668, I figured out what the problem really was. Every time I write Ubuntu on my usb stick from Mac Os  somehow it breaks up the partition table on that USB stick . I've tried to do it with a different usb stick but i end up in the same place .
Should I write Ubuntu on a usb stick from Linux and install from there alongside with Mac Os ?
[/SIZE][/FONT]

---

### Post by oskar22m on 2013-12-20
> **lichun1668 said:**
> When you do "update-grub", it will go through the programs in /etc/grub.d/ to update /boot/grub/grub.cfg .  The file 30_os-prober is responsible for probing other OSes.  Try to add to /etc/default/grub this line:

GRUB_DISABLE_OS_PROBER=true

And then "sudo update-grub".  If you had set default OS, you should change it accordingly.  I have not tested this but let us know if this works.

I don't have the 11,3, which has a nVidia card.  So I don't know how to address issues with it.


Yes, it works ! Now when my Macbook boots i only have:
Ubuntu
Ubuntu more options
MacOs

Thank you

---

### Post by lichun1668 on 2013-12-20
> **oskar22m said:**
> [FONT=Times][SIZE=2]lichun1668, I figured out what the problem really was. Every time I write Ubuntu on my usb stick from Mac Os  somehow it breaks up the partition table on that USB stick . I've tried to do it with a different usb stick but i end up in the same place .
Should I write Ubuntu on a usb stick from Linux and install from there alongside with Mac Os ?
[/SIZE][/FONT]

If you used the dd command to write an iso image to the begining of a USB stick, you are copying faithfully, including the partition table for the image when the image was created.  A BIOS partition table might be more "portable" to a new device (such as a USB stick), while a GPT partition table is probably more complicated.  So the dd way of creating a USB boot stick is probably the culprit for the warning you saw about a corrupt  GPT table.  Despite that it seems your USB drive can boot and install Ubuntu successfully.

I don't know how to create a USB boot drive in MacOS without using dd.  I created my USB boot drive in a Ubuntu machine using Startup Disk Creator.

I hope you enjoy your Ubuntu.  I enjoy it a lot, especially on the mac with SSD and retina screen.

---

### Post by oskar22m on 2013-12-20
> **lichun1668 said:**
> If you used the dd command to write an iso image to the begining of a USB stick, you are copying faithfully, including the partition table for the image when the image was created.  A BIOS partition table might be more "portable" to a new device (such as a USB stick), while a GPT partition table is probably more complicated.  So the dd way of creating a USB boot stick is probably the culprit for the warning you saw about a corrupt  GPT table.  Despite that it seems your USB drive can boot and install Ubuntu successfully.

I don't know how to create a USB boot drive in MacOS without using dd.  I created my USB boot drive in a Ubuntu machine using Startup Disk Creator.

I hope you enjoy your Ubuntu.  I enjoy it a lot, especially on the mac with SSD and retina screen.


Yes, Ubuntu works great and i love it. The only thing is that I like Linux Mint better. I moved to it when Ubuntu addopted the Unity.
I've tried installing Linux mint but I allways get this error "Cannot install grub to dummy" right before the installation finishes. 
Do you know anything about this ?

---

### Post by lichun1668 on 2013-12-20
> **oskar22m said:**
> Yes, Ubuntu works great and i love it. The only thing is that I like Linux Mint better. I moved to it when Ubuntu addopted the Unity.
I've tried installing Linux mint but I allways get this error "Cannot install grub to dummy" right before the installation finishes. 
Do you know anything about this ?

I have never tried Mint and don't know anything about that error.  I have been using gnome-classic (gnome-fallback without compiz) instead of Unity.  This 13.10 is the first time I tried to live with Unity.  I can live with it.  If Canonical would become more like Apple, I would move away from it, maybe to Mint.

---

### Post by lichun1668 on 2013-12-25
I just tested a USB ethernet adapter and it works with hot plug in and can automatically reconnect after suspend.

---

### Post by oskar22m on 2013-12-31
After using Ubuntu gnome fallback on my Macbook pro 11,3 I'm a bit disappointed in this os because programs crash for no reason from time to time .I also can't use gnome fallback with compiz(effects) because it lacks the ALT+TAB option.
I used to love Ubuntu up until 11.04 I think before they changed it.

---

### Post by piti.diablotin on 2014-01-01
Hi everyone !
I'm a new user of the MBP 13" 11,1 with of course ubuntu-gnome.
I have to say that it's a real pleasure to combine ubuntu with such a computer, nevertheless some issues are bothering me !
I followed the excellent tuto on how to install Saucy on this laptop.
My trouble is with the resume of the speakers. 
1) I have to install pm-utils even if the /etc/pm/sleep.d rep exists
2) right after the resume, the speakers work fine with the 99_myfix script.
3) I reboot the computer and it no longer works : before suspend speakers work, after resume speakers don't work at all (I double check the 99_myfix is correctly doing is job)
4) I remove pm-utils, reboot, install pm-utils... it works until the next reboot... and so on.

I guesse there is something wrong with pm-utils when powering on but can not figure out what.

Anyone with the same isue ? Or an idea to solve it ?

Thanks

---

### Post by lichun1668 on 2014-01-01
> **piti.diablotin said:**
> 
1) I have to install pm-utils even if the /etc/pm/sleep.d rep exists
2) right after the resume, the speakers work fine with the 99_myfix script.
3) I reboot the computer and it no longer works : before suspend speakers work, after resume speakers don't work at all (I double check the 99_myfix is correctly doing is job)
4) I remove pm-utils, reboot, install pm-utils... it works until the next reboot... and so on.


Weird.  Could you please check your /proc/asound/card1/codec#0 to compare its content before resume and after each resume to see anything is different, especially in the GPIO section near the top?  This is how I found my solution in my 99_myfix script.  If any of the three flags (enable, dir, data) on the line IO[0] is not set to one, try to issue the commands in 99_myfix to see if they would fix it.

By the way, I also found Ubuntu and the retina/SSD Macbook Pro is a best combination of software and hardware!

---

### Post by piti.diablotin on 2014-01-02
Indeed ! Doing nothing, except installing/removing seems to fix the issue.
So I can not say what was the problem since everything seems to work fine !

Thanks

Let enjoy !

---

### Post by lichun1668 on 2014-01-02
piti.diablotin: It seems something is changed after boot and the remove/install steps you did reset it to allow the fix to work. Instead of removing/installing, you may try 'dpkg-reconfigure pm-utils' to see if it works for you.

---

### Post by piti.diablotin on 2014-01-02
@lichun1668 : Well I was wrong -- again -- and I don't understand !
After doing some work (nothing special) it don't work again.
So I tried what you suggested that I already tried before you told me to. Nothing happened. So I did my remove/install and nothing happened !  Thereby I guess something else is messing my MBP up !
I did a diff of the codec#0 file when it works and not. I want to say that a cat and a vi don't give the same output on the same codec#0 file.
I quote the beginning of the diff command 
> 
27c27
<   Converter: stream=0, channel=0
---
>   Converter: stream=8, channel=0
33c33
<   Power: setting=D0, actual=D3
---
>   Power: setting=D0, actual=D0
43c43
<   Converter: stream=0, channel=0
---
>   Converter: stream=8, channel=0
49c49
<   Power: setting=D0, actual=D3
---
>   Power: setting=D0, actual=D0
58c58
<   Converter: stream=0, channel=0
---
>   Converter: stream=8, channel=0
64c64
<   Power: setting=D0, actual=D3
---
>   Power: setting=D0, actual=D0
75c75
<   Power: setting=D0, actual=D3
---
>   Power: setting=D0, actual=D0
88c88
<   Power: setting=D0, actual=D3
---
>   Power: setting=D0, actual=D0



I don't know what that means ... the flags at GPIO[0] are correctly set.

---

### Post by lichun1668 on 2014-01-02
Sorry to hear that.  I have no clue why your computer requires a removal/install of the pm-utils package to make it work.  It may have been messed up by something you installed.  If you cannot live with your "fix," you could reinstall the OS.  Or, you could explore more by monitoring if any files installed by the pm-utils package got changed.  The list of files installed by the pm-utils package is in /var/lib/dpkg/info/pm-utils.list .  Good luck!

---

### Post by bjornsto on 2014-01-03
Hi everyone..,
I am about to get the MBPr 11.2 (intel Iris 5200 15' ) and install Ubuntu and Maverick dual boot.
Searching the net gives little info re 11.2 but this one [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
for 11.1 . Has anybody tried this instructions on MBPr 11.2 ?

---

### Post by bjornsto on 2014-01-03
H

---

### Post by kjano on 2014-01-04
> **bjornsto said:**
> Hi everyone..,
I am about to get the MBPr 11.2 (intel Iris 5200 15' ) and install Ubuntu and Maverick dual boot.
Searching the net gives little info re 11.2 but this one [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
for 11.1 . Has anybody tried this instructions on MBPr 11.2 ?

As you will see reading this very thread 11.2 works just fine and you will get everything working but the webcam.

---

### Post by bjornsto on 2014-01-04
Hi Kjano..,
Thanks for info but so far haven't read any re:Intel Iris5200 ?
Btw - any  progress re: [http://ubuntuforums.org/showthread.php?t=2195628](http://ubuntuforums.org/showthread.php?t=2195628) ?

MBPr 11.2 = Intel gpu Iris 5200pro
MBPr 11.3 = Nvidia gpu + Intel 5100/5200 ?
MPPr 11.1 = Intel gpu Iris 5100

---

### Post by lichun1668 on 2014-01-04
> **kjano said:**
> As you will see reading this very thread 11.2 works just fine and you will get everything working but the webcam.

I have edited the page [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) to state that the instructions should also work for 11,2 and 11,3.  At the end of that page I added  the issue of GPU selection in 11,3:

"The MacBookPro 11,3 has a nVidia GPU and an Intel GPU.  The nVidia GPU  is used by Ubuntu by default.  It is unknown how to switch to the Intel  GPU, which is supposed to consume less power."

kjano, is this a correct description of the problem?  Thanks.

---

### Post by kssarh on 2014-01-06
> **bjornsto said:**
> Hi Kjano..,
Thanks for info but so far haven't read any re:Intel Iris5200 ?


Havn't tried the patch yet, but this bug seems to report the problem I'm having with the 11,2
[https://bugs.freedesktop.org/show_bug.cgi?id=71049](https://bugs.freedesktop.org/show_bug.cgi?id=71049)

---

### Post by piti.diablotin on 2014-01-08
> **lichun1668 said:**
> Sorry to hear that.  I have no clue why your computer requires a removal/install of the pm-utils package to make it work.  It may have been messed up by something you installed.  If you cannot live with your "fix," you could reinstall the OS.  Or, you could explore more by monitoring if any files installed by the pm-utils package got changed.  The list of files installed by the pm-utils package is in /var/lib/dpkg/info/pm-utils.list .  Good luck!

I found a new weird thing regarding this issue... Actually the reinstall/reconfigure trick does not work at all. What works is when I suspend the computer without using the sound system then after the resume the sound still works.
If I listen music then suspend then resume, the sound will not work. I keep investigating !
Do you use the lock screen after suspend ?

---

### Post by lichun1668 on 2014-01-08
> **piti.diablotin said:**
> I found a new weird thing regarding this issue... Actually the reinstall/reconfigure trick does not work at all. What works is when I suspend the computer without using the sound system then after the resume the sound still works.
If I listen music then suspend then resume, the sound will not work. I keep investigating !
Do you use the lock screen after suspend ?

I always have sound after resume under various combinations.  I use lock screen after suspend.  A fresh install of the OS may solve your issue.  Then you can monitor what additional settings/packages will triger this problem.  Good luck.

---

### Post by plumlis on 2014-01-11
Hi all,I'm just considering to buy a Macbook pro retina 11.1 for ubuntu&#65292;It seems the only problem is iSight &#65292;right&#65311;
But I'm quite care about battery life,conan said he got 6-7 hours maybe but dont sure,Does anyone have more informantion about this&#65311;I mean,with some more customization such as TLP or Laptop-mode-tools.
One more question,Is it possible to swipe OSX out and installed Win8.1/Ubuntu dual boot on Macbook pro11.1,I dont like OSX,but macbook pro's hardware spec is cool.
sorry for my bad english&#65292;I hope you guy could understand me.

---

### Post by kjano on 2014-01-12
Hi plumlis. I am running the 11.3 macbook pro and have to use the nvidia card all the time which clearly consumes more battery. If I reduce the display brightness to 50%, turn of bluetooth and use the mac for email, surfing, and compiling LaTeX documents, I get about 5-6 hours (typically closer to 5). Thus, I think 6-7 hours for the 11.1 is very realistic.

---

### Post by plumlis on 2014-01-13
Thx for reply,and I will go for my Macbook pro soon:popcorn:

---

### Post by Rockmaninoff on 2014-01-13
Hi all,

My MBP Retina with Ubuntu has been very stable for me up until today.  I'm not sure if recent app updates did something, but I'm stuck in a login loop. The machine boots to the nVidia splash screen, then pops up the login screen, flashes briefly, and again pops up the login screen.  Entering my credentials causes the screen to flicker briefly, then the nVidia splash pops up again before returning me to the login screen.

Any help?  How can I access the terminal from the login screen?  Reading up on the issue, I saw a couple of threads pointing to cinnamon as the cause.  Holding Fn+Ctrl+Alt+F2 just sends me to a completely black screen though...

Thanks!

EDIT: A little bit of follow-up here.  I'm able to launch Ubuntu without the login by changing "quiet splash" to "text" in the Grub boot options.  I attempted to remove cinnamon but there's nothing installed matching that package, so it looks like that is not the solution.

I would rather not install the 3.13 RC6 kernel, but some threads indicate that may help.  It really looks like an nVidia issue.  Is it possible to start the GUI from the terminal now that I'm logged in?  Thanks!

EDIT2: Well, typing in "startx" appears to do _something_.  Again, the nVidia splash screen shows up briefly, and them I'm at a full black screen.  :-\

EDIT3: I have solved this issue.  It _appears_ that this is due to the 3.12 kernel not carrying over the nVidia driver properly.  I am not well-versed in the Ubuntu world but I was seeing ERROR (dkms apport): binary package for nvidia: 331.20 not found when attempting to install the 3.13 RC6 kernel.

DO NOT install the 3.13 RC6 kernel (kind of a silly idea on my part as well).  Just update the nVidia driver (latest is 331.38).  It updated in place for me, and there was no need to run through the install process twice.  Never have I been happier to see a "System problem detected" after login :) (that is just an error I get every time I boot...not sure what it is but everything runs fine)

On a related note, now I've got to remove the 3.13 RC6 kernel option from Grub...*grumble grumble*

---

### Post by Slavik81_ on 2014-01-16
I have Ubuntu + Gnome 13.10 running nicely on my 15" Macbook Pro /w NVIDIA graphics (11.3). My one major complaint is that it's a little power hungry. I get half the battery life under Ubuntu that I get under OSX. Is it worth 'downgrading' to the pure-Intel solution for battery life? How is driver support? Are we likely to eventually find a switching solution? I'm still within my return window and debating if I should switch.

Aside from poor support for High DPI from the occasional program, it works pretty well otherwise. Lots of tweaking to make things right, and some things will probably never be perfect, but it works.

---

### Post by piti.diablotin on 2014-01-16
> **plumlis said:**
> Hi all,I'm just considering to buy a Macbook pro retina 11.1 for ubuntu&#65292;It seems the only problem is iSight &#65292;right&#65311;
But I'm quite care about battery life,conan said he got 6-7 hours maybe but dont sure,Does anyone have more informantion about this&#65311;I mean,with some more customization such as TLP or Laptop-mode-tools.
One more question,Is it possible to swipe OSX out and installed Win8.1/Ubuntu dual boot on Macbook pro11.1,I dont like OSX,but macbook pro's hardware spec is cool.
sorry for my bad english&#65292;I hope you guy could understand me.


Hi-

As far as I can say, everything works on my MBP retina 11.1 except iSight (also note that ethernet works only if plugged before booting and can produce a freeze if hot unplugged) The VGA works fine anytime.
The battery lifetime is for me quite long, according to conky/acpi with wifi on, bluetooth off and screen brightness low I have used 47% of battery within 3h52. So the full charge should last around 8 hours.
And I dual boot OSX and ubuntu. It works very well and it is very straight forward. So I guess you can replace OSX by Win since grub first starts and need to be exited to launch OSX. Then you can have an entry for Win in grub.

Hope you gonna enjoy !!

EDIT : the uptime is 8 hours and the battery is at 1%. During the last 2 hours I have been listening music and compiling/debuging on 1 cpu (running at 100% 2.8GHz)

---

### Post by plumlis on 2014-01-16
Many thanks! to my honest I'm just make a hard decision between Thinkpad X240 with FHD and MBP Retina 11.1&#65292;and Now I may go for my macbook pro,
Another thing which I care is about retina display,I heard from some blogs and they said it could be okay on Unity with 140% or 120% font zoom-scale,but somebody says not.
and...... could you post up some screenshots with retina screen? how is it looks like? I loves Unity, and I hope it will works fine.
Sorry for my bad English again,cuz its not my first language.

---

### Post by gofvonx on 2014-01-17
Hi. I have installed Ubuntu-Gnome 13.10 on my MacBook Pro 13 Late 2013. Even after applying the WiFi-after-suspend-fix my WiFi is "unmanagend" after resuming from suspend. Also, it takes quite long (~10-15sec) to resume after suspend. (I don't know if this is normal on this configuration.) Any hints on troubleshooting this problem would be highly appreciated.

---

### Post by Slavik81_ on 2014-01-17
> **Slavik81_ said:**
> I have Ubuntu + Gnome 13.10 running nicely on my 15" Macbook Pro /w NVIDIA graphics (11.3). My one major complaint is that it's a little power hungry. I get half the battery life under Ubuntu that I get under OSX. Is it worth 'downgrading' to the pure-Intel solution for battery life? How is driver support? Are we likely to eventually find a switching solution? I'm still within my return window and debating if I should switch.

Aside from poor support for High DPI from the occasional program, it works pretty well otherwise. Lots of tweaking to make things right, and some things will probably never be perfect, but it works.

My conclusion was that yes, I should switch. The performance difference between the Intel card and the NVIDIA card didn't seem all that huge in the benchmarks anyways. ([NVIDIA]("http://www.notebookcheck.net/NVIDIA-GeForce-GT-750M.90245.0.html"), [Intel]("http://www.notebookcheck.net/Intel-Iris-Pro-Graphics-5200.90965.0.html"))

I visited an Apple Store today and tried a few of the demo units. The Intel graphics driver in the Ubuntu 13.10 image has [a serious bug ]("https://bugs.freedesktop.org/show_bug.cgi?id=71049")making it almost unusable. However, the bug is fixed in kernel 3.12.

I downloaded [the daily build]("http://cdimage.ubuntu.com/daily-live/current/") of Ubuntu 14.04 (Trusty Tahr) and tried it on both 11,2 and 11,3. It seemed to work well enough on both machines. I then ran glmark2 benchmarks, which are available here:

[11,2]("http://paste.ubuntu.com/6770325/") (score: 3173, example fps: 3423)
[11,3]("http://paste.ubuntu.com/6770424/") /w nouveau (score: 105, example fps: 119)

I should also note that the nouveau drivers displayed somewhat corrupted output for OpenGL programs. I believe the same problems can be seen under Ubuntu 13.10, too. Basically, the NVIDIA open source drivers are awful for the 11,3. The desktop and most programs are fine, but OpenGL applications will not run well.

Unfortunately, I didn't have time to test the 11,3 with the NVIDIA proprietary drivers. I suspect they would be much, much better.

Power consumption was another thing I checked. With Bluetooth disabled, the screen slightly dimmed and wifi enabled (browsing the web) I found that the 11,2 drew about 16W of power, while the 11,3 drew about 22W. Basically, this suggests the 11,2 will last ~40% longer under Ubuntu.

---

### Post by piti.diablotin on 2014-01-18
> **plumlis said:**
> 
Another thing which I care is about retina display,I heard from some blogs and they said it could be okay on Unity with 140% or 120% font zoom-scale,but somebody says not.
and...... could you post up some screenshots with retina screen? how is it looks like? I loves Unity, and I hope it will works fine.
Sorry for my bad English again,cuz its not my first language.

I don't use Unity anymore but Gnome. When with the font scaling it is just perfet. You can choose how big you want it. You can do the same in firefox.
The only "non-scaling"  application are those using X library I guess without using gtk. (dirdiff, xmgrace so far)
The retina display is really good !!

---

### Post by gofvonx on 2014-01-19
>  			 				[INDENT] 					Hi. I have installed Ubuntu-Gnome 13.10 on my MacBook Pro 13 Late  2013. Even after applying the WiFi-after-suspend-fix my WiFi is  "unmanagend" after resuming from suspend. Also, it takes quite long  (~10-15sec) to resume after suspend. (I don't know if this is normal on  this configuration.) Any hints on troubleshooting this problem would be  highly appreciated.
[/INDENT]




After playing around some more, it seems to work now.  

But another question rised concerning the ICC-profile. I have completely removed Mac OS X. Is there another possibitliy to obtain the Mac ICC-profile? Thanks

---

### Post by lichun1668 on 2014-01-20
> **gofvonx said:**
> After playing around some more, it seems to work now.  

But another question rised concerning the ICC-profile. I have completely removed Mac OS X. Is there another possibitliy to obtain the Mac ICC-profile? Thanks

MacOS probably generates  the same ICC profile for display panels with the same EDID.  If you have access to another MacBookPro with the same size panel, check its EDID (32 bytes, embeded in the ICC file name /Library/ColorSync/Profiles/Displays/Color LCD-xxxx.icc) and your panel's EDID (embeded in the ICC file name ~/.local/share/icc/edid-xxxx.icc).  If they are the same, you probably can use it without any problem.

---

### Post by oskar22m on 2014-01-20
My Macbook pro 11,3 has ubuntu 13.10 gnome-fallback on it and I'm having two major problems with it:

1 - My gnome-panel keeps crashing all the time
2 - WIFI is slow in Ubuntu and works very well in Mac os x. I've double checked in the same spot, on Ubuntu I get constant time outs to my router but on Mac i have 100% efficiency .

Is anybody else suffering from the slow WIFI problem ?

I'm running kernel 3.13-rc4 on Ubuntu 13.10.

---

### Post by gofvonx on 2014-01-22
> **lichun1668 said:**
> MacOS probably generates  the same ICC profile for display panels with the same EDID.  If you have access to another MacBookPro with the same size panel, check its EDID (32 bytes, embeded in the ICC file name /Library/ColorSync/Profiles/Displays/Color LCD-xxxx.icc) and your panel's EDID (embeded in the ICC file name ~/.local/share/icc/edid-xxxx.icc).  If they are the same, you probably can use it without any problem.

Thanks. Since I don't know anyone personally: Does anybody could provide an ICC profile of her/his MacBook Pro Retina 13 Late 2013?

---

### Post by Meizirkki on 2014-01-25
Mine is /Library/ColorSync/Profiles/Displays/Color LCD-F466F621-B5FA-04A0-0800-CFA6C258DECD.icc
Macbook Pro 11,2

---

### Post by gofvonx on 2014-01-26
Sorry, I forgot to mention mine is a 13-inch 11,1. Thanks anyway!;)

---

### Post by William_Lightning on 2014-01-28
> **Slavik81_ said:**
> 
I visited an Apple Store today and tried a few of the demo units. The Intel graphics driver in the Ubuntu 13.10 image has [a serious bug ]("https://bugs.freedesktop.org/show_bug.cgi?id=71049")making it almost unusable. However, the bug is fixed in kernel 3.12.


I downloaded and installed 3.12.8 kernel from kernel-ppa, and not only did it solve the display issue, but also solved a sound issue. I haven't done a complete investigation to all the issues, but that's a major improvement for me.

---

### Post by kjano on 2014-01-28
> **Slavik81_ said:**
> 

Power consumption was another thing I checked. With Bluetooth disabled, the screen slightly dimmed and wifi enabled (browsing the web) I found that the 11,2 drew about 16W of power, while the 11,3 drew about 22W. Basically, this suggests the 11,2 will last ~40% longer under Ubuntu.

Well, lets be fair here. It suggests that you should run a 11.3 with the intel card if you want to save energy and switch the the NVIDIA card only when you need it. Eg., see [http://ubuntuforums.org/showthread.php?t=2195628](http://ubuntuforums.org/showthread.php?t=2195628) .

---

### Post by piti.diablotin on 2014-02-10
Hi there -

I come to you because I have a new small trouble.
I have bought a TV and the HDMI link works well (even if there are some trouble with the sounds over HDMI when hot plugging but I can live with that for the moment)
I am experiencing, however, a tearing effect (horizontal line) on my TV when watching video, especially when action is occuring.
Do you experience the same ?

How could I fix that ? It does not happen with OSX.

When VLC or mplayer is runing on half the MBP screen and half on the TV, the tearing is only on the TV side. I guess this has to do with the intel iGPU and vertical synch freq or driver ?

Thanks

---

### Post by Henrik_Klagges on 2014-02-15
Greetings,

I had planned to edit the [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) webpage, but was unable to do so. Therefore I post a few datapoints here in this thread, as it was referenced from the aforementioned webpage (thanks for both).

I installed kubuntu 13.10 64bit successfully on the MBPro 11,1, alongside the original MacOS Mavericks.

What works in addition to the stuff already mentioned:
* Running a Dell UH2713HM 27" inch monitor via the Mac's display port at full 2560x1440 resolution works, both dual- and single headed.
* WLAN works out of the box, both after reboot and after resume, without any particular wake-up script.
* KDE scaling: I forced DPI to 192 (good for the retina display) and a bit below (good for the external monitor). Some ideas for tweaking are on this page: [https://community.kde.org/KDE/High-dpi_issues](https://community.kde.org/KDE/High-dpi_issues)

An installation tip:
I followed the installation instructions as given on the webpage, in particular, I ran apt-get update and upgrade for the live system. Still, late during the install, it terminated with the following error: "**grub-install dummy failed.** This is a fatal error." Funnily, I then started the freshly installed system, and it showed no problems.

Issues I am still having:
* Not everything is nicely scaled. This is an issue of KDE, as far as I can tell. But I can live with it.
* Grub's menu during initial boot is in tiny, tiny letters and oddly compressed. The fix for a larger console font becomes active only in the middle of the boot process.
* Alongside the the working MacOS entry (the "exit" :-) in grub's menu), it created two non-working entries. I have to delete them somehow.

Apart of that, pretty much everything works: Display, external display both with HDMI and DisplayPort, speakers, headphones, WLAN out of the box without driver installation, WLAN after suspend, OpenVPN over WLAN, scaled KDE, USB Ethernet, external keyboard, internal German keyboard including "nasty" characters such as | {[]}, magic keys for volume / keyboard lighting / display brightness, ctrl-alt-Fn, touchpad including recognition of two-finger clicks, SSD partitioning, LUKS encryption on /dev/sda5, automatic unlocking of the LUKS partition via pam_mount_conf.xml, etc. 

In summary, the new MacBook Pro is one hell of a Linux machine.

Cheers,
     Henrik

---

### Post by Quackers on 2014-02-15
Henrik will you have a look at something for me please?
If you go to the grub menu and press "c" you will get to the grub command line.
If you then do a "ls" what hard drives are listed?
Obviously there should be just one, however grub's ls command is listing hd0 at a size of 1KiB and hd1 lists all my current partitions. As a consequence of this I have edited my grub files to include an entry for booting OSX as hd1,gpt2 which works. I believe this can happen on some Macs and I'm wondering if yours is the same.
Many thanks.

---

### Post by Henrik_Klagges on 2014-02-17
Greetings,
if I do as you wished, I get the following output from grub's "ls":
(hd0) (hd1) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) failed to read sector "0x0" from hd0

So, my sda, which has sda1-sda5 as partitions (sda4 is my linux boot, sda5 the crypto device) is listed here as hd1.

Cheers,
     Henrik

---

### Post by lichun1668 on 2014-02-17
The GPU selection problem seems to have been solved for 10,1, an earlier version of 15" MBP that has a similar dual CPU configuration as in the 11,3. It will be interesting to know if the same would work for 11,3.  See [http://ubuntuforums.org/showthread.php?t=2098304](http://ubuntuforums.org/showthread.php?t=2098304)

---

### Post by Quackers on 2014-02-18
> **Henrik_Klagges said:**
> Greetings,
if I do as you wished, I get the following output from grub's "ls":
(hd0) (hd1) (hd1,gpt5) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) failed to read sector "0x0" from hd0

So, my sda, which has sda1-sda5 as partitions (sda4 is my linux boot, sda5 the crypto device) is listed here as hd1.

Cheers,
     Henrik
Thanks for checking Henrik - same with mine.

---

### Post by lichun1668 on 2014-02-18
> **Henrik_Klagges said:**
> Greetings,

I had planned to edit the [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) webpage, but was unable to do so. Therefore I post a few datapoints here in this thread, as it was referenced from the aforementioned webpage (thanks for both).


Hi Henrik,

I have added to the webpage above a section on non-Unity issues and a link to your post.  Thanks for the feedback.

---

### Post by lichun1668 on 2014-02-18
> **Quackers said:**
> Thanks for checking Henrik - same with mine.  Same grub output here on 11,1.

---

### Post by Joseph_OHarrow on 2014-02-19
Hey guys.

I was hoping someone could help me with an issue I am having with my 13.10 install on the Mac 11,1. I've used the official MacBookPro11-1/Saucy guide to get things running. I've basically followed the guide to the dot and have Ubuntu installed and running on my system.

However, Ubuntu is always hanging. When I go into Ubuntu it sometimes freezes from the get go before letting me work. And trying to open applications also gives me huge lags where the it seems like my computer is completely frozen, but eventually the application opens. When I try to open a web browser, the screen goes gray for a while and everything stops, until it will eventually open the browser and I can move around again.

Has anyone experienced this? Is there a way for me to fix this?

Thanks

---

### Post by Quackers on 2014-02-20
Did you perform step 7? Did the changes stick after updating grub?
Just check /etc/default/grub to see if they're still there.
That change deals with possible freezing SSD's.

---

### Post by Meizirkki on 2014-02-20
14.04 is working very well with my 11,2

OOB I got the screen, audio, wifi.. pretty much everything working very nicely. Right now I'm frustrated with everything looking either incredibly small or pixelated diarrhea on the retina screen. Out of what I've tested, Enlightenment is the only desktop environment to scale UI elements perfectly.. but then again none of the GTK/Qt apps do that and I'm stuck with good UI but no apps. How do you work around the screen having so many pixels?

---

### Post by Joseph_OHarrow on 2014-02-20
> **Quackers said:**
> Did you perform step 7? Did the changes stick after updating grub?
Just check /etc/default/grub to see if they're still there.
That change deals with possible freezing SSD's.

I performed this step. The installation went smooth. But I get these hangs all the time.

Any ideas?

It may be worthwhile also mentioning that when I load into Ubuntu from the Grub menu, sometimes Ubuntu starts up normally, without delay, whereas other times it just sits there on a blank screen before eventually starting up.

---

### Post by Quackers on 2014-02-20
Again, have you checked /etc/default/grub to make sure the change is permanent?
Other than that I have no explanation or ideas why Ubuntu should load slowly sometimes.

---

### Post by Joseph_OHarrow on 2014-02-20
Well what do you know, there was a typo. Everything works perfectly now.

---

### Post by Quackers on 2014-02-20
Glad to hear that  :D
Enjoy!

---

### Post by Ardipeth on 2014-02-27
Has anyone here been getting a kernel bug? This seems to have started for no apparent reason after I was able to get my macbook pro 11,1 running stably with Ubuntu for months. Now when I check my syslog, I find my kernel running into a problem:
> Tenin kernel:[ 40.134670] BUG: unable to handle kernel NULL pointer dereference at          (null)
and I suspect this is the cause behind certain odd behavior that I've been experiencing. For example, sudo hangs indefinitely and doesn't respond to CTRL+C when I try to sudo anything. When this happens I also can't run nautilus or any broswers, so it's difficult to paste the rest of my error code. And because sudo doesn't work, I have to manually shut down by pressing the power key. 

If anyone has also run into this problem let me know. I was running kernel 3.12 and updated to 3.13, but that didn't seem to help...

---

### Post by Ardipeth on 2014-02-27
A bit more searching and the culprit seems to be a process called 

```
 wl_event_handle 
```

which I think is linked to the broadcom drivers.

---

### Post by eduardoaquiles-ar on 2014-03-02
This looks to be the reason why the camera doesn't work:
"iSight webcam changed from USB to PCIe but no linux driver is available"

source:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1276811](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1276811)

---

### Post by oskar22m on 2014-03-03
Just letting everybody know that I've successfully installed Linux Mint 16 Mate on the Macbook Pro retina 11,3 .At the install I was getting an error related to GRUB but fixed it by manually installing GRUB . It works BEAUTIFUL ! The new Macbook pro and Linux go together perfect !

I hope switching graphic cards will be possible any time soon to make the battery last longer.

Has anybody managed to make the sub woofer working ? The sound is definitely not like in MacOS.

---

### Post by Tristan_Simard on 2014-03-03
Does the sleep/resume work ?

I too have a 11.3, running Ubuntu 13.10 though. I have tried different things with my somewhat limited knowledge and can't get it to resume (tried s2ram, updated to kernel 3.13rc6...). It will only let me move the mouse, without any other interaction. This is the main issue for me, using linux on that laptop.

---

### Post by oskar22m on 2014-03-05
> **Tristan_Simard said:**
> Does the sleep/resume work ?

I too have a 11.3, running Ubuntu 13.10 though. I have tried different things with my somewhat limited knowledge and can't get it to resume (tried s2ram, updated to kernel 3.13rc6...). It will only let me move the mouse, without any other interaction. This is the main issue for me, using linux on that laptop.

Yes, sleep/resume works on both Linux Mint and Ubuntu on the Macbook 11,3. It should work from kernel 3.13-rc3 .I'm currently running kernel 3.14.0-031400rc4-generic on my Linux mint.

I would recommend you to start with a fresh install of Ubuntu following the "Installation" instructions from this guide : [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
Once the installation finishes just updated to the latest kernel 3.14-rc5 : [http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/](http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/)

Sound,Sleep,Resume, etc should all work after you boot the new kernel. 

Good luck

---

### Post by yellow on 2014-03-07
> **oskar22m said:**
> Yes, sleep/resume works on both Linux Mint and Ubuntu on the Macbook 11,3. It should work from kernel 3.13-rc3 .I'm currently running kernel 3.14.0-031400rc4-generic on my Linux mint.

I would recommend you to start with a fresh install of Ubuntu following the "Installation" instructions from this guide : [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
Once the installation finishes just updated to the latest kernel 3.14-rc5 : [http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/](http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/)

Sound,Sleep,Resume, etc should all work after you boot the new kernel. 

Good luck

Well, it depends. 
On my Macbook 11,2 the Sleep option is NOT available (disabled?) when I boot with the Apple Thunderbolt Ethernet adapter. Sleep is available, and works, when I boot without that adapter.
This is the case for any 3.14-rc kernels so far (I'm currently running latest 3.14-rc5), using LinuxMint 16.

And as already known, pulling out the Thunderbolt ethernet adapter (or after hibernate) results in it no longer being recognized until next reboot.
I then also have a problem with shutting down not completing anymore.

I wonder if anyone with a Thunderbolt Ethernet adapter has the same experience, and maybe an idea how to fix or workaround this?

Thanks

---

### Post by jzg-dev on 2014-03-12
Installed Ubuntu 13.10 and 3.13rc1 kernel on my Macbook Pro 11,3 with minimal issues; I haven't really tested the extent of its functionality, but the things I use most often (display drivers, wifi, etc.) all work fine. I am having some issues though with the sound patch fix posted on [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401), can't exactly figure out how to apply this patch (tried compiling with C++ and C, tried applying patch_cirrus.c from [https://github.com/grate-driver/linux](https://github.com/grate-driver/linux) and other various forms of attempts based on that repo to no avail)....If someone wouldn't mind explaining in simple terms how to do this it would be greatly appreciated.

One other question is regarding the SSD partitions created for Ubuntu and the swap disk. created them with no problem but they show as locked in MacBook Disk Utility, diskutil, fdisk, etc. and even show as locked in gparted running from Ubuntu; how can I unlock these disks to resize them?

---

### Post by eindgebruiker on 2014-03-13
> **jzg-dev said:**
> Installed Ubuntu 13.10 and 3.13rc1 kernel on my Macbook Pro 11,3 with minimal issues; I haven't really tested the extent of its functionality, but the things I use most often (display drivers, wifi, etc.) all work fine. I am having some issues though with the sound patch fix posted on [https://bugzilla.kernel.org/show_bug.cgi?id=64401](https://bugzilla.kernel.org/show_bug.cgi?id=64401), can't exactly figure out how to apply this patch (tried compiling with C++ and C, tried applying patch_cirrus.c from [https://github.com/grate-driver/linux](https://github.com/grate-driver/linux) and other various forms of attempts based on that repo to no avail)....If someone wouldn't mind explaining in simple terms how to do this it would be greatly appreciated.
Sound is working fine on my 11,3 with kernel 3.14rc5 (see above).

> **jzg-dev said:**
> One other question is regarding the SSD partitions created for Ubuntu and the swap disk. created them with no problem but they show as locked in MacBook Disk Utility, diskutil, fdisk, etc. and even show as locked in gparted running from Ubuntu; how can I unlock these disks to resize them?
Did you run Ubuntu from a live disk?

---

### Post by jzg-dev on 2014-03-13
havent tried live disk yet, so you're saying if I run from live disk I should have access to the partitions?

---

### Post by Remington_Splettst on 2014-03-23
any luck with sound and sleep? nevermind, could not see previous post.

---

### Post by bunkerbound on 2014-03-30
> **oskar22m said:**
> Yes, sleep/resume works on both Linux Mint and Ubuntu on the Macbook 11,3. It should work from kernel 3.13-rc3 .I'm currently running kernel 3.14.0-031400rc4-generic on my Linux mint.

I would recommend you to start with a fresh install of Ubuntu following the "Installation" instructions from this guide : [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
Once the installation finishes just updated to the latest kernel 3.14-rc5 : [http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/](http://linuxg.net/how-to-install-kernel-3-14-rc5-on-ubuntu-linux-mint-and-elementary-os/)

Sound,Sleep,Resume, etc should all work after you boot the new kernel. 

Good luck

I started with a fresh install of 14.04 on my late 2013 macbook pro retina (13 inch).  After installing 3.14-rc5 and rebooting, I couldn't get wifi to work.  Has anyone else hit this?

**EDIT:** Disregard this, I think.  I reverted back to the previous kernel (3.13), installed a couple of packages (gnome and xfce4), reinstalled 3.14rc5 to try one more time and it worked this time.  I don't necessarily think installing gnome/xfce4 had anything to do with it.  Maybe just something flakey with the broadcom driver... in any case, it seems to be working now.

---

### Post by williamyang on 2014-04-07
I also met the problem as you described "the screen would show up with lines all over the place"(macbookpro 11,2 with intel iris pro), dose this problem have the way to be solved? or is there some methods or version of ubuntu iso on the mbp 11,2 with the intel iris

thx!

---

### Post by williamyang on 2014-04-07
> **bmerlover said:**
> A general note: I don't think the intel iris pro 5200 is ready for Ubuntu. I originally purchased the standard 15" Retina and the screen would show up with lines all over the place. Horrible resolution.

Now I got the MBPr with the Nvidia card and that one seems to work fine. Although no sound like everyone else is what I've noticed.

To answer your question, I tried everything 100 times and now I know what to do, I had the same exact problem as you.

I followed this guide: [http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html](http://randomtutor.blogspot.com/2013/02/installing-ubuntu-1304-on-retina.html) (Please use this as reference, but I will try to explain the part that is relevant to you)

I installed Ubuntu 13.10 with GRUB but after I would select Ubuntu, it would just stay on the purple screen and looks like the GPU would just get really hot, so this is the solution again taken from the link above:

Load a live USB stick and select the try ubuntu option
Go to the partition where you installed Ubuntu (in my case /dev/sda5)
You should see it as one of the hard drives in the task bar in the left or you can mount it through the terminal.
Inside the /dev/sda5, go to your boot directory and copy/paste the **vmlinuz-3.11.0-12-generic** and** initrd.img-3.11.0-12-generic** files to a usb stick or upload it online.
Type 

**sudo blkid /dev/sda5  **

in the terminal and store that long list of characters next to /dev/sda5 in my case because you will need to type it in refind.conf in MacOS X later.

For example: As an example if you see *27c9a93d-6cc8-2395-9a97-d105353e5c07 as your number next to sda5, then write that down* (every computer has a unique number)

Once you have those 2 files and the hex characters, reboot into Mac OS X

Now create a folder called ubuntu in the /EFI directory, store the 2 files (vmlinuz... and initrd....) to that folder

Open up the refind.conf file (i used "sudo nano refind.conf") and go to the section where you see the  "menuentry Linux {"

  menuentry Linux {  
     icon EFI/refind/icons/os_ubuntu.icns  
     volume **5**:  
     loader **EFI/ubuntu/vmlinuz-3.11.0-12-generic  **
     initrd **EFI/ubuntu/initrd.img-3.11.0-12-generic  **
     options "ro root=UUID=***27c9a93d-6cc8-2395-9a97-d105353e5c07***"  
    **#**disabled  
} 

Now edit that part of the file to point it to your files which I have done above if you paste the files in /EFI/ubuntu
Volume must point to the sdaX you installed it on, in my case sda5
and type in your hexadecimal characters after UUID=
Comment out disabled with a #

Save and close the file

Note: if you use the nano command to edit refind.conf then
          ctrl+o is to save the file
          ctrl+x is to exit


Restart from OS X and you will see a new Penguin during boot, mine was the one all the way at the end. Now click on that penguin and it should load Ubuntu, although once in a while it takes some time to load but it does work.
Another thing I noticed is that once in a while it gets laggy.

Hope this helps


as you described "intel iris pro" will lead to the screen would show up with lines all over the place. recently I bought a mbp (11,2 intel iris pro) and when i wanna install ubuntu met the same problem

case our lab need the linux os to install rtos (xenomai), is there method to avoid this or how to fix?

thx firstly!

---

### Post by eindgebruiker on 2014-04-09
Re 11,2 intel iris pro: did you try Trusty with kernel 3.14?
(I have an 11,3 so I can't easily test the iris pro myself)

---

### Post by vsanchez1961 on 2014-04-10
> **eindgebruiker said:**
> Re 11,2 intel iris pro: did you try Trusty with kernel 3.14?
(I have an 11,3 so I can't easily test the iris pro myself)

I have been using Trusty since the first alpha. At the beginning there were problems on and off with the intel chip, however since about 3 weeks the system has stabilized and I have not experienced any problems with the display.

---

### Post by williamyang on 2014-04-12
thx for your reply&#65292;I will try T later and give a conclusion.

---

### Post by rich17 on 2014-04-18
I am having some trouble getting 14.04 LTS to work on my 11,3 rmbp and was looking for advice.
I want to boot OSX normally and be able to select Ubuntu using the option boot.

i repartitioned the ssd to free up 100gb
installed non-mac Ubuntu 14.04 along side osx and modified grub with "libata.force=noncq"
i would prefer not to use refind and i did not change the efi boot order 0000 vs 0080 because i want osx to boot default.

my issue is in the option boot i only see the 2 mac options. I tried to follow post #123 but that did not work.

If anyone can point me in the right direction it would be appreciated, I hope i have not left out any needed info.

Thanks

---

### Post by Quackers on 2014-04-19
Section 5 of the Installation section of the guide below explains why efibootmgr needs to be changed.

[https://help.ubuntu.com/community/MacBookPro11-1/Saucy]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")

EDIT I am not familiar with the method used in post 123, so can't comment on that.
When using that method did you get any error messages?

---

### Post by lichun1668 on 2014-04-19
I just installed 14.04 (Trusty) on MBP 11,1.  Everything on [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) applies except for the speakers, which work at boot and after resume and therefore do not need any fix.

I thus edited the Saucy page to make it applicable to both 13.10 and 14.04.  The page [https://help.ubuntu.com/community/MacBookPro11-1/Trusty](https://help.ubuntu.com/community/MacBookPro11-1/Trusty) simply links back to the Saucy page.

Enjoy the Long-Term Support version!

---

### Post by lichun1668 on 2014-04-19
rich17: Step 8 at [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) may be helpful for dual boot with MacOS as the default.

---

### Post by rich17 on 2014-04-20
Thank you both for the guidance. 

When i followed post #123 the makestandalone command didn't like the -C option so i took a guess and swapped it for -compress.
I received no errors but it also did not give the desired effect.

I followed both steps 5 & 8 and this is what i get:

0,80 gives me grub by default & OSX with an option boot.

80,0 gives me OSX default and no Ubuntu with an option boot.

While i am happy i can now boot each OS, I was looking to have Ubuntu listed under the the OSX option boot screen(MacintoshHD, Recovery, Ubuntu) similar to how it looks booting the usb stick(MacintoshHD, Recovery, EFI).

---

### Post by rich-midwinter on 2014-04-23
Has anyone else suffered with this? I can't seem to configure EFI / use EFI / do anything EFI related.

```

$ sudo efibootmgr 
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```

(Yes, I've tried the modprobe.)

---

### Post by rich-midwinter on 2014-04-23
Also, it's been a while since I've used Linux, but scrolling in Chromium seems to be hugely jerky, even though I've ticked all the options in about:flags?

---

### Post by lichun1668 on 2014-04-24
> **rich-midwinter said:**
> Has anyone else suffered with this? I can't seem to configure EFI / use EFI / do anything EFI related.

```

$ sudo efibootmgr 
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```

(Yes, I've tried the modprobe.)

You could try to boot into a live CD (or USB).  If the error goes away in a live CD environment, it means you don't have hardware problem and you may configure EFI using live CD or reinstall your OS.

---

### Post by rich-midwinter on 2014-04-24
> **lichun1668 said:**
> You could try to boot into a live CD (or USB).  If the error goes away in a live CD environment, it means you don't have hardware problem and you may configure EFI using live CD or reinstall your OS.
Thanks. I've had the same issue booting from USB. Does that mean something's bust?

---

### Post by lichun1668 on 2014-04-24
> **rich-midwinter said:**
> Thanks. I've had the same issue booting from USB. Does that mean something's bust?

I am sorry to hear that.  I think something may be wrong on your hardware.  But if the OS runs great and you forget about tweaking EFI, then enjoy it.

---

### Post by rich-midwinter on 2014-04-26
Just my luck.

It doesn't run particularly well, I'd hoped booting from EFI might affect that. Battery life is about 3 hours instead of 10.

---

### Post by rainwalker on 2014-05-05
I followed the instructions at [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) and successfully installed 14.04 on my MBP 11,2 a couple days ago.

Short version: Sleep/suspend do not work. The computer does not freeze, it simply does not do anything when the lid is closed or when I run [FONT=Courier New]pm-sleep[/FONT]/[FONT=Courier New]pm-suspend[/FONT]

Long version: After the initial install I tried closing the lid to see what would happen; the computer went to sleep, and when I opened the lid again the keyboard backlight came on but the screen didn't. I ended up doing a hard shutdown because the computer wouldn't respond to anything. I've seen this issue mentioned in some other threads. After rebooting and trying again, the computer did wake up after ~5-10 seconds, which I've also seen mentioned a few times. I hadn't applied the [FONT=Courier New]99_myfix[/FONT] fix for the wifi yet so I went ahead and did that, as well as installing some updates that were available. After rebooting, sleep/suspend do not work at all. The computer does not freeze, but it looks like it tries to sleep and then fails. When I close the lid the apple logo will go dark for about a second and then light up again. Upon opening the lid I'm greeted by the lock screen (fully functional, not frozen). Nothing happens if I run [FONT=Courier New]pm-sleep[/FONT] or [FONT=Courier New]pm-suspend[/FONT] in a terminal, the screen doesn't even go dark.

Should I try installing a newer kernel?

---

### Post by Quackers on 2014-05-06
Pretty sure that the nouveau video driver can't cope with sleep yet on a Mac (or it couldn't last time I tried it).

---

### Post by rainwalker on 2014-05-06
> **Quackers said:**
> Pretty sure that the nouveau video driver can't cope with sleep yet on a Mac (or it couldn't last time I tried it).

In my case, I only have the Intel card.

---

### Post by cortman on 2014-06-18
> **rainwalker said:**
> In my case, I only have the Intel card.

Bump.

Is there any solution for suspend on the 11.1 Macbook Pro? As rainwalker says, it uses Intel Iris graphics, not Nvidia.
Currently I get a completely black screen when I select suspend or close the lid. Nothing "wakes" it back up.
Would really like for this to work.

---

### Post by neil-neilking on 2014-06-28
[COLOR=#000000][COLOR=#DD4814][COLOR=#000000]Macbook pro 11,3 here with Ubuntu 14.04 and suspend not woking like most others.  Kjano or anyone,  pleeeease tell us what magic is to be performed to get suspend working?[/COLOR][/COLOR][/COLOR]

---

### Post by rainwalker on 2014-07-03
> **neil-neilking said:**
> [COLOR=#000000][COLOR=#DD4814][COLOR=#000000]Macbook pro 11,3 here with Ubuntu 14.04 and suspend not woking like most others.  Kjano or anyone,  pleeeease tell us what magic is to be performed to get suspend working?[/COLOR][/COLOR][/COLOR]

In what way does yours not work? I seem to be the only one having the problem where closing the lid does nothing at all. Everyone else seems to have the problem where resuming just shows a black screen.

---

### Post by pragalathan2 on 2014-07-16
HI,
I have MacBookPro 11,1 and installed Ubuntu (64bit non-Mac ISO) as per the instruction given in [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy) and installed kubuntu-desktop.

I couldnt use the kubuntu ISO directly as it didnt boot automatically. 

The   problem im facing is, when I connect the external monitor im unable to  position it. I connected using VGA/display connector cable.
 "System Settings" forgets the external monitor, when i try,
1. to position the external monitor in the below screen OR
2. to make the external monitor as primary display OR
3. to clone the display OR
4. to turn off the laptop display.

OS: Kubuntu 14.04 (64bit)
Hardware: MacBookPro 11,1 Intel Haswell
Monitor: Samsung S24C350L, 23"
-Pragalathan M[ATTACH=CONFIG]254760[/ATTACH]
P.S I tried with Unity also. im unable to turn off the laptop display. but able to make the external monitor as primary. but the font size is messed up in that case)

---

### Post by pragalathan2 on 2014-07-16
Surprisingly, my DELL U2412M 24" monitor works perfectly fine. Dont know how to fix the display for the above mentioned Samsung monitor. Any help is appreciated.

---

### Post by jay52 on 2014-07-18
Thanks for sharing you views. I want to buy Macbook and laptop. Please suggest me some online stores.

---

### Post by shafiee01 on 2014-07-27
Hello Guys,

 I bought a macbook pro 13 with intel iris pro yesterday, and similar to the rest of you guys, sleep did not work neither.  I played around with it and here is what I found. It's a great machine in every sense, batter, sound, display, and keyboard. I did some debugging for suspend and here is what I found.  In the older version of kernel there are couple of segmentation faults during sleep/resume process which are fixed in the latest version of kernel (I tried 3.16 rc6 and it was fine, no segfault). However, it was not completely ok though, but it did sleep properly and suspend with a delay of ~30-40 seconds. Other than that, nothing failed during sleep or resume, because I did check the log files and also tried s2ram which is being mentioned by the kernel documentation. However, keep in mind guys if you want the latest version of kernel. you need to compile wifi driver again and install the latest one(actually there is a patch that you should apply it, because one function is being called with one less argument that the header interface in newer kernels >= 3.15). Google for the driver, and find the git hub repository of driver and apply the patch or change it manually. 

Anyway, I was happy with the machine, and after I got everything to work(sleep with delay though). I realized the extremely high resolution of this machine make it difficult to use apps on linux, and I needed eclipse because it's my main development IDE and I can't live without it! and technically speaking, I did not find any app except Firefox to support HIDPI! so I just returned the machine and waiting for better support of HIDPI.

P.S, I tried both unity and cinnamon (form Linux mint), and I found cinnamon does a better job in HIDPI than unity.

---

### Post by Daniel_Evans on 2014-07-27
I have the same problem

---

### Post by neil-neilking on 2014-07-30
> **rainwalker said:**
> In what way does yours not work? I seem to be the only one having the problem where closing the lid does nothing at all. Everyone else seems to have the problem where resuming just shows a black screen.

It fails in the same way as many others.  Seems to successfully go into sleep but resume results in a black screen (no backlight).

---

### Post by shafiee01 on 2014-08-02
Guys, 

The new kernel release(3.16-rc7) has [this commet:]("http://lkml.iu.edu/hypermail/linux/kernel/1407.3/02223.html") "Hugh Dickins (6): drm/i915: fix freeze with blank screen booting highmem" I guess that's what was affecting macbooks as well. I don't have access to a macook any more. Can any one give it a shot?

Thanks,

---

### Post by josf on 2014-09-04
I just installed Ubuntu 14.4 LTS on my new MacBook Pro 11,2 using the non-Mac download. 

Everything works, except for suspend. 

I followed the instructions and everything worked fine, but the first re-boot scared me:

After installing Ubuntu and doing the post-install configurations I rebooted. After grub, the screen went black. The keyboard backlight was still on but otherwise the computer seemed to be dead. I held down the power button until the computer turned off. I turned it on again and it booted just fine.

---

### Post by shx2 on 2014-09-13
I have the same problem as josf (14.04, new MBP 11,2). Resume from suspend doesn't work, which is a serious issue.
I also started a new thread about this (since it's a new version of MBP), but no one commented on it...

---

### Post by zyghom on 2014-09-21
hi,
Installed ubuntu 14.04 mac-iso on Macbook Pro 11,3 (i7 qc, 2.5GHz, 16GB RAM, 500GB SSD, 15")
Issues:
1-vga does not load nvidia (although showing nvidia in software update) - always on nouveau
2-temperature high(er) than under Mac OS - workaround is macfanctl - temp goes down but fan always on and not so silent machine anymore like on Mac OS
3-no camera
4-suspend not working 
5-bluetooth mouse (Apple white one) is dissappearing so using logitech wireless mouse - this is solved now

I believe nvidia makes it high temperature
Also ubuntu does not remember the cpu profile and brightness - every restart I have to set it up again (but Fn keys are ok and working - just annoying that I have to repeat it always  - this is working now

still suspend and camera not ok

---

### Post by kmsquire on 2014-10-01
For the suspend problem on MBP 11,3: shafiee01 posted a solution back on July 27th ([http://ubuntuforums.org/showthread.php?t=2184760&page=23&p=13084456#post13084456](http://ubuntuforums.org/showthread.php?t=2184760&page=23&p=13084456#post13084456)).

As an update, you can download the latest Ubuntu package for the bcmwl driver here: [https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.141+bdcom-0ubuntu3/+build/6005918](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.141+bdcom-0ubuntu3/+build/6005918)
And the latest kernel here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

(For me, v3.16.3 worked, but you can probably choose the last non-rc version safely.)

**Edit:** The bcmwl driver I pointed to does not compile with kernel 3.17.x.  As of 24 Oct 2014, it does work with 3.16.6.)

---

### Post by zyghom on 2014-10-06
ok, suspend is working with kernel initrd.img-3.17.0-031700-generic
but neither wlan nor virtualbox modules can be compiled
once this is sorted then one more problem is solved ;-)

---

### Post by shx2 on 2014-10-16
@zyghom, I installed 14.04.1, and upgraded the kernel to 3.17.0-031700, but I'm still getting the same 40sec delay when resuming from suspend.

When you're saying "suspend is working", I'm guessing you mean you're not experiencing the annoying delay. Is that right?

Any idea what I'm missing?

---

### Post by kmsquire on 2014-10-24
Just a quick update: the bcmwl driver that I pointed to above does not compile with linux kernel 3.17.x.  You'll need to either use a 3.16.x kernel (3.16.6 works), or check for an updated bcmwl driver that works with 3.17.x.

---

### Post by josf on 2014-10-27
I updated to Utopic on my 11,2. I've noticed no regressions, but no improvements either (i.e. suspend doesn't work, thunderbolt ethernet adapter must be plugged in at boot...). 

When/if updating to Utopic, remember to run [FONT=Courier New]sudo efibootmgr -o 0,80[/FONT] ([as described in the installation guide]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy#line-31")).

I forgot and had to boot Ubuntu from a USB to fix it.

---

### Post by vsanchez1961 on 2014-11-03
Hi, I made the mistake you mentioned... but to make it interesting just going out for a trip. I have serveral problems, perhaps other will have the same. 

I cannot make a bootable USB drive even following the instructions in [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick). How do I need to initiatialize the USB Drive? As HFS volume? 

If I manage to boot from the USB drive, does the command efibootmgr will work from the EFI in the USB stick? or how do I make it modify the EFI partition in the disk?? 

Sorry, but I am far from home with a bad internet conection and little time for experimentation!!!

---

### Post by bfarbod on 2014-11-05
Hello everyone
I love macbook and I want to buy one but the problem is if ubuntu wouldn't work I can't return it and get my money back and everyone told me that ubuntu won't work properly on this machine so I was really depressed and after reading this thread I wan't sure if I couldn't take my hope high so please help me because you are the only professional ones and skilled enough that could help me in this matter :

the model that I have in mind is Macbook pro retina mgx 82 which is the macbook pro 11,1 MGX82xx/A 13.3&#8221;/2.6 i5/8GB/256-Flash

can I install ubuntu 14.04 trusty tahr (ubuntu-14.04-desktop-amd64) with instruction in official ubuntu site 
**[[SIZE=2]MacBookPro11-1/[/SIZE]]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")[SIZE=2][Saucy]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy?action=fullsearch&value=linkto%3A%22MacBookPro11-1%2FSaucy%22&context=180")[/SIZE]**

[COLOR=#ff0000]
without even rEFIt or rEFInd [/COLOR]

if I cannot use the mentioned ubuntu iso what is the best iso?

and what problems I will counter by installing ubuntu 14.04 in macbook pro that I mentioned? (will it be the same as problems in official ubuntu site which could be easily fixed  or there are other problems as well?)

and why nobody talks about 14.04 only 13.01?

I am a newbie ... take it easy on me if my questions aren't good enough :( ,  but I looked everywhere and I asked everyone...this is my last ... please help me

With Regards

---

### Post by vsanchez1961 on 2014-11-06
Hmm, back home. I could boot from an Ubuntu 14.10 DVD and modify the EFI boot order. I never managed to create a bootable USB stick, and also had problems booting from a Kubuntu-Plasma5 14.10 DVD image. 

I am having some problems with the trackpad after the upgrade... at the beginning it was not working (not moving the cursor, but the rest will work). I had to take the xorg tricks and special configurations recomended in the HOWTO and it works but it is "slugish". Sometimes it seems to get stuck, maybe a sensitivity issue. I will need to put back some of the configuration to see what is going on..

---

### Post by rainwalker on 2014-11-08
> **bfarbod said:**
> can I install ubuntu 14.04 trusty tahr (ubuntu-14.04-desktop-amd64) with instruction in official ubuntu site 
**[[SIZE=2]MacBookPro11-1/[/SIZE]]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy")[SIZE=2][Saucy]("https://help.ubuntu.com/community/MacBookPro11-1/Saucy?action=fullsearch&value=linkto%3A%22MacBookPro11-1%2FSaucy%22&context=180")[/SIZE]**

[COLOR=#ff0000]
without even rEFIt or rEFInd [/COLOR]

if I cannot use the mentioned ubuntu iso what is the best iso?

and what problems I will counter by installing ubuntu 14.04 in macbook pro that I mentioned? (will it be the same as problems in official ubuntu site which could be easily fixed  or there are other problems as well?)

Yes, that is the guide I followed. You will end up using GRUB instead of rEFIt/rEFInd. Read through this thread to see the problems you will probably face. Suspend/resume is the most problematic, but there are a few others. Another option would be to use Bootcamp, but I have not tried that personally so you're on your own (see [this link]("https://apple.stackexchange.com/questions/128141/bootcamp-with-ubuntu-linux/128145#128145"))

---

### Post by bfarbod on 2014-12-11
> **rainwalker said:**
> Yes, that is the guide I followed. You will end up using GRUB instead of rEFIt/rEFInd. Read through this thread to see the problems you will probably face. Suspend/resume is the most problematic, but there are a few others. Another option would be to use Bootcamp, but I have not tried that personally so you're on your own (see [this link]("https://apple.stackexchange.com/questions/128141/bootcamp-with-ubuntu-linux/128145#128145"))


I don't know what to say but after a while I didn't get my hope so high after checking every week, day and hour
 but you gave me hope

I wasn't hoping for an answer but thank you thank you so much

you don't know what it means to me that you answered my question

I hope you don't mind asking you another question :

can I fix macbook pro mgx82 (which doesn't have geforce graphic just 5100 HD) problems about sleep and hibernate?

and if there is a fix, is it a permenant fix? and hibernate and sleep problem will not happen again?

with regards

farbod

---

### Post by migu2 on 2015-01-22
Just installed kernel 3.18 and the newest wireless driver on MBP11.3 with Ubuntu 14.04. Suspend seems to work without delay and wireless is working fine.

Links:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-vivid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.18-vivid/)
[https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu2/+build/6555554](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.248+bdcom-0ubuntu2/+build/6555554)

---

### Post by bingen2 on 2015-02-03
Which video driver are you using? I'm having trouble trying to install this kernel with nvidia-331 package.

Does suspend works the second time you try? With kernel 3.16 it was working on my MBP 11,3, but just once. After I wake it up it no longer suspends.

Thanks,

   ßingen.

---

### Post by aswinthomas on 2015-02-21
I just upgraded to 3.18.7 and everything related to susped/resume works well, except when a thnderbolt display is plugged in. But this is already a great improvement.

---

### Post by bingen2 on 2015-02-22
Can you guys using 3.18 kernel please tell me which video driver are you using? I was using nvidia-331 without luck. I installed kernel 3.18.7 and I upgraded to nvidia-340 as suggested here:

[https://help.ubuntu.com/community/MacBookPro11-3](https://help.ubuntu.com/community/MacBookPro11-3)

But now it just freezes on login screen.

Thanks,

   ßingen.

---

### Post by ceres2 on 2015-03-15
Hi,

i use on macbook air 11" 2013 i915, but kernel 3.19.1
lsmod | grep -i i915
i915                 1087090  7 
drm_kms_helper        123797  1 i915
video                  24803  2 i915,mba6x_bl
drm                   341532  6 i915,drm_kms_helper
i2c_algo_bit           13564  1 i915

Best,
 CereS

---

### Post by jorge8 on 2015-04-08
zyghom, I had the same problem using macfanctl on my macbookpro10,2.  It was too loud for me, so I wrote a script to control the fans so that I can fine-tune it to my liking.  I set up a chron job to run this script once per minute, and this script iterates every few seconds to re-adjust the fans.  Running it this much only seems to take up less than 0.05% of the CPU load.  Hope this solves one of your problems! :)

```

#!/bin/bash

temp1=`sensors | grep 'Physical id' | tr -s ' ' | cut -f 4 -d ' ' | cut -f 2 -d '+' | cut -f 1 -d '.'`
temp2=temp1
temp3=temp2
temp4=temp3

for (( NUM=1 ; NUM<=60; NUM++ ))
do

    temp1=temp2
    temp2=temp3
    temp3=temp4
    temp4=temp5
    temp5=`sensors | grep 'Physical id' | tr -s ' ' | cut -f 4 -d ' ' | cut -f 2 -d '+' | cut -f 1 -d '.'`
    avg=$(( ($temp1 + $temp2 + $temp3 + $temp4 + $temp5)/5 ))

    if [[ avg -lt 60 ]] ; then
        speed=$(( $avg*83 ))                   #regular slope
    else
        speed=$(( $avg*100 - 1000 ))      #steeper slope above 60 degrees celcius
    fi

    if [[ speed -lt 2000 ]] ; then
        speed=2000
    else
        if [[ speed -gt 6500 ]] ; then
            speed=6500
        fi
    fi

    echo $speed > /sys/devices/platform/applesmc.768/fan1_min
    echo $speed > /sys/devices/platform/applesmc.768/fan2_min

    sleep 1
done

```

---

### Post by UpSignal on 2015-04-25
how come no one talks about battery?
Macbook pro 15", intel iris pro only.
went from 9 hours battery ( on osx ) to about 2:30
installed tlp ow whatever called, no joy. any ideas?

---

### Post by migu2 on 2015-08-07
A bit late to your post but leaving this here for further reference. Had similar issues with battery life and quick googling revealed a trick that improved the situation so that I can get about 6-7h again.

On my macbook, there was an interrupt that was causing 100% cpu usage on one core. If you check top and see kworker high up the list, this may affect you too. You can check your interrupts using:

```
grep . -r /sys/firmware/acpi/interrupts/
```

Look for an interrupt that has very high number, for me it was /sys/firmware/acpi/interrupts/gpe66. Then disable it:

```
sudo echo "disable" > /sys/firmware/acpi/interrupts/<interrupt>
```

If you get permission error, elevate to root login shell with sudo -i. Note that this does not persist through reboots so you have to add the disable line somewhere where it gets executed at startup.

Also note that randomly disabling interrupts may have adverse effect on your system. I haven't had any negative impact but I take no responsibility if you do.

---

### Post by borzwazie2 on 2015-08-11
Just a quick note here: I installed 14.04 on a MBP 11,2. Screen brightness wouldn't change automatically on battery/AC, short battery life, wifi didn't work out of the box. I added some changes to the documentation for these issues. [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)

All except the camera is working well now. There's no fix for the camera yet.

---

### Post by mattholl82 on 2015-08-13
> **migu2 said:**
> A bit late to your post but leaving this here for further reference. Had similar issues with battery life and quick googling revealed a trick that improved the situation so that I can get about 6-7h again.

On my macbook, there was an interrupt that was causing 100% cpu usage on one core. If you check top and see kworker high up the list, this may affect you too. You can check your interrupts using:

```
grep . -r /sys/firmware/acpi/interrupts/
```

Look for an interrupt that has very high number, for me it was /sys/firmware/acpi/interrupts/gpe66. Then disable it:

```
sudo echo "disable" > /sys/firmware/acpi/interrupts/<interrupt>
```

If you get permission error, elevate to root login shell with sudo -i. Note that this does not persist through reboots so you have to add the disable line somewhere where it gets executed at startup.

Also note that randomly disabling interrupts may have adverse effect on your system. I haven't had any negative impact but I take no responsibility if you do.



Awesome man have a similar issue.  CPU usage on my first core was consistently up above 90%.  For me disabling gpe16 did the trick.

---

### Post by nykhedimus on 2015-10-09
I finally have suspend on MBP 11,2 Ubuntu Gnome 14.04.  Just a note: I had to do the disable XHCI wakeup trick in order for it to work more than once after a reboot.  Thanks for the help, much appreciated.

---

### Post by oren2 on 2015-10-19
latest linux kernel fix the problem, to install
```

sudo apt-get install linux-generic-lts-vivid

```

---

### Post by eindgebruiker on 2015-10-22
The screen brightness adjustment keys (F1 and F2) stopped working since upgrading to Wily. No notification bubble, brightness stays at maximum.
The other keys like keyboard brightness and volume still work.
I'm on an MBP 11,3 using nouveau.
Did anyone else encounter this?

---

### Post by mahtin360 on 2015-11-16
Hi Guys 
its been a while since I have used my Ubuntu on Macbook pro. Remember I logged in about 3-4 weeks ago and everything seemed fine.

Today I tried to log in again but after choosing my partition in refind, all i'm getting is a black screen. Tried to use a liveUSB, however that also ends up in showing a black screen and with my keyboard lights on. Nothing else works. i have access to the Ubuntu partition from my mac so data is not so much an issue. 

Has anyone else encountered this issue? I have no clue what to do from there, just tried a few boot options including nomodeset using 'e' in the menu of either, the already installed partition and the liveUSB, none of that got me any further.

I'd be really thankful for any hints.

---

