---
title: "delete ubuntu partition mac osx"
date: 2015-06-28
forum: Apple Hardware Users
---

### Post by frankyboynl on 2015-06-28
hello, I have my system set for dual boot mac os x yosemity and ubuntu. For this I used the Refind program. Now I would like to remove ubuntu and resize the os x partition so that it covers the whole disk.

thanks in advance,

frank

---

### Post by bapoumba on 2015-06-28
May be here :
[http://apple.stackexchange.com/questions/188190/uninstall-refind-0-8-3-7-on-yosemite](http://apple.stackexchange.com/questions/188190/uninstall-refind-0-8-3-7-on-yosemite)
[http://www.rodsbooks.com/refind/installing.html#uinst_osx](http://www.rodsbooks.com/refind/installing.html#uinst_osx)

---

### Post by frankyboynl on 2015-06-28
got it to work. simply go to settings and set mac os x as boot. then when restarted use disks to delete the ubuntu partition and resize the mac os x partition to its original state.



grtz, Frank

---

### Post by bapoumba on 2015-06-28
@frankyboynl : glad to see you got it to work. I've never dual-booted on the Macs, and from what I read, looks like what I was guessing :)
If you still want to use Ubuntu on a Mac, I run it in VirtualBox. Works great and all the hardware is taken care of by MacOS. Just remember to give all the video mem that VB allows you to and install the guest additions for drivers. I run it on half of the cores and half of ram, no issue on the host or the guest. The only thing that does not work is copy/pasting between host and guest (although everything relevant is checked) but I have not looked at all. I'm sure I've forgotten something.

Please mark your thread as solved (under Thread Tools), thanks !

---

