---
title: "Ubuntu on external"
date: 2007-08-14
forum: Apple Intel Users
---

### Post by T4tav on 2007-08-14
Hi , I have a 20" imac with a ATI x1600 graphics card. 

I want to install ubuntu onto a external firewire drive and boot from it , any ideas how to do this ? 

Thanks :popcorn:

---

### Post by cyberdork33 on 2007-08-14
> **T4tav said:**
> Hi , I have a 20" imac with a ATI x1600 graphics card. 

I want to install ubuntu onto a external firewire drive and boot from it , any ideas how to do this ? 

Thanks :popcorn:

Please search the forum. Several people have asked this. 

It can be done, but is not straightforward. You still have to make a boot partition on your main hard drive.

---

### Post by T4tav on 2007-08-14
I cant find any clear method on how to do this

---

### Post by viciouslime on 2007-08-14
> **cyberdork33 said:**
> Please search the forum. Several people have asked this. 

It can be done, but is not straightforward. You still have to make a boot partition on your main hard drive.

Now that's not very helpful is it? :rolleyes:

You might like to try this: [http://macubuntu.blogspot.com/]("http://macubuntu.blogspot.com/")

Scroll down to where it says:  NAILED: HOWTO install bootable mac ubuntu on your external firewire harddrive

---

### Post by cyberdork33 on 2007-08-14
> **viciouslime said:**
> Now that's not very helpful is it? :rolleyes:

You might like to try this: [http://macubuntu.blogspot.com/](http://macubuntu.blogspot.com/)

Scroll down to where it says:  NAILED: HOWTO install bootable mac ubuntu on your external firewire harddrive

Too bad that is not for Intel Macs. yaboot is the bootstrap loader for PPC macs.

The only person that has got it to work posted here:
[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

There is no *clear* method to be found.

---

### Post by T4tav on 2007-08-15
How do I go abot putting /boot onto my main drive ?

---

### Post by pxwpxw on 2007-08-15
On the main disk you make 100MB space available for a primary partition. How you do that depends on what you have on the main drive.

Then from the Ubuntu installer partitioner, make the 100MB mount point  /boot, with type ext3 or ext2, and later install grub to that partition (actually grub stage1 goes to the boot sector of the partition).

The installer will put all the boot files and grub menu.lst in 100MB partition.

That system worked for me with ubuntu on a usb flash drive, macosx  and refit and ext2 partition on the main drive.

---

### Post by cyberdork33 on 2007-08-15
So, you will have to resize your OSX partition. You can use bootcamp to do this or 'diskutil resizeVolume' in an OSX Terminal. You can find more info about that here: [http://www.mactel-linux.org/wiki/HOWTO](http://www.mactel-linux.org/wiki/HOWTO) 

Of course, if you have to do that, you might just install ubuntu to your main hard drive unless you are really pressed for space.

---

### Post by T4tav on 2007-08-16
I have a new problem now , When I put the live install CD in , it doesn't accept my bluetooth mouse and keyboard :confused:

---

### Post by cyberdork33 on 2007-08-16
> **T4tav said:**
> I have a new problem now , When I put the live install CD in , it doesn't accept my bluetooth mouse and keyboard :confused:
Nope, you will have to use something wired until you can setup the bluetooth config:
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by T4tav on 2007-08-16
Is it possible to get through the install with a wired mouse ? I havnt got a wired keyboard

---

### Post by cyberdork33 on 2007-08-16
> **T4tav said:**
> Is it possible to get through the install with a wired mouse ? I havnt got a wired keyboard
Sorry, No. The keyboard is more important actually. I do not have a Ubuntu machine to play with right now, but I think there is an onscreen keyboard that you could try. Of course, if you encounter problems booting up or anything (like x fails to start) you will be out of luck.

Do you have another computer? you could install remotely!

---

### Post by T4tav on 2007-08-16
Ive got an acer laptop that im typing this on atm.
 
Remote sounds fun, Sounds hard though
 
[SIZE="1"]I could install ubuntu to the ext drive from my laptop , but I still wouldnt have the boot partition on my imac[/SIZE]

So , How do i remote install ?

---

### Post by T4tav on 2007-08-16
I managed to install ubuntu and it works great , But now I cant log on as there is no virtual keyboard at log on , and i have no keyboard that can talk with usb.  I can read linux from osx, So what can I do ????

---

### Post by cyberdork33 on 2007-08-16
you can edit the /etc/gdm/gdm.conf file to use autologin. That ought to get you into gnome where you can access the virtual keyboard.

Look for this section:
```

# Automatic login, if true the first local screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
#AutomaticLogin=
```set the first part to true, and put your login name on the second line. Don't forget to uncomment the second option!

---

### Post by T4tav on 2007-08-16
ok , Ive done that , and i know im being a pain now , But i havnt got any wifi to get the bluetooth drivers. My wifi card is a Broadcom BCM43xx 1.0 (4.80.79.1). So can I use the madWIFI drivers ?

---

### Post by cyberdork33 on 2007-08-16
> **T4tav said:**
> ok , Ive done that , and i know im being a pain now , But i havnt got any wifi to get the bluetooth drivers. My wifi card is a Broadcom BCM43xx 1.0 (4.80.79.1). So can I use the madWIFI drivers ?

You have a couple options, madWiFi is not one of them :)
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

---

### Post by russell.h on 2007-08-17
Cyberdork, how does one install ubuntu remotely? I'm contemplating getting a "desktop" (more like a server) for college, but I don't want to be bothered to buy a monitor and all that garbage (the need to haul all that crap around is the reason I'm leaving my current desktop home to start with).

---

### Post by cyberdork33 on 2007-08-17
> **russell.h said:**
> Cyberdork, how does one install ubuntu remotely? I'm contemplating getting a "desktop" (more like a server) for college, but I don't want to be bothered to buy a monitor and all that garbage (the need to haul all that crap around is the reason I'm leaving my current desktop home to start with).

What 'I' would do is login via ssh and run the ncurses installer. I don't think the SSH server is on by default though, you might have to modify the image before burning or do some stuff blind before getting started. I used to install via ssh with gentoo when I used it more. This is really kind of an advanced topic and I probably shouldn't have suggested it. Here is some info though:

[https://lists.ubuntu.com/archives/ubuntu-users/2006-March/070706.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-March/070706.html)

It would be easy to install with a monitor, and then just manage it headless though. Borrow one or something. Only need it for the actual install.

---

