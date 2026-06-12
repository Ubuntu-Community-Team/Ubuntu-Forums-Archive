---
title: "Infra-red use?"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-02-24
I installed Ubuntu 5.10 on my Powerbook which has built-in infra-red.  Is there anything that I can do with it or any programs available for infra-red?

Thanks

---

### Post by tgalati4 on 2007-02-25
Infrared is a stange beast.  You can use if for short range networking (few feet max) to ftp files between machines, share internet connections, print files to an infrared printer.  You can also use it to sync your phone and push files (music and pictures for instance) to it.  It's not fast.

Bluetooth is a better option.

I have it working on a Dell laptop, not sure how well it is supported on PPC.

Search irda, obex, and infrared in synaptic to see what is available in ppc.

Most people want to control their TV with their laptop.  It can be done, but it's a pain.

Others want to control iTunes or xmms with a TV remote.  This too is viable, but again its not easy to set up.

irda-utils are the baseline apps to start with.  Search the forums for other's aspirations with infrared.  There are also a few decent tutorials on the web.  Google infrared linux

Good luck.

---

### Post by mdknaebel on 2007-02-25
Thanks!

---

### Post by mdknaebel on 2007-02-25
uhhh.... maybe this is too advanced for me... I don't really understand how to even install other programs, and I cannot find the ones installed from the synaptic...

Oh well...

---

### Post by tgalati4 on 2007-02-27
Most of the development of infrared drivers is from the pc side so I don't expect a lot of work on the ppc side.  It's difficult to cross-compile such software because it is hardware specific.  And mac hardware is difficult to get specs for in the first place.

I have a powerbook g4 15", 1.0 GHz.  It runs the Ubuntu Live CD OK (dapper drake)  I don't have infrared on it.  But bluetooth works pretty well.  I use a remote-control application on my phone to control iTunes via bluetooth.

I have my pbook plugged into my home stereo to listen to podcasts and the pbook will fade to mute when my cell phone gets a call.  The program will resume when the call ends.  It's pretty slick.

I have infrared on an old Dell Inspiron 7500 laptop and I can communicate with my cell phone under Dapper Drake transfering files and syncing contacts.  I tried to get TV remote control to work but I'm getting compilation errors so I haven't built the programs yet.  Even then, reports from the web indicate it is iffy at best.  Most laptop infrared chipsets are designed for short range, high-speed communication.  Hacking them to work with consumer-grade TV remotes is difficult because of the different timing and optical properties involved.

So, if you can't find any infrared programs in synaptic, that means nobody has compiled them successfully to work on the PPC platform.

On my powerbook, I run Tiger 10.4.8 and XDarwin and I can run gnome applications (including the entire Gnome Window Manager) in a separate desktop.  This means I don't need to dual boot to enjoy Linux goodness and I have all of the hardware supported under Tiger.

Good luck

---

