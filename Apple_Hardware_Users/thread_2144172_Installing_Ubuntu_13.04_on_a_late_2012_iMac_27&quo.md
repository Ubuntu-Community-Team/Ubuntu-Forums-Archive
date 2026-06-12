---
title: "Installing Ubuntu 13.04 on a late 2012 iMac 27&quot; on external drive with no refind"
date: 2013-05-11
forum: Apple Hardware Users
---

### Post by Fun Miles on 2013-05-11
Having benefited from a lot of information around the web, I want to give back by posting information on my success last night in installing Ubuntu 13.04 on my late 2012 iMac 27".
I will try to keep updating this post as I gather more information and test more features and hope it will be of use to some of you.

What I have and wanted:

**I have** 

[LIST]
[*]Late 2012 27" iMac with
[*]Intel i7 3.4GHz CPU
[*]8GB of ram
[*]NVidia GTX 680MX graphic card with 2GB memory
[*]Apple wired keyboard (I believe it is an important detail)
[*]thunderbolt ethernet adapter
[*]Apple bluetooth trackpad (not working yet)
[*]Wired non-apple mouse
[*]Internal 1TB HDD with auxiliary 123MB SSD (Fusion drive)
[/LIST]

**What I wanted: **
[LIST]
[*]run linux (ubuntu has been my go to distro, especially in its kubuntu form for the last 10 years or so) on the iMac
[*]**without** touching or installing anything on the internal hard drive
[*]Run NVidia drivers to get OpenGL 4.3 working (Mac OS is stuck at OpenGL 3.2)
[/LIST]

Last night, after a few attempts and some failures, I finally got all I wanted. Here is how I did it:

I purchased 2 more pieces of equipment:
[LIST]
[*]A 64GB flash thumb drive. I will use it for other purposes, hence the large size, but a 1GB one might be sufficient
[*]An external HD. I do not think the details are important but just for the record, it's a 1TB Seagate Backup Plus for PC and Mac with USB 3.0
[/LIST]

I then proceeded with the installation:

[LIST=1]
[*]Reformat the HDD under Mac OS. This will erase all the data on your disk. You need to make sure the partition table is GUID. Without it, EFI booting will fail (I learned it the hard way). This is a simple operation using diskutility under MacOS. [This page ]("http://linuxmacbookproretina.blogspot.com/2012/12/ubuntu-1304-daily-build-macbook-pro.html")has some information on how to proceed. When you do this, disk-utility will install an EFI partition on the hard drive for you.
[*]Install a bootable Ubuntu 13.04 image onto the thumb drive:
[LIST=1]
[*]Download the image from [http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/) I picked [ubuntu-13.04-desktop-amd64+mac.iso]("http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64+mac.iso") as the image of choice
[*]Follow the instructions on [this page.]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx")
[/LIST]

[*]Plug in the thunderbolt ethernet adapter if you want immediate internet/updates/additional driver downloads (Not fundamental to get basic ubuntu running I believe, but quite handy if you want to get the NVidia drivers working)
[*]Plug in the keyboard and mouse. I am not sure if the installation software can recognize bluetooth.
[*]Plug in the external HDD
[*]Plug in the thumb drive
[*]Turn off your Mac and turn it back on while holding the *option key* down. It should allow you to select your boot drive. Select the thumb drive. It appeared labeled as a Windows drive.
[*]Once booted, you will be greeted by a welcome screen of Ubuntu, asking if you want to install or try ubuntu. I selected *try Ubuntu* and then from there checked I had internet connection (again it may not be necessary to install Ubuntu without updates or additional drivers)
[*]Select the installation from the menu on the right.
[*]Follow the instructions until you get to *Installation type*. The default is to erase the entire disk and install ubuntu. Of course this is not what we want since we want to install on the external drive. Pick the last option, labeled *Something else.*
[*]Next, proceed to partition the HD. On my system, sda is the internal HD, sdb is the SSD drive part of the fusion drive, sdc is the thumb drive and sdd is the external reformatted HD. You can make sure you have the correct drives by looking at the size and types of the partitions they contain. If you do not have a fusion drive, your external HD is probably going to be sdc (or sdb, I am not sure if the order depends on the USB port in which the HDD and the flash drive are plugged in)
[LIST]
[*]Keep the EFI partition that should be there as created by step 1 of the whole process. If it is not there, you may have forgotten this important step. GO back.
[*]Delete the HFS+ partition created by step 1
[*]I created 3 partitions: a 100GB one under ext4 and mounted to /, a 400GB for /home and a swap partition of 32GB.
[*]A note: I believe the partition utility told me it needed to unmount the sdd partition to flush data to the drive. Just accept it. You can also unmount the external HD before starting the installation utility from a terminal window.
[/LIST]

[*]Start the installation process and follow the instructions. It should not have any trouble.
[*]Once it is finished, it will tell you to remove the installation CD before pressing return to reboot. Just press return and unplug thumb drive when the screen is dark.
[*]Hold the *option *key when rebooting. Select the external HD (Still labeled as "Windows" for me) and you will have a working Ubuntu 13.04 on your iMac!
[/LIST]

The final step was to install the NVidia drivers to get OpenGL 4.3 running. Looking at the output of glxinfo, the basic installation only seem to support OpenGL 3.0.
I had read some warnings that NVidia drivers do not work with EFI booting as found on Macs. I still gave it a try and it seems this warning is outdated.
So here is how to install the NVidia drivers:
[LIST=1]
[*]Start firefox and open [the nvidia driver download page]("http://www.geforce.com/drivers") and download the drivers for GeForce 600M (Notebook) series, GTX 680MX, 64 bit drivers for Linux. Some of you may have a slightly different card in your iMac and you should select the correct one, though I believe it is the same actual driver for all those models.
[*]Firefox should download the file into your Download directory.
[*]Once it is downloaded, switch to a console view by pressing *control-alt-fn-F2*
[*]Log in and type:
[LIST]
[*]sudo service lightdm stop # *This stops the X driver and is required by the NVidia installer.*
[*]cd Download
[*]sudo sh NVIDIA-Linux-x86_64-319.17.run  # *can be shortened into*sudo sh NV*
[/LIST]

[*]Follow the instructions. At some point it will tell you that the Nouveau drivers create conflict and propose a way to get rid of them. Accept the solution.
[*]Once done, reboot, once again holding the *option key* down.
[*]At this point I believe you should have a full NVidia based system. For some reason I had messed up something and I had to reinstall the NVidia drivers but after that it worked perfectly
[/LIST]



This is where I am at this stage. I hope this will be useful to others. Let me know if I missed anything or if you have some tricks to make it easier.
Now I need to get the internal ethernet to work and try to get the bluetooth based trackpad and magic mouse to work

---

### Post by Fun Miles on 2013-05-12
Some notes on further experiments:
[LIST=1]
[*]I am unable so far to get the trackpad to work. It does show up intermittently in the bluetooth discovery but then disappears...
[*]The same external hard drive allows me to boot my latest generation Macbook Pro with retina display. :p Though the font and icons are small. I will go read in the relevan thread to see if there is something I can do so that it adjust to the computer on which it was started.
[/LIST]

---

### Post by andsetinn on 2013-10-25
Thank you for sharing. I have 21.5" Imac 2012 (the thin one) and I'm planning on installing Ubuntu, like I have on my laptop. But I don't want to do the install if I'm not sure it will work properly. I don't want to brick my Imac and have to pay fortune to have Apple inc. restore it to previous condition or spend days trying to get Ubuntu to work. So I'm reading posts like yours, trying to find step by step guide for my computer, while I gather courage to go ahead with the install. :)

PS. I use the Imac on a daily basis so the installation _has_ to go seamlessly.

---

### Post by wn1ytw on 2014-02-18
I have a mid-2011 21.5 iMac with an unusable 'superdrive' (don't ask!), OSX 10.9 and have been wanting to get Ubuntu on it also. This sounds like it might do the trick, I have a USB keyboard & mouse in the closet. Anyone else succeed?

scott
EDIT I cannot get the iMac to read the disks or usb...

---

