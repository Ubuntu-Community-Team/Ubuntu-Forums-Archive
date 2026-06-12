---
title: "driver for unity on macbook"
date: 2011-01-10
forum: Apple Hardware Users
---

### Post by Kingcheese26 on 2011-01-10
I have maverick currently installed on my MacBook 2,1 (mid-2007 model) and I decided to get myself an iso of the natty alpha 1 to run in a VM. When I booted into it, it said I couldn't run unity because I didn't have the required drivers. I kinda expected that (it's a pretty old computer, though it runs fast), but I'd like to know where I could maybe get a supported driver for this model of Macbook. thanks :guitar:!

---

### Post by zekopeko on 2011-01-10
> **Kingcheese26 said:**
> I have maverick currently installed on my MacBook 2,1 (mid-2007 model) and I decided to get myself an iso of the natty alpha 1 to run in a VM. When I booted into it, it said I couldn't run unity because I didn't have the required drivers. I kinda expected that (it's a pretty old computer, though it runs fast), but I'd like to know where I could maybe get a supported driver for this model of Macbook. thanks :guitar:!

For Unity to work you need working OpenGL drivers. If you can run Ubuntu with Compiz/3D effects then you can run Unity.

Wikipedia tells me your machine has an Intel GMA950 as a graphic card. That should be sufficient to run Unity if you install Ubuntu on your Macbook (not to mention that Intel cards have the best supported drivers).

Now I see you are trying this in a VM (which one?). You probably need to enable hardware acceleration in the VM so you can get 3D to work. But last I heard Unity in a VM was still a little problematic. Enabling hardware acceleration in whatever VM software you are using and installing guest addition/tools inside the Ubuntu guest could make Unity work in a virtual environment.

---

### Post by Kingcheese26 on 2011-01-10
I downloaded the iso with the TestDrive program which launched a VM in QEMU. I don't have compiz (or any desktop effects) enabled right now, but i'll test that out and check the settings. Thanks!

---

### Post by alexmurray on 2011-01-11
QEMU doesn't support 3d acceleration for guest OSes so you'll never get it going that way - try installing Natty in VirtualBox instead.

---

### Post by Kingcheese26 on 2011-01-11
i tested it in vbox... still doesn't work (I did enable 3d acceleration)

---

### Post by Kingcheese26 on 2011-01-11
i tested it in vbox... still doesn't work (I did enable 3d acceleration)

---

### Post by Kingcheese26 on 2011-01-11
i tested it in vbox... still doesn't work (I did enable 3d acceleration)

---

### Post by Kingcheese26 on 2011-01-11
Sorry... I didnt mean to post so many times :oops:

---

### Post by Kingcheese26 on 2011-01-12
ok so i burned a live cd of the alpha and unity works (but not very well, it' an alpha :lolflag:) but it does seem it can work on my computer.

---

