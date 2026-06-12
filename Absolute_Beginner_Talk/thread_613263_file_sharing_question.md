---
title: "file sharing question"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-11-14
i have a big ubuntu desktop computer and a little debian laptop (see my sig for specs) the debian computer has no usb and and i need to put files on it that are bigger than what a floppy can handle.

how do i share files between ubuntu and debian (mostly from ubuntu to debian) over a network (the debian computer is commandline only)?

---

### Post by Dr Small on 2007-11-14
If they are both on the same network, you can use Samba to share between systems.

---

### Post by llamakc on 2007-11-14
Or you can install an ftp server on the laptop. Or use ssh to scp files over to it. I recommend installing Debian's ssh-server package and doing it that way.

---

### Post by Inxsible on 2007-11-14
+ 1 on ssh.

---

### Post by Dr Small on 2007-11-14
> **llamakc said:**
> Or you can install an ftp server on the laptop. Or use ssh to scp files over to it. I recommend installing Debian's ssh-server package and doing it that way.
+1
SSH or SCP are alot faster than Samba, but Samba is just more of your casual "Shares", of which you can access in Nautilus. But then again, you can set SCP up like that too ;)

---

### Post by 900donuts on 2007-11-14
i must have said something wrong i want to get the file from the ubuntu computer to the to the debian one and either way i don't know how to ssh, ftp, or samba i'm a total noob at transferring files with linux

---

### Post by Dr Small on 2007-11-14
To get SSH, run:
```
sudo apt-get install openssh-server
```

Then when at one computer, wanting to transfer to the other, use SCP. All of this has man pages, which explain the usage of it, fairly well. Or, you can check out the WIki:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by louieb on 2007-11-14
another +1 for ssh.
[LIST]
[*]install openssh-server on the laptop
[*]give it a static ip (your router can do it easy look of someting called lan ip setup - netgear router others are similar)
[*]on the desktop places >conect to server>server type>ssh
[*]give the ip of the laptop it will prompt to log on. Then it will just be another place in the places menu.[/LIST]Drag and drop from the desktop to the laptop using Nautilus

---

### Post by 900donuts on 2007-11-14
so which computer am i installing ssh on?

---

### Post by Inxsible on 2007-11-14
> **900donuts said:**
> so which computer am i installing ssh on?on your laptop it will be the openssh-server

---

### Post by 900donuts on 2007-11-14
ok i installed it now what do i do

---

### Post by Inxsible on 2007-11-14
> **900donuts said:**
> ok i installed it now what do i do
On your desktop```
sudo scp -v [user@]host1: *filename*
```for eg if you are copying mypic.jpg to your server whose ip is lets say 192.168.1.1 and your user name at the server is donuts, then the command will be
```
sudo scp -v donuts@192.168.1.1: mypic.jpg
```

The above assumes that you have not changed the default ssh port during installation of openssh-server. if you have, then you will need to use the -P flag in the command and supply the appropriate port number

---

### Post by 900donuts on 2007-11-14
i got back this 

shh: droid1138-desktop: temporary failure in name resolution

was i supposed to type the command into the desktop or the laptop

---

### Post by 900donuts on 2007-11-15
i should probably describe the way my home network is set up 

it is 3 seperate computers that physically swap (by pulling the cables) the internet connection (i do have a hub lying from several failed attempts to share the connection through ubuntu)

---

### Post by hyper_ch on 2007-11-15
use the IP address instead of hostname...

OR add the hostanmes to your hosts file:

/etc/hosts
```

192.168.1.11 droid1138-desktop

```

That will tell that droid1138-desktop can be found at IP address 192.168.1.11

---

### Post by Inxsible on 2007-11-15
> **900donuts said:**
> it is 3 seperate computers that physically swap (by pulling the cables) the internet connection The two are connected to the internet at the same time aren't they ?

---

### Post by 900donuts on 2007-11-16
no they plug into the web one at a time

---

### Post by Inxsible on 2007-11-16
> **900donuts said:**
> no they plug into the web one at a timeThen how are you going to transfer files between them via the internet ?

you need to get yourself a wireless router or an IP splitter to connect multiple computers at the same time.

---

### Post by 900donuts on 2007-11-16
i'm not going to transfer file between them using the internet 
this is what i'm planing

[desktop]---[hub]---[laptop]

directly connected and configured on the fly thats what i'm trying to make work

---

