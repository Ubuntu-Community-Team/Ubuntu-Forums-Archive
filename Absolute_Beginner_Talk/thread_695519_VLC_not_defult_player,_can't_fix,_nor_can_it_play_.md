---
title: "VLC not defult player, can't fix, nor can it play via samba"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by jijin on 2008-02-13
Hello, 

I seem to have a problem with VLC. It absolutely refuses to play a mp3 from a local network on a windows machine via samba.

VLC will play through ntfs-3g just fine and it is setup as the default player in both the mp3 properties as well as the system>pref>preferred apps

It works perfectly other then anytime I access media via samba.

Movie player keeps coming up and after I installed the codecs it worked great.

Any ideas?

Thanks in advance.

EDIT: I also wanted to add dragging it into VLC does not work either. I do get a plus sign but nothing else.

---

### Post by chewearn on 2008-02-14
This is a known limitation of VLC in ubuntu.  VLC does not support smb:// protocol; therefore, it got confused when asked to play a file in the ubuntu Places > Network.

If you really what VLC to play via samba, you need to manually mount the samba shares to your directory tree, using mount command and smbfs/cifs.

An instruction on how to mount (there might be others, just search for it):
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by oedha on 2008-02-14
yup...even xmms can not do that too
but ....totem can......

---

