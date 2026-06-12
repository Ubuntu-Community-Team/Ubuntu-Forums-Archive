---
title: "Disc Permissions - Newbie help needed!"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by ChrisCummins on 2007-05-24
Hiya, I have an external hard drive and a slave hard drive on my computer. After an installation of Feisty Fawn 7.04, they are now appearing as 'Video Scratch 1' and 'disk' (the external hard drive was previously used for video editing on a windows pc). 

[[IMG]http://img387.imageshack.us/img387/659/screenshotdesktopbh0.jpg[/IMG]](http://imageshack.us)

However, whenever I try copying something onto them, I get the message "you do not have the right permissions". What I want to do is:

[LIST=1]
[*]Format them
[*]Set them up for general use in Ubuntu - storing mp3's, images etc etc
[*]Rename the drives
[/LIST]

I'm wondering what I need to do to get the right permissions? Thanks alot! :)
Chris

---

### Post by taurus on 2007-05-24
What is the filesystem on that external harddrive?  If it's ntfs, then you need to install ntfs-3g driver before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by richaoj on 2007-05-24
the easiest way to reformat/repartition is using gparted,  
in a terminal

> sudo apt-get install gparted

you will have to unmount the drive before you reformat it. 
there you will be able to reformat to your heart's desire.

to change permissions in general, you have to be the root user.  you can simply do:
Alt+F2

> gksu nautilus

browse to whatever you want to change permissions on,
right click, properties, permissions

---

### Post by ChrisCummins on 2007-05-24
Thanks a lot!

I'm running that gparted program now, but I'm wondering what filesystem I should format it to? fat32, linux-swap etc etc.

@ taurus, at the moment it's ntfs I think, but I might reformat it to some other filesystem, depending on people's responses to the above question.

Thanks again! :) Chris

---

### Post by ICUR2Ys on 2007-05-24
Hi

I had the same problem.  I copied files to a lacie external.  I don't want to lose the files.  I installed ntfs-3g.  When I look at the properties it states that I am not the owner and cannot change to permissions.  Being able use the lacie would really add storage to this system.

Thanks for your help.

dace

---

### Post by mattmole on 2007-05-24
Hi, it depends what you want to do.

If you want to plug your drives into a windows machine then go for fat32. However if this is not an issue then I would suggest ext3. Fat32 also suffers from max file size of 4Gb I believe.

Mattmole

---

### Post by ChrisCummins on 2007-05-24
Hi Matt, the slave hard drive will be for Ubuntu only, so I'll format that as ext3. It would be helpful if I could also plug it into a windows pc, as I'll be using it to store my music library.

Depending on how Dace gets on with the ntfs-3g driver, I might format it as ntfs.

Chris

---

### Post by ChrisCummins on 2007-05-24
Ok, one final question! I have now formatted disk as ext3, but when I open the root file browser using 'gksudo nautilus', it only lists root, desktop and file system in the Places bar. How can I get to 'disk' from the nautilus file browser? Cheers

Chris

---

### Post by ChrisCummins on 2007-05-24
Ok here's a screenshot to illustrate my point: 

[[IMG]http://img489.imageshack.us/img489/4426/screenshotgd8.jpg[/IMG]](http://imageshack.us)

Hope that helps.

---

### Post by taurus on 2007-05-24
You are looking at your root's $HOME directory, /root.  You need to click the Up arrow to move up and over to /media.

---

### Post by Carlos Santiago on 2007-05-24
Use FAT 32.

---

### Post by ChrisCummins on 2007-05-24
Ok this problem is getting annoying now! I've followed your advice taurus (thanks! I knew it'd be something simple like that!), and am on the preferences tab of the properties window. However, whenever I change the folder access and file access tabs and close the window, the selections revert themselves to their original states! Also, when I try and rename the disk, it comes up with an error box telling me it couldn't rename it. Thanks for the help so far! :)

Chris

---

