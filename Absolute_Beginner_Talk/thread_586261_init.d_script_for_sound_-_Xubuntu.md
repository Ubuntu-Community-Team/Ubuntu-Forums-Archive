---
title: "init.d script for sound - Xubuntu"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by TimSup on 2007-10-22
Hello again,

I'm trying to get my sound to work on my laptop. I found a guide on the internet for the type of laptop I have and it gives some advice on how to get the sound working.

Here is the site I found: [http://linux-laptop.net/hosted/xubuntu-thinkpad770e.html](http://linux-laptop.net/hosted/xubuntu-thinkpad770e.html)

The first thing it says is to install pnpbios-tools which I did using the package manager.

However the next parts I have no idea how to do. Apparently I need to make a script in a certain directory with this included, here's what he says:
[FONT="Courier New"]
I made a script which is placed in /etc/init.d/ibm-sound and is run on boot. Here it is:

setpnp 0e on
setpnp 0f on
setpnp 11 on
modprobe snd-pcm
modprobe snd-cs4236 index=0 port=0x530 cport=0x538 dma1=1 dma2=0 irq=5 isapnp=0[/FONT]

So my question is, how do I go about making this script and putting it in the proper directory? Or is there an easier way to do this?

---

