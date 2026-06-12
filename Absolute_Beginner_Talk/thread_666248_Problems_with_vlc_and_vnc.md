---
title: "Problems with vlc and vnc"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by huntis619 on 2008-01-13
Hi all. It's been a week since I installed ubuntu and I'm lovin' it. There have been a few problems though (1) I installed vlc player but it wont open media files on network pc.  (2) I installed vnc to remote access said network pc, but when I open  vnc the password option is faded out. I was wondering if something was missing during installation of ubuntu.Thats how it seems to me.I've been windozzzzzzzzed for so long I was thinking about reinstallation of ubuntu.Please help me.

---

### Post by Xavieran on 2008-01-13
Does that network PC have windows on it?
Does it,instead of asking for a password want the user of that computers comfirmation?
Make sure the other PC's vnc server is configured correctly...
Also if worse comes to worse a simple ```
sudo apt-get remove vnc && sudo apt-get install vnc
```
should suffice...

About VLC...have you installed samba and nfs support?
```
sudo apt-get install samba nfs
```

---

### Post by huntis619 on 2008-01-13
Yes the network pc does have windows on it. I was reading about file servers and thinking about turning that desktop into one. Its only used for downloading media files anyway.But another question I have (I'M A TOTAL NOOB) It seems from reading your thread that the desktop with the files on it needs to have samba on it for the vlc player to access its files? I'm also at another quandary. My setup is- (2) laptops AMD64 3000   60GB HD  512MB  RAM NVIDIA GeForce 4 440 Go 64 MB   CD-RW/DVD Combo drive. Ubuntu is installed on one while the other is windows xp  and (1) Desktop AMD64 3400  6 hard drives  (2) 400 GB  (2) 160 GB  (1) 40 GB (1) 200 GB     2GB RAM  ATI RADEON 9600XT PRO (AGP) AND A DVD BURNER. I don't know should I  upgrade my laptops and retire my desktop or  turn my desktop into a server and if I do would I have to upgrade my laptops (upgrade memory hard drive in laptops) or both.

---

### Post by chewearn on 2008-01-13
Just one note: VLC cannot interprete smb://
So the "virtual mount" to a samba share via "Connect to Server..." would not work with VLC.  You have to copy the file to your local harddisk first, or manually mount via smbfs.  (there has been threads in the past discussing this).

---

### Post by huntis619 on 2008-01-13
OK how about this. I already have a windows home network. I can see the other computers on network. I can use totem movie player to view the movies I have on the desktop.So why can't I do the same with the vlc player. Also can totem movie player play rmvb files?

---

### Post by huntis619 on 2008-01-13
I'm sorry I just looked it says I don't have vnc but xvncviewer. I need to work on commands in terminal. how do I open programs using the terminal.

---

### Post by chewearn on 2008-01-13
> **huntis619 said:**
> OK how about this. I already have a windows home network. I can see the other computers on network. I can use totem movie player to view the movies I have on the desktop.So why can't I do the same with the vlc player. Also can totem movie player play rmvb files?

Again, it's the smb:// protocol.  I don't understand the technical aspect, but totem can understand smb:// but VLC can't.  So, unfortunately, totem can play a file directly through samba but VLC can't.

If you really want to use VLC (I'm in the same boat, prefer VLC over other movie players), you need to set-up mount manually.  First install smbfs:

```
sudo aptitude install smbfs
```Then, run these command to mount:
```
sudo mkdir /media/share
sudo mount -t smbfs //<server>/<share> /media/share
```Now, the directory /media/share will appeared as "local" and you can use VLC.

---

### Post by huntis619 on 2008-01-13
~$ sudo aptitude install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
steven@steven-laptop:~$ sudo mkdir /media/share
mkdir: cannot create directory `/media/share': File exists
steven@steven-laptop:~$ sudo mount -t smbfs //<server>/<share> /media/share
bash: server: No such file or directory


OK what did I wrong.

---

### Post by chewearn on 2008-01-13
So sorry, I thought it is self-explanatory, I did not explain it better :(

When you run:
```
sudo mkdir /media/share
```
It says file exist.  Therefore, you should use another, so as not to mask your existing mount; e.g.
```
sudo mkdir /media/share1
```


Then, in the second command, you should replace <server> with your server name or ip; and <share> with the share folder.

E.g. if your server ip is 192.168.1.5, and you are sharing a folder called "public"
```
sudo mount -t smbfs //192.168.1.5/public /media/share
```

---

### Post by huntis619 on 2008-01-13
OK I'm sorry I'm such  a noob (LOL). I followed your instructions and got a SMB connection failure. I did tell you the folder I'm trying to access is on a windows pc.

---

