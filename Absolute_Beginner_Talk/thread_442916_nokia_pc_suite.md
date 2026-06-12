---
title: "nokia pc suite"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-05-14
i isntalled nokia pc suite with crossover linux still i am unable to transfer music to my phone

---

### Post by loell on 2007-05-14
thats because nokia pc suite is designed to natively access hardware in windows, which wine can not.

---

### Post by zerobinary on 2007-05-15
but is there any solution for transfering music to my cellphone

---

### Post by loell on 2007-05-15
what's specific nokia phone model do you have?

how about, transfering it via a card reader?

you can also try [gnokii]("http://www.gnokii.org/")

you can install via  add/remove software

or in the terminal type

**sudo apt-get install gnokii**

---

### Post by Kobalt on 2007-05-15
I use the bluetooth to transfer things from my Nokia to my laptop...

---

### Post by zerobinary on 2007-05-15
nokia 6280

---

### Post by loell on 2007-05-15
i see reading at the phone spec, your options are , 

1. you can transfer files via a card reader if you have one
2. you can transfer files via bluetooth as cobalt suggested if you have a bluetooth module on your computer.

i googled  gnokii and nokia 6280, and the results are not good yet - guess you'll have to wait for gnokii to support your phone and cable connector.

---

### Post by MrKlean on 2007-05-15
There's also a program called  KMobileTools that might help you ; )

---

### Post by zerobinary on 2007-05-15
not working

---

### Post by MrKlean on 2007-05-16
what's that mean ????

---

### Post by Steve H on 2007-05-16
Nokia Pc Suite is one of only two windows programs that I use which WINE cannot handle. After much head scratching I came up with a bit of a long winded way to get it working. It involves my n70, a VMware player XP installation, a SAMBA share and a symlink to my music share on Ubuntu. Complicated but it works.

If you want I'll send/post the instructions for you, just let me know.

:)

---

### Post by AlanR8 on 2007-05-16
I have a 6280 and am running Feisty. I don't need any SW to move files between phone and laptop. I use the supplied USB cable connector and when the phone recognises it and asks what data mode, select data transfer. 

A new "file manager" window will automatically open and you can see the files on your phone. Alternatively just navigate to /media and you'll see your phone as a USB device.....

---

### Post by zerobinary on 2007-05-16
i can't connect it the app can't recongize it

---

### Post by zerobinary on 2007-05-17
then how do u transfer music mp3 files can't be transfer the music folder

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

### Post by jxd on 2007-05-24
> **zerobinary said:**
> i can't connect it the app can't recongize it

Two steps that were not mentioned!

#1) Make sure you have added a USB controller to your virtual machine

#2) Once that is added, you have to go to the vmware console > VM > Removable devices > USB and actually select the Nokia phone. The phone has to already be connected in PC Suite mode at the time before you turn on the virtual machine, then it will be in that list, and just check it. As soon as windows boots up u'll detect the new device and voila, it works.

Hope this helps those of you who are still stuck :)

---

### Post by zerobinary on 2007-06-13
sorry i have a mistake and alanr8's way actually work

---

