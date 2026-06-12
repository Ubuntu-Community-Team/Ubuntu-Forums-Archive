---
title: "File sharing"
date: 2011-12-03
forum: Apple Hardware Users
---

### Post by Pat910art on 2011-12-03
I already have an iMac and have now bought a netbook on which I have Ubuntu installed.  Can anyone tell me how to share files between my machines?  I am already connected wirelessly to my iMac from my netbook.

---

### Post by Lars Noodén on 2011-12-03
Can you login from one to the other with SSH?  If so then you could use SFTP to connect.  SSHFS is convenient but there are also SFTP clients built into Dolphin and Nautilus.

---

### Post by tr33m4n on 2011-12-03
If you right click a folder on your netbook in Nautilus (file manager) there should be sharing options in the context menu. Ubuntu will ask you to install some additional software (samba client etc) then in theory you should be able to browse those shared folders from your iMac? I have a MacBook however as soon as I got it I wiped it and install Ubuntu so I'm not 100% sure how to browse/share things from your iMac. I would imagine it's something similar to do with samba (file sharing system)

---

### Post by Pat910art on 2012-01-06
Hi Lars

I can access the files remotely but I want to be able to edit them as well as just looking at them.  On my Mac I have given myself read and write facilities but they don't seem to show up on my netbook.

---

### Post by Lars Noodén on 2012-01-06
The easiest way is to connect from your Ubuntu machine to your Mac.

On your Mac:

Apple Menu->System Preferences->Sharing->Remote Login

On your Ubuntu Machine, install [SSHFS](https://help.ubuntu.com/community/SSHFS).  Then connect to you Mac.

---

