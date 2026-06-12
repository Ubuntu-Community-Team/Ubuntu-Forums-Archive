---
title: "Webcam Drivers"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Abbobo on 2007-04-04
Hi,

Im trying to get drivers for my webcam. Im am running 64bit edgy, and have a Labtec Webcam Pro, shown at the bottom of this page:
[http://www.kaiser-linux.li/index.php/Linux_and_Webcams#Logitech_QuickCam_for_Notebooks](http://www.kaiser-linux.li/index.php/Linux_and_Webcams#Logitech_QuickCam_for_Notebooks)

I downloaded the driver that the page suggests, but I have no idea how ti install it. I have unpackaged the tar.gz to my desktop, but dont know where to put the folder, or what to do with it!

Any help appreciated,
thanks
abi

---

### Post by Maestro23 on 2007-04-04
You are trying to install/compile from source.  Read Section 4 here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

*Also, there should be a README/INSTALL doc in the extracted directory.

---

### Post by Abbobo on 2007-04-04
Thanks. I read that through, and tried the:
make
sudo make install

method, but it doesnt seem to have worked. I am trying to test the cam in xawtv and amsn. xawtv doesnt do anything; terminal returns:
This is xawtv-3.95, running on Linux/x86_64 (2.6.17-11-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

and amsn just dies and wont work again until I restart.

I have been trying to install easycam too, but the repo doesnt work :(

any other tips?
abi

---

### Post by Maestro23 on 2007-04-04
Do you have the "make " command installed on your system?  Are there any INSTALL/README docs in the extracted folder that offer some instructions.

---

### Post by Abbobo on 2007-04-04
I have no idea if i have make installed :S I will look into it. No readme's. Theres a bunch of folders and a changelog, gspca.h, gspca_build, gspca_core.c and Makeuild files.

Ill have a look around about this making business

abi

---

### Post by LaurelLynn on 2007-04-04
Thanks Abbobo,

I couldn´t find drivers for my webcam because I didn´t know the model. Those drivers worked for me.\\:D/ 

Here is what I did:

Note there are two versions of the drivers, the one that
matches your kernal should be the one that starts with a ¨g¨

The steps to Installing are:

Double Click on its Desktop Icon.
       Select Extract from the toolbar

That gives you an unpacked folder named ¨gspcav1-20070110¨

Open a terminal from: Applications -> Accesories->Terminal

cd ~/Desktop/gspcav1-20070110
make
make install    ( uninstall if you latter need to remove it )

reboot

At this point it should have installed the modules and given you
    ¨/dev/video¨ and ¨/dev/video0¨ drivers.

Laurel Lynn

---

### Post by Abbobo on 2007-04-04
glad it helped someone!

I can't get mine to work with either of those drivers. I have the dev.video and video0 files, but still crashing camorama :( maybe it's just not meant to be

abi

---

### Post by LaurelLynn on 2007-04-04
Be sure that you haven´t installed both set of drivers to the same device. Do a ¨make uninstall¨ for both sets of drivers.

Look in the /boot directory to see which kernal you have. Below 2.6.11 it said the ¨s¨ driver and higher was the ¨g¨ version.

It is also possible that driver doesn´t include your webcam. When I Googled for Quickcams I found a host of different drivers for each model. Most were very specific to a particular model number.

Best of Luck

Laurel Lynn

---

