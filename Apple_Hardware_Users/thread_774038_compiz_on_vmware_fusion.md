---
title: "compiz on vmware fusion"
date: 2008-04-29
forum: Apple Hardware Users
---

### Post by tresdey on 2008-04-29
I have ubuntu 8.04 installed on vmware fusion version 1.1.2 with vmware tools installed, and I want to know if its possible to enable compiz fusion and how to do it. Mi apple computer is a Macbook with core 2 duo and a intel GMA X3100 Graphic Card and 2GB ram. I know it can be possible because i see it. Please can anyone help me?

Thank you very much.

I wait answer.

---

### Post by ubersolid on 2008-04-29
Hello, you could try enabling 3d in your virtual machine by following this guide:
[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

I have no idea if it works for you tough. Didn't work for me with ubuntu as host and Vista as guest OS. Gfx card was an ati (mobility)radeon X1100.

If it doesnt work, simply edit the .vmx file and undo your changes.

---

### Post by tresdey on 2008-04-29
Thank you, it didn't work, because it is suposed enabled because i have select enable on vmware fusion setting option. The problem is that ubuntu says it hasn't 3d acceleration with the glxdirect I grep info. I don't know how can i enable inside ubuntu.

---

### Post by ubersolid on 2008-04-29
Sorry to hear that it didn't work for you. Don't know what else there is to do. Maybe someone else  can help?

---

### Post by cyberdork33 on 2008-04-29
you cannot get 3d acceleration in Linux on a vm, thus no compiz.

---

### Post by tresdey on 2008-04-30
I don't think so. I see it on youtube videos, ans i read it in support page vmware. So it is true I have try it and I don't be able to do it. I give up, it is not I can't, it is i don't know how. 

Thank you!

bye.

---

### Post by cyberdork33 on 2008-04-30
> **tresdey said:**
> I don't think so. I see it on youtube videos, ans i read it in support page vmware. So it is true I have try it and I don't be able to do it. I give up, it is not I can't, it is i don't know how. 

Thank you!

bye.

well if that is the case it is not offically a feature and would require some manipulation. please point us in the direction of your video though, i'd like to see it.

---

### Post by russo.mic on 2008-04-30
I'm getting a tingley that this video doesn't exist.

Russo

---

### Post by ElijahLynn on 2008-07-30
Yah, it doesn't work. Bummer. Unity doesn't work either.

---

### Post by ggore on 2011-06-27
3D acceleration has never been and never will be, a capability of Linux on either VMWare Fusion or Parallels on a Mac.   Neither developer has ever worked on this problem or issued a statement as to whether they have any intention of implementing this capability now or in the future.   It is a MAJOR stumbling block to use of Linux in all its functionality and capabilities in a virtual machine on a Mac.  Just sad.

---

