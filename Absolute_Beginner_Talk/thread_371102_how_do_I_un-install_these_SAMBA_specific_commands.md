---
title: "how do I un-install these SAMBA specific commands?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-26
I've been having many problems before by following different tutorials on installing SAMBA, so now I want to fix this.  But instead of bug tracking every possible aspect I first want to begin easy by going back to square one.  So how do I un-install the below installs and clean any configuration files from the below commands that didn't work for me?

```
sudo apt-get install smbfs
mkdir Network
sudo mount -t smbfs -o username=[network user],password=[network pass],uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //[whatever you named the Samba server]/[network user] /home/`whoami`/Network
```

---

### Post by raja on 2007-02-26
If you questions is how to cleanly remove the smbfs that you installed with apt-get, all you have to do is
```
sudo apt-get --purge remove smbfs
```

---

### Post by jingo811 on 2007-02-27
tnx raja.
New problem, as I said previously I've been following different SAMBA tutorials which might have made my SAMBA network a little confused namewise.
I have installed using this in terminal:
```
sudo apt-get install samba
```
and I have installed SAMBA trough synaptic.  I think I'm able to clean them both out and start from sqaure one.  But out of curiousity will installing SAMBA twice with these 2 methods complicate the SAMBA setup?
So I won't make the same mistake again and advice other ppl from not doing like so in case they wan't to configure SAMBA properly in the future.

---

### Post by raja on 2007-02-27
As I understand it, any method of installation will check if the latest version of the application is already installed before installing anything. So if you have samba already installed and try to install it again, you should just get the message that the latest version is already installed.

---

### Post by jingo811 on 2007-02-27
tnx again.
Maybe you could help me with my SAMBA problems, I've posted on a different thread before so I know what needs to be done to share between Ubuntu and Windows XP.
But I'm having trouble with the **"names and labels"** when using XP to connect to my Ubuntu Samba share.  This is what I did to install and setup SAMBA.
1.)
```
Right click on folder -> Share folder
```
```
Shared folder -> Share with: Select "SMB"
Share properties -> Name: Specify the share name
```
[IMG]http://i15.tinypic.com/30lhtw7.jpg[/IMG]
[http://i15.tinypic.com/30lhtw7.jpg](http://i15.tinypic.com/30lhtw7.jpg)

2.)
Then I did this to see if there's something I could do, I saw that my names and Workgroup was OK so I didn't do anything to this file.
```
sudo gedit /etc/samba/smb.conf
```

3.)
Then I ran Network wizard on Windows XP, rebooted and got this.  The names and Workgroup are all messed up :confused: 
[IMG]http://i12.tinypic.com/35a7nut.jpg[/IMG]
[http://i12.tinypic.com/35a7nut.jpg](http://i12.tinypic.com/35a7nut.jpg)


I named my Ubuntu sharing PC's workgroup to
[COLOR="Red"]Gamabunta[/COLOR]
and host description to
[COLOR="Red"]%h server[/COLOR]
but I get the extra **(Samba, Ubuntu)(Sanka)** even if my GUI doesn't say that and even the /etc/samba/smb.conf file doesn't have those labels in it.

Despite all this my Ubuntu PC show up under the Workgroup
**MSHOME**
which I deleted and replaced with Gamabunta earlier.
Do you see what I might be doing wrong with the labeling issues :confused:

---

### Post by jingo811 on 2007-02-27
Never mind I solved it myself by typing in this
```
sudo testparm
sudo /etc/init.d/samba restart
```
Ater that there's no more M$HOME to be seen :lolflag: and I got both my Ubuntu and Win XP machines to appear under Workgroup Gamabunta.  Also I got rid of those extra annoying labels for my Ubuntu server.  Finally I've got visual control over SAMBA :KS
Next obstacle is to assign my shared folder to select users on my Network.  That I will do tommorrow!  Now sleepy time......zzzz

---

