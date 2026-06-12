---
title: "Remove grub?"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-02-28
So I had two hardrives in my desktop. A Windows install and a blank.

I had them both on the same cable.
WIndows as the Master, and the Blank as the slave.

I installed Xubuntu on the blank,A
hoping that I could just switch between the OS by selecting which hardrive to boot from in the BIOS.

Unfortunately it installed GRUB on the Windows install, without even asking me.

I cannot use the BIOS to select which OS I want, only if I select the master for boot and use grub to do it.

And the most insane part...I cannot boot Windows unless I have the LInux HDD hooked in.
That is utterly ridiculous. If my Linux HDD gets trashed for any reason it will also make my Windows HDD uselss (I cannot re-instill Windows because I have no back-up CD

So if anyone knows how I can remove Grub from my Windows HDD,
and just be able to switch OSs in the BIOS it would be greatly appreciated.

I hope in upcoming distros they remove this feature or at least let you have the option.
Because this is incredibly dumb, especially in the case where you install Ubuntu to an external hardrive.

---

### Post by hyper_ch on 2008-02-28
> **Xarok said:**
> Unfortunately it installed GRUB on the Windows install, without even asking me.

I guess you used guided partitioning and even then you could have, before the actual partitioning took place, checked the operations that were selected to be done. The last one of those was installing grub. So it actually DID ask you.

> **Xarok said:**
> 
And the most insane part...I cannot boot Windows unless I have the LInux HDD hooked in.
That is utterly ridiculous. If my Linux HDD gets trashed for any reason it will also make my Windows HDD uselss (I cannot re-instill Windows because I have no back-up CD
That's wrong. Grub just did install itself on the main harddisk and have a pointer to the /boot partition. You can setup a /boot partition on your windows drive also... then you won't have to hook in your linux hdd... it is not ridiculous ;)

> **Xarok said:**
> 
So if anyone knows how I can remove Grub from my Windows HDD,
and just be able to switch OSs in the BIOS it would be greatly appreciated.

(1) You'll have to install Grub on your second harddisk, otherwise linux become unbootable
(2) Search for restoring the Windows boot loader.

> **Xarok said:**
> 
I hope in upcoming distros they remove this feature

I hope not so... 

> **Xarok said:**
> 
Because this is incredibly dumb
The way grub works is actually quite smart.

---

### Post by jken146 on 2008-02-28
> **hyper_ch said:**
> I guess you used guided partitioning and even then you could have, before the actual partitioning took place, checked the operations that were selected to be done. The last one of those was installing grub. So it actually DID ask you.


That's wrong. Grub just did install itself on the main harddisk and have a pointer to the /boot partition. You can setup a /boot partition on your windows drive also... then you won't have to hook in your linux hdd... it is not ridiculous ;)


(1) You'll have to install Grub on your second harddisk, otherwise linux become unbootable
(2) Search for restoring the Windows boot loader.


I hope not so... 


The way grub works is actually quite smart.
+1

---

### Post by Xarok on 2008-02-28
So when I boot off the windows HDD without the Linux HDD it gives me "Error 21"
how can I fix this?

Also If I remove the windows HDD and just use the Linux HDD I get the grub screen, but when I select Linux it won't run, I get "Error 21: Selected disk does not exist"

My Xubuntu install in currently messed up, so I have to reinstall from scatch.
If I reintsall will it install another grub? What will happen?

---

### Post by hyper_ch on 2008-02-28
> **Xarok said:**
> Well I did select the blank drive for installation.
Should have warned me that it was going to mess with my windows HDD.
You were warned but you did not read the text... I know, reading text is annoying... but sometimes it really does help...

> **Xarok said:**
> 
I believe Grub is installed on the Linux HDD, because when I select it for Boot in the BIOS, it shows grub... but it can't boot anything.


And if Grub is installed on the Windows HDD, why can't I run Windows with the Linux HDD gone?

The bootload is installed on your windows disk. Only grub config files and stuff is installed on the linux disk in /boot/grub

> **Xarok said:**
> 
Why in Gods name would it require me to have the Linux HDD attached to run the Windows HDD?
God has nothing to do with that... and if you read what I wrote you'd know the answer.

> **Xarok said:**
> 
You have to admit that *IS* quite dumb.
I don't have to admit anything... but you are wrong. Your setup is not typical. 99% of the users don't install an OS on a removable drive (at least not nowadays). So it is not quite dumb ;)

---

### Post by Xarok on 2008-02-28
Sorry, I'm stressed. I've been having a lot of ocmputer problems today.

So I'm using Xubuntu 6.06 right now, which is messing up (It can't update for some wierd reason).

If I use 7.10 to make another install will it mess anything up?

Will it install another grup? Can it just use the same one?

I can't restore the Windows bootloder because I have no windows CD for this computer.
I have a windows CD for another computer. Will that work?

---

### Post by bumanie on 2008-02-28
You should read this page
 [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm). 
It explains virtually everything there is to know about grub and provides a number of solutions to problems. I don't know how to reinstall windows mbr without a disc that's why I suggest you read this.

---

### Post by forestpixie on 2008-02-28
you can use supergrub apparently

---

