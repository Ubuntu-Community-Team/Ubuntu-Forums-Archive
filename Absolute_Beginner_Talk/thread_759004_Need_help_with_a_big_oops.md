---
title: "Need help with a big oops"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by knottshawk on 2008-04-18
I was trying to install synCE.... unfortunately they had me do the following:

sudo rmmod rndis_host cdc_ether usbnet
sudo rm /lib/modules/`uname -r`/kernel/drivers/net/usb/{rndis_host,cdc_ether,usbnet}.ko

This is fine and dandy except that, if I understand those commands, they had me delete my USB drivers.... Problem is that I use USB to get on the internet. SO.... how can I get these drivers and put them on my system?

I have, obviously, other machines with internet access... but I need help!!!

EDIT: Here's the drivers they say to get:
sudo apt-get install usb-rndis-source cdbs
sudo module-assistant auto-install usb-rndis

---

### Post by quirks on 2008-04-18
You can download the packages manually from the Ubuntu servers:

The CDBS package can be found here: [http://archive.ubuntu.com/ubuntu/pool/main/c/cdbs/](http://archive.ubuntu.com/ubuntu/pool/main/c/cdbs/)
It should be either the file cdbs_0.4.51ubuntu1_all.deb or cdbs_0.4.49ubuntu2_all.deb that you need to install. Try installing the newer version first (first file) - the system will tell you when it is not compatible with your system. In that case, try installing the older version (second file).

As for the second package, I could not find it in the repositories so far, but I will keep looking.

After you have downloaded the packages, you can copy them to your Ubuntu machine with a USB-Stick. Then you can open them with Nautilus, which will start the package installer. The installer will probably prompt you for your administrative password.

Tell me if you have any trouble performing the above steps.

quirks

---

### Post by knottshawk on 2008-04-18
> **quirks said:**
> 

After you have downloaded the packages, you can copy them to your Ubuntu machine with a USB-Stick. 



lol.... I can use a CD.... but the USB stick will be hard since USB isn't working. :)

What's nautilus?

---

### Post by Thelasko on 2008-04-18
Edit your sources to include the CD.  In the menus its System>administration>software sources.
In that dialog you should see a box to use the CD.

---

### Post by Thelasko on 2008-04-18
By CD I mean the CD you installed Ubuntu with.

---

### Post by quirks on 2008-04-18
> lol.... I can use a CD.... but the USB stick will be hard since USB isn't working.
Oh ... right, stupid me. :)

I found the other package. You can download it here:
[http://ppa.launchpad.net/synce/ubuntu/pool/main/u/usb-rndis/](http://ppa.launchpad.net/synce/ubuntu/pool/main/u/usb-rndis/)
Make sure you download the correct version for your Ubuntu (feisty, gutsy, hardy).

Nautilus is the file browser in Ubuntu. It is the application that shows when you go to Places -> Home Folder, for example.

quirks

---

### Post by quirks on 2008-04-18
> Edit your sources to include the CD. In the menus its System>administration>software sources.
In that dialog you should see a box to use the CD.
This will only work for the CDBS package, since the other package is not in the official Ubuntu repositories.

quirks

---

### Post by knottshawk on 2008-04-18
How do I know my version....

Sorry for all the stupid questions

EDIT: Nevermind... I found it. Gutsy Gibbon

---

### Post by knottshawk on 2008-04-18
The first file went fine(cdbs), but the second one says "Error: Dependency is not satisfiable: debhelper"

My USB is working now... but my internet is still down. I used to have 2 network adapters listed, and now I have 1.... NOT COOL. Any ideas? Does this second file have anything to do with this? It seems unlikely.... I'm not even sure how to tell if I have an IP address on linux

---

### Post by quirks on 2008-04-18
Ok, I just found the tutorial you are following and I realized that installing these two packages won't solve your problem. They don't contain the files you accidentally deleted in the /lib/modules/... directory. The files are contained in the kernel package. The following procedure should bring the Internet back again.

1. Reboot your system. When it says something like "Press ESC to enter GRUB ... 3 ... 2 ... 1", press Escape to enter the boot menu.
2. The menu gives you several options similar to the following:
```
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
Ubuntu 7.10, memtest86+
```
Select the third entry with the arrow keys (in my case that would be "Ubuntu 7.10, kernel 2.6.20-16-generic"). Do not select something with "(recovery mode)" or "memtest" at the end. If you do not have so many entries, tell me. In such a case we need to proceed differently.
3. Press "b" to boot the kernel. After the system has booted, the drivers should be back, you will probably have network connectivity again, too.
4. If you can access the Internet again (check with Firefox, for example), open Synatic. If you can't, tell me, and I will try to give you further advice.
5. In Synaptic, search for a package named "linux-image-generic". Right-click the entry and click "Mark for Reinstallation". After that, click the apply button. The program will download the kernel package anew and reinstall it.
6. Reboot your system. After that everything should be back to normal again.

If you have trouble, performing any of these steps, post it here. I can't promise you to reply immediately, because I might go to sleep soon, but someone else will probably (or me tomorrow).

quirks

---

### Post by knottshawk on 2008-04-18
Well, mine only had these options:

Ubuntu 7.10, kernel 2.6.20-16-generic
Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
Ubuntu 7.10, memtest86+

So I tried booting into the first one and still don't have internet. It all has something to do with my network interface. I used to have 2 network interfaces (one for IPv4 and one for IPv6) and now I only have IPv6. Which I don't think works with my network. IPv4 is still listed in the devices tab in my network tools. But if I try to configure it, I get "The interface does not exist". 

Like I mentioned, my USB is working now (I can plug a flash drive in it) but my networking is still down.

---

### Post by quirks on 2008-04-19
Sorry, I didn't see your post for a while, because it was on another page. *roll-eyes*

The reason, why your second network device is not there yet, is because you deleted the necessary modules in /lib/modules/`uname -r`/kernel/drivers/net/usb/ and you need to get them back somehow. The modules are contained in every kernel package.

Download a new kernel package and install it over the old one following this procedure:

1. In a terminal, run this command:
```
uname -a
```
The output should be similar to this:
```
Linux Grumpy 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
```

2. If it says something like i386, i586 or i686 near the end of the output, download this package:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb)
If it says something like amd64 near the end of the output, download this package:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-generic_2.6.24-16.30_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-16-generic_2.6.24-16.30_amd64.deb)

3. Copy the file to your Ubuntu PC and double-click it in the file browser (Nautilus) to launch the installer. I'm crossing my fingers for you, that there are no unfulfilled dependencies.

4. Reboot your system. If everything works fine, the second network adapter should be back again. If you're lucky, you might even have an Internet connection again.

Post it here, if anything does not work.

quirks

---

### Post by knottshawk on 2008-04-19
That downloaded a zip with 3 files in it... which do I install? There's:
debian-binary
control.tar.gz
data.tar.bz2

EDIT: within the control.tar.gz is-
control
md5sums
postinst
postrm
preinst
prerm

Within the data.tar.bz2 are 3 more folders:
boot
lib
usr

---

### Post by quirks on 2008-04-19
Doesn't the deb-Package open with **GDebi Package Installer** on your system? It shouldn't open with your archive manager (also, the extension should be .deb, and not .zip). Can you right-click it and say **Open with another program**? Alternatively, you can open a terminal and install the package from the command-line (assuming that you have saved the file to your desktop):
```
cd ~/Desktop
dpkg -i linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb
```
The command produces a lot of output and may take some seconds. After that you must restart your system.

quirks

---

### Post by knottshawk on 2008-04-19
Oops... I got it. But I got an "error: dependency is not satisfiable: module-init-tools"

Well... I'm thinking reformat. Whatta you think?

---

### Post by quirks on 2008-04-19
Sorry, I didn't find the deb-package for your kernel in the first place, so I took the most recent one, but your system obviously doesn't fulfill the dependencies. I think, I found the package for your kernel version now. If you want to give it another shot, try to install this package:

For i386/i586/i686:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.35_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.35_i386.deb)
For amd64:
[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.35_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-generic_2.6.20-16.35_amd64.deb)

Sorry, for the confusion. I'm just trying to help.

---

### Post by knottshawk on 2008-04-19
> **quirks said:**
> 
Sorry, for the confusion. I'm just trying to help.

Oh I know! I really appreciate it...

I'm planning on eventually doing wireless on this system and I'm kinda dreading it after fighting wired network this much.... I'll try the new link and see what happens

---

### Post by knottshawk on 2008-04-19
Did it and no change.... :(
I'm just gonna reinstall. It's not worth all this headache.... Plus, it's a new install so it's not like I have a bunch of stuff saved on here yet.... Thanks so much for all the help.

---

### Post by quirks on 2008-04-19
Oh, I'm sorry for you. The problem is actually not difficult to solve. All you need are these damn modules. Jesus Christ, I could even send you mine (I've got the same kernel on my system), if it wasn't a bad idea to trust some anonymous person on the Internet, who could potentially send you malicious software ...

Anyway, I wish you better luck with your next installation. The bottom line is: do not use USB for network connection. I have always thought this to be a bad idea. I am a friend of traditional network cards and twisted pair cable. :)

quirks

---

### Post by quirks on 2008-04-19
Wait a second:

The installation of the package succeeded? If so, have you restarted your system ever since? You must restart the system for the changes to take effect. If you have already done that, ignore this post.

quirks

---

