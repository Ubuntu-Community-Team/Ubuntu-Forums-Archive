---
title: "how to access files on a windows computer"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by decrot on 2007-09-06
i have a vista computer that contains files that i would like to access. all the computers are on a router and i want to access a shared folder. ive gone to places->network->windows network and nothing shows up. is there anyway to do this

---

### Post by Dr Small on 2007-09-06
Do you have Samba? If not, try:
```
sudo apt-get install samba
```

and then try connecting to your windows computer like this:
```
smb://ipaddress
```

Dr Small

---

### Post by reckless2k2 on 2007-09-06
it's vista blocking. look up enabling vista networking via google. i can't remember where you activate the filing sharing on vista. somewhere in the firewall settings.

---

### Post by decrot on 2007-09-06
well i tried both of your advices, when i try to install samba i get a error saying the version is too old.

and vista should be opened, i can access it with a win2k computer.

---

### Post by Dr Small on 2007-09-06
If you haven't been to System > Administration > Shared Folders, you should first be prompted to install samba or nfts as your shares. Install samba that way, although the other way should have worked also.

By the way, what version of Ubuntu are you running? 7.04, Feisty Fawn?

Dr Small

---

### Post by reckless2k2 on 2007-09-06
an error that it's too old? i've never heard of an error like that. how did you try to install samba? 

anyway,samba package is more like if you will have server on linuxbox and windows needs access.  

vista "should" since win2k can. hhmmm....not sure about that one. it's all about the protocols baby.hahaha. and vista is noted as being shaky with networking in general. sometimes working right and sometimes not. sp1 should fix the bugs noted.

do you have the livecd? if so, fire it up and see if you can browse your windows network with the livecd. that feature is kinda of factory so it should work.

---

### Post by decrot on 2007-09-06
ok, i have samba installed on my computer, but still no connectivity. i have a vista and xp comp on my network and i can't see either one.

---

### Post by p_quarles on 2007-09-06
Samba is a file server. It does not allow Linux machines to access NTFS drives; rather, it creates SMB shares that can be accessed from Windows. That's not what the OP is trying to do. 

I can suggest a couple things, but I haven't tried either of them and can't promise they'll work.
1) Install ntfs-3g on the Linux box:
```
sudo apt-get install ntfs-3g
```
Assuming you're using Gnome, you can now go to Applications >> System Tools >> NTFS Configuration. This program allows you to mount NTFS partitions. I'm not sure it will work with network-shared folders, though.
2) Format the shared folder as a FAT32 partition.

---

### Post by decrot on 2007-09-06
i tried to install ntfs-3g but i get a couldn't find package error
its not listed in synaptic either

by the way im using dapper

---

### Post by BrendanM on 2007-09-06
Due respect to the posters above, but I don't think their answers are really right.

You shouldn't need NTFS-3g to access network file shares. As long as both computers are using Samba, it will resolve the differences between file systems. Your linux box will just see it as a smbfs.

Descrot, unless you have a reason not to upgrade, I'd suggest maybe upgrading to a newer version of Ubuntu and see if you have better results.

Another thing you could try is using either PyNeighborhood or XSmbrowser, which are both graphical frontends to the smbclient.

Also, before you do anything, you should test basic network connectivity: make sure you can ping the windows machines from Ubuntu.

---

### Post by RDaneel623 on 2007-09-06
Vista made changes to how it handles networking... specificaly the directory pointers. The Samba version included in the repo's don't know how to properly handle the new pointer structure of Vista. Attempts to browse Vista shares will often result in errors that Nautilus cannot open the file. The latest version of Samba clears up that problem pretty well (not perfectly, but a huge improvement). 

The procedure to upgrade your Samba is on the second post of this thread: 

[http://ubuntuforums.org/showthread.php?t=428093&page=2]("http://ubuntuforums.org/showthread.php?t=428093&page=2")

It's a complicated procedure but it pretty much mandatory if you ever want to be able to sucessfuly use your Vista shares. 

Also, as previous posters pointed out, you need to make sure your permissions are set properly in the Network and Sharing Center in Vista. If Win2k can see the folders then it sounds like they are properly set to share, just update the old Samba in Dapper with the new build and you should be all set.

---

### Post by parsu4linux on 2007-09-07
Hi decrot,

You may need to upgrade your ubuntu. And install samba using the Synaptic Package Manager. Its easy to use the GUI.

**Note:** If you are accessing the Windows system, you need to **login as the Windows user from ubuntu** (using the Windows username and password).

Bye.

---

