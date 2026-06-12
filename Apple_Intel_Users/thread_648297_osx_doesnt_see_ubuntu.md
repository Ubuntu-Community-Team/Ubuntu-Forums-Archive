---
title: "osx doesnt see ubuntu"
date: 2007-12-23
forum: Apple Intel Users
---

### Post by brandon333 on 2007-12-23
ubuntu sees the osx drive fine and i can read from  it but in osx the only place I can see ubuntu is in disc utility but it is grayed out, I would like both drives to:

see each other and be able to read/write to each other

---

### Post by Zaff on 2007-12-23
> **brandon333 said:**
> ubuntu sees the osx drive fine and i can read from  it but in osx the only place I can see ubuntu is in disc utility but it is grayed out, I would like both drives to:

see each other and be able to read/write to each other
You can access you ubuntu drive using ext2fsx (use the dev version, it is pretty stable, i've yet to come across a problem with it) : [http://sourceforge.net/project/showfiles.php?group_id=64713](http://sourceforge.net/project/showfiles.php?group_id=64713).
However be carefull when writing from one to an other because it can mess with internal stuff later (such as permissions and such) which is why I personnaly just read the mac partition from ubuntu and vice versa.

---

### Post by brandon333 on 2007-12-23
yes this could get more involved then I thought, actually honestly now that I think about it I would like it to be that in ubuntu or macosx I can read and write to my external, I can read and write to it with osx but only read in ubuntu, how would I go abouth this..

this may be better atleast for me as a newcomer to linux, keep both partitions seperate, probably better for security, I am using a mac mini so after making partitions installing osx leopard and ubuntu, I am not working with much space since the mini only came with 80, all my pictures,movies,music go to the external which soon I plan networking to a ps3 for playback on my tv.

so basically just want full access to external via ubuntu, maybe partition the external?

---

### Post by Zaff on 2007-12-23
> **brandon333 said:**
> yes this could get more involved then I thought, actually honestly now that I think about it I would like it to be that in ubuntu or macosx I can read and write to my external, I can read and write to it with osx but only read in ubuntu, how would I go abouth this..

this may be better atleast for me as a newcomer to linux, keep both partitions seperate, probably better for security, I am using a mac mini so after making partitions installing osx leopard and ubuntu, I am not working with much space since the mini only came with 80, all my pictures,movies,music go to the external which soon I plan networking to a ps3 for playback on my tv.

so basically just want full access to external via ubuntu, maybe partition the external?

Yeah so as far as I know there is a permission issue on mac osx drives (external or not) preventing ubuntu from writing on them. I know there's probably a solution, but I haven't got around to find it yet. I've had the same issue with my brother's drive and we ended up burning stuff cuz I just didn't want t spend the night on it.
If you do find a solution please let me know. I am interested. Sorry I can't be more help.

---

### Post by cyberdork33 on 2007-12-23
you have to disable journaling to make HFS+ mount read/write.
[http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling](http://gentoo-wiki.com/HOWTO_hfsplus#Disable_Journaling)

---

### Post by pbascomb on 2007-12-31
G'day

My problem is a bit different. I have a Ubuntu machine (desktop) and an iMac. I can access the iMac fine - read and write to and from the iMac using the Ubuntu machine.

The problem is that while I can see the Ubuntu machine from the iMac (running Leopard) I can't actually connect to it. What happens is it comes up and asks me for my username and password - so it seems to have happily recognized the machine - but when I type in my Ubuntu username and password I get the error message that I've entered incorrect name or password. 

I don't have a problem accessing work's windows network via a vpn. Go through the same process as for the linux share and all works fine.

So what have I done wrong in Ubuntu to get the problem? I have set up a share called peter.linux using SMB on on the ubuntu machine.

TIA

Peter

---

### Post by cyberdork33 on 2008-01-02
> **pbascomb said:**
> G'day

My problem is a bit different. I have a Ubuntu machine (desktop) and an iMac. I can access the iMac fine - read and write to and from the iMac using the Ubuntu machine.

The problem is that while I can see the Ubuntu machine from the iMac (running Leopard) I can't actually connect to it. What happens is it comes up and asks me for my username and password - so it seems to have happily recognized the machine - but when I type in my Ubuntu username and password I get the error message that I've entered incorrect name or password. 

I don't have a problem accessing work's windows network via a vpn. Go through the same process as for the linux share and all works fine.

So what have I done wrong in Ubuntu to get the problem? I have set up a share called peter.linux using SMB on on the ubuntu machine.

TIA

Peter
I would guess that your samba share is setup incorrectly on the Ubuntu machine. If you only need to share with a Mac, then you might be better off using a *nix native network share like NFS.

---

### Post by Prefader on 2008-01-02
Have you set up a samba user on the ubuntu machine yet?  The username and password you're prompted for are NOT your ubuntu username and password.

To do this, type smbpasswd -a [username], and then enter the password you want for that user.  These can be the same as your ubuntu username and password if you'd like.

---

### Post by cyberdork33 on 2008-01-02
Use this:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by pbascomb on 2008-01-02
Thanks for your help.

When I set up the share on Ubuntu, the only option available was SMB. I thought about using a NFS share but couldn't find out how to do it in the quick look at the newtorking tools in desktop.

I will do some more research tonight and see how I go. If NFS is 'native' then the fact that the option wasn't there suggests that I answered some question wrong in the install. Will have a play and see what I come up with.

rgds

Peter

---

### Post by cyberdork33 on 2008-01-03
> **pbascomb said:**
> Thanks for your help.

When I set up the share on Ubuntu, the only option available was SMB. I thought about using a NFS share but couldn't find out how to do it in the quick look at the newtorking tools in desktop.

I will do some more research tonight and see how I go. If NFS is 'native' then the fact that the option wasn't there suggests that I answered some question wrong in the install. Will have a play and see what I come up with.

rgds

Peter
Here is a how to for NFS:
[http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/](http://www.cyberciti.biz/faq/how-to-ubuntu-nfs-server-configuration-howto/)

---

### Post by pbascomb on 2008-01-03
thanks for the pointer. I had found something similar but when I type in the sudo command I get an error message "package nfs-kernal-server has no installation candiate".

Prior to that message it goes through reading package lists; building dependency tree; reading state information; package nfs-kernel-server is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source.

So my problem remains.  Any other ideas?

TIA

Peter

---

### Post by pbascomb on 2008-01-03
Belay that. I rebooted the machine and the install worked OK. I set up a nfs share after deleting the smb share. On the Mac I still cannot connect to the linux machine.

I go to the connect to server, rather than browse to it, and type nfs://ipex/home/peter I don't get the chance to enter my name/password - simply comes straight back with an error saying incorrect name or password.

Sorry I'm such a novice at this.

---

### Post by cyberdork33 on 2008-01-04
It seems that you need to make sure you are suing the insecure parameter for the Mac ([http://www.macosxhints.com/article.php?story=20031121094436907](http://www.macosxhints.com/article.php?story=20031121094436907))

Also, try using the IP address rather than the server name.

If you still have trouble, post the line you created in your exports file.

Here is the line I used:
```
/home/cyberdork33 192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
```

Then I restarted the NFS server:
```
sudo /etc/init.d/nfs-kernel-server restart
```

Then it mounted quite easily on Ubuntu with:
```
sudo mount <serverip>:/home/cyberdork33 /media/nfsmount
```

I know you are trying to mount in OSX, but I do not have a separate mac machine to try. It worked very well in Ubuntu though.

---

### Post by pbascomb on 2008-01-05
THanks a lot - have it mounted but only in read only mode even though my /etc/exports line reads exactly as your post ie (rw,fsid=0 etc.

---

### Post by pbascomb on 2008-01-07
Thanks to your guidace I now have it working. Even though I had shared the directory as per your post, I hadn't set the permissions on my home directory. Now I can read and write from the Mac ... but even though I applied to the permissions to the enclosed files I still only get RO access. This is of no great bother - I've achieved my goal of having the linix machine sitting quietly in the corner and being able to back up my photos to it.

Again - thanks for all your help.  :)

Peter

---

### Post by cyberdork33 on 2008-01-07
glad to help.

Please mark this thread as solved.

---

