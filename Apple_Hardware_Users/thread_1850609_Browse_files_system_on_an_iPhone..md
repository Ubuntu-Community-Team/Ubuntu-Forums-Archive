---
title: "Browse files system on an iPhone."
date: 2011-09-26
forum: Apple Hardware Users
---

### Post by noahdiehl on 2011-09-26
Might anyone know how I can get full access to the file system on an iPhone4?... like one gets with "iPhone Browser" on Windows?

When I dock my phone now I can see several folders, but this is far from the full file system... just wanna do some mods and swap out some tiles.


Thanks for any help you can give,
-Noah

---

### Post by noahdiehl on 2011-09-27
...I guess the right phrase would be, view the root files..... Anyone?.... I'll give you a dollaaaaarrrr.

---

### Post by loughmillermedia on 2011-09-27
I would love a dollar but don't have a clue. Sorry that nobody has answered this yet.

---

### Post by scorp123 on 2011-09-29
> **noahdiehl said:**
> Might anyone know how I can get full access to the file system on an iPhone4?  You will obviously need to **jailbreak** it. Please use Google, it will give you all the infos you need.

---

### Post by noahdiehl on 2011-10-02
I am Jailbroken... and you don't need to be Jailbroken to do this.

---

### Post by hansdown on 2011-10-02
Hi noahdiehl.

I probably won't be much help, but can you drag and drop the folders to your desktop?

Also, try right clicking the folders, and left click properties.

I don't have an iphone, so I'm just curious.

Thanks.

This may help.

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by dave01945 on 2011-10-02
you can get full file system through ssh you can install openssh from cydia i never done this on a iphone only a ipad but they are the same software so should be the same

--edit--

also if you don't know already the default root password is **alpine** it is recommended you change this because if your on a public network with ssh running anyone can log in

---

### Post by noahdiehl on 2011-10-02
Well, not sure why but it does indeed seem that for some reason Ubuntu cant just browse the file system... on Windows or Mac you would just need to install something like iPhone browser. So SSH is the only way I have been able to find (meaning indeed you need to jailbreak to browse the iPhone root in Ubuntu. As said above, via Cydia make sure you have OpenSSH installed then do this...

[http://www.ifans.com/forums/showthread.php?t=71907](http://www.ifans.com/forums/showthread.php?t=71907)

---

### Post by dave01945 on 2011-10-02
just did a quick google have you tried with ifuse it's for mounting iphone root filesystem here is the manpage

[http://manpages.ubuntu.com/manpages/lucid/man1/ifuse.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/ifuse.1.html)

google is your friend

---

### Post by scorp123 on 2011-10-03
> **noahdiehl said:**
>  ... and you don't need to be Jailbroken to do this. On a non-jailbroken phone you will only see what Steve Jobs lets you see. As the others have already written: You will need OpenSSH-server from Cydia ... or iFuse. 

I access my iPhone via SSH. I have a bookmark in my Nautilus file manager and my router makes sure that my iPhone always gets the same IP address.

On the iPhone itself you could use something like iFile and manage files directly that way.

---

### Post by noahdiehl on 2011-10-03
It's seeming like it can only be done with SSH in the Ubuntu environment... but outside of Ubuntu, you do not need to be jail broken... you can't install app unless you are jailbroken... but you are able to access to the root files. You can do basic re-skining by swapping out .png files on an iPhone that is not jailbroken. I used iPhoneBrowser in the past on Windows, was hoping there was something similar for Ubuntu but SSH will have to due.

---

### Post by cmsj on 2011-10-04
those browsing tools, if they really do what you say on non-jailbroken phones, are probably exploiting the phone to get that much access. You are not supposed to be able to change system files that way.

---

### Post by dave01945 on 2011-10-04
according to the iphonebrowser (Windows app) project home page it only works on jailbroken iphones

[http://code.google.com/p/iphonebrowser/](http://code.google.com/p/iphonebrowser/)

---

