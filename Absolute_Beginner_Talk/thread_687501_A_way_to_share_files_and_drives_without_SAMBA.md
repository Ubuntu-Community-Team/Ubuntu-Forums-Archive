---
title: "A way to share files and drives without SAMBA?"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ubuntu1sttimer on 2008-02-04
Am wondering if there is a way to share files and/or drives without using SAMBA? Had SAMBA working after weeks of fighting it only to have UBUNTU fill the root drive and trash it's self. Had to start with a new load. SAMBA is a very good and powerful program but a pain to set up when one is not used to it. That is confirmed by the number of SAMBA messages on these forums. 

Looking for some thing that is more like the way Windows does it. Need to tie a couple UBUNTU machines and a Windows machine for home use.

Is there any way to do this?

---

### Post by bodhi.zazen on 2008-02-04
You can look at NFS, samba, ftp, http.

IMO samba is best for your needs, I advise you look at this link. After that, try to describe your probelam and we will try to help. 

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

IMO, I would not draw the same conclusion re: number of samba threads. When you are new to an OS it takes time to learn and we are here to help. I think the number of threads is s testament to the community.

---

### Post by ubuntu1sttimer on 2008-02-04
Thank you for taking the time to reply to my message.

My question is if there is a way  to share files/drives with mixed operating systems without using SAMBA. I have tried SAMBA and followed many threads until I no longer want to spend time on that option.

---

### Post by scorp123 on 2008-02-04
> **ubuntu1sttimer said:**
>  Looking for some thing that is more like the way Windows does it. Need to tie a couple UBUNTU machines and a Windows machine for home use.  Why not just stick to SSH and use that? With SSH you just need a valid login on each Linux machine, and that's it. You can connect to your machines via the **Places > Connect to Server > Service Type: SSH** program, and you then get a drive icon onto your desktop. All you need to know is the username and the password on the remote machine. Voila, you're done, you can drag & drop things between your Linux machines. Windows can do SSH too, e.g. programs such as **WinSCP** (freeware, as far as I remember) or **Filezilla** (freeware too) give you an explorer like interface where you can drag & drop things from and to your SSH connections to your Linux machines. 

If you're tired of Samba I'd try this.

---

### Post by bodhi.zazen on 2008-02-04
OK, take a look at NFS , ssh, ftp, or http (apache).

ftp is easiest, and least secure.

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)

NFS is a little complex, but works :

[http://doc.gwos.org/index.php/MountNFS](http://doc.gwos.org/index.php/MountNFS)

[http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows](http://www.openfree.org/pet/index.php/Mount_an_NFS_share_from_Windows)

Apache may be a little over kill.

ssh is also an option :

[uwiki]HowtoSSH[/uwiki]

With what ever you choose, make sure you know how to secure it.

---

