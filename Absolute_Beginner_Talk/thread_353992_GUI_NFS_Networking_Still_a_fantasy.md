---
title: "GUI NFS Networking Still a fantasy?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by hotani on 2007-02-05
All of the tutorials I have seen for connecting two Ubuntu machines together using the Unix NFS standard involve CLI commands and editing fstab. Is there really no other way? All the GUI tools seem to be in place for establishing a machine as a server, but connecting to it requires some sysadmin level tweaking. Shouldn't it be the other way around? 

Here is the task: connect to an NFS server without opening 'Terminal' (a la Windows "Map Network Drive", and "Reconnect on login"), GO!

I ask because this weekend I wanted to quickly connect a laptop to my home network to throw some photos onto the server, which was opened up and made available via NFS. It became a personal mission to do it without Terminal--as most of my exercises in Linux--which turned out to be futile. In the end, I just connected via SFTP which works well in Nautilus.

---

### Post by Shay Stephens on 2007-02-05
I am in the same boat.  I was trying to share a folder yesterday and nothing was working.  I looked at the tutorials, and they all went into steps that should not need to be done in the 21st century.  I know I am not going to get my Dad to do them that way.  I want, and yes dare say **need** a simple gui method to simply share a folder across the network as simply as it is done with windows.

It is nearly there now, just a few more things to make that "Share Folder" right click menu item really do what it looks like it should be doing.

---

### Post by hotani on 2007-02-05
SMB sharing seems to be doable via GUI, which is interesting as NFS is touted as the preferred method of networking two *nix boxes. Still, for just tossing files around, SFTP has been the easiest to get going quickly.

---

### Post by Shay Stephens on 2007-02-05
I was under the same impression that NFS was "it".  I am installing samba now, hopefully that will do it.

---

### Post by _simon_ on 2007-02-05
IN the past I've found SMB to be easier!

Just found this though: [http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

---

### Post by reberic on 2007-02-06
Agreed -- I've spent way too much time trying to get my two Macs OSX 10.4.x to connect to my Ubuntu 6.10 box on my local network. 

Seems like there should be a GUI way to do it. I've set up the shared folders as NFS shares under Admin > Shared Folders. No luck.

---

### Post by QCompson on 2007-02-07
It's pretty ridiculous how convoluted and difficult it is to share files between two linux machines using nfs.  

I guess I don't understand the purpose of System-->Administration-->Shared Folders  in gnome.  It doesn't seem to be able to set up nfs shares on its own, and still requires the user to fiddle around with /etc/exports and manually restart with "/etc/init.d/nfs-kernel-common restart".  

I find dealing with nfs to be extremely frustrating.  I don't want to have to read through a howto everytime I want to share a folder!

---

