---
title: "3 Newbie Questions, SSH / Network / Formatting Drives"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-01
I have setup Ubuntu on 2 different boxes, 1 desktop and 1 server.  I have a few questions to get them configured the way that I need them.

1)  By default, my Ubuntu Server machine setup on a network group called MSHOME.  How do I change this?  I have the desktop GUI installed on this box, so either cmd line or thru the GUI, I need to change it.

2)  I think that I successfully installed SSH server and client on each of these machines, but I can't find it.  How do I activate and configure the SSH server in Ubuntu?

3)  I have 2 SATA drives installed in my machine running Ubuntu Server 6.10.  However, the OS doesn't seem to detect them.  There is no option for "disks" under the Administration Menu on Server as there is on Desktop.  And when I go to Computer, it doesn't show these disks at all.  The machine shows the disks in the bootup menu under the SATA RAID controller, but Ubuntu isn't seeing them for some reason.

4)  I have also installed VMware on the Desktop machine so I can run some Windows programs, but for the life of me, I cannot find it anywhere.  I tried adding it in the Ala Carte menu and it said that it found it, but when I try and launch it, nothing happens.

Thanks for all the help

---

### Post by kc5hwb on 2007-04-01
anyone?

---

### Post by rada on 2007-04-01
> **kc5hwb said:**
> 
2)  I think that I successfully installed SSH server and client on each of these machines, but I can't find it.  How do I activate and configure the SSH server in Ubuntu?

well, I'm hesitant to reply.. I may be newer than you. But gui-wise you can find out what files each package has installed by finding the package in synaptic, clicking properties, and looking in the installed files tab.  (I, uh.. :redface: still haven't learned to use apt and locate very well yet.)

openssh-server ran as soon as installed for me. You should be able to ssh using passwords right out of the box.

```
$ ps -e | grep ssh
```
should show sshd (server) and ssh-agent (client) both running.

[[COLOR="Green"]This guide [/COLOR]]("http://doc.gwos.org/index.php/SecureSSH#Avoid_Using_Passwords") helped me configure my ssh. But I have about the simplest network you can imagine. And my DNS is still not set up right, so uh.. Many better people to answer your questions than me.

---

### Post by kc5hwb on 2007-04-01
What SSH client do you use?  Have you connected from a Windows box?

Thanks for your help

---

### Post by kc5hwb on 2007-04-01
You were right, I was able to SSH into each box.  But I am not able to startx.  Maybe I misunderstood, but can you run X thru SSH?

---

### Post by prensing on 2007-04-01
The Windows network "Group" is set in the file /etc/samba/smb.conf. Just change the Workgroup line and then reload the smb config file  (sudo /etc/init.d/smb reload).

For SSH, the server can be started by "sudo /etc/init.d/sshd start", but that has to be done every time you reboot. To set it permanently, do "sudo update-rc.d sshd defaults".

SATA drives show up as SCSI drives, so they will be named like "/dev/sdaX", "dev/sdbX", etc. Try "mount" and you may find they are already mounted.

Not sure where VMWare shows up in the menus. First, try "vmware" from the command line to see if it is there. If so, maybe it is hidden "for your convenience"; go to System->Preferences->Menu Layout to edit your system menu.

---

### Post by alien21010 on 2007-04-01
> **kc5hwb said:**
> You were right, I was able to SSH into each box.  But I am not able to startx.  Maybe I misunderstood, but can you run X thru SSH?

You can tunnel Xserver through SSH, but it is slow and generally not recommended to do so... If you still must try it, there are a host of tutorials out there on the web (try googling it).  

I think it is Putty, that is the Windows OpenSSH client.

---

### Post by kc5hwb on 2007-04-01
vmware from the cmd line shows "command not found" but I know that I have installed this and it shows installed in the Synapatic Pkg Mgr.  If I do a whereis vmware it shows me:

/usr/share/man/man4/vmware.4

I added this line to my Ala Carte Menu and when I click on it, nothing happens.

---

### Post by kc5hwb on 2007-04-01
> **alien21010 said:**
> You can tunnel Xserver through SSH, but it is slow and generally not recommended to do so... If you still must try it, there are a host of tutorials out there on the web (try googling it).  

I think it is Putty, that is the Windows OpenSSH client.

Yea, I tried it with Putty, it doesn't work that great.  I think I am going to use VNC instead.

---

### Post by kc5hwb on 2007-04-01
> **prensing said:**
> 

SATA drives show up as SCSI drives, so they will be named like "/dev/sdaX", "dev/sdbX", etc. Try "mount" and you may find they are already mounted.



Ok, I see /dev/sda1 and /dev/sdb1 but I don't think they are mounted.  If I go to Places ->Computer, they do not show up in this view.  And my option for "Disks" under System-> idn't there in the server install, so I can't go in and try and mount them to another folder, like I have done on my desktop.

---

### Post by kc5hwb on 2007-04-02
anyone have any other ideas on this?

---

### Post by kc5hwb on 2007-04-04
> **prensing said:**
> The Windows network "Group" is set in the file /etc/samba/smb.conf. Just change the Workgroup line and then reload the smb config file  (sudo /etc/init.d/smb reload).


It won't let me do this thru the GUI, I assume because I am not logged in at root.  And I don't know how to edit that file with cmd line.

---

### Post by psynyd on 2007-04-05
Another newbie trying to help out.. to edit the file as superuser:

sudo gedit /etc/samba/smb.conf

---

### Post by kc5hwb on 2007-04-05
That worked, thanks.  But the reload cmd above doesn't work...

---

