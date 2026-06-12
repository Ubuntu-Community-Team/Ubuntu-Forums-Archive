---
title: "boot straight into ubuntu &amp; check services"
date: 2007-07-02
forum: Apple PPC Users
---

### Post by peady on 2007-07-02
HI,

I have a G4 running 6.10 (what command do I run to check that?). I'd like to be able to boot straight into Ubuntu on restart. Currently I have to press return once yaboot has run, which sucks if I edit something remotely that requires a system restart and I'm not at home. Also I want to switch it off from time to time and not have to plug in a darn monitor to make sure it's up and running again.

Does this involve editing the yaboot.conf file? Current dump below:

```
boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"
```

Also, I have ssh & apache running. What do I review/edit to ensure those services are running on restart?

And, just in case there's some guru out there, I'd like to stop hiding my web server behind my router firewall and need some pointers on security issues/fixes I'd need to check before doing that. Anyone got a link or 2?

Thanks in advance,
Dave :D

---

### Post by peady on 2007-07-08
OK, I've managed to find some answers myself, will post back for searchers of the thread and want to bump this post, with other questions!

First, the command to find out which version your running: lsb_release -a

Second, to boot straight into ubuntu, according to my yaboot dump previous, just change timeout=0

HOWEVER, now my question.

I want to run a headless (without a monitor) server. If a monitor is connected, then linux will boot.

But, if the monitor is then disconnected and I restart, yaboot/linux doesn't boot.....!?

I've read somewhere that some BIOSes need a video card in order for yaboot to run. Could it be that when the monitor is disconnected and the box restarted it's as though there isn't a video card therefore linux won't boot?

This seems strange on a server edition of ubuntu, no? I'd have thought most servers were headless?

Help anyone?

Cheers,
Dave

---

### Post by herkamire on 2007-07-14
I'm pretty sure that's a hardware/BIOS problem. When I first started doing webserver administration around 2001 we baught these cheap little things that plugged into the vga ports and pretended to be a monitor.

That made it so they would boot properly.

You can probably still get them somewhere, I wish I remember what they're called.

Best of luck,

     - Jason

---

### Post by stmiller on 2007-07-15
Dave,

Macs don't have a BIOS. There is somewhat of an issue getting Powermacs to boot headless. I saw some chatter about this on another mailing list recently. I know some have done it.

For managing services, install the boot-up-manager

$ sudo apt-get install bum

then run with

$ sudo bum

---

### Post by peady on 2007-07-16
Thanks for the heads up chaps.

Jason - I have come across a useful site which details a sort of 'terminator' for video cards but I'm yet to give it a go.

[http://tvtool.info/go.htm?http://tvtool.info/english/dummy_e.htm]("http://tvtool.info/go.htm?http://tvtool.info/english/dummy_e.htm") 

stmiller - Would you say that Open Firmware is a kind of BIOS? Thanks for the boot-up manager pointer :D

---

### Post by Tommy on 2007-07-16
> **peady said:**
> Would you say that Open Firmware is a kind of BIOS? 

Open Firmware and BIOS are not the same, but serve a similar purpose -- preparing the computer to load the operating system.

I believe Open Firmware is closer to an actual operating system (akin to DOS on a PC), except you interact with it in the Forth language. 

By contrast, a PC's BIOS generally presents only a setup application that lets you change a few flags in the non-volatile RAM, set the clock, etc. and nothing else. 

As this article says, Open Firmware is a Foot Shooting tool of substantial power: [http://lwn.net/Articles/209301/](http://lwn.net/Articles/209301/)

And of course, the Wikipedia has an article: [http://en.wikipedia.org/wiki/Open_Firmware](http://en.wikipedia.org/wiki/Open_Firmware)

SO you could say a Mac or Sparc system is a functional computer even BEFORE loading the operating system, as opposed to a PC that can only load the setup screens. 

One counter-intuitive difference -- Open Firmware usually requires "secret" knowledge (Forth commands) to operate, because Open Firmware systems may not even HAVE a setup application. (Macs don't -- I don't remember whether Sparc systems do.)

---

