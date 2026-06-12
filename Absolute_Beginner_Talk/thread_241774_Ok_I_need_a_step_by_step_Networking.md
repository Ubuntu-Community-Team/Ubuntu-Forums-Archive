---
title: "Ok I need a step by step Networking"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by joecrouse on 2006-08-22
walkthrough for moving many many many files over a network consisting of two   ubuntu machines. 

the people that I have been asking seem to want to skip lots of steps or they arent explainging exactly what to click and what to type.

---

### Post by John.Michael.Kane on 2006-08-22
Here these should give you what you need

[NFS-HOWTO/index]("http://www.linuxselfhelp.com/HOWTO/NFS-HOWTO/index.html")
[**LinuxTutorialNetworking**]("http://yolinux.com/TUTORIALS/LinuxTutorialNetworking.html")
[**Network-Install-HOWTO**]("http://www.faqs.org/docs/Linux-HOWTO/Network-Install-HOWTO.html")
[**network_howto**]("http://www.neilgunton.com/network_howto/")
[**ssh guide**]("http://www.suso.org/docs/shell/ssh.sdf")
[**shh-securing-ssh-howto**]("http://blogs.ittoolbox.com/linux/locutus/archives/shh-securing-ssh-howto-10640")

---

### Post by tagra123 on 2006-08-22
STEP-BY-STEP HOW TO SHARE USING NFS

Connecting 2 Ubuntu (Linux Computers)

I prefer NFS Shares so this will show how to set up an nfs share.

***_On the first computer do the following_***

Open a terminal

Top Panel Menu :  Applications > Accesories > Terminal

First make sure you have the necessary programs installed.
```
sudo apt-get install portmap nfs-common nfs-kernel-server

```

Make a folder to share with the other computer.
```

sudo mkdir /home/YourUserName/CompOneSharedFolder

```

Open the exports file and enter the share. (You will need to know the IP if Your LAN network.


```
 ifconfig 
```

It will display several lines. Look for a line similar to the following something similar to the following You want the information that is in bold print below. ( the eth0 could also be listed as wlan0 or ath0 )
eth0      Link encap:Ethernet  HWaddr EE:EF:9D:FF:AA:45
          **inet addr:192.168.1.X  Bcast:192.168.1.255  Mask:255.255.255.0**

_**Write the inet addr down you will need it for the second computer too.**_


```

sudo gedit /etc/exports

```
**********************************************
Notice that:
The directory you created above is going to be shared so you enter the complete path to that directory followed by the inet addr 192.168.1.X is replaced with 192.168.1.0 (below) then a  "/" (slash) then the Mask 255.255.255.0 followed by (rw) for read/write access. 

It should look similar to this
```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
/home/YourUserName/CompOneSharedFolder 192.168.1.0/255.255.255.0(rw) 

```

**********************************************

Save the file


Back in the terminal we need to restart the nfs and portmap to update the changes we just made.
```


sudo /etc/init.d/nfs-common restart
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/portmap restart

```

The first computer is ready to share its /home/YourUserName/CompOneSharedFolder

=================================================

***_On the second computer do the following_***

Open a terminal

Top Panel Menu :  Applications > Accesories > Terminal

First make sure you have the necessary programs installed.
```
sudo apt-get install portmap nfs-common nfs-kernel-server

```

```

sudo mkdir /media/SharedFromCompOne
```

Now remember the inet addr from above enter it exactly for (replace the x with your number)

An easy way to remember the command below is 

mount IP:/RemotePath /LocalPath

Enter this in the terminal.
```

sudo mount 192.168.1.X:/home/YourUserName/CompOneSharedFolder /media/SharedFromCompOne

```

You should now be able to read and write files from computer 1 to computer 2

**This SharedFromCompOne should display in nautilus and on your desktop as an icon.

When you are done you can unmount the folder by typing this in a terminal

```

sudo unmount /media/SharedFromCompOne

```

To be able to share folders/directories from the second to the first repeat the above steps except whenever you see CompOneShareFolder Type CompTwoShareFolder


You can also have the shared folder/directory automount by editing the /etc/fstab file. 

Google for: ---- mount nfs fstab


Chime in if you have any trouble.

---

