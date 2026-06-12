---
title: "ubuntu can not edit ntfs and can not see fat32 files"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by paulmars on 2007-03-21
files on win ntfs file storage partition (D) can not be edited in ubuntu. Somewhere I found that ubuntu can not edit ntfs files, but can edit fat files. So, in xp I reformated my win storage partition to fat32 and moved the files back to this fat32 partition. Back in ubuntu and file manager now does not see D. It saw D when it was ntfs and I could open files, but not edit. So, I moved the files off D, changed it to fat32, moved the files back to D. I did all this in xp os. So, how do I get ubuntu to see my D again?

Also, my internet shortcuts (favorates) are on D, and they would not open their sites when dbl clicked under ubuntu. Will they work, after D was changed to fat32?

No videos I have work. Sorry for this question, since I have not done a search first, but....It says I need updated codacs, but I see no method to get updated codacs.

Also, after several days with the wrong time, I changed it yesterday. Today, I see that it reverted to the incorrect time. I do not have it set to check and update automatically.

Thanks,
paul      6.10

---

### Post by taurus on 2007-03-21
Can you post the output of this command from a terminal and tell me which one is D that you want to mount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

For codecs and others, here's a link.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by John.Michael.Kane on 2007-03-21
This may help.

Frist make sure all the repos enabled.You can uncomment the lines running the command listed.
```
gksudo gedit /etc/apt/sources.list 
``` you should see a few lines with # next to it remove that symbol.

save the file,and run 

```
gksudo aptitude update
```


Next up installing the files you want.

Run the command listed:
```
gksudo aptitude install totem-xine acidrip brasero libdvdread3 gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui 

```

After that.

Run this:
```
gksudo /usr/share/doc/libdvdread3/install-css.sh
```

You should now have dvd playback.

Note: if playback has issues you can try installing vlc
```
gksudo aptitude install vlc
```

Options for mounting windows partitions:

[** Mounting Windows Partitions in Ubuntu**]("http://www.psychocats.net/ubuntu/mountwindows")

[**ntfs-3g how to**]("http://www.ubuntuforums.org/showthread.php?t=217009&highlight=ntsf-3g")


Hope this helps.

---

### Post by dracomordag on 2007-03-21
there is a ntfs read/write patch for ubuntu, but it sounds like it's a little too late for that

---

### Post by paulmars on 2007-03-21
> **taurus said:**
> Can you post the output of this command from a terminal and tell me which one is D that you want to mount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```


hda2

---

### Post by taurus on 2007-03-21
Do you have any entry in /etc/fstab for /dev/hda2?

```
cat /etc/fstab
```
Edit /etc/fstab from a terminal with

```
gksudo gedit /etc/fstab
```
and remove the old entry for /dev/hda2 if there is one.  Otherwise, add this one to the end of it.

```
/dev/hda2   /media/hda2   vfat   iocharset=utf8,umask=000   0   0
```
Save it.  Now, create a new mount point and mount it.

```
sudo mkdir /media/hda2
sudo mount -a
df -h
```

---

### Post by belikralj on 2007-03-21
If you lost your partition you might want to have a look at the /etc/fstab file. It contains all the mounting (getting ubuntu to see drives) commands that run automatically when you start your computer. So could you post the contents of it. As for a temporary fix here's the command:
sudo mkdir /media/<name>   
- makes a directory in which you want to put the contents of that drive (to mount the drive)
sudo mount -t vfat /dev/hda2 /media/<name>
- the  -t vfat  option says that the partition is fat32
- the /dev/hda2  says that your hard drive is plugged into IDE channel 1 as master and that you want the number 2 partition
- the /media/<name> says that you want that drive mounted (all its files put in a directory) to folder you just made in /media/<name>

It has to be either /media/<your folder> or /mnt/<your folder> because those are the few locations you can actually mount to

---

### Post by belikralj on 2007-03-21
Sorry, I just saw that Taurus posted some links explaining what I tried to say.
Ooops

---

### Post by paulmars on 2007-03-21
Thanks for all the help, but I think I am outta here. Just too many issues. I clicked hybernate when I left and ubuntu closed and the computer offed. Is that really what hybernate means?

Also,if I save a web page bookmark to the desktop I get one file and one folder and sometimes the file works as a link, other times no. Other times it never gets saved at all.

I also save web pages to default bookmarks, but I cant find the bookmark folder anywhere. Some of them are listed in recently used files, but they do not open.

When I turned on the computer after the hybernate off, it froose while booting, so I rebooted....just like windows....hmmmmmm

---

### Post by belikralj on 2007-03-22
I can't help with hibernate cause I never even tried to use it, but for the bookmarks I think you were saving the webpage not the bookmark. It woun't save the link but it will save the entire webpage and put all the images in the folder and the webpage html code in that file which when you open it should open the page in firefox but in the address bar it will say somthing like /home/<your user>/Desktop/<webpage> which means that it is reading from your desktop. Windows does the same thing

---

