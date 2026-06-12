---
title: "Shared folder command keeps crashing HELP!"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by hubbadub on 2005-10-26
I am having a problem with Breezy Badger.  When I go to System/Admin/Shared Folders, to add some data to share, it pops up all greyed out, and freezes there. I cant kill it through process manager either, only way I know to end it is logging out.

Also, when browsing my files on the HD, right clicking on a file/folder and choosing share folder, nothing happens.

Can anyone tell me what the problem might be and what I can do to fix it?  Thanks!

---

### Post by patrick295767 on 2005-10-27
[QUOTE=hubbadub]I am having a problem with Breezy Badger.  When I go to System/Admin/Shared Folders, to add some data to share, it pops up all greyed out, and freezes there. I cant kill it through process manager either, only way I know to end it is logging out.

Also, when browsing my files on the HD, right clicking on a file/folder and choosing share folder, nothing happens.

Can anyone tell me what the problem might be and what I can do to fix it?  Thanks![/QUOTE]

try maybe with the console the nfs sharing ... 
[http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)

Good courage !

---

### Post by darth_vector on 2005-10-27
if you are having trouble killing a processes there is no need to log out. open up a shell and type

sudo ps -aux

this will give you a list of all processes, their owners, their PID's, etc. find the process you want to kill and take note of its PID (process id), then type

sudo kill -9 pid

this will an uncachable termination signal to the process and kill it for good.

---

