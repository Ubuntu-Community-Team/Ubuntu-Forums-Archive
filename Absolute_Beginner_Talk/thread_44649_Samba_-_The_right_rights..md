---
title: "Samba - The right rights."
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by tbresson on 2005-06-27
Hi there.

I'm new to linux and trying to understand some of the samba system and the logic behind the rights.

Let's say I just mounted a harddrive like:
sudo mount -t reiserfs /dev/hda1 /home/mynick/photo

When I look at the "photo" folder it has the following rights: (can't remember precisely but something like this:)

rwx r-x r-x

Now, when I want to share this on the network with Samba I'm confused about the following settings in samba:

create mask = 0700
directory mask = 0700

I found out what they mean .. but which rights has superior rights, the filesystem rights or the samba rights? If the file system says "others" can "write" to the dir but the directory mask is "0000" what then? I mean I could try out different solutions and see what happens, but I was hoping someone could tell me the basic logic here.

BTW: When mounting a drive at boot time via /etc/fstab does it applies some sort of default rights on that folder? I mean if I where to change the rights on folder "photo" to 777 and I reboot, would the box when change the rights when auto-mounting?

---

### Post by patrick295767 on 2005-10-06
Since the post is pretty old, did you manage to progress with samba ?

Me too, i am trying to progress with it ... 
I am not yet very satisfied of teh results

---

### Post by brentoboy on 2005-10-06
[QUOTE=tbresson] which rights has superior rights, the filesystem rights or the samba rights? If the file system says "others" can "write" to the dir but the directory mask is "0000" what then? I mean I could try out different solutions and see what happens, but I was hoping someone could tell me the basic logic here.
[/QUOTE]
The filesystem rights defined by linux rules the entire filesystem.  Smb is just a program - it gets no more rights than the user that is accessing the files. The premissions offered by samba set the maxumum rights that a remote pc will be able to get to your files.  But, if your linux system has stronger restrictions on a file or folder, smb doesnt override that.

Smb is a huge topic, I recommend either buying the book "Samba-3 by example" or browsing the online version and doing all the examples.
[http://us4.samba.org/samba/docs/man/Samba-Guide/](http://us4.samba.org/samba/docs/man/Samba-Guide/)

---

### Post by brentoboy on 2005-10-06
[QUOTE=patrick295767]i am trying to progress with it ... 
I am not yet very satisfied of teh results[/QUOTE]

After playing with samba for a few days and absolutly hating it, my only light of hope was the fact that, at the office, our file-server is running samba, and so I can see first hand that all the stuff I want to do is indeed possible.

It is so flexible that it is beastly to configure. Its a powerful program and if you want to do more than share a folder to your local network, you need the book.

---

### Post by tbresson on 2005-10-06
I have managed to setup the samba with the purpose of sharing the linux folders to my WinXP PC, and it's working. But... I'm only one user, and I have had one purpose and that was getting it working for ME, a single user.

This of course means that I don't know how far the complications go for a company network using Samba and as usual people who don't understand rights usually just chmod 777 anyways.. which leads me back to my own question, namely which rights comes first.

We've gotten an answer to that... the FS does and then samba. I havn't tried anything based on this information but doing 0777 in the samba config makes sense now if you're having trouble .. don't you agree?

Posting your config here might help people, so here's the few changes I did to the original: (sudo gedit /etc/samba/smb.conf)

workgroup = MyWorkgroup
netbios name = MyServer
security = user
username map = /etc/samba/smbusers

The netbios didn't make any difference, and I don't use it now.
The username map I'm not completely sure about, I don't remember if it made any difference, but the command smbpasswd might store info. there.. I havn't really checked.

You can add users this way:
smbpasswd -a username

You need to do this to make it work. But you also need to add the user to the system before you can add the user to the samba system.
(System -> Administration -> Users and Groups).
I use the user I created during install which is the only one I use, that user might have some permissions I don't know if a new user will have, so problems might occur here... or not.

If you have problems after changing the config you can always restart the samba service like this:

sudo /etc/init.d/samba restart

---

### Post by patrick295767 on 2005-10-09
Please is there a easy way to share a folder (i havent nautilus but rox-filer) ??

thank you very much !!
Pat'

---

### Post by tbresson on 2005-10-10
According to the unofficial Ubuntu guide you do this:

Right click on folder -> Share folder
Shared folder -> Share with: Select "SMB"
Share properties -> Name: Specify the share name

I havn't tried it yet and it seems you still need SMB which you can find through Synaptic.

---

### Post by patrick295767 on 2005-10-10
I installed samba & also rox-filer (not nautilus, i prefer rox-filer for older pc)
  
sudo apt-get install samba
I right clicked on the folder and couldnt find in my rox-filer 'share' the folder... i looked also in properties... I dont know maybe additional stuffs to do...?   
   
  
I'll try tonight if it's possible to do : 
sudo apt-get install smb 
   
then try again 'right click' on the folder ...

Thank you very much !

Patrick
---
Liking very much this powerful linux

---

