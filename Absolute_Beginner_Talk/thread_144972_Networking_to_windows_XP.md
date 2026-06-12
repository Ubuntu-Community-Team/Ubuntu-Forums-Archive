---
title: "Networking to windows XP"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-03-15
Hello,

I have finally gotten my new installation of Ubuntu networking with my other computers . . . well partly. When I try the shared doc directory (or any other) I get an error message: 
smbmnt must be installed suid root for direct user mounts

I am not at all sure what that means or how to go about it. 

Thank you, Tim

---

### Post by tribaal on 2006-03-15
I believe a simple:

```
sudo apt-get install smbmnt
```
Should get you out of trouble on this one.
*apt-get* is one of the commands you will probably use most in the beginning, as it's debian's way of managing packages.

For extra help on how to use *apt*, search the web, forums, or simply type ```
man apt-get
``` in a terminal.

Hope this helps =)

- Trib'

---

### Post by SVwanders on 2006-03-15
Thank you for the info . . . I still have some problems. Smb4k now finds MSHOME and all of my shared directories on both the machines on the network. I guess I am going to have to learn to get zone alarm to work with DHCP because when I assign an IP I mess up things. However I still get the error message when I try to access the share directories. It is the same message I believe I had before: 
smbmnt must be installed suid root for direct user mounts (1000,1000)
smbmnt failed: 1

smbmnt is already installed but perhaps it is not in the correct place or something. I have made some progress before I wasn't even getting to MSHOME. Any ideas on what I am doing wrong . . . and if anyone knows a way to get zone alarm to let this machine talk to my others that would be helpful also. 

Thanks, Tim

---

### Post by Justin Holt on 2006-03-15
I was wondering, where would i go for a good guide to networking with my two other windows pcs?

---

### Post by SVwanders on 2006-03-15
Justin, that is exactly what I am looking to do. I am getting there my ubuntu machine can "see" both other computers as long as I have zone alarm up, but I get that error message in my last post when I try to open a shared directory. I guess I also need to learn a little bit about zone alarm. I have always thought that program was a real pain . . . especially the free edition.

Tim

---

### Post by Justin Holt on 2006-03-15
how did you even get it to read the other machines

---

### Post by tribaal on 2006-03-16
I suggest you have a look at [this article]("http://doc.gwos.org/index.php/Share_files_using_Samba"). It's very well written and should answer your questions.

Thanks for writing it vnbuddy2002 =)

- Trib'

---

### Post by SVwanders on 2006-03-16
Hi Trib',

I was able to understand and follow the direction at the link you provided without any problems until it got to the part on the Windows machine. These might be commands common with Win98 but XP doesn't have the items listed. I tried all sorts of combinations to get it to work but never got anywhere with it. Somewhere I heard that Unbuntu had a hard time networking with Windows. Maybe I should try a different distro, but I hate to give up! When I point towards Add New Network connect toward Linux it just rejects it. When I try to and a folder to my network group it is rejected . . . 

It is very confusing.

Tim

---

### Post by noswal on 2006-03-16
In your Zonealarm  in Firewall, Main tab, the trusted zone has to be set to Medium and in Zones tab click  and add an entry for ip address range 192.168.0.0to 192.168.0.255 as well as an entry for the ip address of the XP- at least thats what mine is.

---

### Post by SVwanders on 2006-03-16
Thanks! I had forgotten all about the range! Okay, now if I can just figure out the rest of this . . . slowly step by step . . .

TM

---

