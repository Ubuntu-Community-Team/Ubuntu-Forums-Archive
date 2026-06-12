---
title: "Remote Desktop"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-05-23
Is there a Remote Desktop program like the one that comes with Windows XP pro so that I can connect to my Linux machine using anything supporting the protocol like, "Remote Desktop Connection" in windows or "Terminal Client" in ubuntu? I found something uner Administration but I don't know if this will work.

---

### Post by Ek0nomik on 2007-05-24
In Ubuntu, under Preferences, there is an option called Remote Desktop.  You can set it up that way.  The software Ubuntu uses out of the box for Remote Desktop is called Vino.  Personally, I find it to be a bit sketchy.  I find it rather slow and the screen drawings can get pretty lagged out.

When I had Edgy I used x11vnc, (search the forums, you will find tutorials for it), and it worked perfectly.  Plus, with x11vnc, you could login to the "Log in" screen which was beneficial.  x11vnc uses display :0.

Otherwise, you can always use SSH.  There are plenty of sites that explain SSH, but all you should have to do to install it is:

```
sudo aptitude install openssh-server
```

SSH will allow you to get to the terminal in your Ubuntu box, but you can also run programs on your local machine that are installed on your remote Ubuntu machine.  If you are using Ubuntu as your local machine, you just need to be running the same window environment or have the correct library files installed.  If you are connecting to Ubuntu from Windows, than you can get a X Server emulator (Xming is an example of a free program for Windows that will do that).

I suggest you try SSH just for kicks, but you can also just settle on Remote Desktop, but it isn't quite up to par in comparison to Windows boxes... at least not yet.

---

### Post by arvevans on 2007-05-24
The beauty of VNC  (I use "tightVNC") is that there are compatible client and server packages for MS-Windows as well as for OS-X, UNIX, BSD, and Linux.  Thus you can do remote desktop with most of the world's operating systems.

Arv
_._

---

### Post by Ek0nomik on 2007-05-24
> **arvevans@earthlink.net said:**
> The beauty of VNC  (I use "tightVNC") is that there are compatible client and server packages for MS-Windows as well as for OS-X, UNIX, BSD, and Linux.  Thus you can do remote desktop with most of the world's operating systems.

Arv
_._

You use TightVNC as a Remote Desktop Server on Ubuntu?

---

### Post by Emerzen on 2007-05-24
Hey guys thought I'd add my 2 cents.  Indeed vino will act as a vnc-server and RDC from xp-pro will be able to view your desktop.

However, I'd give SSH a second thought for a few reasons.  If you install the SSH server on your Ubuntu box w/ the SSHFS package, you can then browse your computer in GUI mode from a client.  On a windows client, d/l the WinSCP program (FOSS).  With WinSCP you can log into your SSH server and view the entire file structure.  This is great for file transfers SFTP and SSCP.  You can also have a terminal window to control your server box from Windows by d/l and installing PuTTY on the windows-client side.  The advantage is that all the traffic is encrypted.  VNC/RDP only encrypts your username and password, all other traffic is sent in the clear.  However, if you really want to have that "I'm sitting in front of my desktop" than RDP is the way to go.  If you're really adventurous, you can set up VNC to be tunnelled by SSH thereby getting the best of both worlds.

---

### Post by arvevans on 2007-06-17
"*You use TightVNC as a Remote Desktop Server on Ubuntu?*"

Yes.  Tight-VNC install includes both server and client software.
I run it on this computer and via a VPN with a RedHat Linux system that i administer remotely.

It is in the Synaptic Package Manager list of installable programs.
_._

---

