---
title: "how to install"
date: 2007-08-27
forum: Apple Intel Users
---

### Post by stealthsniper96 on 2007-08-27
once i get a new hard drive for my macbook, im hoping to run ubuntu on it through bootcamp. i read through the "how to install ubuntu on a macbook" guide and i can understand most of it but i have a few questions. first, that is a very long guide, and i didnt read through all of it, so i wana make sure i read everything i need.
>    

1. First, update MacOS X to the latest version using [WWW] Software Update and upgrade the [WWW] firmware to the latest version.
   2.Use the [WWW] Boot Camp to partition the drive in two. When asked whether to create a driver disk, answer "no" and click on "reboot" at the end of the process. This way you have a shrunk Mac OS X partition and a windows partition which you will replace with some Linux partitions.
   3.Get the [WWW] Live CD and boot on it. Choose your language and/or keymap.

    * ||

      (!) To prevent a kernel panic which might occasionally occur, press F6 and enter one of the following parameters at the boot: prompt:
      lpj=8000000 (for 2 GHz MacBook) or lpj=7330000 (for 1.83 GHz MacBook)
      N.B.: It will automatically be applied to the installed system so you won't have to enter it manually ever again!

(note: on mine, it didnt put it in and my system was crashing, so make sure to check your grub setup after install.||

    *Select Start or install Ubuntu.

   1.To install Ubuntu, double-click Install on your desktop, then click through the installer as usual. The defaults are fine most of the time. For the default partition scheme, follow these steps:

    *At step 4, "Prepare disk space", choose Manually edit partition table and click Forward. Delete /dev/sda3 (and /dev/sda4 if it exists) from /dev/sda. Create an ext3 partition taking up all but 512MB of the disk and mount it on /, and create a swap partition taking up the remaining 512MB. Click Forward.

   1.Continue through the remaining questions, and finally click Install to start the installation process.
   2.The installation will be completed without an error. Choose Restart now to reboot.
   3.Hold down the Alt/Option key at boot time to select the operating system to boot. To boot Linux, choose "Windows" (yes, really).
1.Log in on your system. Now let's fix it up. Proceed to the "Common" section below.

> If you have a first generation MacBook (Core Duo) then your wireless should just starting working. Second generation MacBooks (Core 2 Duo) have a newer version of the Atheros Wifi chipset, so you have to install the latest madwifi drivers which came out after the feisty release. [WWW] bug #122703

(On gutsy, you'll find that this is too old, and you should rather use [WWW] [http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz) or grab the sources directly with svn: svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi)

Here are the latest madwifi instructions:

    * sudo aptitude install build-essential
      wget [http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz)
      tar -zxvf madwifi<tab>
      cd madwifi<tab>
      make
      sudo make install   (answer 'r' when asked)

at this point you can reboot and you will probably have working wifi. Or you can play around with these commands.



is that all? if i do that and only that will i have ubuntu running? also, the things next to the *, are they like, terminal commands or sumthing? and the website in the second line thats "wget http://snapshots.madwifi.org....." is that where i go to download what i need? how am i supposed to go there without working internet? or is it only the wireless that doesnt work and i can download the driver connected thru an ethernet cable? thank you in advance for the help. and [here]("https://help.ubuntu.com/community/MacBook") is the original guide.

---

### Post by aysiu on 2007-08-27
Not all things next to * are terminal commands, but some of them are. These, for example, are: ```
sudo aptitude install build-essential
wget http://snapshots.madwifi.org/madwifi-hal-0.9.30.13-current.tar.gz
tar -zxvf madwifi-hal-0.9.30.13-current.tar.gz
cd madwifi-hal-0.9.30.13-current
make
sudo make install
```

---

### Post by stealthsniper96 on 2007-08-27
ok thanks. so all i have to do is enter that stuff in the terminal after i get ubuntu running and the internet will work?

---

### Post by dodgeman79 on 2007-08-27
generally yes it will.  do you plan to turn on security for your wireless?

---

### Post by stealthsniper96 on 2007-08-27
security? you mean like download a firewall? yea.

---

### Post by dodgeman79 on 2007-08-27
that's good, but i was refering to WEP, WAP, and WAP2 wireless security.

---

### Post by cyberdork33 on 2007-08-28
> **stealthsniper96 said:**
> security? you mean like download a firewall? yea.

Hey,

There are several people here in the Apple Intel Forum that will be glad to help you out. You can start off by downloading and burning a copy of the Ubuntu Live CD and booting it on your Mac. You can run a full install of Ubuntu from the CD without changing anything on your hard drive. This would give you an idea of what will work "out-of-the-box". If you are really to install after that, you can go ahead with partitioning and such.

Also, there will likely be a lot of interaction with the terminal. Several commands are entered at the commandline. Such is life in linux.

---

### Post by stealthsniper96 on 2007-09-01
> **dodgeman79 said:**
> that's good, but i was refering to WEP, WAP, and WAP2 wireless security.

yea probably WEP on my home network but i dont know if there will be any kind on my school network.

---

