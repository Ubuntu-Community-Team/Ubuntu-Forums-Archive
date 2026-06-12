---
title: "TrueCrypt: Everyday use info, please"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by JAYCEE1 on 2007-08-22
I have read several howtos on TrueCrypt but they were all written for windows users. I'm looking for practical, day-to-day usage info on truecrypting drives.

I am unclear if Truecrypt can be safely used on an existing system or if it needs to be installed prior to installing Ubuntu. Will Truecrypt tear up my computer?

Can I safely TrueCrypt my hard drive that is running fiesty? What are the commands to Truecrypt the whole HD and make a hidden volume?

Can I safely Truecrypt a USB mem stick that has data on it? If so, what are the commands?

Computer is a Dell laptop. Mem stick is a 512 meg cruzer.

Thanks!

---

### Post by AusIV4 on 2007-08-22
I've used truecrypt a fair amount, but I only use it to encrypt things that specifically need to be encrypted. For example, I use GnuCash for managing my finances. I keep "finance.tc" in my Documents folder. I've modified the GnuCash Launcher to run Truecrypt, ask me for a password, launch GnuCash, and when GnuCash closes, it unmounts the volume.

I don't know if you could encrypt the entire system, as TrueCrypt needs Linux to be running before it can decrypt a volume.

This guide: [http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/) talks about how to encrypt your home directory, which should be sufficient encryption for a home or office user (server use may be another story).

Now, this stores the home file system in a file called /root/home.txt. If you have a separate drive, you can replace all instances of "/root/home.txt" in the guide with "/dev/sda" to encrypt a drive (sda) or "/dev/sda1" to encrypt a partition.

---

### Post by JAYCEE1 on 2007-08-22
I guess I'm looking for how to decrypt the volume after I encrypt it. I do not find anywhere the day-to-day usage instructions for this program. What would I do after I power up my computer? How do I put in the password? I'm just not finding useful documentation on TrueCrypt.

I _tried_ to register at the TrueCrypt forum. They are not exactly eager to help over there.

Thanks!

---

### Post by JAYCEE1 on 2007-08-23
I was able to make a keyfile, but when I type truecrypt -vl nothing happens.

What should I do next?

Thanks!

---

### Post by euler_fan on 2007-08-23
> **AusIV4 said:**
> I've used truecrypt a fair amount, but I only use it to encrypt things that specifically need to be encrypted. For example, I use GnuCash for managing my finances. I keep "finance.tc" in my Documents folder. I've modified the GnuCash Launcher to run Truecrypt, ask me for a password, launch GnuCash, and when GnuCash closes, it unmounts the volume.


I use GnuCash and would like to do the same . . . would you please post how you modified the launcher?

Thanks.

---

### Post by Kilarin on 2007-08-27
[quote="Jaycee1"]I _tried_ to register at the TrueCrypt forum. They are not exactly eager to help over there.[/quote]
That seems odd, they have a pretty active forum over there.

[quote="Jaycee1"]I guess I'm looking for how to decrypt the volume after I encrypt it. I do not find anywhere the day-to-day usage instructions for this program. What would I do after I power up my computer? How do I put in the password? I'm just not finding useful documentation on TrueCrypt.[/quote]

I decrypt and mount a truecrypt volume on Ubuntu FF 7 like this:
From the terminal go into the media directory and create a new folder to mount the true crypt volume on.  I named mine tc1 (for truecrypt1), but you can name it whatever you want.  The commands to do this are:
cd /media               <-this takes you to the media folder
sudo mkdir tc1          <-this creates the tc1 folder, you will have to enter your password

Now, you can mount your truecrypt volume on to tc1 using this command in the terminal:

truecrypt -u /media/sda1/mytruecryptvol /media/tc1

of course, change /media/sda1/mytruecryptvol to whatever the location and name of your encrypted truecrypt volume is.

You will now be prompted twice, once to enter your user password for root access, then again for the password of the encrypted volume.  

Once you've typed both in, your truecrypt volume is mounted and available, a shortcut to it should appear on your desktop.

If the volume is formatted as ntfs so that you can also access it from windows, and assuming you have already installed ntfs-3g drivers for read write access to ntfs volumes, change your mount command to:

truecrypt -u /media/sda1/mytruecryptvol /media/tc1 --filesystem ntfs-3g

When you are ready to dismount the volume, enter the terminal command:
truecrypt -d /media/tc1

truecrypt -d
will dismount all volumes that are not currently busy.

Now then, there is another pesky and annoying detail.  having to enter your user password every time you mount a volume, as well as the volume password, is quite... frustrating.  you can eliminate this problem (at the cost of slightly lower security) by doing the following:

export EDITOR=gedit
sudo visudo

now you are editing the /etc/sudoers file.  at end add:
yourusername ALL= NOPASSWD: /usr/bin/truecrypt

Save and exit and now truecrypt will not require your user password.

BUT, if you are mounting the same volume all the time, you don't really want to have to type in the terminal command every time you log on.  So, you can set up a launcher like this:

right click top bar/add to panel/custom application launcher
  type=application in terminal  name=truecrypt-mount              
      command=truecrypt -u /media/sda1/mytruecryptvol /media/tc1
  
of course change the name to whatever you want, and the command to use the correct location of your encrypted volume and its mount point.

You can also create a "dismount all" launcher in a similar manner:

right click top bar/add to panel/custom application launcher
  type=application in terminal  name=truecrypt-dismount-all  command=truecrypt-d
  
  
BUT, while clicking on a launcher is certainly more convenient than retyping the entire command into the terminal, well, you MIGHT just want to have the truecrypt volume mount automatically every time you log on, without you having to click ANYTHING, and this you can do!  You just have to add the mount command to your session startup program list.  And thats actually pretty easy to do:  

System/Preferences/Sessions
From the "Startup Programs" tab, click "New"
  Name=truecrypt-mount
  Command=/usr/bin/gnome-terminal -x /usr/bin/truecrypt -u media/disk/DCH/evol/dch /media/tc1

usr/bin/gnome-terminal -x /usr/bin/truecrypt -u /media/sda1/mytruecryptvol /media/tc1

Again using your own encrypted volume path and mount point.  You need the gnome-terminal because you can't actually enter the password unless you have a terminal window to enter the password in!

One warning when using this method.  If your encrypted volume is on a USB drive, this will probably not work because the USB drive will not be mounted when the startup programs run.

TrueCrypt is really a handy program.  Good luck!

---

