---
title: "any way to switch over from linux to windows and vice versa"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by RETR0spec on 2008-02-01
ok. i dont know where this thread belongs. and it sounds like a noob question to me. so...

i have dual booted vista and ubuntu 7.10 on my hp pavillion dv6636nr laptop (dunno if my model number would help you guys out any). anyways. i have a whole bunch of stuff on windows of course like games and blah blah.

is there a way i can switch which os im using without having to shutdown and booting up again?

i like having windows and ubuntu. im not looking to COMPLETELY switch to ubuntu, nor using wine or something like that.

and if not. just tell me. i dont wanna keep wondering. thanks

---

### Post by iansane on 2008-02-01
I don't think that can be done without rebooting. That's why vmware, wine and cedega seem to be so popular I think. Have to either reboot or find ways to make everything work in Ubunt. Or use ntfs-3g to access windows drive from Ubuntu

---

### Post by emarkd on 2008-02-01
You can use VMWare to boot that Windows partition, but it takes a bit of work.  For instance, VMWare emulates different hardware that you probably actually own, so your Windows partition running in VMWare has to have a different hardware profile than when you boot it directly in your computer.  Also, and more importantly for you, VMWare doesn't emulate a DirectX compatible video card, so no 3D games running that way.

---

### Post by philinux on 2008-02-01
> **RETR0spec said:**
> ok. i dont know where this thread belongs. and it sounds like a noob question to me. so...

i have dual booted vista and ubuntu 7.10 on my hp pavillion dv6636nr laptop (dunno if my model number would help you guys out any). anyways. i have a whole bunch of stuff on windows of course like games and blah blah.

is there a way i can switch which os im using without having to shutdown and booting up again?

i like having windows and ubuntu. im not looking to COMPLETELY switch to ubuntu, nor using wine or something like that.

and if not. just tell me. i dont wanna keep wondering. thanks

The only way to do that is to install windows from within ubuntu as a virtual OS using something like virtualbox or vmware.

I've never done it so someone else may help. You could make a post here.
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by emarkd on 2008-02-01
> **philinux said:**
> The only way to do that is to install windows from within ubuntu as a virtual OS using something like virtualbox or vmware.

No, it's not the only way.  See my previous post.  You can boot a real physical drive/partition with VMWare, but it's a bit involved and it still won't let you run DirectX stuff from Windows in VMWare in Ubuntu; you have to reboot directly into Windows.  If you install Windows inside VMware, you get no 3D either and you lose the option to boot directly into it from GRUB.

---

### Post by philinux on 2008-02-01
Ok I see, I'm not an expert like i said - never done this. I think i was typing that before you posted LOL

---

### Post by RETR0spec on 2008-02-01
alright. thanks guys.

---

