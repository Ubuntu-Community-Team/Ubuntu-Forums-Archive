---
title: "AV Linux in dual boot or in a V. box?"
date: 2019-04-13
forum: Any Other OS
---

### Post by rva1945 on 2019-04-13
Hi:

I decided to install AV Linux as I want to use Guitarix. Tried it with the AV Linux live CD and it worked as a charm, Jack was easy to configure and I could play the guitar while a mp3 file was played by the media player (thus playing the guitar on a backing track).

The reason being that running Jack and Guitarix in Ubuntu doesn't work as expected, I get lots of aural clicks and artifacts, but the worse is that I can't play a mp3 file along with Guitarix, no matter the connections in Jack.

This PC has a W7 running and so far I don't want to get rid of it. There are some applications that I use, Guitar Rig to mention one. So I aim for a dual boot (AVL and W7).

I tried to install AVL but the partitions managing was not so friendly  and I ended ruinning everything. It took me hours to fix the MBR and  later the GRUB after I installed Ubuntu 12.04 which I have running in  another PC and works ok. So I now have Ubuntu 12.04 LTS and Windows in a  dual boot system.

1st question:
The first "problem" I noticed was that while AVL in live CD detected the wireless, I selected the network and the password was asked but then it didn't connect. Is that related to the live CD session or what? IF I manage to install it, will I be able to connect to the internet once in AV Linux? The internet connection is via a USB wireless antenna (that of course works fine in Ubuntu and W7).

2nd question:
Can I install AVL without having to alter the partitions? I mean, using the partitions already created where Ubuntu 12.04 is installed, also using the swap and root. This will overwrite Ubuntu but I don't care, as long as I will still keep the dual boot (AVL and W7).

3rd question:
Is it an option to install AVL in a Virtual box in Ubuntu? Will it see the input line? Or will I have to properly set Jack outside the VB as it will inherit Ubuntu environment?

Thanks

---

### Post by yancek on 2019-04-13
> The first "problem" I noticed was that while AVL in live CD detected the wireless, I selected the network and the password was asked but then it didn't connect. Is that related to the live CD session or what?

No.  Nothing is saved/changed on a Live CD, when you reboot any settings/changes are lost.  Are you referring to the passphrase for the wireless or the sudo password?  The only way to find out if you can connect to the wireless in AV Linux is to install it.  I doubt many here are familiar with it.

You should be able to install AV Linux to the same partition on which you now have Ubuntu.  No need to do anything with swap if it already exists.

Might be simpler to install VBox and test it that way.  I'm not familiar with GuitarX so have no idea about that.

---

### Post by wildmanne39 on 2019-04-13
*Thread moved to **Any Other OS a more appropriate sub-forum**.*

---

### Post by rva1945 on 2019-04-14
I know how live CDs work. Been trying live CDs prior to installing since Ubuntu version 9.

I don't think it has to do with sudo as the wireless connection is detected aa well as the networks. And every Linux live session I tried connected to the internet, which in turn is necesssary for installation as it downloads updates.

As for installing a Linux inside a Linux, that is, in a Vbox, will I have to create the partitions as in a real installation?

---

### Post by Frogs Hair on 2019-04-14
> [COLOR=#000000]will I have to create the partitions as in a real installation?[/COLOR] I have some audio applications such as Audacity, Ardour5, and Hydrogen installed I my Ubuntu Budgie and I think for stability you would want an HD installation for audio production unless you have loads of memory . Just my 2 cents worth.

---

