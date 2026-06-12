---
title: "FreeNAS fuctionality with Ubuntu/Kubuntu?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Sven Nijs on 2007-04-28
Hi, i'm an absolute beginner!

I have built up a Dell server with Pentium D9 processor, 80Gb IDE OS drive & 500Gb SATA 'data' drive.
I would ultimately like to add another 2 or 3 500Gb's and run software RAID5. This was intended to be purely for use as a 'headless' storage box in a home environment.

It would therefore seem be very easy to install FreeNAS (or to a lesser extent Clark Connect) and  be done with it but....
seeing as I have a fast-ish dual core processor, it would make sense to also give it the ability to download torrents, encode video etc etc while it's sat there powered up.

I am clueless with CL so having a GUI is important to me (until I learn more) as would be the ability to administer the box from another PC on the network (so I can stick it in a cupboard out of the reach of small childrens fingers/toast etc).
I will need Samba so I can store data from my MS box (and a future linux HTPC) and I want the ability to set up, run & expand a RAID array (from 3 disk to a max of 4).

Is this a feasable/sensible plan?
Is it better do this this with a complete desktop install or the 'CL only' server install and add packages?
If a desktop install *is* preferable: should I use the AMD64 ISO for compatability the pentium D.
Is there a preferable flavour of ubuntu/kubuntu/xubuntu to use for my plan or does it not matter if it's Gnome or KDE?

As further background: in the past week I have installed and briefly looked at:
ubuntu **&** kubuntu **&** ubuntu server versions of 7.04
Fedora Core 5 (*seems* to have better/more obvious, built in disk management than ubuntu?)
FreeNAS (ideal for the storage side of things but I don't know how it would react if a RAID disk failed or when another was to be added)
Windows Home Server (just creates a big 'pool' of storage - definitely don't know what happens if a disk fails!!)

So, there you go. This is probably all very simple fair for Linux experts but seems complex to me.
What do the experts think?
Thanks in advance :D

---

### Post by [S|G] on 2007-04-28
If you're going to use it to download, encode video and do other things, I don't think that FreeNAS would be appropriate, since it is a quite minimalistic distro that would be hard to expand.

If you choose to use ubuntu, you could use the i386 images without worry, since most users report that there is no visible performance loss and is usually more stable than the 64-bit version (I use the x86 on my core 2 duo myself).

The desktop environment (kde, gnome, xfce) is totally up to your preferences, and you can run a VNC server to have access to the graphical interface remotely.

---

### Post by Sven Nijs on 2007-04-29
Thanks for the response and advice [SlG] :)
I've done a little more reading and it has been suggested the *alternate* version may be better for my needs as it contains mdadm in the ISO. I'm downloading it now and will have to give it a go later.

---

