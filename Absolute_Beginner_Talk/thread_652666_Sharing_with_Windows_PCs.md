---
title: "Sharing with Windows PCs"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by peterhuang913 on 2007-12-29
How do I share files between Ubuntu and Windows. I've heard of Samba. I do see the other computers on the workgroup but when I click on it, I can't access it.

---

### Post by doorknob60 on 2007-12-29
Go to System>Administration>Shared Folders, and it will install SAMBA, which should be what you need. Next, in General Properties type in the name of the workgroup, make sure it's set the same on your other computers. Then, in shared folders tab, add folders that you want to be accesible over the network.

---

### Post by peterhuang913 on 2007-12-29
It still says "the files could not be displayed"

---

### Post by doorknob60 on 2007-12-29
Try restarting? Worth a shot anyways :P

---

### Post by peterhuang913 on 2007-12-29
> **doorknob60 said:**
> Try restarting? Worth a shot anyways :P

Still doesn't work.

---

### Post by NullHead on 2007-12-29
I'm interested in this subject too. This is how I always wanted samba to work.

I share a file ... I look for it from a windows computer and then i can access it with out needing a user name or password. The other way around as well.

---

### Post by peterhuang913 on 2007-12-29
> **NullHead said:**
> I'm interested in this subject too. This is how I always wanted samba to work.

I share a file ... I look for it from a windows computer and then i can access it with out needing a user name or password. The other way around as well.

That's what I'm aiming for.

---

### Post by Danners on 2007-12-29
This is what I'm looking for, I've shared folders on my ubuntu laptop, but when I try to access the share from a windows machine, it asks for a username and password. I've tried every combination I can think (username, root and passwords) to login but it still says incorrect.

Anyone have any ideas?

Ta.

---

### Post by Dngrsone on 2007-12-29
You likely need to edit your /etc/samba/smb.conf file for the folder in question.

[Here's](http://www.samba.netfirms.com/) a good tutorial on setting up Samba.

---

### Post by JillSwift on 2007-12-29
For those wanting a no-password access to the shares ([SIZE=1]***which is so very _not_ recommended***[/SIZE]), in your smb.conf file, you'll find a line configuring security, it'll look like so:```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = user
```change it to```
security=share
```and no one will have to log in to see your samba shares.

You'll find the file in /etc/samba/
You'll have to re-start samba server to load the new config:```
sudo /etc/init.d/samba restart
```

---

### Post by Danners on 2007-12-29
Thanks for your help guys! Got it sorted, I am quite happy to have passwords.

I thought the U/P would be the same as your UNIX login, didn't realise samba has its own user accounts.

I just added a new user with *sudo smbpasswd -a username* and it worked straight away :)

Thanks again.

---

### Post by peterhuang913 on 2007-12-29
All these methods are just so that Win PCs can see Ubuntu PCs, but can it be the other way around?

---

### Post by NullHead on 2007-12-29
> **Danners said:**
> Thanks for your help guys! Got it sorted, I am quite happy to have passwords.

I thought the U/P would be the same as your UNIX login, didn't realise samba has its own user accounts.

I just added a new user with *sudo smbpasswd -a username* and it worked straight away :)

Thanks again.

Hay what you said works for me too. When one would need to access files all you need to do is sign in with the username and password and you can read and write files from windows, but to access windows files from Ubuntu I use PyNeighborhood to mount and access files on a windows box.

---

### Post by peterhuang913 on 2007-12-29
> **NullHead said:**
> Hay what you said works for me too. When one would need to access files all you need to do is sign in with the username and password and you can read and write files from windows, but to access windows files from Ubuntu I use PyNeighborhood to mount and access files on a windows box.

I DLed and extracted Py but how do I install it?

---

### Post by NullHead on 2007-12-29
What I did to install it is just an```
sudo apt-get install pyneighborhood
``` and then just run ```
gksudo  pyNeighborhood
``` make sure to change the mount point in the  edit> preferences and change it to /media/lan to have gnome-volume-manager let you see it as a normal mount. If you you can't find the mount point then just do this```
sudo mkdir /media/lan
```

---

### Post by peterhuang913 on 2007-12-29
I installed Py but it won't mount the folders.

---

### Post by NullHead on 2007-12-29
what does it say for an error output?

---

### Post by peterhuang913 on 2007-12-29
> **NullHead said:**
> what does it say for an error output?

I can navigate the workgroup up into the users. I can even see the shared folders. But when I click to mount, its says "Unable to mount."

---

### Post by NullHead on 2007-12-29
I'm not sure why you're having issues but you need to run the program as root. I do this by```
gksudo pyNeighborhood
``` and also if you're having problems using the program I'm working on a video of how I have it set up and how to use it.

---

### Post by NullHead on 2007-12-29
I've made a video of how I use phNeighborhood to mount my shares. You need to download it to watch it. Download it here [http://www.mediafire.com/?abv1kfbdlb8](http://www.mediafire.com/?abv1kfbdlb8)

---

### Post by peterhuang913 on 2007-12-29
> **NullHead said:**
> I'm not sure why you're having issues but you need to run the program as root. I do this by```
gksudo pyNeighborhood
``` and also if you're having problems using the program I'm working on a video of how I have it set up and how to use it.

I see. But this is so annoying. Why do I have to use "sudo" everytime? Can I make my account have root privileges? I will try what you have mentioned after I get back on the Ubuntu rig. Thank you, and everyone else for your help thus far.

---

### Post by peterhuang913 on 2007-12-29
Yay! It seems to work now... but for how long. Thanks guys. [SOLVED]

---

### Post by Baskins on 2007-12-30
This is the thing that always torqued me about Samba and Ubuntu. You can right-click on the folder you're interested in sharing. If Samba's not installed it will detect that and ask if you'd like it to auto-install the service for you (at least with Gutsy). You can give it a share name and the permissions with a couple of check boxes. And you can even make the initial connection at least getting a login prompt from your Windows box. All that it fine and good, but....until you do the *sudo smbpasswd -a username* you aren't getting anywhere. There's no GUI option to take care of this or smb.conf component to edit (which is the file everyone always wants to see when you're having problems), and it's always the step I forget.

They need to integrate the process of adding/removing Samba users as part of the interface somewhere, otherwise the rest of it is pointless.

---

### Post by mdsmedia on 2007-12-30
> **Baskins said:**
> This is the thing that always torqued me about Samba and Ubuntu. You can right-click on the folder you're interested in sharing. If Samba's not installed it will detect that and ask if you'd like it to auto-install the service for you (at least with Gutsy). You can give it a share name and the permissions with a couple of check boxes. And you can even make the initial connection at least getting a login prompt from your Windows box. All that it fine and good, but....until you do the *sudo smbpasswd -a username* you aren't getting anywhere. There's no GUI option to take care of this or smb.conf component to edit (which is the file everyone always wants to see when you're having problems), and it's always the step I forget.

They need to integrate the process of adding/removing Samba users as part of the interface somewhere, otherwise the rest of it is pointless.Not having used SAMBA, and having learned a lot in this thread, I tend to agree that this appears to be a logical GUI option, or at least should automatically occur during installation. Probably a GUI option would make sense, since it appears that it's a necessity for every installation of SAMBA (correct me if I'm wrong).

I'm looking at options for upgrading my 2 PCs today (or in the next few days) as I need to use Windows for my work (at home) and I'm looking at reinstalling Windows in a VM so I can access it, and jump between my main OS (Ubuntu) and Windows, without dual-booting. Networking is one thing I want to setup, for printing etc from my laptop, but looking at all sorts of options for the setup.

---

