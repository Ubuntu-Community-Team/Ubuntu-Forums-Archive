---
title: "How do I install checkinstall 1.6.0 from source?"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by rvbhute on 2005-12-23
I want to install checkinstall 1.6.0 from the deb files given from its website. Plus, there are other packages I want to install using checkinstall.
[LIST=1]
[*]Can I use the 2 deb files provided on the checkinstall website? Will they be integrated into Synaptic?
[*]How are the deb files created by checkinstall integrated into Synaptic?
[*]Can I setup a local repository of deb files created by checkinstall ?
[/LIST]

Using Synaptic to download packages is not possible becuase my ISP doesn't support Linux :( . I have to use win32 to download tarballs and carry on.

---

### Post by GoldBuggie on 2005-12-23
All  .deb files you install will show up in synaptic.

The .deb files on the checkinstall page might work then again might not work perfectly. Most debian packages should work but there is a reason for them repackaging it. The practical view is just install it, it will work(I don´t think you will have any problems with it).

If you want to download the ubuntu package which isn't the latest version just go to [http://archive.ubuntu.com/ubuntu/pool/universe/c/checkinstall/](http://archive.ubuntu.com/ubuntu/pool/universe/c/checkinstall/)

Didn't really understand the thing about your ISP not allowing linux. Could you expand on that? So you can't do any surfingwhile on linux? I've not heard of anything similar before.

> How are the deb files created by checkinstall integrated into Synaptic?Don't know the technicalities but checkinstall builds a .deb package and installs it using dpkg and since that gets into synaptic all is fine.

---

### Post by rvbhute on 2005-12-23
> Most debian packages should work but there is a reason for them repackaging it. 
I saw this thread about checkinstall 1.5.3 - [http://ubuntuforums.org/showthread.php?t=107089](http://ubuntuforums.org/showthread.php?t=107089)
> If you want to download the ubuntu package which isn't the latest version just go to [http://archive.ubuntu.com/ubuntu/pool/universe/c/checkinstall/](http://archive.ubuntu.com/ubuntu/pool/universe/c/checkinstall/)
Thanks, am going around hunting for some stuff there :smile: 
> Didn't really understand the thing about your ISP not allowing linux. Could you expand on that? So you can't do any surfingwhile on linux? I've not heard of anything similar before.
My ISP uses RASPPPoE. It requires a special *username*@linuxuser id to surf from Linux, while just *username* (and a proprietary dialer) will do from win32. It has "speed" packs and Linux support is available only above 64Kbps. Mine is 48 Kbps. Internet is still on the costlier side here!

BTW, have I posted in the wrong forum? I wanted to move this into the Repository Support or programming Talk.

---

