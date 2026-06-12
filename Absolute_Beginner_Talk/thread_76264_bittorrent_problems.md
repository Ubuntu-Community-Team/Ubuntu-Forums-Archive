---
title: "bittorrent problems"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-10-14
Hi, I try to download files with high seeds and downloads but for some reason my downloads don't go anywhere.  I am on a cable line.  Does anyone else have this problem?  How can I get my torrent files???

---

### Post by DJ_Max on 2005-10-14
What bittorrent application are you using? When you open the torrent file, where do you chose to save the file, and do you choose a proper name?

---

### Post by racermike1967 on 2005-10-14
I'm using the client that came with ubuntu. when i download a torrent, i open it with the client and save the file to the desktop.

---

### Post by DJ_Max on 2005-10-14
This is odd, what version of Ubuntu are you running. I haven't used Gnome-BT on Breezy yet.

---

### Post by nitricacid on 2005-10-15
The fact of the matter is that if no one else has the same file that you are trying to download with bittorent then you are not going to be downloading anything.

Bittorent is a p2p program that searches for the rest of the bit file that you have downloaded.
The only problem is, is that if the file name is wrong or no one else is on their bittorent you will not be able to download said file.
---

I just spend 30 minutes trying to download a bit-file that I got from a website only to not have it download.
I actually found it faster by searching for the whole file and downloading it that way.

---

### Post by Kirky_D on 2005-10-15
It could be that the tracker (website) you downloaded from has blacklisted the default bittorrent port 6881 i believe. you have to change these ports and restart maybe. Because as you say you downlaod a file that has high seeds which should mean the download will go fast. 

If you are using the bittorrent that came with ubuntu this is how you change the ports:
```
sudo gedit /usr/share/applications/gnome-btdownload.desktop
```

You should edit the part "Exec=gnome-btdownload" of the file to "Exec=gnome-btdownload --minport 1234 --maxport 1234" and save.
Hope I helped.

The minport and maxport only need to be about 10-20 numbers apart. For example 

Exec=gnome-btdownload --minport 42000 --maxport 42010

Choose a random number and don't post your ports on the internet as it is a security risk.

Information found from: [http://www.ubuntuforums.org/showthread.php?t=40488&highlight=gnome+bittorrent+ports](http://www.ubuntuforums.org/showthread.php?t=40488&highlight=gnome+bittorrent+ports)

post #2

Hope it helps

---

