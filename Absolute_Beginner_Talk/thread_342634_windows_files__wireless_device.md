---
title: "windows files / wireless device"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Bob Pendleton on 2007-01-20
Hello,

	I have a Compaq Presario notebook running Windows XP Pro and I just inserted an Ubuntu live disk, as I've been thinking of changing OS.

	The CD booted just fine and I examined what I could.  I'm already familier with Open Office, Firefox, and Thunderbird.  I wanted to try out Gimp (see below), and I wanted to get on the internet.

	The hotel has wireless, and Presario uses an Intel PRO/Wireless 2200BG, and I went to [http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/).  It looked fairly intimidating to try to get Linux to drive the wireless.  Moreover, although I made some downloads, they are available within my Windows file structure and not (apparently) to Linux.

	I wanted to use Gimp to manipulate some images, but the images are stored on my Windows partition.

	I'm writing because the Ubuntu blurb says the development team likes to write documentation (now that all the smart folks are wired, documentation is essential to get the rest of the world wired).  So my questions are:

	How do I get Linux to recognize the Windows partition of my hard drive?

	How do I set up Linux to manage the Intel PRO/Wireless 2200BG?

Thanks very much for any help or pointers you can give.

Bob Pendleton

---

### Post by mysticmarks on 2007-01-20
wireless: click system-->admin-->network  you will get a pop up window wireless is off by default. click the radio check box. them select the wireless and do enable properties. if its a nonencrypted open connection, that should be it, if not, you need to config the adapter through the properties and you will need the network name, type of encrypt(wap,wep,etc) and also the network password. if you set it all up and dont get a connection, you may need to switch the option for the network passkey fron hexidecimal to ASCII depending on the routers settings.

windows partition, if its a NTFS file system, you will need to read alot more about accessing NTFS partitions, if it is fat32 you should see it in your places-->computer listings and you can read/write to fat32 with ease. If you wnat to use ntfs there are some not so easy ways to do this, but still very dangerous if your not quite sure what you're doing. The easiest way might be to just burn the files to disc and then load ubunt and the disc will not be a problem to read. This is a bit easier than going through the ntfs access system. If you MUST do it, then you will need to add the ntfs package from synaptic packet manager. you will also need to chang the system-->file sources to include the extra repositories in order to add the package. WARNING!-accessing the NTFS is very risky to that partition, beware!;)

---

