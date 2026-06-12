---
title: "is nouveau+compiz coming to 10.10 for powerpc?"
date: 2010-06-04
forum: Apple Hardware Users
---

### Post by roberto.tomas on 2010-06-04
it's been on the intel side for at least a couple months:
[http://dmolinap.blogspot.com/2010/04/compiz-nouveau-en-lucid-lynx-beta2.html](http://dmolinap.blogspot.com/2010/04/compiz-nouveau-en-lucid-lynx-beta2.html)
[http://dmolinap.blogspot.com/2010/05/3d-con-nvidia-en-ubuntu-lucid-lynx_17.html](http://dmolinap.blogspot.com/2010/05/3d-con-nvidia-en-ubuntu-lucid-lynx_17.html)

---

### Post by sha.goyjo on 2010-06-05
You can compile it into the kernel yourself. It's really not that difficult. And the xorg packages are already in the repo's

---

### Post by roberto.tomas on 2010-06-06
I already have xorg at 1.7 -- although I dont see any gallium package and that is required in the pc-version instructions.  

just waiting for the kernel :)

---

### Post by sha.goyjo on 2010-06-06
Why don't you compile it yourself?

---

### Post by roberto.tomas on 2010-06-06
> **sha.goyjo said:**
> Why don't you compile it yourself?

why don't I compile what myself? the nouveau kernel module is already in the kernel -- now. gillium already is an ubuntu package, it just hasn't been picked up by the ubuntu powerpc team yet.

I just grabbed the xorg packages off the edge server for that part.

Now I just have to wait for a kernel (can't get support at all if you go off the farm on the kernel, so gotta wait on that)

---

### Post by sha.goyjo on 2010-06-06
I guess what I was referring to was compiling Gallium. I think the reason we don't have it yet is because it is fairly tricky to do. We're missing a couple packages in PowerPC land. Not impossible if you pull some stuff from the debian and arch repo's, though. 

[http://nouveau.freedesktop.org/wiki/GalliumHowto](http://nouveau.freedesktop.org/wiki/GalliumHowto)

---

### Post by roberto.tomas on 2010-06-06
> **sha.goyjo said:**
> I guess what I was referring to was compiling Gallium. I think the reason we don't have it yet is because it is fairly tricky to do. We're missing a couple packages in PowerPC land. Not impossible if you pull some stuff from the debian and arch repo's, though. 

[http://nouveau.freedesktop.org/wiki/GalliumHowto](http://nouveau.freedesktop.org/wiki/GalliumHowto)

so far as I know, we are only missing the kernel (2.6.34+), and xorg (1.7+) and support libs for those two. xoreg is up on powerpcs on the edge servers :) just need the kernel now for it to be possible.

---

### Post by sha.goyjo on 2010-06-06
> **roberto.tomas said:**
> so far as I know, we are only missing the kernel (2.6.34+), and xorg (1.7+) and support libs for those two. xoreg is up on powerpcs on the edge servers :) just need the kernel now for it to be possible.


I guess I'm not quite understanding what you are saying.

Are you saying you need a 2.6.34+ kernel? Probably won't happen till maverick (or a good backport), but there are tons of tutorials on compiling kernels. I run 2.6.34-ck1, and my fiancee runs 2.6.34-pf1, on mactel and powerpc respectively. They work great, compiled from a patched vanilla with kernel-package. That would fix that problem.

If you have a different problem, I'm not sure what it is. Could you explain to me again?

---

### Post by roberto.tomas on 2010-06-06
> **sha.goyjo said:**
> I guess I'm not quite understanding what you are saying.
If you have a different problem, I'm not sure what it is. Could you explain to me again

I don't have a problem. I had a question -- gossip would be just as good of a response as actual isntructions :) Thank you for volunteering -- if you're wanting to understand better go back and please reread the first post

---

### Post by sha.goyjo on 2010-06-06
I very seriously do not understand what you are looking for. Please explain clearly. You have said several different things. I do not understand which one takes priority for you. If you don't get the message across to me, I can't do anything. :confused:

---

### Post by roberto.tomas on 2010-06-06
> **sha.goyjo said:**
> I very seriously do not understand what you are looking for. Please explain clearly. You have said several different things. I do not understand which one takes priority for you. If you don't get the message across to me, I can't do anything. :confused:

:) aja this is getting almost comical -- I guess I really don't want you to do any more, thank you again.  I just wanted to know when nouveau+compiz is coming to the powerpc, ie, when a powerpc user with an nvidia card can expect to use compiz.

the path to accomplish this has shown up in blog posts from about april, so sooner-or-later you'd expect it to come to powerpc -- it was happening early enough that , if things had happened quickly with the gallium package, we could have had it on 10.04's kernel -- but they don't keep their old packages (I'm told on the nouveau irc channel) so now there's a required wait for the 2.6.34 kernel.

edit: spelling errors

---

### Post by sha.goyjo on 2010-06-06
> **roberto.tomas said:**
> :) aja this is getting almost comical -- I guess I really don't want you to do any more, thank you again.  I just wanted to know when nouveau+compiz is coming to the powerpc, ie, when a powerpc user with an nvidia card can expect to use compiz.

the path to accomplish this has shown up in blog posts from about april, so sooner-or-later you'd expect it to come to powerpc -- it was happening early enough that , if things had happened quickly with the gallium package, we could have had it on 10.04's kernel -- but they don't keep their old packages (I'm told on the nouveau irc channel) so now there's a required wait for the 2.6.34 kernel.

edit: spelling errors

Alright. It seems to me that what you are saying is that in order to for Gallium to work you need 2.6.34+, a fact to which I concur. So, I ask, why not compile your own 2.6.34 kernel on a PowerPC machine under lucid, and then use Gallium. That way you can have it without having to wait around for maverick.

If I've misunderstood something, it would be great if you could clarify.

---

