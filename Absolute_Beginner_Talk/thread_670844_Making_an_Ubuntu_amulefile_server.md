---
title: "Making an Ubuntu amule/file server"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by spranto on 2008-01-17
Hi to you all.

I'm trying to get rid of windows by parts. First I've installed ubuntu in this laptop. Next I'd like to install ubuntu as well in my emule file server but first I need your help. I want that the pc to do:

1-Work without any keyboard, mouse and monitor. Auto start amule.
2-Read/Write on ntfs partitions
3-Allow access, read/write, from windows machines on my network to shared partions.
4-Ability to login remotely, such as windows does

Can you all help me? Thanks in advance!

---

### Post by cmittle on 2008-01-18
1a.  I recently built a file server for my new house.  I followed [this]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/") guide using Xubuntu.  This does not need any peripherals.

1b.  I'm not familiar with amule, but I'm sure you can add it to the list of programs started at login.

2.   I'm not sure why you'd need the server to have the ability to read/write ntfs?  If you're concerned about a remote machine being able to read it you can install something on the windows machine that will allow them to read/write to ext2/3 formats (google "ext3 windows" you'll find it).

3.  The servers drives can easily be mapped in the network connections area of XP.

4.  I can log in via the terminal from my Ubuntu laptop, also I can launch a remote X session (similar to VNC).  I've read that you can use a vnc to connect from a windows computer, but have not tried that.

If you elect to go ahead and follow that walk-through I might be able to help if you have any questions.

---

### Post by spranto on 2008-01-18
> **cmittle said:**
> 1a.  I recently built a file server for my new house.  I followed [this]("http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/") guide using Xubuntu.  This does not need any peripherals.

1b.  I'm not familiar with amule, but I'm sure you can add it to the list of programs started at login.

2.   I'm not sure why you'd need the server to have the ability to read/write ntfs?  If you're concerned about a remote machine being able to read it you can install something on the windows machine that will allow them to read/write to ext2/3 formats (google "ext3 windows" you'll find it).

3.  The servers drives can easily be mapped in the network connections area of XP.

4.  I can log in via the terminal from my Ubuntu laptop, also I can launch a remote X session (similar to VNC).  I've read that you can use a vnc to connect from a windows computer, but have not tried that.

If you elect to go ahead and follow that walk-through I might be able to help if you have any questions.

First of all thanks for your answer.

I'd like to stick with ubuntu since that are more people involved in its improvement/update and even support then xubuntu.

The reason that I want to read/write NTFS is because me file server disk is 250Gb full of data, and to format it and use ext3 would be a pain.

Can you explain better how to login remotly?

Thanks again!

---

### Post by cmittle on 2008-01-19
You can follow the guide I mentioned above for Ubuntu as well (I should mention I skipped page 5 dealing with FTP).  The primary difference between Ubuntu and X/K ubuntu is the desktop environment, alsmot everything else is the same.  

As far as NTFS support ntfs-3g I believe is what you'll want to research.

[This]("http://infectedproject.com/2007/07/09/forwarding-gnome-via-ssh/") is the guide I used to setup my remote desktop.

Hope this helps a little.

Cory

---

