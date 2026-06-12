---
title: "Help.. error initializing HAL.."
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by dreaswar on 2007-08-01
hi...

i am just a newbie and need some help. 

till yesterday night ubuntu was worling great

then suddenly screen froze and mouse wouldnt move. i also lost network connectivity

i usea Ubuntu 7.04 on laptop with wireless PCI card. 

when i restarted ( i had to do a hard shutdown and restart) my USB external device ( in NTFS format ) did not auto mount. also i did not get wireless connectivity. 

the network icon said no wireless devices detected.

on boot up i repeatedly get this error .. Internal error.. HAL failed to initialize. 

i am now using my Win XP to post this. I have installed Ubuntu through Wubi. 

please help me ... i was just begening to have fun with ubuntu .. now its pretty much useless without all this.

i have not changed any configurations or anything.. i dodnt have beryl ...

i read somewhere that these can cause similar error messages. 

some post suggested reenabling the dbus will work .... is that the problem??

---

### Post by hamburglar6 on 2007-08-02
try the following:
```
sudo dpkg-reconfigure hal
sudo dpkg-reconfigure dbus
```

and reboot.

---

### Post by ashishgoel on 2007-08-08
SOLVED

Re: the infamous Failed to initialize hal error

--------------------------------------------------------------------------------

I also suffered from this problem. After much searching, it seems that these hal issues might be the result of a recent hal update via Ubuntus automatic update system (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt. But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update. Below are the steps I followed to accomplish this.

First, when this error occured I lost all USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

************************************************** *********************************

Re: Recent HAL update caused frequently failure for "suspend when lid closes"

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...

---

### Post by abzolutxero on 2007-08-27
ok, when i attempt that fix, synaptics wants to get on the internet to download hal 0.5.8.1, but i dont have internet connectivity.  how do i get around this?

---

### Post by bibobx on 2007-08-31
hi i'm a newbie in ubuntu world, i solved the issue "internal errorr : HAL fail initialed"
searching the net i don't remember where sombody dicovered : Copyng the simlink S12Dbus from /etc/rc3.d/ to /etc/rc2.d/ works. It worked for me Greets from Italy:confused::lolflag:

---

### Post by bibobx on 2007-08-31
i forget: Gutsy on amd xp 1800 old machine .....
is this usefull for you ? bye

---

### Post by bibobx on 2007-08-31
anybody there, want ansewr me ?

---

### Post by LinuxNewbie2007 on 2007-09-13
Abzolutxero ---

To install a package when you don't have I-net connection you will need to download a copy of the .deb files from an online source at another computer an then move the files to the computer via CD or USB thumb drive.  Once you have the .deb files you need you will need to run the following in a terminal window: 

```
sudo dpkg -i  *packageName*
```  

This will downgrade the packages for you to the previous version.  You can get the package sources from the following link:

[http://us.archive.ubuntu.com/ubuntu/pool/]("http://us.archive.ubuntu.com/ubuntu/pool/")

This info comes from the following source:

[http://codeidol.com/unix/ubuntu/Package-Management/Install-and-Remove-Standalone-.deb-Files/]("http://codeidol.com/unix/ubuntu/Package-Management/Install-and-Remove-Standalone-.deb-Files/")

---

