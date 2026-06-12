---
title: "Going to go back to xp can't get wireless working"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Drifter on 2007-06-09
I am on xp now in the forum, I am going to have to go back to xp because of the wireless situation in ubuntu 7.04.  I have as of yet been able to get online with my wireless card.  It is a driver problem i suppose but I don't know where to get one.  What cards if any will work out of the box in 7.04, maybe I can buy a new one and not go back to xp.

---

### Post by jimrz on 2007-06-09
> **Drifter said:**
> I am on xp now in the forum, I am going to have to go back to xp because of the wireless situation in ubuntu 7.04.  I have as of yet been able to get online with my wireless card.  It is a driver problem i suppose but I don't know where to get one.  What cards if any will work out of the box in 7.04, maybe I can buy a new one and not go back to xp.

just posted a reply to your previous posting re your broadcom card...check it out.

hang in there your chipset can be difficult, but it also can be gotten running properly

---

### Post by AAM on 2007-06-09
hey Drifter,
how do you use your wireless card in XP?

---

### Post by Drifter on 2007-06-09
I have an xp driver for it, and it works fine in xp.  The driver will not install in ubuntu.  It is a motorola and they don't have a driver for it.

---

### Post by ghost_ryder35 on 2007-06-09
use ndiswrapper

---

### Post by Drifter on 2007-06-09
what is that and where do I get it.

---

### Post by reidms on 2007-06-09
```
http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29
```

---

### Post by ghost_ryder35 on 2007-06-09
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

---

### Post by Drifter on 2007-06-09
Remember I can't get online in ubuntu would need to do it with xp then try to remember the how to.

---

### Post by Sweet Mercury on 2007-06-09
> **Drifter said:**
> I am on xp now in the forum, I am going to have to go back to xp because of the wireless situation in ubuntu 7.04.  I have as of yet been able to get online with my wireless card.  It is a driver problem i suppose but I don't know where to get one.  What cards if any will work out of the box in 7.04, maybe I can buy a new one and not go back to xp.

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

Try that walkthrough. It helped me out.

If your running Feisty, in step 12, change 'bcmlw5.inf' to 'bcmlw5a.inf' to get it working properly.

edit: That is, of course, if you have the broadcom card as another poster mentioned.

---

### Post by ghost_ryder35 on 2007-06-09
can you get online by plugging a cat5 cable in your computer?

---

### Post by AAM on 2007-06-09
I shall presume that you have an Install CD.

You need to install **ndiswrapper-common** and **ndiswrapper-utils-1.9** from the Live CD. To do that, you start your Ubuntu install and then put the install CD in the caddy. It do two things - open the file manager (Nautilus) and ask you if you want to use the package manager (that's what you want!).

When package manager is running then type 'ndis'.. until the ndiswrapper packages appear. Select both for installation and "apply".

Now you need to get the windows drivers for your chipset, they will be on the Windows install CD. they have the same name and there is a SYS and INF file. Simpolest thing is to find the directory with thise things included and copy them into a single directory on your home folder.

You are now ready to follow the Broadcom HOWTOs listed by others.

---

### Post by AAM on 2007-06-09
As best I can work out this is a listing of the commands that you will need to use:

**have the hardware plugged in, and then enter the following in the terminal:**
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
cd [directory with INF & SYS files]
sudo ndiswrapper -i [file_name].inf
sudo modprobe ndiswrapper
sudo depmod -a
sudo ndiswrapper -m
[INDENT]ndiswrapper -l (this will check that you have driver and hardware detected)
[/INDENT]echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'wlan0 mac [your_card_MAC_here] arp 1' | sudo tee -a /etc/iftab
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
echo 'wireless-essid [your_access_point]' | sudo tee -a /etc/network/interfaces
echo 'wireless-mode managed' | sudo tee -a /etc/network/interfaces
echo 'wireless-key [your_WEP_key]' | sudo tee -a /etc/network/interfaces
sudo ifdown wlan0
sudo ifup wlan0
[INDENT]you should reboot here, and if not working you may need to repeat the last two commands. The following command is helpful in detecting a functioning connection.
[/INDENT] ping [www.google.com]("http://www.google.com") (to see if it working!)

---

### Post by Drifter on 2007-06-09
O K I give up, I tried the how to just can't seem to get it right.  Looks like I need a new wireless card that will work out of the box, any suggustions.

---

### Post by Kobalt on 2007-06-09
What card precisely do you have ? You can find out with the command line ```
sudo lshw -C network
```
Before tryin to install any driver you should know which one to pick depending on your card...

---

### Post by Drifter on 2007-06-09
I have motorola wpci810g

---

### Post by Kobalt on 2007-06-09
Your card can be either a Prism54 or Boradcom based chipset : isn't this displayed bu the previous command ? If not, you may find it running ```
lspci
```

---

### Post by Drifter on 2007-06-09
The card is a broadcom

---

