---
title: "expose image dd over USB"
date: 2015-11-03
forum: Apple Hardware Users
---

### Post by yasa2 on 2015-11-03
Hello,

I am looking to preform something like Target Disk Mode of Apple.
I have an image dd of usb flash drive and I want to expose it to another laptop using a USB port.
Is it possible? Any leads where should I go look? Or what should I do?

Thank you very much,
Yasa

---

### Post by sudodus on 2015-11-03
You can clone a drive with ***dd*** - copy every byte from the source drive to the target drive. You should realize that dd is a very powerful but also risky tool. It does what you tell it to do without asking any questions. If you tell it to wipe your family pictures by a slight mistake ... It is nick-named disk destroyer. You can use it, but double-check and triple-check that the target drive is really the drive you want to write to.

I don't use Apple computers, so I don't know what you mean by Target Disk Mode, but I can guess that it is writing to a block device (not to a file).

- Have you got an image, and you want to write it to a USB flash drive?

- Or the opposite, a USB drive with a system, that you want to write to an image file?

- Or do you want to clone from one USB flash drive to another USB flash drive?

-o-

Linux operating systems are normally distributed via ISO files. They can be copied to USB pendrives with dd. ***mkusb*** is a tool that wraps a safety belt around dd. It can also expand other [compressed] image files into USB pendrives.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

-o-

If you want to clone a drive, you can also use another tool, ***Clonezilla***, that is safer and also more efficient than dd.

[clonezilla.org](clonezilla.org)

---

### Post by Jacob_Ritorto on 2015-11-04
Let me restate your problem so I'm sure I'm understanding you:
[INDENT]You have a system hard drive image on a usb stick.  You want to write that image to an actual laptop's hard drive.
[/INDENT]

Correct?
If so, here's a brainstorm idea: 

1) Boot your laptop using an Ubuntu Alternate install image from disc or USB, then kill or ignore the installation sequence and use one of the shells on a virtual console to do your dirty work.

2) identify disks on the system by scanning through dmesg to figure out which device is which.

3) image the hard drive. ```
dd if=/dev/<usbstickname> of=/dev/<harddrivename> bs=512
```

Easy, right?  Just do take copious backups of the stick, the laptop, anything that's at all important before you try any of this.  A normal person would at least once make a mistake and destroy something he didn't mean to.

hth
jake

---

### Post by yasa2 on 2015-11-04
Hello,

Thank you for you response!
Let me state again my problem:
I have 2 ubuntu laptop.
On 1 I have an image dd of an hard drive done before and ready for work.
I want to expose this image dd file over USB or some other port on the 1 ubuntu laptop.
Than when I will connect a cable (let say USB male to USB male) to the 2 ubuntu laptop it will recognise my image dd file as a mass storage device, just like I connected 
a flash drive to the 2 ubuntu laptop but it will actually be the image dd.

Thank you,
Yasa

---

### Post by sudodus on 2015-11-04
Your image of the hard disk drive can be cloned to another drive (mass storage device) of the same or bigger size.

It can be a USB pendrive (if it is big enough), or an HDD or SSD. The HDD or SSD can be connected internally via a SATA connector or cable, or externally via eSATA or USB.

If the Ubuntu system is installed with the free drivers (no proprietary drivers for graphics or wifi), you can expect that it is portable, that it works in different computers. I have made and tested several such systems, and I know that it works.

If you want the system to work in both UEFI mode and BIOS (alias CSM alias legacy) mode, it is more complicated.

-o-

I think you can simply go ahead and try :-)

- I'm still not sure what you want. What do you mean by expose?

- What answer are you waiting for? What should we try to explain better?

---

### Post by yasa2 on 2015-11-04
Hey,

I think you didn't understand what i am trying to do...
I have a laptop with image dd file and I want other laptops to be able to access this image file as mass storage device using one of the ports in the laptop.
Like Target Disk Mode of Apple Mac laptops.
[https://en.wikipedia.org/wiki/Target_Disk_Mode](https://en.wikipedia.org/wiki/Target_Disk_Mode)   video - [https://www.youtube.com/watch?v=etMf9w6Ko8M](https://www.youtube.com/watch?v=etMf9w6Ko8M)
The only different is that I want to make it of an image dd file and not a real whole hard drive.

Yasa

---

### Post by sudodus on 2015-11-04
No, I did not understand. But now I know about Target Disk Mode of Apple Mac laptops.

I don't think there is something 'exactly the same' in Ubuntu. If there is, ***I hope and think someone else who reads this thread will chip in and help you***.

But it is rather easy to make standard Ubuntu and the Ubuntu flavours (Kubuntu, Lubuntu, ... Xubuntu) into servers. Install ***openssh-server***, and connect from another computer via the network (wired 'ethernet' is usually faster and more reliable than wireless).

```
sudo apt-get install openssh-server
```

See this link for detailed instructions

[OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

You can login remotely via ***ssh*** and start file transfers via ***sftp***, or use some GUI tool. Most ***linux file browsers*** have built-in support for ssh/sftp. You can also use ***filezilla*** or ***Winscp***.

This way you can get remote access to all the drives (mass storage devices) in the computer where you have installed openssh-server.

-o-

If you want the fastest possible connection, it might be better to move the source drive to the target computer, and connect it internally or with eSATA or USB 3. But with Gigabit LAN, you have quite good transfer rate via the network. (The network is faster than USB 2.)

---

### Post by Jacob_Ritorto on 2015-11-04
So, Yasa, your target disk mode idea sounds a bit alien in the ubuntu world.  I've done target disk mode in the mac world and I don't know of an equivalent in ubuntu, but I have to admit that I'm more of a unix guy than a linux guy.

Anyway, if we forget about the "how" and focus on the result you want, I'll rephrase again and you can tell me if I'm right this time:

You have a file that's a hard drive image.   It was made using dd.  You want to write this image.dd file directly to a real hard drive on another target laptop and boot it.

Correct?

I like the idea of doing it over the network best, myself.  Heck, you could just simple unix stuff for this.  Stream out the image file on the first laptop using something simple like nc.

```
cat image.dd | nc -l 8000 
```

Then temporarily boot the target laptop from an ubuntu alternate install (cd, usb, whatever).  

On the target laptop, write the local disk by consuming the host laptop's nc stream.

```
nc <hostLaptopIP> 8000 | dd of=/dev/sda 
```

Reboot the target machine and you're done.


You'll want to verify disk names by looking at dmesg or something on the target, of course, but this is a likely guess.  Again, it sounds like you care nothing about the previous contents of the target laptop's disk.  But if you do, remember to back it up as this method most deliberately clobbers the disk.

--jake

---

### Post by yasa2 on 2015-11-04
Thanks for all your ideas.
My main goal is to boot from this image file but with out needing to write it back again to a mass storage device.
But I liked your idea of doing boot from network. Is it possible to use nc in order to expose the image file but to perform a boot using net boot(not involving any other boot such as ubuntu)?
I mean direct boot from the image file...

Yasa

---

### Post by Jacob_Ritorto on 2015-11-05
nope, I don't know of a way to expose stuff like that with ubuntu, but bear in mind that it's still kind of a new toy to me, so keep asking around.  closest I'd guess you could get to that in this world would be via some sort of virtualisation software where your virtual machine uses the image as its drive image.  And yeah, Apple's target disk mode would be perfect for this.  Some servers I've worked with were able to jump on an iscsi lun as root filesystem, but that was back in the glorious days of OpenSolaris and big centralised, scary SANs, etc.  This practise seems to have fallen by the wayside as there's too large a single point of failure and people learnt about that the hard way.

Hm, just remembered -- There is the good old eighties Sun/BSD unix way of doing rpc netboot via NFS possibly these days mixed with PXE boot, but the scope of that is probably enormous for what you're trying to do here.   That said, it's *really* cool when it's working.  I know the BSD and Illumos guys can so it, not sure about Linux.  If you want to investigate this route, I'd ask around in communities who get excited about hosting, scalability, etc. and somebody may have more answers.

---

### Post by sudodus on 2015-11-05
> **yasa2 said:**
> Thanks for all your ideas.
My main goal is to boot from this image file but with out needing to write it back again to a mass storage device.
But I liked your idea of doing boot from network. Is it possible to use nc in order to expose the image file but to perform a boot using net boot(not involving any other boot such as ubuntu)?
I mean direct boot from the image file...

Yasa

When you boot from an Ubuntu [ISO file via grub](https://help.ubuntu.com/community/Grub2/ISOBoot), you boot via an image file without needing to write it back again to a mass storage device.

But I guess your image file is not an ISO file. Like suggested by Jacob_Ritorto, it is possible to create an virtual machine, for example with [KVM and VirtManager](https://help.ubuntu.com/community/KVM/Installation). I have booted such virtual machines from dd images of installed systems (in other words without writing back again to a mass storage device).

---

### Post by yasa2 on 2015-11-07
Thanks for the suggestions.
I will try to ask some other communities as well.
I hoped that this could be possible using Ubuntu but I will keep trying...
If any one will have more ideas I would be very happy to hear :)

---

