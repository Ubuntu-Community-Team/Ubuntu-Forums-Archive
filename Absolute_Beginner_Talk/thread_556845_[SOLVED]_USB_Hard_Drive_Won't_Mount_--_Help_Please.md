---
title: "[SOLVED] USB Hard Drive Won't Mount -- Help Please!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by lespaul_rentals on 2007-09-21
**SOLVED -- MODS PLEASE CHANGE NAME TO [SOLVED] SO THIS CAN HELP OTHERS**

Running Kubuntu 7.04.

Okay, I am at my wits end.  This is extremely frusterating.  I cannot access my USB hard drive.  When I plug it in, it gives me the autorun popup, asking me what I want to do.  Access my files in a new window, I say.  But when I click it it just disappears and nothing happens.

On my previous install this was VERY easy to fix after a lot of searching around.  Because I chose to install Kubuntu, it left out the gnome-volume-manager which was the magic package.  I just installed then it worked like a charm.

However, on THIS install it's a gigantic headache.  I tried installing gnome-volume-manager, killed it and reopened it many a time.  I still get the autorun window, but it amounts to jack-crap when I select an option.  It just won't mount my drive.

After some messing around in the terminal, I finally got it to mount.  The USB device is now in the media folder, linked to a drive called "USB1."  When I plug it in, "Simpledrive device" appears on my desktop.  I was very happy...except when I clicked on either /media/usb1 or "Simpledrive device" on my desktop, I got a message saying I "did not have access rights to this location."

I googled and ubuntuforumed for a long time more, until I stumbled across a command that was supposed to give me privileges.  I ran it and it said sufficient read/write priveleges were given to my username for the device, and it DID change something.  Instead of saying I "did not have access rights to this location" it said I "lacked sufficient privileges."

*sigh*  I am very frusterated.  Please help me out.  :(

---

### Post by tedonastick on 2007-09-21
Sadly, I don't have an answer, but the same problem.  Iset up Ubuntu on my desktop as a dual-boot system so I could gte away from Vista, but it won't let me save to my hard-drive outside of the Ubuntu system directory (which is too small) or my usb HD (which it thinks is root).  I just need some storage space for stuff that can be accessed from Windows or Ubuntu, but neither works.  I'm close to a complete re-format/reinstall of everything.

Blah. . . 

Ted

---

### Post by lespaul_rentals on 2007-09-21
Thanks for posting mate, glad to know I'm not alone.

I solved this, by the way.  I'm going to leave this thread up so other people can hopefully be helped by my directions:

I restarted my computer then X Server.  I switched my session to a brand new instance of KDE.  Log in, and verify that gnome-volume-manager is installed.

```
sudo apt-get install gnome-volume-manager
```

Once you are SURE it's installed, type this:

```
gnome-volume-manager
```

Plug your device in.  Select Open New Window.  It should work now.

---

### Post by ravenwere on 2007-09-23
Rather than hybridize KDE and Gnome. You can use the konsole to mount the usb hdd. using the sudo mount /dev/sd?? command.

To facilitate this you also need to add a line to your fstab file.

KDE doesn't automount usb hdd very well, especially if they are formatted as NTFS.

However if you are prepared to use the command line its no big deal.

---

### Post by byourg on 2007-09-24
I'm using Kubuntu 6.06 Dapper and the automount of USB drives is broke also. I transfer files by these drives once in a while and now I can't. I'll try some of the konsole tricks til they come up with a fix I hope.

---

### Post by lespaul_rentals on 2007-09-26
I'm comfortable with command line, but I much prefer plug-and-play style when it comes to devices.  If I want to transfer a single text file from my USB hard drive, why type a mount command every single time?

---

