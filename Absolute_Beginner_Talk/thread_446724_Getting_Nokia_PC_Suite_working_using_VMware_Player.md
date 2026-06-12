---
title: "Getting Nokia PC Suite working using VMware Player &amp; SAMBA"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Steve H on 2007-05-17
I have spent some time trying to find a reliable way of getting PC Suite working with Ubuntu, seeing as WINE doesn´t handle it very well. After much head scratching I came up with the following method which involves using a VMware Player installation of XP and a SAMBA Share.

First let´s start by setting up the [_VMware Player_]("http://www.vmware.com/products/player/"), which is virtualisation software that allows us to run XP from within Ubuntu. There are other virtual machine software packages out there, such as Virtual box, but I used VMware, so this thread will deal with that.

To set up VMware follow [_this thread_]("http://ubuntuforums.org/showthread.php?t=380699") by inapad. It is how I set up my virtual XP installation. Personally I deleted my old XP install, resized the partition and then installed XP through VMware. This was to avoid the [_0x000007B_]("http://support.microsoft.com/kb/314082") error that a lot of people (including myself) seem to receive when using their old XP installation. You could of course just do as the thread suggest and use a Virtual disk image, there are plenty about, or you could create one yourself. However you get your ¨Virtual XP¨ working is up to you (don´t forget to install [_VMware tools_]("http://www.advicesource.org/ubuntu/files/windows.rar")), but once you have it working then it is time to set up the SAMBA share.

SAMBA is a file server that can help us transfer files between Ubuntu and the Virtual XP guest. I learned the hard way that just navigating to the partition with my XP guest installed on it, is a sure fire way to corrupt the data. So the easiest and most secure way is to set up SAMBA as a ¨middle man¨ between host and guest.
I followed [_this thread_]("http://ubuntuforums.org/showthread.php?t=296668") by Ziggy72. It is a great thread with lots of help to set up SAMBA.
Personally I had trouble setting up SAMBA because of the smb.conf file I was using had a problem with it. So I have attached a copy of the one I managed to get working. Just fill in the ******´s with your own setup and rename it as smb.conf (or copy and paste the contents)

Now you should have a working XP guest running through VMware and a SAMBA share which can be accessed through XP. Now you can download [_Nokia PC Suite_]("http://www.nokia.com/A4144907"), stick it in your SAMBA shared folder and install it on your XP guest.The next stage is adding links that point to the various folders used by Nokia PC suite. In your SAMBA you can add any number of links to your ¨My Pictures"folder or your Music files/folder. If you find you cannot create a link of a folder or partition then type:
```


gksudo nautilus
```

That will allow you root access through Nautilus, so be careful!! Simply right click on the Folder you want to create a link to and ¨Make Link¨, now move the link to your SAMBA share. It is all now just a case of configuring Nokia PC Suite to look at the mapped drive and the linked folders pointig to your Ubuntu folders.

I hope this helps, it worked a treat for me.

:)

---

### Post by 5T5 on 2007-06-04
Have a look at SymSMB.

---

### Post by jure1873 on 2008-03-25
my pc suite doesn't see the phone from inside vmware. do i have to change some other settings in vmware too?
EDIT: managed to get it working by restarting windows...

---

