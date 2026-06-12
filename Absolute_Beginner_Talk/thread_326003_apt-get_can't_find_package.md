---
title: "apt-get can't find package?"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by upinVermont on 2006-12-26
OK, so this is probably a no-brainer for the rest of you, but I try to run the following command:

apt-get install linux-image-2.6.17-6-686

And the console tells me it can't find the package? I thought this command was supposed to go out and "get" the package from a central repository? Or is that just my fantasy?

Anyway, what do I do?

---

### Post by STREETURCHINE on 2006-12-26
did you .

                sudo apt-get install   or just apt-get install

---

### Post by invalid on 2006-12-26
You may need to enable extra repos for this package. 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Installing_Addtional_Software")

---

### Post by 23meg on 2006-12-26
What version of Ubuntu are you using, and why exactly do you need that package? It's probably not in the repositories for the version you're using.

(Edit: I've searched for that in [http://packages.ubuntu.com](http://packages.ubuntu.com) and there's no such package in any version.)

---

### Post by az on 2006-12-26
Edgy uses 2.6.17-10-generic

[http://packages.ubuntu.com/edgy/base/linux-image-686](http://packages.ubuntu.com/edgy/base/linux-image-686)

linux-image-686 points to linux-image-generic which currently points to linux-image-2.6.17-10-generic (2.6.17.1-10.34)


There is no linux-image-2.6.17-6-686

And you should use the linux-686 or linux-generic metapackage and not install individual kernel-images (unless you want to avoid the restricted modules;  in that case use linux-image-686 or linux-image-generic)

---

### Post by invalid on 2006-12-26
edit: azz beat me to it!

---

### Post by upinVermont on 2006-12-26
I'm just trying to connect with my netdisk- a.k.a. NDAS.

Trying to follow the instructions at the following site:

[http://code.ximeta.com/trac-ndas/wiki/Ubuntu6.10]("http://code.ximeta.com/trac-ndas/wiki/Ubuntu6.10")

Ximeta claims its software won't run on the 80386 Kernel.

So... I'm just trying to do what I'm told. That's all... I swear....

---

### Post by az on 2006-12-26
> **upinVermont said:**
> 
Ximeta claims its software won't run on the 80386 Kernel.
.

They don't know what they are talking about.  If it worked for them to use the 686 kernel, then it probably means they were running the generic kernel.  Try to build it with the generic kernel and edit that wiki page accordingly.  I already edited it out of curtesy, but I never even heard of their software before, So I cannot provide a definitive answer.

---

### Post by upinVermont on 2006-12-26
OK...

I've been reading and re-reading all of your comments, and now I *really* don't know what to do. It appears that I am already running the "generic" package - 2.6.17-10-generic?

Does this mean I shouldn't have to upgrade?

](*,)  Am I running 386 or 868?

---

### Post by upinVermont on 2006-12-26
Oh... I tried to edit my last comment when I saw your post Azz.

Thanks,

I'll try to get on with it...

---

### Post by upinVermont on 2006-12-26
I tried installing the packages and all went well until the last one.  I tried re-installing and received the following. Unless it is something obvious, I might  give up on this one. It's all Greek to me. 


---
home@home-laptop:~/Desktop$ sudo dpkg -i ndas-admin_1.0.3-101_i386.deb
(Reading database ... 78263 files and directories currently installed.)
Preparing to replace ndas-admin 1.0.3-101 (using ndas-admin_1.0.3-101_i386.deb) ...
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: error processing ndas-admin_1.0.3-101_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
 System startup links for /etc/init.d/ndas already exist.
/etc/init.d/ndas: 14: Syntax error: "(" unexpected
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ndas-admin_1.0.3-101_i386.deb

---

