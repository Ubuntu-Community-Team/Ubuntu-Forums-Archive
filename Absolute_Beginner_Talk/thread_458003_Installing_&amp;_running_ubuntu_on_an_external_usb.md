---
title: "Installing &amp; running ubuntu on an external usb drive."
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by realmendont on 2007-05-29
Wanting to install and run ubuntu on an external usb drive. Is this possible? Will it run as normal?

Thanks in advance.

---

### Post by LaRoza on 2007-05-29
It is possible, make sure you can boot from USB drives though.

If your computer can boot from USB, it probably is not first on the list, by default, the boot order is: floppy,cd,first primary partition on a master drive, usb

---

### Post by realmendont on 2007-05-29
Thanks!

---

### Post by Mykle87 on 2007-05-29
It is very possible. I have done it a couple times. The biggest problem you will run into is with GRUB. If you want to boot and run Ubuntu entirely off your external hard drive, make sure you put GRUB there instead of overwriting the MBR on your main drive. You have to remember the name of your external hard drive (something like "/dev/sdb"). Also I recommend using the alternate desktop cd and use the text installer. I hear you have more configurable options. Check out this thread if you run into problems with GRUB and also to configure GRUB:
[http://ubuntuforums.org/showthread.php?t=439411](http://ubuntuforums.org/showthread.php?t=439411)

Good luck!

---

### Post by realmendont on 2007-05-29
Thanks Mykle87! I'm new at all this computer stuff, I might be in over my head. I do have a few more questions.

1) Can I get a live cd shipped to Canada?
2) When you run the cd, can you store the ubuntu program directly on external drive?
3) Is this wise to install ubuntu by an individual with limited knowledge in computer programming?

---

### Post by nutz on 2007-05-29
I have my Ubuntu installed to an external USB HD and it works flawlessly! The trick to getting it to work right is disabling any other hard drives in the system so the installer doesn't see them. If the installer can see the internal disks it will put grub on them instead of the external drive and you will have issues. It is also VERY important that you make the USB hard drive the first boot device. I have done several of these now for myself and friends so if you want a more detailed description just let me know but the basics are something like this&#8230;   This method should work for installing to any USB storage device, I have used it with success on many jump drives and external USB hard drives...

Disable any other drives in the system such as internal hard drives. In some cases the bois will not give you the option to completely disable and hide a drive (like with some laptops). In these cases you will have to physically disconnect the internal drive! 

I ran into this issue on my Dell Latitude D620, the bios does not allow you to completely disable and hide the internal drive. So after a visit to Dell's web site I found the documents that detailed the procedure for upgrading the internal hard drive. I used the information in these documents to disconnect the internal hard drive. All I did was remove two screws and it slid right out; took no more than 5 minutes and only required a phillips head screwdriver!

On a laptop this is often very easy since they are setup to make stuff like the hard disk easy to swap these days. Check with the manufacturer for your device for procedures on upgrading or replacing drives. That should tell you how to do it&#8230;

Next make sure you have legacy devices or compatibility mode supported in your bios. This will make your bios initialize the external drive so it can boot to it. Then make sure the external USB drive option is the first boot device selected. Your boot order should look like this...

1.USB HD
2.CD
3. Nothing!

Now you are ready to install! 

With the external drive you want to install Ubuntu on disconnected, boot up to the CD install image. 

When you get to the screen that prompts you to select your boot option do not continue!

At this time you can plug in the USB hard drive and power it on. Make sure it is properly connected and ready to go.

Now you can continue with the boot process to the live desktop for install.

Once you get through all the mundane install stuff and make it to the part where you are partitioning your drive make sure there are no other drives visible and that you are working with the correct drive. It should show up as SDA or SDB while internal drives will show up as HDA. 

If everything looks good then proceed with the install; it will format the external drive and install Ubuntu on it.

After the install you will want to enable your internal hard drive and set your boot sequence as follows making sure the USB HD option is always first.

1.USB HD
2.Internal HD
3.Whatever else...

I am sure there is tons of ways to install Ubuntu on an external drive but this was the easiest and cleanest method I came up with. When the USB drive is not plugged in it will boot windows normally; no changes have been made to the internal drive during this process! When you want to boot Ubuntu just plug the USB drive in and boot to it. Simple as that and the performance from the external USB hard drive is much better than you would think. In fact I don't notice any difference in performance from the external or internal hard drive. This method also facilitates using your Ubuntu installation in multiple hardware configurations...

---

### Post by realmendont on 2007-05-30
Thanks a lot for all the great insight to USB installation. If I couds only get my Live CD, I would be up and running.

---

### Post by nutz on 2007-05-31
> **realmendont said:**
> Thanks a lot for all the great insight to USB installation. If I couds only get my Live CD, I would be up and running.

Is downloading it not an option?

---

### Post by realmendont on 2007-06-05
Tried downloading Ubuntu from one of the University's servers. Didn't work. I'll try again from one of the other download centers.

If you can't boot from USB port, can this still work?

---

### Post by nutz on 2007-06-23
> **realmendont said:**
> Tried downloading Ubuntu from one of the University's servers. Didn't work. I'll try again from one of the other download centers.

If you can't boot from USB port, can this still work?

No.

Your computer must have the ability to boot to a USB drive in order for it to work. If you do not see this option in your boot menu or one like it then chances are your computer does not support USB device booting.

---

