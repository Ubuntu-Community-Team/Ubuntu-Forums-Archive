---
title: "Ssh"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Istonian on 2007-07-02
I have heard of SSH. How exactly is it installed? How do you access your desktop from someone elses computer? I know nothing about this topic.

---

### Post by Istonian on 2007-07-02
I have got the ssh server and client installed. Now I need to know how to use it. How I can access my desktop from other peoples computers.

---

### Post by KIAaze on 2007-07-02
Install the openssh-client package.

After that to connect to another PC, use the following command:
```
ssh login@host
```
or
```
ssh login@IP_address
```

If you want to be able to use GUI apps from the other PC, you have to use X11 forwarding which is done by using the "-X" option:
```
ssh -X login@host
```
or
```
ssh -X login@IP_address
```
I don't know how to get the complete desktop on your screen though.

And if you want to access your own PC, you might have to install the openssh-server package too and configure it so that external ssh connections are allowed.

I only know how to use ssh to connect to other PCs but don't know how to configure it exactly.
But this should help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_via_VNC]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Desktop_Sharing.2FDuplication_via_VNC")\

edit:
If you want to copy files from a remote PC to your own, you might be interested in the "scp" command. ;)
> scp login@host:dir/file dir/file
scp dir/file login@host:dir/file


---

### Post by Istonian on 2007-07-02
Ok, thanks I will try that.

---

### Post by eternalsword on 2007-07-02
if you are on a windows machine sshing to your linux machine, you can use winscp [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) to transfer files.  if you are sshing from another linux machine, look into sshfs [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html) which allows mounting remote ssh on the local machine

---

### Post by LancerDragoon on 2007-07-02
Try [this]("http://ubuntuforums.org/showthread.php?t=256102&highlight=ssh+ddclient") guide.

---

