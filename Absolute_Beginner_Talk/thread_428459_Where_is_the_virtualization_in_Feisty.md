---
title: "Where is the virtualization in Feisty"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by ndefontenay on 2007-04-30
Hi all,

I feel a bit disappointed...

I mean. Canonical has been claiming for a while that feisty had virtualization...

The first thing I was looking for after upgrading was to virtualize my windows OS...

I've seen nothing pre installed and I have a lot of trouble virtualizing after downloading vmware...

Does anybody has any idea of how to do it?

I'm lost

Thanks.

---

### Post by Malta paul on 2007-04-30
Try System>preferences>desktop effects.
Its unstable but you can enable & disable.
Hope this is of help.

---

### Post by Churnd on 2007-04-30
Virtualbox:  [http://www.virtualbox.org/](http://www.virtualbox.org/)

Download the Feisty .deb:  [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb)

Make sure you add yourself to the vboxusers group once it's installed, or you won't be able to use it.

Once you have windows installed, make sure you also install the guest tools.  It'll make it work seamlessly within Ubuntu.

---

### Post by Capitao Caverna on 2007-04-30
I read something about virtualization in Feisty as well, but I didn't try to learn more because I'm quite happy with VirtualBox...

---

### Post by dasunst3r on 2007-04-30
Can VirtualBox take advantage of the virtualization capabilities in my Core 2 Duo and/or the Linux kernel?

---

### Post by Capitao Caverna on 2007-04-30
I'll pass this one.... :-)

---

### Post by Churnd on 2007-04-30
> **dasunst3r said:**
> Can VirtualBox take advantage of the virtualization capabilities in my Core 2 Duo and/or the Linux kernel?

IIRC, Vbox will use both procs and spins it's own kernel that latches onto the linux kernel.

---

