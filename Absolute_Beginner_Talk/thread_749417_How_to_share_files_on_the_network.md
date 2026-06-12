---
title: "How to share files on the network?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-04-08
What are the exact steps for sharing files on the LAN from an Ubuntu box to an Ubuntu box?

---

### Post by avtolle on 2008-04-08
Look at the discussion of using ssh in this guide. I'd suggest that is the easiest way to accomplish what you want to do.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

---

### Post by sayakb on 2008-04-08
> **avtolle said:**
> Look at the discussion of using ssh in this guide. I'd suggest that is the easiest way to accomplish what you want to do.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Thanks for the link.. will check it out..

---

### Post by herbster on 2008-04-08
SSH is the way if you use SCP and a terminal. If you want to have them accessible as shares, use NFS: [http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html](http://www.cyberciti.biz/tips/ubuntu-linux-nfs-client-configuration-to-mount-nfs-share.html)

---

### Post by avtolle on 2008-04-08
You might also find this thread to be of some assistance: see
[http://ubuntuforums.org/showthread.php?t=730066](http://ubuntuforums.org/showthread.php?t=730066) Post number 2 for a "quick and dirty" easy way to share files between two Ubuntu boxes. I'm using this way, and have been lazy; I just use the IP addresses of the two boxes on the LAN to navigate between them.

---

### Post by notwen on 2008-04-08
If both boxes are running Linux, you want to look into NFS.  I use NFS to share(stream) videos and music from my media server to my laptop.  Once you mount the shared folder, all of it's contents appear as if they are part of your local file system.  =]

Check out [this guide]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NFS_Server") at Ubuntu Guide and see if this is close to what you're wanting.  Best of luck.  =]

---

### Post by sayakb on 2008-04-10
Thanks to all for replying. Ssh worked for me :)

---

### Post by hyper_ch on 2008-04-10
or use sshfs to locally mount a remote folder (using ssh for transfer)

---

### Post by sayakb on 2008-04-10
> **hyper_ch said:**
> or use sshfs to locally mount a remote folder (using ssh for transfer)
 
I created a launcher pointing to sftp://IP.ADD.RE.SS and that works. If I mount it through sshfs, can I add music resources to rhythmbox?

---

### Post by AndyCooll on 2008-04-10
Although SSH is fine, it's a bit overkill if you just want a basic server type environment.

If you want the equivalent of a media server (for instance) and hence want to set up a simple server then NFS (and Samba if you need access from a Windows pc) is the way to go. Obviously for this it will mean one computer always being switched on, and you'll need your lan to be behind a firewall (e.g. your routers firewall if you have one).

With such a system you could then set your pc's up so that your connection to the server is done automatically when your computer starts up.

[HOWTO: NFS Server/Client]("http://ubuntuforums.org/showthread.php?t=249889")
[Setting up NFS: Howto]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

:cool:

---

### Post by hyper_ch on 2008-04-10
> **LinuxIsInnovation said:**
> I created a launcher pointing to sftp://IP.ADD.RE.SS and that works. If I mount it through sshfs, can I add music resources to rhythmbox?

Yes you can... with sshfs you will mount a remote directoy into your local file system. It appears then as part of your system (only operations will take longer for reading/writing)

you can even auto-mount a remote folder into your local file system by adding it to the fstab...

---

### Post by nycjeff on 2008-05-28
should the nfs process mentioned above still work between two Hardy Heron machines?

---

### Post by hyper_ch on 2008-05-28
yes, between linux systems you can use NFS instead of SSHFS... the difference is that NFS is unencrypted and SSHFS is encrypted.

In your local lan you may want to use NFS - as it is your lan it should be secure.

However if you want to access a remote machine over the internet, then use SSHFS to encrypt the traffic.

---

### Post by kcnnc on 2008-05-30
Quick question:
With NFS can a user share his folder using Nautilus (like with Samba)?
If so how to set this up?

---

### Post by hyper_ch on 2008-05-30
With NFS the remote folder will be mounted into your local filesystem. You will not see any difference to /home or /media/USB-STICK or ....

It will just be a bit slower to update content and stuff.

---

