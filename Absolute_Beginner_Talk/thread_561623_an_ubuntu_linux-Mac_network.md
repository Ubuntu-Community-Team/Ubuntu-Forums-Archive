---
title: "an ubuntu linux-Mac network"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by willfriedwald on 2007-09-27
I have a linux ubuntu PC and a Mac G5 on the same network

It's comparatively easy for the ubuntu to "see" the mac - to read files and copy from the mac...

how do I do that the other way around?  what's the easiest way to get the mac to share a volume from the ubuntu?  I imagine it involves NFS...

thanks!

w

---

### Post by kelnage on 2007-09-27
Basically, you right click on the folder you want to share and select "Share Folder". If Ubuntu prompts you to, allow it to install both NFS and SMB sharing (you never know when SMB can come in use).

Once that is complete, select "UNIX networks (NFS)" from the "Share through:" pull down list and enter the hosts you wish to be able to access the folder.

If that doesn't work, share the folder again, but this time share through SMB - Mac should be able to handle it.

---

### Post by willfriedwald on 2007-09-27
someone had this same problem a month ago - at that point there was no answer :

I indicate, on ubuntu, which folders are to be shared.

on the mac network panel, those folders do indeed come up when I click on my linux name

I try to access the ubuntu folders on the mac, it asks me to authenticate

I put in correct name & password - but then I get a message that the alias is incorrect, so I can't connect.

does anyone know what causes that & how to fix it?  anyhow, will try those steps you mention above - thanks for the response!

willfriedwald

---

### Post by willfriedwald on 2007-09-28
tricky stuff!

on ubuntu: I made the folder share-able, then I fixed it in permissions so that it should be open to virtually everybody (read & write etc) in properties.

on Mac: I click on "will-linux" and it gives me the option to choose the folder, but when I click on it (and enter the password), I get the error message: "the alias will-linux can not be opened because the original can not be found."

what to do?

thanks!

---

### Post by willfriedwald on 2007-09-28
trying again:

I found the "share through" option that you're talking about - however, it ONLY gives me the option of sharing through "windows network SMB."  There is no option for "UNIX networks (NFS)" - how do I get that?

In permissions (under properties), I see that it gives a whole bunch of choices under "group" - I selected myself ("will"), am not sure what the other "groups" mean.  

for folder access, I put in "create & delete files"
for file access, I put in "read & write"
I also clicked "apply permissions to enclosed files"

but still, when I click on will-linux on the mac end, I get the same error, "the alias will-linux can not be opened because the original can not be found."

am sure I have to go into terminal and do some sort of sudo something to get this working, but at least that's better than a "pseudo" something!

w

---

### Post by kelnage on 2007-09-28
Sounds like NFS isn't installed on your machine. However, honestly that shouldn't matter, as Mac can certainly handle SMB mounts.

I'm afraid I've got not experience with Macs when it comes to networks, so I've got no idea what that error really means.

IIRC, part of your problem is that it's asking for a username and password. In my experience, that means something is going wrong.

This is what I added to /etc/samba/smb.conf to get my shared files working:

```
[share]
path=/absolute/path/to/dir
comment=Name
guest only=yes
writable=yes
read only=no
available=yes
browsable=yes
public=yes
```

And somehow that worked on my Windows network. I guess it couldn't hurt to try.

---

### Post by LORDnoogie on 2007-10-02
having same problem as everyone else i think. shared folder on linux, go to networks on mac - Mshome - 'name'-Desktop - click connect and requires authentication (whichever way you share) but will not proceed as cannot be opened because the original item cannot be found?!!! bastards!

---

### Post by rfurman24 on 2007-10-20
I can access ubuntu files from mac. I shared the folder I wanted to share then set samba password with -"smbpasswd -a user" in a terminal minus the quotations and where user is you. Then in finder went to go-connect to server and connected to smb:// I.P. address. It asks for user name and password and you enter the user name and password you set up the the command I just gave. I for some reason can not connect to the mac the opposite way. I hope this helps and maybe someone can point out what I am doing wrong to access my mac folders.

---

### Post by rfurman24 on 2007-10-22
I finally got the mac to share to Ubuntu. My Ubuntu machine was seeing the mac automatically but I could not access files. When I gave read/write privileges to the desired folders the Ubuntu machine quit seeing the mac so I used connect to server and entered the IP and everything now works.

---

