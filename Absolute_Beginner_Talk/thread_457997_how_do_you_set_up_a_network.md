---
title: "how do you set up a network"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by cosmoshell on 2007-05-29
how do you set up a network in ubuntu?

---

### Post by LaRoza on 2007-05-29
I am not sure what you are asking, installing samba is neccessary for networking if that is what you asking.

Search for samba to get details, I am not experienced in using it or in networking.

---

### Post by cosmoshell on 2007-05-29
how do you setup a home network. like you can in windows so i can move files to one computer to anouther?

---

### Post by LaRoza on 2007-05-29
A simple network with a crossover ethernet cable is easy.

I am not an expert at this but first you will need to install samba and configure it, I did it once and it was easy, although I do not remember the specifics.

For sharing files, making a separate partition with a FAT32 file system is the easiest way.

---

### Post by cosmoshell on 2007-05-29
this will work between to ubuntu computers?

---

### Post by LaRoza on 2007-05-29
If you have two Ubuntu computers, you shouldn't use FAT32. I recommended FAT32 because it can be used by Linux and Windows without trouble. I thought you were networking with a Windows computer.

It will work fine between two Ubuntu computers. I still recommend a separate partition for shared files, but it is not necessary.

---

### Post by xpod on 2007-05-29
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

Thats what i use between 2 ubuntu pc`s.
Or you could also use ssh but nfs is better for 2 Ubu`s

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

I`m no expert mind you but the basics of setting it up are pretty simple regardless of experience:)
good luck

---

### Post by techno-mole on 2007-05-29
you can set up networking between pc's very easily with fiesty (7.04)  and it works with windows based systems as well.
ok here goes. 9this is for networking ubuntu with windows)
go to --> system --> administration --> then click shared folders, you may get a prompt to install some files, install them.
then under the " general properties " enter the network name (usually MSHOME) then under the "shared folders" click add and select the folders you want to make available on the network.
(make sure that in the "share through" box you select windows networks (smb) )
you should then see your linux system under work group computers (in windows)
you may get asked for a password when you try to access your linux system from a windows pc.
 open terminal and type sudo smbpasswd -a your user name (obviously use your own user name)
this adds a user.
then in terminal type sudo smbpasswd -e your user name - this command should enable the user.
and that should be that.
just one note though - if you have upgraded your kernel networking may not work, i upgraded mine to the latest version and it killed the networking.
cheers

---

### Post by lazyart on 2007-05-29
Great post techno-mole.  There are a lot of suggestions and ideas on getting samba to work in Lin-Win networks.  You beat me to the answer but it is just that simple. :)

---

### Post by helliewm on 2007-05-29
I am trying to share files on 2 ubuntu computers. I have gone to Shared folders added my folder and selected UNIX networks but am very unsure what to put for Add Allowed Host under Properties where do I find my hostname, IP Address or Network this confusing me greatly???

Both computers just run Ubuntu. My desktop is Wired and my Laptop is Wireless.

---

### Post by lazyart on 2007-05-29
You can find your computer name by opening the terminal.  It will show:

username@computername /~:

or something similar. Before the @ is your user name.  After it (ending with a space) is the computername.  Probably "username-desktop" or "username-laptop".

---

### Post by helliewm on 2007-05-29
That does not work I still cannot access my files from either my Desktop or Laptop?

---

### Post by LaRoza on 2007-05-29
To find IP address, open a terminal type: ifconfig

---

### Post by lazyart on 2007-05-29
Can you see the machines when you browse the network?

---

### Post by helliewm on 2007-05-29
Thanks will give this a try a bit later and let you know how I get on.

---

### Post by helliewm on 2007-05-29
How do I browse the network?

---

### Post by lazyart on 2007-05-29
Hmmm... Go to Places>Network and look around.

I'm curious how you knew your networking wasn't working.

---

### Post by helliewm on 2007-05-29
That is what I was doing, just thought I might have missed something. There is nothing in Networking?

---

### Post by helliewm on 2007-05-29
See previous/last post anyone any ideas over Networking? There is nothing in Networking? Its a Wired Desktop and Wireless Laptop I am trying to share files between the 2  Ubuntu computers??

---

### Post by rapsball4 on 2007-05-29
Hi,

I'm also trying to network - Ubuntu Christian Edition to Windows Vista (Home Premium, 64-bit) to SuSE 10.2 (32-bit) is what I'm hoping for, starting with Ubuntu to Vista.  I followed the instructions on the previous page of replies for setting up a network.  Nothing is showing up on the Vista when I look at the Network page still except for the Vista itself, and Windows Network is showing up under Network on the Ubuntu, but nothing when I click on that.

Thanks for any help

---

### Post by helliewm on 2007-05-30
Bump anyone

---

### Post by Docter on 2007-05-30
Here is what I do between two linux machines:

```
scp filename Lee@192.168.0.2:.
```

Scp will copy "filename" to my home folder, denoted by the colon and fullstop ":." via a secure encrypted shell.
```

ssh -XYg Lee@192.168.0.2
```

Will log me in to a terminal on my connected machine with X fowarding, which means that I can call graphical programs running on the remote computer right on my desktop. Better than VNC.

so 

```
sudo nautilus
```

Will open me a file browser with root priiveleges for the remote machine.

As for vista... I guess the best way would be to let vista set itself up automatically then manually set the domain, IP, broadcast, subnet etc on the ubuntu machine. To be honest though, I avoid samba and windows.

---

