---
title: "ndiswarpper error"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tentel on 2007-12-02
when i try to install ndiswrapper from  the synaptics package  manager, i get this error:

E: /cdrom//pool/main/n/ndiswrapper/ndiswrapper-
common_1.43-1ubuntu2_all.deb: trying to overwrite ' /sbin/
loadndisdriver', which is also in package ndiswrapper



i also cannot get on the internet through a wired connection.
i went through the help menus, and nothing worked.

---

### Post by Blutack on 2007-12-02
Is that a typo or is that actually ndidwrapper?!
You need to remove ALL the ndiswrapper related stuff, then start again by installing ndiswrapper only.

---

### Post by tentel on 2007-12-02
oops  >_<

yeah, that was a typo.



how do i remove all the ndiswrapper stuff?



thanks.
-tim

---

### Post by tentel on 2007-12-02
Do you mean in synaptic package manager, right clicking and selceting "mark for complete removal"?



i just tried that, and i got the same error, when trying to install it again.

---

### Post by tentel on 2007-12-02
evry solution i have been able to find seems to require that i have at least a wired connection.


would it be possible to download something on my other comuter, burn it to a disk, and then run it on my ubuntu computer?

---

### Post by tentel on 2007-12-02
hmmm...


i'm just thinking...

i have the amd64 version.



could that be why i'm getting this weird error?

---

### Post by bobyy on 2007-12-02
Hello
if you want toremove al stuff related to Ndiswrapper you must try that:
first 
> $sudo aptitude purge ndiswrapper
second try to find it is remayning something:
> $sudo locate ndiswrapper
if somethig appears just just deleted manually
after that just try to install Ndiswrapper from sources...it is the best way for amd64..
regards

---

### Post by tentel on 2007-12-02
hey!

it worked.



but then when i was trying to find instructions for using ndiswrapper, i stumbled upon a guide for installing bcm43xx cutter, so i tried that, and it worked!


but i still can't get online, and all of a sudden, my normally lightning fast computer is very very sluggish.



i'll try to find a guide for installing ndiswrapper offline.

---

### Post by tentel on 2007-12-02
actually, does anyone have any suggestions for why my computer suddenly slowed down?

i think i may have read that it is a known problem with using the bcm firmware.

though i may be just going insane.




in which case, could someone recommend a way for me to install ndiswrapper offline?
a link would be nice.
i understand that no one wants to yet again explain how to install stuff to a newb.


i can download stuff on another computer and put it onto a disc, but that's about it.




thanks
-tim

---

### Post by bobyy on 2007-12-03
how to installndiswrapper
> [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
> [http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)
 hope will be useful
if i can i help you but first post herepleasethe output of:
> 
$sudo lshw -C network
$sudo ifconfig

you say your computer it slowing down? what is mean this ? post here the output of :
> 
$top
$free -m

---

