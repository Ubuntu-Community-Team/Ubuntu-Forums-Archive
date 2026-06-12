---
title: "Mount Windows Shared Folder"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by hen3rz on 2006-11-24
Hello,

I would like to know if it is possible/how-to mount a shared windows folder onto my Ubuntu box??

My plan is to mount the shared folder so i can use gnump3d to stream it for me. If I'm going about this the wrong way please just let me know. I'm open for any suggestions.

Appreciate any help.
hen3rz.

---

### Post by hen3rz on 2006-11-24
problem solved. 

Install Samba
```
sudo apt-get install samba smbfs
```

Network computer's IP: 192.168.0.1 
    Network computer's Username: myusername 
    Network computer's Password: mypassword 
    Shared folder's name: linux 
    Local mount folder: /media/sharename 

Mount the Folder.
```
     
sudo mkdir /media/sharename
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

```

---

### Post by taurus on 2006-11-24
Are the XP and Ubuntu on the same machine or are they separate machines?  And if they are separate machines, do they both connect through a router?

---

### Post by CoolHand on 2006-11-24
What you used to connect was correct but there is no need to install all of Samba unless you intend to share files from your PC as well.  Samba is the server that emulates windows shares.  To mount a share all you really need is your second argument...smbfs.  Good to see you got it working on your own though.

---

### Post by hen3rz on 2006-11-24
Thanks for the uber fast replies from you both. unfortunatley ive come into more trouble. I tried changing the root directory of GNUMP3d to point to the mounted windows share:

/media/music

But when i try load the page it hangs big time and nothing loads. I was wondering if this is to do with my collection being to big 27.3GB or the fact that i cant point to anything out of the /var folder?

---

