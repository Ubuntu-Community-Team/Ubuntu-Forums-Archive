---
title: "photoshop on ubuntu"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by TrevorRS on 2007-06-19
is it possible to use photoshop on ubuntu and if so how do i go about it i own a copy but dont have a clue how to go about it!

Cheers
Trevor

---

### Post by p_quarles on 2007-06-19
I understand it works well with Wine. You can find the Wine instruction manual here:
[http://www.winehq.org/docs/en/wineusr-guide.html](http://www.winehq.org/docs/en/wineusr-guide.html)

---

### Post by Fakircho on 2007-06-19
check this out, hope it helps

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

---

### Post by silkstone on 2007-06-19
AFAIK Photoshop 7 runs under WIne or Crossover, but later versions do not.

BTW it's the same for Paint Shop Pro - v7.04 runs under Crossover (I couldn't get it to work under Wine) but not later versions.

---

### Post by Golyadkin on 2007-06-19
I run Photoshop CS3 succesfully in a VirtualBox. It works like a charm.

---

### Post by TrevorRS on 2007-06-19
was it hard to install virtual box and photoshop cs3 on it?

Cheers
Trevor

---

### Post by Golyadkin on 2007-06-19
It was super easy.

What I did was simply install virtualbox by downloading the .deb from the Virtualbox website. 
Then I made a new virtual machine using the wizard in Virtualbox. (Which is very easy to follow the steps)
I inserted my Windows XP CD and started the visual machine, went through the Windows installation and then simply inserted my Photoshop DVD and installed it.

Everything together didn't take more than 30 minutes.

[Virtualbox]("http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb") installer for 32 bits Ubuntu.
[Virtualbox]("http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb") installer for 64 bits Ubuntu.

This is a [tutorial ]("http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/")on how to do it.

---

### Post by TrevorRS on 2007-06-19
is it sore on ram because this laptop only has 512mb ram and is using 280 with all my other website editing software up and running

Cheers
Trevor

---

### Post by moredhel on 2007-06-19
photoshop cs2 works fine in wine as well, if that's what you have.

And yes it uses a bit of ram, but how well your pc would run could only be really found out by just trying it.

---

### Post by Golyadkin on 2007-06-19
Well, you choose yourself during the virtual machine creation how much RAM you want to give to the virtual machine and thus to Photoshop. You should never give more than half your RAM to a virtual machine, but running Windows XP and Photoshop on 256 MB is gonna be slow. Also, your Ubuntu itself will slow down to a crawl because it is going to swap a lot. 
I myself have a gigabyte of RAM and assigned 512MB to the virtual machine, and that runs okay, but not superbly. You will have more luck running an older version of Photoshop with wine if you have 512MB of RAM.

---

### Post by p_quarles on 2007-06-19
Of course, it depends on what you're doing, but the GIMP is really good photo-editing software. It can't do everything Photoshop can, but it I find it's better than good for everything I need to do.

---

### Post by Golyadkin on 2007-06-19
True, but if you spent so much money on a Photoshop license, you want to be able to use it.

---

### Post by PartisanEntity on 2007-06-19
> **Golyadkin said:**
> It was super easy.

What I did was simply install virtualbox by downloading the .deb from the Virtualbox website. 
Then I made a new virtual machine using the wizard in Virtualbox. (Which is very easy to follow the steps)
I inserted my Windows XP CD and started the visual machine, went through the Windows installation and then simply inserted my Photoshop DVD and installed it.

Everything together didn't take more than 30 minutes.

[Virtualbox]("http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb") installer for 32 bits Ubuntu.
[Virtualbox]("http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_amd64.deb") installer for 64 bits Ubuntu.

This is a [tutorial ]("http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/")on how to do it.

What about rendering, does that work too? I once installed Photoshop inside a VMWare installation of XP and it seemed that all effects that required some kind of rendering were grayed out and could not be used.

---

### Post by Golyadkin on 2007-06-19
I am going to try that out for you right now. Any specific effect you want me to try?

---

### Post by Golyadkin on 2007-06-19
Here you go sir, works like a charm!

[img]http://www.android42.net/got/PhotoshopRenderInVirtualBox.png[/img]

If you want me to try out some other filters, just let me know :) I will keep the virtual machine running for a while.

---

