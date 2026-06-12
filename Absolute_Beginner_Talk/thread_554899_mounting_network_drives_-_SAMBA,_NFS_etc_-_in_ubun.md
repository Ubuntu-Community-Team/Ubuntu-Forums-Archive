---
title: "mounting network drives - SAMBA, NFS etc - in ubuntu"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-19
Am  trying to use Amarok to play music files that  are stored on a PowerMac G5 on the same network...

this morning, I thought I had a breakthrough when I found out that I can access & view files on the Mac through a regular desktop browser window.

but now I realize that I have to really mount the Mac drive to put the sound files in the library.

Can someone advise me on the simplest way to do that?  I am a totally neo-newbie-phyte, have had no experience (or luck) with terminal so far.  

I have been told that I can do this with NFS easier than SAMBA, but either way, I need to proceed in spoon-fed, tiny-little baby steps.

thanks again

Willfriedwald

---

### Post by reckless2k2 on 2007-09-19
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

let me know if you need more help.

---

### Post by willfriedwald on 2007-09-19
you don't seem remotely evil!  Just the opposite, in fact...


Okay, am struggling with terminal - forgive my ignorance 

first, am not sure if these instructions are for Mac as well as PC, but assuming they are :

if the basic terminal command is

smbmount //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

The mount equivelant is:

mount -t smbfs //servername/sharename /mountdirectory -o username=mywindowsusername,password=mywindowspassword

//servername/sharename refers to the name of the Windows computer and the name of the share.

/mountdirectory refers to the directory you use as the mount point on the Linux workstation. It can be any directory as long as the user executing the command has rights to it. 

the name of my my Mac on the network is: power-mac-g5.local
my password is: evilconservative (it isn't, but let's say it is)
my username on the mac is: unclefreeds
the volume I wish to mount (on the mac) is: matrix june 1.8


how would I phrase that command line to mount that volume? I would prefer to do it permanently.  (although, once I get it going, it's not that big a deal to run it every day...)

thanks!

willfriedwald

---

### Post by odinb on 2007-09-19
Have you tried smb4k?

It is semi-permanent, but uses a GUI.....

---

### Post by willfriedwald on 2007-09-19
hey  - will try that - how do I find & get smb4k?

love GUI - in my case it stands for GREAT UNDERSTANDING for IDIOTS!

will

PS:

Hey great - I got it - will have some questions -

just taking a look at it, I see that SMB4K does indeed find the Mac.  When I click on it, I get three printer options (potentially useful someday) and my user name / home directory.

when I click on that, trying to mount it, I get an error message: 
smbmnt must be install suid root for direct user mounts
(1000,1000)

so what do I do?  It looks like I have to do something in  the terminal after all - please advise!

also: I know that in Mac, when I click on my user-home directory, I get the stuff in that directory.  But what I am really trying to do is mount other drives that are attached to the Mac.  As I mentioned earlier, I know I can access them via the basic ubuntu desktop browser window, but I am trying to actually mount them rather than just access them (it's just today that I realized there was a difference...) 

so I guess what I need to do is make SMB4K see the other volumes and then mount them - again, need advice!

thanks yet again



Will

---

### Post by reckless2k2 on 2007-09-20
there is a bit on the smb4k page that explains about the permissions for smbmnt. there's a thing in linux/unix that's called sticky bit and yadda yadda....i won't go into the full boring details. you basically need root permissions to mount. you would do this with sudo normally and some suggest running smb4k with sudo to avoid the errors. ideally, you do not want to run it this way at all and mount in fstab but i realize you are struggling with the concepts. just do this from the terminal and you will be able to mount and umount as yourself. 

```
sudo chmod u+s 'which smbmnt'
```

and

```
sudo chmod u+s 'which smbumount'
```


that will allow you to mount and umount. talk to me if you still would rather a permanent mount using fstab. first thing is make your computer hostnames simple. hahahaha. ...like MAC and PC or UBUNTU.haha

---

### Post by willfriedwald on 2007-09-20
I tried both of those commands with nebulous results - somehow I just can't get this stuff (SMB, NFS, SAMBA) to work for me!

here's the results of the two commands: 

will@will-linux:~$ sudo chmod u+s 'which smbmnt'
Password:

<at this point I entered the password, which seemed to be accepted, but all I got was>

chmod: cannot access `which smbmnt': No such file or directory

here are the results of the second prompt - it didn't ask me for a password:

will@will-linux:~$ sudo chmod u+s 'which smbumount'
chmod: cannot access `which smbumount': No such file or directory
will@will-linux:~$ 

help!  what do I try next?  If I could only mount this mother, I know I could access the music upon it.  And then I would be one happy camperino, as Ned Flanders would say..

thanks again - awaiting further instructions....

Will

PS: you're welcome to access my ubuntu machine via VNC11 (or whatever the remote control program is) and implement this...

---

### Post by reckless2k2 on 2007-09-21
sometimes the 'which smbmt' doesn't work because it's a "finder" feature. it just doesn't always work and i was crossing fingers it would. you just need the full path to smbmnt and smbumount is right there too. funny because "which" works for me but it may be because i have it or something it gives installed. the path is /usr/bin/smbmnt so you just do this

```
sudo chmod u+s /usr/bin/smbmnt
```

and

```
sudo chmod u+s /usr/bin/smbumount
```


the the mounting and umounting in smb4k will work. this is all referenced right in the smb4k FAQ on their page. it can be found simply with a google search on smb4k.

let me know how that works for ya. once you get more comfortable, you can explore perm mounts in fstab if you like.

---

### Post by willfriedwald on 2007-09-21
my message from late last night has gone missing - I thought I posted a reply that I WAS at long last able to fix the permissions (thanks to your input) - not only that, I was able to write to the drive I wanted and even use it for a backup.  My first ubuntu backup.  This is a major step forward for little old me!  thanks for all your help!

---

### Post by reckless2k2 on 2007-09-21
not a problem at all.

---

### Post by willfriedwald on 2007-09-21
hey - if you're still in the mood to answer questions - I've got one for you - check out this link to elsewhere in the u-forums:

[http://ubuntuforums.org/showthread.php?t=556593&highlight=willfriedwald](http://ubuntuforums.org/showthread.php?t=556593&highlight=willfriedwald)

thanks!

w

---

