---
title: "Is VMWare what I need?"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by andyho on 2008-04-14
Alrighty, so I don't really have THAT much of a problem with Wine. But I would like something a little more stable to run Windows progs on, so I was hoping to achieve that by running VMWare. I've already tried Crossover, but it's about the same as Wine! LOL! But I'm a little confused on what I need to make it work. Do I need workstation or server?? Right now my desktop is the only linux machine in the house, but we'd like to convert the other 4 over to linux too. And since they're networked I'm not sure if I should just install VMWare server to save myself any hassels, or if it even really matters.  I've just had some problems with some progs not playing nice with Wine so I figured the easiest way to fix the problem would be to run a virtual desktop of Windows! Right?? Thanks for any help with this!!!

---

### Post by Het Irv on 2008-04-14
It depends on the programs you are using, VM are not the best for games, but other programs should work fine.  If you want to game, dual-booting might be your best bet.

---

### Post by pytheas22 on 2008-04-14
Yes, a virtual machine is probably the best solution if you're looking for a way to run Windows programs that wine doesn't handle well, especially if you have a decent amount of memory and a processor with virtualization extensions (I think all of the Intel and AMD processors come with these now). Windows XP flies for me with about 800 megabytes of RAM on my Ubuntu host a Core 2 Duo.

As an alternative to VMware, however, keep in mind that you could go with VirtualBox, a completely free virtual machine manager.  VMware offers a "player" that can run virtual machines for free, but without the commercial product, it's a hassle to set up virtual machines, although it can still be done legally at websites like [http://www.easyvmx.com/](http://www.easyvmx.com/)  If you already have VMware server or don't mind spending the money, however, it might be a simpler and more efficient solution, since you wouldn't have to install a virtual machine image on each of your computers.  But Virtual Box is quite easy to use and very stable, in my experience.

Also keep in mind that if you want to run games on your virtual machine, Virtual Box doesn't yet provide any support for 3d-acceleration.  VMware does, but it's still in beta mode, and I've never been able to get any 3d-accelerated  Windows games to run acceptably in it.

---

### Post by andyho on 2008-04-14
Nope no gaming to worry about! Well somewhat, but they're REAL basic kids games (Jumpstart 1st grade and such, mostly 2D) and the only problems I've found within them with Wine is sometimes the video graphics or audio hangs. Other than that the only prog I use religiously is Photoshop, and that runs fine in Wine. I am trying to learn Gimp though since it's just as useful! Other than that I‘ve been forgoing the Dreamweaver and been handcoding more! That's about the only progs I use, designing and the internet... maybe some goofy games like Virtual Villagers or Cake Mania. ;) I just figured a vm would give me more fluidity rather than the hang time I tend to get with Wine. I'll definitely check into VirtualBox though!! Thanks!!

---

### Post by bodhi.zazen on 2008-04-14
Both VMWare and Virtual Box (or qemu) are all options / alternates to wine. You will fine they each have advantages and disadvantages and there is some minor variability depending on the application you are wanting to run. In general, the more complex the application the harder to run on wine.

---

### Post by hyper_ch on 2008-04-14
vbox is generally not as demanding as vmware however I think networking and usb doesn't work out of the box as good as vmware...

---

### Post by chrisdugdale on 2008-04-15
I don't play games. Had zero problems with VMware

---

### Post by Tom--d on 2008-04-15
I've been using VirtualBox and it worked straight away (not USB as I don't need it) but networking just worked. Shared folders worked :) 

I would go with VirtualBox as its free.. unlike VMWare has a free 'player'.

---

### Post by linuxlizard on 2008-04-15
I've used both products- I found virtualbox is much easier to use and setup, and faster as well.

Get the latest at:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

Note that this is not the open source edition, but it is free as in free beer. This version has all the bells and whistles that the open source edition does not have built in.

---

### Post by Achtung on 2008-04-15
I would just like to point out that VMware server is also free and has been free for 2+ years now. All you need to do is register (for free!) with the VMware team on their website to download VMware server (for free!). The server version lets you create your own virtual PC images. I don't have a network I can fiddle with so I haven't tried the program's server abilities. 

I have not run VirtualBox yet, as my VMware install (which I installed as my first try in virtualization) works fine with shared folders, USB keys and all that jazz. So if you have the time, try them both and see what works best for you :) Don't forget to report your progress.

---

### Post by Het Irv on 2008-04-15
Yeah, VMware server is free, you just have to sign up for all the junk mail.  As for setting up VMware server is just as easy as Vbox, but it is harder to find an install file because it is kernal specific.

---

