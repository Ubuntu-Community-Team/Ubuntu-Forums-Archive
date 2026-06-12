---
title: "mounting network drives - preliminary questions"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-21
I have a mac G5 and a ubuntu PC on the same network.

am slowly trying to figure out how to mount a drive from the Mac onto the ubuntu desktop.

I gather I need to do something with SMBmount (not the right name, I know).

but I also know that one important step is to figure out what the name is for the Mac drive (which is actually a RAID array).  

Once I know what the name is, then I can use a terminal command to mount it (I guess temporarily at first, but then I can figure out how to mount it permanently.)

So, as a first step, can someone tell me how to figure out the name of the drive...

and as a second step, which terminal commands (SMBmount etc) should I be using to mount it?

(somehow I wasn't able to do this with SMB4K - although I would have loved to use something GUI rather than a terminal command - I got error messages with SM4K saying that submount needed to be implemented, so despite trying to avoid the terminal, looks like I need to use it anyhow!)

anyhow, ubuntu can SEE the mac volume - I can find it very easily in a browser window - but I know that I have to formally MOUNT the volume in order for Amarok to play music files from the volume, which is my primary goal.

thanks again ubuntu wizards!

willfriedwald

---

### Post by reckless2k2 on 2007-09-21
ok...have you enabled samba on the MAC and have you shared the folder with the music you want to mount? i assume firewall on MAC has been opened for samba as well. 

now make the directory on your ubuntu box where you will mount the mac shared folder. 

example:

make a music folder in your home directory NOT using sudo. just right click in there and make the folder. 

go to the terminal and type:

```
sudo apt-get install smbfs
```

once that's install now edit this file (copy it before just in case you blow it up):

back it up
```
sudo cp /etc/fstab /etc/fstab.bak

```

now open for edit
```
gksudo gedit /etc/fstab

```

now at the bottom put a line with the following:
```

//ipaddressoftheMAC/sharedfile /home/whateveryourusernameis/music    smbfs   macusername=username,macpassword=password    0     0

```

i think you get what i'm saying here. if not view that link i gave you before in the other thread. 

now from the terminal type:

```
sudo mount -a

```

now go to that folder in your home directory and see if the music is there. if you get an error with mount -a post it.

---

### Post by deserthowler on 2007-09-22
I run xsmbrowser which allows me to mount a samba share in my home directory.  It is in the repositories and is pretty self explanatory.  

Earl

---

### Post by willfriedwald on 2007-09-22
hey thanks - am out of the home-office today, but will try this as soon as I get back, tom'w or monday...

I have the firewall turned off on the Mac to prevent any possible problems...

another possible issue is that the music is not in the user/music folder in that mac - the only thing that's in there are the XML files that manage iTunes - the music itself is on an other volume.  Am anticipating that this is going to possibly be a problem, although, like I say, ubuntu sees the other volume as part of the Mac on the network.

//ipaddressoftheMAC/sharedfile /home/whateveryourusernameis/music    smbfs   macusername=username,macpassword=password    0     0

SMB4K does tell me the IP address of the mac in a very direct way, so I should take it from that

shared file is the directory on the mac?  or the one I just created on the ubuntu machine

//168.101.1.1./file on ubuntu /home/whateveryourusernameis/music    smbfs   macusername=username,macpassword=password    0     0

will also look into xsmbrowser - that's another GUI networking application?  Is it different from SMB4K?  Will see if I have any better luck.

Okay - thanks again - will let you know. If I can get this going, I will have officially achieved everything I want to do with linux & ubuntu!

will

---

### Post by reckless2k2 on 2007-09-22
> **willfriedwald said:**
> 
shared file is the directory on the mac?  or the one I just created on the ubuntu machine

//168.101.1.1./file on ubuntu /home/whateveryourusernameis/music    smbfs   macusername=username,macpassword=password    0     0


the sharedfile (i should have said folder) is on the MAC. this is whatever directory youhave shared on the MAC that you "see" when doing the samba connection via the browser or smb4k. that's what you are mounting on ubuntu in your home directory under music. 

you're mounting that mac music directory in your home directory on ubuntu.

---

### Post by willfriedwald on 2007-09-23
I turned on "personal file sharing" on the Mac - it doesn't ask me to pick specific files - am hoping that when file sharing is ON, then I can access any file on the mac - hopefully that also means any drive or volume connected to the Mac.  I can certainly access any file or folder or volume through the network (although, as I now know, accessing and mounting are two differerent stories...)

more info:

the folder I just created in the ubuntu home folder is "musichome"

/home/will/musichome

the ip address of the Mac (as seen by SMB4K) is 192.168.1.101

what else do I need to find out?

thanks again - hoping to work on this tom'w ....

W

---

### Post by reckless2k2 on 2007-09-23
your going to need to know what the mount point is on the mac. it's been some time since i played with a mac so i don't remember. you should know or see it on smb4k as well. not sure.

---

### Post by willfriedwald on 2007-09-24
am not sure if you can see this or not ...

[http://docs.google.com/Doc?id=ddh4f5pd_05czj3f](http://docs.google.com/Doc?id=ddh4f5pd_05czj3f)

or maybe you need a password to access a google doc?

will try to post this somewhere & figure out a password I can give you...

---

