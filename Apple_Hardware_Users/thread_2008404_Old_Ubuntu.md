---
title: "Old Ubuntu"
date: 2012-06-22
forum: Apple Hardware Users
---

### Post by awesomemac on 2012-06-22
Hi,

I have a PPC G4, 500 MHz with maxed RAM (2 GB). I am not able to boot from any of the live CDs and I have gotten the Ubuntu 6.10 Live CD. The problem here is, upon boot, I get an orange screen with a frozen mouse. I Had resorted back to Ubuntu 5.10, and downloaded the Live CD version first to make sure it would work. I get it to boot up, although I can't access the internet. When I open Gimp or Firefox, I get nothing. There is a little thing in the bottom left hand corner stating that it is starting firefox, but then it disappears and goes away. Gimp shows the Loading The Gimp thing but freezes. The OS runs fine otherwise, I can open terminal and any of the games. I know this is an old version, but can you please help me? I know it has long since dropped official support, and possibly community support, but I'd appreciate it if I could get some help. I'll install it tonight and post an update tomorrow stating how the installation went. Also, note that I've tried installing Debian many times along with the Ubuntu 6.10 Alternate install and 10.04 netinstall CDs and always came up with an error at "Select and Install Software". Anyone know what this is?

---

### Post by gordintoronto on 2012-06-22
This web page:
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

tells you how to get a current version of Ubuntu. Old versions have potential security issues, and get no updates. Do not use an old version.

---

### Post by awesomemac on 2012-06-23
I know, although I have such an old processor, that new versions won't work. My processor is a 500 MHz G4. From what I know, it may work with 10.04, but nothing past that. I don't care about security, I just want to get my computer working! I have only a 10.6 install DVD, which won't work with PPC processors. The best I have is mac OS 9, which is too old for my requirements. I know everything there is about security, so security is not an issue. Can you please help me to get it to work?

---

### Post by zombifier25 on 2012-06-23
Then you should not be using Ubuntu at all. Use something really, really light like Puppy Linux or Damn Small Linux.

---

### Post by gordintoronto on 2012-06-24
> **awesomemac said:**
> I know, although I have such an old processor, that new versions won't work. My processor is a 500 MHz G4. From what I know, it may work with 10.04, but nothing past that. I don't care about security, I just want to get my computer working! I have only a 10.6 install DVD, which won't work with PPC processors. The best I have is mac OS 9, which is too old for my requirements. I know everything there is about security, so security is not an issue. Can you please help me to get it to work?

The main reason old computers don't work with Ubuntu is that they don't have enough memory. Your computer has lots. Ubuntu 12.04 should work fine, assuming there is a PPC version. It might be a bit slow.

Oh, it's here: [http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

---

### Post by awesomemac on 2012-06-24
Ok, I'll try it. Are you sure the processor is not too old? I thought for 11.10 the minimum processor requirement was 1 GHz. Maybe it was something else. Like you said, as far as RAM goes, I'm fine, but the only reason why I'm trying 5.10 is 1. It is the last and latest officially supported version of ubuntu, and 2. Since it's older, it might not run as sluggishly on my computer. I did get the 5.10 Live CD to work with firefox, finally, but when I tried to install, it froze at 91% at copying remainder of packages to disk, then restarted. I guess it's a debian problem, and I shall try something newer, as well as 12.04. I have it on my laptop, and it's great! I'll see what happens.

---

### Post by awesomemac on 2012-06-27
Ok, I just did a CLI install of ubuntu 12.04 LTS. I just did the command sudo apt-get install ubuntu-desktop. It is now downloading all the required packages, with 13 minutes and 55 seconds remaining. I'll keep you posted on what happens after the installation. Also, are you sure that 500 MHz is fine?

---

### Post by awesomemac on 2012-06-27
Ok. The installation seems to have done good. I issued sudo reboot and upon reboot, I get the usual ubuntu 12.04 screen, and some orange text, and now a window stating that The System is running in low-graphics mode
your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself. 
I get an X as a cursor and press OK. I am now presented with another window asking me what I'd like to do. I can Run in low-graphics mode for just one session, Reconfigure Graphics, Troubleshoot the error, or Exit to console login. I press Run in low-graphics mode for just one session and get a little window that says "Stand by one minute while the display restarts..." and an ok button. After waiting 60 seconds, I press ok. There is an orange bar, which I imagine is the progress bar, that is all the way filled up. I press OK and I get a CLI login screen. What is this? I know from previous experience that I may need an xorg.conf file. Help please!

---

### Post by Iolo34 on 2012-06-27
Run the following command at the CLI:

lspci | grep VGA

Make note of what graphics adaptor you have. Then go to:

[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

Download a template xorg.conf file that matches your machine and copy it to /etc/X11/ . You may have to edit it to make it work correctly. See:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

for more information on how to edit the xorg.conf.

---

### Post by awesomemac on 2012-06-27
Okay, well, I restart my computer and type in "Linux 1" at the yaboot prompt, and now upon boot I get a message stating the following:
fsck from util-linux 2.20.1
/dev/sda3 contains a file system with errors, check forced.
/dev/sda3: Resize inode not valid.

/dev/sda3: UNEXPECTED CONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
mountall: fsck / [279] terminated with status 4
mountall: Filesystem has errors: /
Errors were found while checking the disk drive for /.
Press F to attempt to fix the errors, I to ignore, S to skip mounting, or M for manual recovery.
I pressed F and rebooted, I get the same message. Did it twice more, same message again. Pressing I goes into single-user mode, I type my root password. Now, my Hard Drive is locked into Read-Only mode! Is this the fault of Linux, or is my HD failing? If my HD is failing, can I install to a 4 GB USB? Thanks.

---

### Post by Iolo34 on 2012-06-28
I'd boot the machine off the ubuntu / lubuntu 12.04 cd and run fsck from there. Note, fsck only works when the drive being repaired is not mounted (hence the booting from cd part).

---

### Post by gordintoronto on 2012-06-29
It does sound like a failing hard drive. To install Ubuntu, use an 8 GB flash drive. 4 GB might get you running, but as soon as you download the system updates, you're dead in the water.

---

### Post by rsavage on 2012-06-29
Installing to a USB device is not straight forward. The PowerPC FAQ has instructions to do it. You could certainly set up a persistent live 'CD' on your 4GB drive (assuming your computer can boot from USB).
 
EDIT: If you ask around I bet one of your friends or family has a spare hard drive sitting around.  I know I have at least 3!

---

