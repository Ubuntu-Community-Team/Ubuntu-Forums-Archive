---
title: "New to Linux help please"
date: 2012-10-18
forum: Apple Hardware Users
---

### Post by Nagantman on 2012-10-18
Hi, I am completely new to Linux. I have a Macbook pro 13" 2010, 10.6.8 intel core 2 duo. I want to use Ubuntu, but I still want os x on the computer. Could I perhaps put the Ubuntu operating system on a flash drive and when I want to boot with Ubuntu just plug in the flash drive when i start the computer. Then go from there? I just need a starting point, I heard from many that Linux is great so I have been really wanting to try it.

---

### Post by varunendra on 2012-10-18
Hi Nagantman welcome to the forums!
> **Nagantman said:**
> Could I perhaps put the Ubuntu operating system on a flash drive and when I want to boot with Ubuntu just plug in the flash drive when i start the computer.
^exactly that's how you should do it until you are comfortable with Ubuntu and get familiar with some know-how about it. It is safe and ideal for testing a new OS :)

A few elaborations though -
[list]
[*]You can put Ubuntu on a usb flash drive in one of two modes- 1)as a 'Live system', 2) as a 'full' installation. A live system would be just like a 'live' cd/dvd, only booting from usb. While a full installation would be faster and have more functionality.
[*]A full installation needs more read-write operations to & fro the disk where it is installed.
[*]Live installation is compact in size, does not need to 'write' to the media where it boots from (although you can when and if you need in case of a flash drive), and even read operations are far less than a full installation.
[*]Since the number of read-write cycles for a flash drive is very limited in comparison to hard drives, therefore a live installation is recommended for flash drives.
[*]Be aware though- you won't get full functionality and performance in 'Live' mode. Still it is good for testing and getting familiar with the OS, even doing most of the things a full installation can do, just at a lower performance and with a few limitations.
[*]Ubuntu 12.10 is out, but I'd personally recommend [12.04 LTS]("http://www.ubuntu.com/download/desktop") for stability. If your system supports 64-bit, use that one (x86_64), else download the 32-bit version.
[*]If you instead wish to try a full installation on USB, please be careful to install GRUB on the usb drive itself, not on the native HDD.
[*]Live or Full, once installed, you should be able to choose to boot from the flash drive at booting time. (In the latest imacs, the option to boot from a flash drive has been disabled. But it should be available on older systems. If not, consider using a Live CD instead)
[/list]


Once you get familiar with Ubuntu, and wish to install it natively (as a dual boot with osx) on your hard disk, post back here, or better, start a new thread asking help for the same.

About howto create a live usb, please follow the [official Ubuntu guide]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx"), or use [Unetbootin]("http://unetbootin.sourceforge.net/").

Please don't hesitate to ask questions if you have more. The more info, the better the experience! :)

Good luck!

---

### Post by 2F4U on 2012-10-19
If you have enough RAM you can also install VirtualBox on OSX and install Ubuntu inside VirtualBox. That way, when you want to play with Ubuntu you just start VirtualBox and boot Ubuntu in it. You will be able to work both in OSX and Ubuntu in parallel, since VirtualBox runs as an application in OSX.

---

### Post by Nagantman on 2012-10-19
Okay thanks a lot both of you guys. A few more bits of information i had forgotten to mention, 32 bit, 4 gigs of ram. Also i want to be able to like i said keep os x on the computer, I'm doing this on my brothers laptop. He has no interest in Linux atm. So i would need to be sure os x is fine on the computer, as well as the hard drive stays completely stable.

---

### Post by Nagantman on 2012-10-19
I have a macbook pro 32 bit 2010 13" with 4 gigs of ram intel core 2 duo os x version 10.6.8. I am trying to boot up Ubuntu using a flash drive. Trying to use the instructions but i'm having trouble. Using these instructions [http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx) 
I managed to convert the file to a .img but from there on I am a bit lost. Any help would be appreciated.

---

### Post by hakermania on 2012-10-19
Welcome to the forums!

I am not an expert on Mac but I am completely sure that anyone willing to help you will need to know exactly where you've stuck.

---

### Post by 2F4U on 2012-10-19
What is the exact problem? The instructions seem to be pretty straightforward, so at what step do you have problems?
Also, it might be easier to burn the Ubuntu iso on a CD. Some people have reported problems booting from a USB stick.

---

### Post by howefield on 2012-10-19
Thread moved to "*Apple Users*" forum.

---

### Post by mörgæs on 2012-10-19
- and duplicate threads merged. 

Please don't double-post.

---

### Post by Nagantman on 2012-10-19
Sorry morgaes it won't happen again. I'm now at step 9. on these directions [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) After typing in the sudo dd if=/path/to/download.img of=/dev/diskN bs=1m I get "dd: /dev/disk1: Resource busy.

---

### Post by varunendra on 2012-10-19
> **Nagantman said:**
> I'm now at step 9. on these directions [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick) After typing in the sudo dd if=/path/to/download.img of=/dev/diskN bs=1m I get "dd: **/dev/disk1: Resource busy**.

From the [original link I posted]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-mac-osx"), step-8:
> If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive
So did you follow that?
Unetbootin, as I said earlier, is also a nice tool to make these things easier.

I personally prefer a different method which has never failed me -
just use the live cd iso itself to boot a virtual machine > connect the USB to the vm > use the native "Startup Disk Creator" to make the USB live! Simple and reliable, no additional softwares or head-banging required :) (oh, the vm is something I use regularly anyway, so it's not an 'additional' stuff for 'me').

---

