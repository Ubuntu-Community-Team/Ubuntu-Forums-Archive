---
title: "VLC can't play files over network? WTF?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by aeonwings on 2007-10-29
I'm quite confused here. I'm super new to ubuntu and linux, but I'm learning more and more as I go on, thanks to this great forum. After spending hours trying to learn how to setup my LAN network, I manage to achieved it through samba, with the help of a howto post here. I went in to test my files, but to my surprise VLC can't play media files. Instead, totem media player would come up. Then I tried right-click and chose "play with other programs" option and picked VLC, it didn't work either. 

search this forum but didn't see any post talking about this, so I thought I'd ask. I read somewhere it was about some mounting issue? don't know. hopefully someone does.

---

### Post by daengbo on 2007-10-29
Totem is a Gnome-aware application, and so works in network-tranparency pretty well. VLC may not understand the smb:// protocol. I use Totem, so I'm not sure about that. I know that I have a similar problem when I try to use MPlayer over the network for some kinds of files, like .bins. (BTW, Totem plays just about everything, so I recommend staying with it and just installing the codecs for it.)

A sure way to solve the VLC problem is to actually mount the share you want. If it's over your home LAN, then make the SMB share appear to be a local folder to the computer.

Try installing xsmbbrowser. Open System -> Administration -> Synaptic Package Manager. Search for xsmbrowser and install the program.

Once it's installed, type ALT-F2 and enter xsmbrowser in the dialog. you will see the program start. Click on the Workgroups button and choose your workgroup, computer, and share. Once you see the share you want, right click and choose "Mount Share." Note where the share will be mounted (generally under {your home}/mnt/) and click "Make Dir" then "Mount." You should then be able to browse to your share at the location you noted before.

VLC or any other program will treat these files like they are local.

Best of luck!

Daeng Bo
[http://ibeentoubuntu.blogspot.com](http://ibeentoubuntu.blogspot.com)

---

### Post by hyper_ch on 2007-10-29
VLC can play smb streams (at least this page does suggest so:  [http://www.videolan.org/developers/vlc/doc/doxygen/html/smb_8c.html](http://www.videolan.org/developers/vlc/doc/doxygen/html/smb_8c.html) )

---

### Post by aeonwings on 2007-10-29
> **daengbo said:**
> Totem is a Gnome-aware application, and so works in network-tranparency pretty well. VLC may not understand the smb:// protocol. I use Totem, so I'm not sure about that. I know that I have a similar problem when I try to use MPlayer over the network for some kinds of files, like .bins. (BTW, Totem plays just about everything, so I recommend staying with it and just installing the codecs for it.)

A sure way to solve the VLC problem is to actually mount the share you want. If it's over your home LAN, then make the SMB share appear to be a local folder to the computer.

Try installing xsmbbrowser. Open System -> Administration -> Synaptic Package Manager. Search for xsmbrowser and install the program.

Once it's installed, type ALT-F2 and enter xsmbrowser in the dialog. you will see the program start. Click on the Workgroups button and choose your workgroup, computer, and share. Once you see the share you want, right click and choose "Mount Share." Note where the share will be mounted (generally under {your home}/mnt/) and click "Make Dir" then "Mount." You should then be able to browse to your share at the location you noted before.

VLC or any other program will treat these files like they are local.

Best of luck!

Daeng Bo
[http://ibeentoubuntu.blogspot.com](http://ibeentoubuntu.blogspot.com)



alright. I'll give it a go and see how it is. thanks!

---

### Post by BrendanM on 2007-10-29
I've actually encountered this exact same issue and it does annoy me, especially because I love VLC.

You might try pyNeighborhood instead of xSMBrowser, I think it's a much prettier application that provides almost all the same functionality with a more intuitive UI. [http://pyneighborhood.sourceforge.net/](http://pyneighborhood.sourceforge.net/)

Still, mounting the network drives is really only a workaround. One of the only things I really like about windows is the ability to transparently browse network shares without mounting them.

---

### Post by daengbo on 2007-10-30
You can do this in Gnome, but the program must be set to use Gnome's Virtual File System. If the program doesn't, then there's not much to do but mount the share. That's why I try to use Gnome apps (in this case, Totem) with Ubuntu whenever possible.

---

