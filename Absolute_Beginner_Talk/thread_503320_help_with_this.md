---
title: "help with this"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-17
[http://ubuntuforums.org/showthread.php?p=3031482#post3031482](http://ubuntuforums.org/showthread.php?p=3031482#post3031482)

---

### Post by Rocket2DMn on 2007-07-17
For future reference, please restate your problem clearly when you start a new thread and give it a related title.

Now, it sounds like you want to run a Windows program while you have Ubuntu running, without using wine.  A computer can only run one operating system at a time, so it is not possible to run Windows at the same time you are running Ubuntu.  This is why wine was created, and this is why programs like VMWare are really useful - they allow you to run programs that only exist in Windows by simulating a Windows environment.

---

### Post by zerobinary on 2007-07-17
i want to continue that torrent download will vmware help ?????????

---

### Post by Rocket2DMn on 2007-07-17
VMware probably won't help you with your torrent download, but there are torrent programs for linux.  You might be able to open the .torrent file in a torrent client for linux and have it save to the windows directory (assuming your ntfs-3g is working) that you have the original files in, but there are no guarantees.
You might find it easier to just restart your download in Ubuntu.

---

### Post by ugm6hr on 2007-07-17
To continue a torrent:
Pick a Torrent download engine (KTorrent is my choice) and install it from Synaptic (I think there is a default torrent engine in Ubuntu - I use Xubuntu, so not sure which).
Open .torrent file for the download from within Torrent Engine, and chose to save to same location that it was downloading to from Windows.  If you didn't save the .torrent file, you will have to find it again online.
I know Ktorrent (and presumably others) will identify pre-existing parts downloaded, and start where you left off.

---

### Post by zerobinary on 2007-07-17
will transmission work

---

### Post by regomodo on 2007-07-17
> **ugm6hr said:**
> To continue a torrent:
Pick a Torrent download engine (KTorrent is my choice) and install it from Synaptic (I think there is a default torrent engine in Ubuntu - I use Xubuntu, so not sure which).
Open .torrent file for the download from within Torrent Engine, and chose to save to same location that it was downloading to from Windows.  If you didn't save the .torrent file, you will have to find it again online.
I know Ktorrent (and presumably others) will identify pre-existing parts downloaded, and start where you left off.

if it doesn't  tell it to re-check the torrent

---

### Post by zerobinary on 2007-07-17
the nfts configuration tools is not working for me 
not stable is there a way to completely remove it since i try a lot of ways to reinstall it but the previous setting is still there is there
the ntfs patition is motify so other ntfs app won't work is so help

---

### Post by Rocket2DMn on 2007-07-17
You can uninstall ntfs-3g and clean your downloaded packages:
```
sudo apt-get autoremove ntfs-3g
sudo apt-get autoclean
```
then reinstall ntfs-3g - you can follow [this guide]("http://ubuntuforums.org/showthread.php?t=217009"), starting at **"3. Automatic Configuration"**
You should then be able to read your windows partition.

---

### Post by zerobinary on 2007-07-17
is ok fixed now my hdd for window is too small i need more space is there a way to resize my window patition so i have enough space to finish the download how do i use gparted u know one step wrong will kill me so help plz 
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-1-3.png[/IMG]

---

### Post by Rocket2DMn on 2007-07-17
If you really want to do this, you can use either gparted or qtparted - I think these require using the LiveCD, but I'm not sure.  You should start a new thread about this since most people do not want to INCREASE the size of their ntfs partition.

However, perhaps you can just clean some stuff off of your windows drive.  If you have a lot of old garbage on that drive, navigate through it using nautilus in ubuntu and delete what you don't need.  To "empty" the trash and finally clear up the space you need to navigate to the root of the windows partition (say /media/windows/ mount point), show hidden files by hitting CTRL+H in nautilus, and opening the folder called .Trash-yourusername then deleting the files inside (e.g. the stuff you just "deleted" from the ntfs drive).
You would then have more space on your windows partition.

---

### Post by zerobinary on 2007-07-17
cleaning a room for 10 gb u know is almost impossible that patition only has 21 gb in total

---

### Post by zerobinary on 2007-07-17
i use ktorrent to hash check it but it display i only have 0.20% completed 
but bitcomet in window xp display i have 40.9% download

---

