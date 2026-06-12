---
title: "VMware"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by That Guy X on 2006-08-22
Hi,I wanted to run windows out of linux so i downloaded VMware.But i have know idea were to go from there.Im running Xubuntu and im trying to install a windows xp home cd :confused:

---

### Post by gruffy-06 on 2006-08-22
Which VMware version do you have?

---

### Post by That Guy X on 2006-08-22
1.0.1 build-19317

---

### Post by gruffy-06 on 2006-08-22
Of VMware Player?

---

### Post by That Guy X on 2006-08-22
yeah VMware player

---

### Post by gruffy-06 on 2006-08-22
VMware Player is designed for running preconfigured virtual machines, which means that you cannot install Windows without further assistance.

I will gladly help you through this, though:

1. Run the following command:

sudo apt-get install build-essential (needs Internet access)

2. Extract the tarball you downloaded to a directory where you have write permissions (e.g. /tmp/)

3. Open a terminal and cd to the vmware-player-distrib folder.

4. Run the following command:

sudo ./vmware-install.pl

5. Follow the on-screen instructions to install VMware Player. Ensure you build the vmmon and vmnet modules if necessary.

Reply back when finished. Good luck!

---

### Post by That Guy X on 2006-08-22
Ok i ran the first command and i got this Setting up build-essential (11.1) ...
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

Also i dont kno what you mean when you say extract the tar ball 

(im a noob :confused: )

---

### Post by gruffy-06 on 2006-08-22
The tarball is the .tar.gz file that you downloaded from the VMware web site.

Did you download the RPM package?

---

### Post by That Guy X on 2006-08-22
no i didnt download it yet i thought that cammand did that.

---

### Post by gruffy-06 on 2006-08-22
I heard of other users that had problems when installing VMware Player using synaptic.

Uninstall the current VMware Player with synaptic and go to:

[http://www.vmware.com/download/player/](http://www.vmware.com/download/player/)

Ensure you download version 1.0.2 in .tar format. Then carry on from step 2.

---

### Post by anaconda on 2006-08-22
I just followed the easy instructions here:

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)

And installed VMWare server (not player!) which was also free.. And everything went just as instructed with 0 problems!!

You have to install VMWare server if you vant to make the virtual machine yourself(=install windowsXP)

---

### Post by btdown on 2006-08-22
Sorry to interject, but I too, just figured out how to install my windows XP  in ubuntu using vwmare. They key here is to install VMware Server, not vmware player. Vmware server is also free, and does everything that vmplayer does, plus allows you to create the virtual machine from a cdrom (or an iso). Download it from the vmware.com page. Its pretty self explanatory to install once you download the tar file..I just hit <enter> for every question is asks you and then ran it, and it was pretty intuitive on how to create the new virtual machine.

---

