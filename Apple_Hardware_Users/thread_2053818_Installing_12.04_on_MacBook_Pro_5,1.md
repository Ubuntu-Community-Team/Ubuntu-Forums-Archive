---
title: "Installing 12.04 on MacBook Pro 5,1"
date: 2012-09-06
forum: Apple Hardware Users
---

### Post by niyam on 2012-09-06
after two weeks of trying, I'm still struggling to install Ubuntu 12.04.


In brief:

Machine: Apple macbook pro 5,1 which i've recently upgraded to Mac OSX 10.8.1 Mountain Lion, after upgrading the internal HDD.

The optical disc is damaged or for whatever random reason, consistently spits out failed discs while reading or writing. So am not replacing that. Hence i've taken the route of trying to install 12.04 using a usb-stick and/or from a separate partition on my hdd.

For this, i spent about 7 days researching into all issues. The two best methods are mentioned here:
[http://forums.macrumors.com/showthread.php?t=1329407](http://forums.macrumors.com/showthread.php?t=1329407)

and

[http://cweiske.de/tagebuch/ubuntu-on-macbook-air.htm](http://cweiske.de/tagebuch/ubuntu-on-macbook-air.htm)

Note: none of these are specific to my MacBook Pro 5,1 but the concepts are applicable.

My status: 

1. Used gparted to add dos partition tables to a usb-stick.

2. Used Unetbootin to install the mac-alternative.iso of 12.04 to the usb-stick.

3. Created several partitions on my mac hdd, and in the fourth partition, used the powerful 'dd' command to install the image on the usb-stick to the internal hdd. at this stage, the first problem occured, my terminal just hung, the image was copied.

4. restarted and synced rEFIT, which i installed a few days earlier, prior to installing ubuntu.

4.Clicking on the 'tux' option in rEFIT i got the unetbootin option, but instead of booting a live version it just went into installing. So i did. it went through the steps, but showed errors while installing software apps, so had to skip that step, and also failed to install grub.

5. on the restart, the tux logo shows up next to the mac os logo. clicking on it just leads to a black screen.

6. holding down the option key, and rebooting, i get the boot from 'legacy OS' option. clicking on that i seem to get into loading, but the 'missing operating system' error pops up immediately.

for sure, apple has made it extremely tough and challenging to install linux on their laptops.
i've never experienced so much suffering in trying to install linux in the 14 years i've used it.

the documentation on the ubuntu site also has nothing on how to install on the macbookpro 5,1 without an optical disc. Actually, am still eagerly looking forward to the documentation on how to install Ubuntu 12.04 on MacBookpro 5,1 on the official documentation wiki.

Frustrated.

I'm willing to start again, but could you please guide me what steps to use?
Thanks for your help.

Regards
Niyam

---

### Post by vibe3 on 2012-09-06
I can't help you but I'm having similar problems with my MBP 5,3. For some reason the ubuntu iso's (even the ones with +mac) simply won't work. I've heard that burning a CD is the way to go instead of a usb stick but I haven't tried that yet.

---

### Post by davidryderuk on 2012-09-08
You mean this CD?
ubuntu-12.04.1-alternate-amd64+mac.iso

In this case alternate refers to the fact that the CD is a text based installer, and is different from the desktop, live CD. The +mac bit refers to the fact that EFI booting has been disabled. If you want to boot a live CD in BIOS compatibility mode, then try this CD:

ubuntu-12.04.1-desktop-amd64+mac.iso

Alternatively you could try booting with EFI, which makes USB booting possible, but has some obscure GPU issues. In this case look for this CD:

ubuntu-12.04.1-desktop-amd64.iso

And possibly read this blog post:

[http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/](http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/)

p.s. Did you check the CD integrity before installing?

---

### Post by niyam on 2012-09-08
My optical disc went became unusable twice. The first time it happened under warranty, so apple replaced it gratis. Now it's on the blink again. In India, for the quoted price of its replacement, I can buy an i5 or higher multi-core laptop that also includes an optical disc. Besides, I will only need the Mac's superdrive for this one install of ubuntu, and apart from that have no need for the optical disc. All workflows are now either via usb-sticks or the cloud. So that over-priced purchase is essentially futile for me. I'd rather get this Ubuntu install working with usb-sticks and partitions, a procedure I'd assume exists since 5 years or more, and which the Linux/FOSS community would have hopefully taken to a mature and stable level by now.

---

### Post by niyam on 2012-09-08
> **davidryderuk said:**
> You mean this CD?
ubuntu-12.04.1-alternate-amd64+mac.iso


er... yes, but mine does not have that 12.04.1 iteration, it's only 12.04. thanks for the heads-up. perhaps that's the culprit.


In this case alternate refers to the fact that the CD is a text based installer, and is different from the desktop, live CD. The +mac bit refers to the fact that EFI booting has been disabled. If you want to boot a live CD in BIOS compatibility mode, then try this CD:

ubuntu-12.04.1-desktop-amd64+mac.iso


Alternatively you could try booting with EFI, which makes USB booting possible, but has some obscure GPU issues. In this case look for this CD:

ubuntu-12.04.1-desktop-amd64.iso


okaie dokie. Here's what I'm doing. I've decided to simply erase all the partitions I created on my Mac's HD, save of course, the EFI, the Mac OSX, and the MAC OSX boot partitions that Apple decrees its users must have. Having said that, I find it strange I cannot delete the swap partition of 4GB that I had created earlier. But let's see what happens when I come to the fresh install stages again.

Next, am downloading not one but four iso images, all 12.04.1 versions. At least hopefully one of them should work using the usb-stick or the special partition method:

1. ubuntu-12.04.1-dvd-amd64.iso
2. ubuntu-12.04.1-dvd-i386.iso
3. ubuntu-12.04.1-alternative-amd64.mac.iso
4. ubuntu-12.04.1-desktop-amd64.mac.iso

am going to attempt the install starting with 4. then 3. then 2. then 1.
after that i should probably take a sledgehammer to my macbookpro and buy an intel ultra book. but sadly, that is not an option. i do need Apple LogicPro and some other Mac software. sigh!



And possibly read this blog post:

[http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/](http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/)


thanks for the link. this one for brave hearts. I don't qualify.


p.s. Did you check the CD integrity before installing?

nope. i know i should. let me start with the new install, and will post here again.

thanks so much.

regards
niyam

---

### Post by niyam on 2012-09-08
Oops! Some of my responses are in-line in the post above. Please find them there. Thanks. - Niyam

---

### Post by niyam on 2012-09-08
> **davidryderuk said:**
> 
[snip]

And possibly read this blog post:

[http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/](http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/)


Just noticed that blogpost is from May 2011, and deals with ubuntu 11.04. That time, Mountain Lion did not exist either Would be wary to try out those steps, as I wouldn't know which ones are redundant today.

regards
niyam

---

### Post by niyam on 2012-09-08
The ubuntu-12.04.1-desktop-amd64+mac.iso image *does* work. I'm typing this from a live boot of Ubuntu 12.04 from my MacBook Pro 5,1. Here's how I did it.
1. Made fresh partitions on the Macbook Pro's internal HD. swap was the third partition, and a new partition i labelled 'BOOT' was the fourth. a fifth partition was 'Tux'.
 
2. On the usb-stick, recreated the partition table by using gparted on an Ubuntu running on another laptop. Deleted all partitions on the usb-stick, then recreated the msdos partition-table. 

3. Created a fresh FAT32 partition on the stick, used Unetbootin on another generic laptop with linux, to install the *.iso mentioned above to that partition. 

4. Booted into the Mac OSX and used the dd command to clone the usb-stick's into the fourth partition. wait a while till the command-line gives you back the $ prompt. so far no errors were generated. rebooted, synced the rEFIT partitions. 

5. rebooted once more, this time with option-key. (yes, this second reboot seems important)

6. selected 'windows' rather than rEFIT in options available. Voila! Unetbootin displays its boot options!

7. press [tab] to get kernel-options before booting the 'live' ubuntu. Here, at the end of the options are '- -'. Take your cursor to before this mark, type 'nomodest' then add a space, then move the cursor to the end of '- -' and press return.

8. keep watching that screen, it might re-display the unetbootin screen, but that's a framebuffer image, the cursor's blinking on the bottom left. you'll then get a black screen for a few seconds, then a dark grey one, and then the Ubuntu boot up screen appears. just be a bit patient. and there you have it!

9. okay, the wi-fi wasn't working, but clicking on the wi-fi icon on the top-right, i got an 'activate' dialog-box to install broadcom drivers. i did. the dialog-box then prompted me to reboot for changes to take effect. no need. just wait 5 seconds, and click the wi-fi button on the task-bar on the top-right again. type in your wi-fi password and you're in.

next step: am going to install this ubuntu 12.04 on my hard-disk. But tomorrow. it's 4:54am here, been struggling with this since 12 hours! Need a shut-eye.

PS: i've got 12.04 working on another laptop, but on the Apple MacBook Pro 5,1 it looks just gorgeous! The screen is so beautiful and comfortable! Fonts so crisp! Wow!

---

### Post by TheLoneCuber on 2012-09-08
> **niyam said:**
> 

1. Made fresh partitions on the Macbook Pro's internal HD. swap was the third partition, and a new partition i labelled 'BOOT' was the fourth. a fifth partition was 'Tux'.
 
2. On the usb-stick, recreated the partition table by using gparted on an Ubuntu running on another laptop. Deleted all partitions on the usb-stick, then recreated the msdos partition-table. 

3. Created a fresh FAT32 partition on the stick, used Unetbootin on another generic laptop with linux, to install the *.iso mentioned above to that partition. 

7. press [tab] to get kernel-options before booting the 'live' ubuntu. Here, at the end of the options are '- -'. Take your cursor to before this mark, type 'nomodest' then add a space, then move the cursor to the end of '- -' and press return.


re: #1 - Does this mean you can *only* use the USB on a computer that has specific partitions for Ubuntu? It kinda defeats the purpose for me - I was thinking/hoping I could have a mobile Ubuntu USB to use on foreign computers (when I don't have my computer with me).

re: #2 - I only have a Mac to work with, so don't have the option to doing any config via another OS

re: #3 - Unetbootin's official documentation states that "resulting USB drives are bootable only on PCs (not on Macs)". I've read conflicting reports about this, but I've not tried Unetbootin in my Mac only attempts.

re: #7 - I have read elsewhere about the 'nomodest' step. I must try that out.

---

### Post by cweiske on 2012-09-09
> **TheLoneCuber said:**
> re: #2 - I only have a Mac to work with, so don't have the option to doing any config via another OS

You can install VirtualBox on OSX and boot a live cd in there. When you unmounted the usb stick in OSX via the CLI diskutil unmount command, you can use it in the virtualbox and write it from there.

---

### Post by davidryderuk on 2012-09-10
Glad you got it working. I agree about it being more difficult. 

With regards to the blog post there were a few key steps right at the top of the post, with other advice being a bit more general. In particular if you wanted to boot via EFI mode (with the ubuntu-12.04.1-desktop-amd64.iso), then you could try these steps:

> 
   [LIST=1]
[*]Boot into OSX, go to System Preferences -> Energy Saver, and select the high performance option (vs. the battery option). This turns on the fancy NVidia 9600M video card.
[*]    Reboot into the Live CD. When you see the accessibility logos on the bottom of the screen, hit the any key, then F6, and then Esc to get rid of that annoying menu that reminded me of Clippy for some reason.
[*]    Anyways, in that boot options line, before the “–”, write in “nouveau.noaccel=1&#8243;. You need this because nouveau is still in early development, and it thinks it knows how to handle your video card. It doesn’t.
[/LIST]


I was wondering whether you could have used the OS X version of Unetbootin to carry out steps 2 and 3. In any case, thanks for detailing the whole process.

> I was thinking/hoping I could have a mobile Ubuntu USB to use on foreign computers (when I don't have my computer with me).

Personally I'm happy enough if I can convince someone to install a recent version of LibreOffice or Firefox. Failing that, I sometimes use this website:

[http://portableapps.com/](http://portableapps.com/)

---

### Post by niyam on 2012-09-11
> **TheLoneCuber said:**
> re: #1 - Does this mean you can *only* use the USB on a computer that has specific partitions for Ubuntu? It kinda defeats the purpose for me - I was thinking/hoping I could have a mobile Ubuntu USB to use on foreign computers (when I don't have my computer with me). 

For your sake, I plugged in the USB-stick created using the 'dd' command as explained in my thread earlier. It does show up in rEFIt, but clicking on it, the system either hangs, or gives the 'missing operating system' error. So this does not work. It does work on non-Macs though.

>  re: #2 - I only have a Mac to work with, so don't have the option to doing any config via another OS 

Erm... Then you could try using unetbootin with the Mac. I did not try it for no particular reason. Do share your results here.

>  re: #3 - Unetbootin's official documentation states that "resulting USB drives are bootable only on PCs (not on Macs)". I've read conflicting reports about this, but I've not tried Unetbootin in my Mac only attempts. 

The problem is not with the stick. And the solution is in installing it in a partition on your 'startup disk' which in our case is the internal HDD, on a sweet little partition.

>  re: #7 - I have read elsewhere about the 'nomodest' step. I must try that out.

Works like a charm. once you update to a stable and working version of a nVidia or alternative driver, the nomodeset gets overriden. This is I read somewhere in the large churns of documentation been reading off the web to get my machine to work.

---

### Post by niyam on 2012-09-11
Damn! I just spent more than an hour and a half documenting how I installed Ubuntu 12.04 in dual-boot, but the Ubuntu forums engine reset itself and I lost it all. Grumble! Will attempt it once more tomorrow. What a waste of time!
sigh!
update: just found it on a page, but could not publish it from there, so copied and pasted below. Whew!

---

### Post by niyam on 2012-09-11
I've finally got Ubuntu 12.04 Precise Pangolin, installed and running on my Apple MacBook Pro, 5,1. Here are the steps.

**Preparation:**
Install the 'Live CD' version on a small and dedicated partition for this task, on your internal Hard-disk. Then boot from this Live-CD-On-A-Partition.
To do these tasks, please follow the steps I mentioned in post #1 and post #8 of this thread-conversation. These are obviously the first and the eighth post here.

The 'Live' version works nicely, but the moment you shut down all preferences, wi-fi access settings, and other settings and even data may be lost. Time to install a native version on the Hard-disk of the MacBookPro.


**Dual-Boot Mac OSX 10.8 Mountain Lion and Ubuntu 12.04 Precise Pangolin**


After a few hit-and-trial attempts, here are the steps that worked for me:

0. If you've made a few attempts, you'll soon find a persistent swap partition on the hard-disk, that does not get deleted whether you use Disk Utility under the Mac OSX, or even GParted under your Live-CD-running-off-the-HD. You may even find your LiveCD-mode partition is not immediately after your Mac OSX HFS+ partition (excluding any freespace buffer). Generally, the situation is begging for a fresh start.

So after booting into the Live-mode of Ubuntu 12.04, go to the terminal and issue these commands:
> 
$ sudo cp -r /cdrom /cdrom2
$ sudo umount -lfr /cdrom
$ sudo rmdir /cdrom
$ sudo mv /cdrom2 /cdrom


Then, launch 'Disk Utility' under Ubuntu 12.04. Yes, that's the actual name of the software here (don't ask). Delete the swap-partition, and every other partition, save the crucial ones: EFI; the HFS+ that contains your MacOSX; and the partition that contains your LiveCD mode of Ubuntu.
Do note: I've even deleted my Mac emergency recovery / backup partition. Keep yours.

1. Reboot. At the rEFIt menu on startup, do choose the partition-tools to sync your partitions, by typing 'y' at the prompt. Then boot into Mac OSX.

2. Use 'diskutil list' on the mac's terminal to find your partitions. Then launch 'Disk Utility' in Mac, and delete even that partition containing your LiveCD-mode. Reboot to sync partitions in rEFIT, and then come back to MacOSX for your freshest and final install of Ubuntu:

3. Using 'Disk Utility' on the Mac, create a FAT32 partition called 'LIVECD' of 1GB. Note: The size of this partition has to be bigger than the filesize of the CD-image you are going to 'dd' here. Since my *.iso filesize of the CD-image was about 700MB+, I used 1GB. Having the exact size may create problems, it did so for me. So a little buffer is good. Make sure this partition is the third partition on the hard-disk, after EFI and HFS+. In my case, this was disk0s3.

4. Add another partition, give it a generic name, such as 'FREEDOM', have it in ext4 or FAT32, and save that too. This is the space we will later free up and start carving into neat little partitions for installing Ubuntu under the LiveCD mode. For me this was disk0s4.

5. Unmount both partitions, 'LIVECD' and 'FREEDOM' disk0s3 and disk0s4. Plug in your USB-stick that contains the partition on which you've used Unetbootin to install your Ubuntu-installer. (This is explained in post #1 and post #8).

6. On the terminal, use the 'dd' command to clone the usb-stick partition (in my case disk1s1) to the 'LiveCD' partition. In my case, this was
$ dd if=/dev/disk1s1 of=/dev/disk0s3 bs =1m

please double-check your exact partitions before attempting this.

7. Okay, time to reboot. under rEFIt, use its second icon in the bottom row to sync partitions. Then boot into the LiveCD mode of Ubuntu. If the system appears to hang immediately after selecting the Tux icon, and for beyond 2 minutes, just reboot. It works in a reboot or two. Some sort of rEFIt blessing this! :-)

8. Once the Tux icon here boots, for a few seconds you may see just the Tux icon, then the screen goes black for a few seconds, then dark grey, and then you may see the Unetboot menu options, with a countdown about to launch Ubuntu. Immediately press the tab key, and add 'nomodeset' before the '--' to the kernel options there. then bring your cursor to the right of the '--' and press enter.

9. Your screen may show the same screen again after blanking, with a blinking cursor at the bottom, and after a few pixel splutters for a few seconds, you'll find yourself booting into the Live Ubuntu cd.

10. Once you come to the desktop, wait for 2 minutes. Then, on the top-right you'll see to the left of the wi-fi icon, a restricted drivers icon. Click it, 'activate' your wi-fi drivers for the broadcom wifi chip. No need to reboot. Just wait 2 minutes after the install's complete. You'll find your wifi accesspoint on clicking the wifi icon. Type in your access password and settings to log into wi-fi. You need internet. Alternatively, you may also use a wired connection, or whatever else.

11. Go to step 0, mentioned here, and do the routine of the sudo commands on the /cdrom /cdrom2 jiggle. Then come back here.

12. Click the Install Ubuntu icon. Once you come to the choice of Allocate Drive Space, choose the third option 'Something Else'.

13. You'll see here:
sda1: EFI
sda2: HFS+
freespace
sda3: FAT32 with 'LIVECD'

notice that immediately after the second partition, the HFS+ one that contains MAC OSX, there's some freespace, perhaps at 134MB or so. That's a very good thing, used by the Mac to update itself and perhaps for upgrades, so please don't touch it.

14. Then, the next immediate partition will be the LIVECD one, in my case, sda3.

15. Now add partitions. 
sda4 should be of type 'Reserved for BIOS' I gave it a delicious 8MB (note 'Mega' and not giga). This is an important partition, and has to be in the first four partitions.

sda5 should be of type ext2, mount-point should be /BOOT. I gave it a generous 2 GB. This is where I'm going to install the /boot files for my installed Ubuntu. Why? Multiple attempts to install it over the 'LIVECD' partition just failed, no matter what I tried with permission-settings. So came up with this idea to have a dedicated partition for each.

sda6: of type EXT4, and for mountpoint / i've allocated 250GB because my data-needs are huge. I'd recommend atleast 20GB to get started. ymmv.

sda7: /swap and this has to be exactly the size of your RAM. this is the clincher. Keep the /swap at the last. This way, your partition numbers are less messy during multiple installs. The exact RAM is because /swap is used while moving the machine to sleep or hibernation modes. I read the swap FAQ on ubuntu documentation thoroughly. That laid my doubts to rest, on whether I needed swap or not. Yes, we all do.

For 'device for bootloader' option, I chose the /boot partition, which is sda5.

16. I then clicked through the remaining install screen-steps. Did choose to install 'restricted plugins' in one of the screens, but no the automatic updates, as I wanted to it first install as is. Ubuntu installed normally. and quickly.

17. Once done. I shut down. Not restart. Then switched on the machine again. Noticed rEFIt choices for one Mac OS, and two Linux Tux choices. The first of these is for the LiveCD and the second for the new install. But first, I synced partitions with rEFIT. Booted into Mac to check it's still safe and sound. Rebooted. Chose the third-option. Got the grub. Pressed 'e' to edit the kernel options, added 'nomodeset' and booted.

18. Once booted, edited grub to add 'nomodeset' in grub's config and then ran the update-grub command. Noticed my wifi settings came through as well.

End-note: Observed i can no longer boot into the LIVECD mode. Also will install tools to auto-mount in read-only the HFS+ partition of the Mac.

Hope this helps.

---

### Post by sdlnxgk on 2012-10-11
> **cweiske said:**
> You can install VirtualBox on OSX and boot a live cd in there. When you unmounted the usb stick in OSX via the CLI diskutil unmount command, you can use it in the virtualbox and write it from there.

I'm unable to boot using the live CD for Ubuntu 12.04 on my MacBookPro 9,2  I keep getting a black screen with a blinking cursor in the  upper left corner of the screen.

---

### Post by niyam on 2012-10-12
MacBookPro 9,2? I'm sorry I don't have access to that beauty so won't be able to offer any assistance for that particular model. Others on this thread may respond. You may also try the other approach mentioned earlier in this thread, of using virtualbox under MacOSX to run the live CD.

regards
n

---

