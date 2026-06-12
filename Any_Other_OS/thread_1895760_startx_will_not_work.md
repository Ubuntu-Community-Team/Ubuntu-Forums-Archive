---
title: "startx will not work"
date: 2011-12-15
forum: Any Other OS
---

### Post by p4ndemic on 2011-12-15
hi all.  When I login to either root or user, and type in startx, i get the following error.
     '/tmp/.x11-unix has suspicious mode(not 1777)or directory does                   not exist'  

So essentially, I cannot get to my desktop on my linux partition.

please help.  Thanks.

---

### Post by TeoBigusGeekus on 2011-12-15
It's in the /tmp folder, so you can delete it
```
sudo rm -r /tmp/.x11-unix
```

---

### Post by Bobhuber on 2011-12-15
> **p4ndemic said:**
> hi all.  When I login to either root or user, and type in startx, i get the following error.
     '/tmp/.x11-unix has suspicious mode(not 1777)or directory does                   not exist'  

So essentially, I cannot get to my desktop on my linux partition.

please help.  Thanks.
What version of Ubuntu are you using ?? 11.10 uses Lightdm so the command as root would be > sudo start lightdm

---

### Post by p4ndemic on 2011-12-15
i am using backtrack 4, which is based off Ubuntu

---

### Post by p4ndemic on 2011-12-15
well i used the command 
'sudo rm -r /tmp/.x11-unix' and the following message appeared.

'Cannot remove '/tmp/.x11-unix' : no such file or directory

I tried to make the directory with
'sudo mkdir /tmp/.x11-unix' and it does not recognize 'mkdir'

---

### Post by bluexrider on 2011-12-15
> **p4ndemic said:**
> well i used the command 
'sudo rm -r /tmp/.x11-unix' and the following message appeared.

'Cannot remove '/tmp/.x11-unix' : no such file or directory

I tried to make the directory with
'sudo mkdir /tmp/.x11-unix' and it does not recognize 'mkdir'


```

sudo rm -r /tmp/*
```
WARNING this will flush it all

---

### Post by oldos2er on 2011-12-15
Moved to Other OS/Distro Talk.

---

### Post by MrQwilson on 2012-04-10
> **p4ndemic said:**
> well i used the command 
'sudo rm -r /tmp/.x11-unix' and the following message appeared.

'Cannot remove '/tmp/.x11-unix' : no such file or directory

I tried to make the directory with
'sudo mkdir /tmp/.x11-unix' and it does not recognize 'mkdir'

I realize this thread is getting a bit old but I wanted to point out "'Cannot remove '/tmp/.x11-unix' " We all (should know ) Linux is case sensitive. I think you made a simple mistake by not capitalizing...
Should be: rm -r /tmp/.**X**11-unix

BTW... This was the answer for starting the X server.

---

