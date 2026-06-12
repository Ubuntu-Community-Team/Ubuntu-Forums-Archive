---
title: "Which program on XP allows remote session to Ubuntu"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by Panasonica on 2006-12-04
Hi,

I've just set up my first Linux box (Dapper). Hooray :D 
It can succesfully see the other Windows boxes and printers on the same LAN.
I now want to run a terminal session on my (remote-client) XP box, viewing and controlling my (remote-server) Linux box.

What program do I run on the XP box to allow this ?
What do I have to enable on the Linux box to allow it to act as a Remote Server ?

(I believe I need some kind of SSH client on the XP box - is this correct ?)

Many Thanks in Advance
P

---

### Post by Tasu on 2006-12-04
Well, for SSH you can use putty and winscp to transfer files.
If you want a remote desktop solution, well, you have to configure vino on ubuntu (if using gnome) and use any vnc client you find under windows.
But since this is a server you don't have a desktop environment, I guess, so the first option is the one to go with! ^_^

---

### Post by bodhi.zazen on 2006-12-04
Second vote for [putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by notch on 2006-12-04
[PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") is very good, but personally i use [portaPuTTY]("http://socialistsushi.com/portaputty.zip") as  it doesn't store any info in the registry of the windows machine you run it from.

This allows you to run it from a usb key or such and not leave any info on the host machine if you are accessing your remote box from somewhere like an internet cafe or friends PC.

---

### Post by bodhi.zazen on 2006-12-04
> **notch said:**
> [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html") is very good, but personally i use [portaPuTTY]("http://socialistsushi.com/portaputty.zip") as  it doesn't store any info in the registry of the windows machine you run it from.

This allows you to run it from a usb key or such and not leave any info on the host machine if you are accessing your remote box from somewhere like an internet cafe or friends PC.

Thanks for the link. I have a use for portaputty :p

---

### Post by z0d on 2006-12-04
If you're behind a firewall or NAT device (good network or many standard home `broadband' routers), you can enable XDMCP on the Ubuntu box and run a program called "XMing" on the Windows PC. (Xming is my favourite XServer for Win32 at the moment. It claims to need XP but that's not true. I unpacked under WINE pretending to be WinXP and copied to a network share - it ran just fine from Win2k.)

This will allow remote desktop like access to your Ubuntu PC, although I'd recommend not using the same account in two full desktop sessions simultaneously (remotely & locally). It's really good for running individual programs too, you can run e.g. gedit and edit your Ubuntu files from your windows box, that kind of thing.

If you need/want a more secure solution, or you want to use the remote access over the internet, it's possible to forward your XDMCP connection via SSH, and use PuTTY on the Windows client to unwrap it the other end.

However, the easiest `secure' solution I've found is [FreeNX]("https://wiki.ubuntu.com/FreeNX"). Install the FreeNX server on your Ubuntu machine and the client on the Windows PC. This will give you the ability to easily access a remote desktop from pretty much anywhere, though if you are NAT'ed your going to have to put a port forward in your router for TCP port 22 to the Ubuntu server. This has the advantage of being fairly flexible, e.g. it is possible to also access the Ubuntu machine via command-line ssh whilst using the FreeNX session. I understand that FreeNX isn't `free' as in FOSS, though.

I personally don't like VNC, it doesn't take a very long time to crack. :( [YMMV]("http://www.acronymfinder.com/acronym.aspx?rec={8D6FBB07-89E8-11D4-8351-00C04FC2C2BF}").

PS - Also read [http://ubuntuforums.org/showpost.php?p=245962&postcount=5](http://ubuntuforums.org/showpost.php?p=245962&postcount=5). Enjoy Ubuntu!

---

