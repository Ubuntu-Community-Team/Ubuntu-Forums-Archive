---
title: "[SOLVED] graphical application for connecting UBUNTU to windows LAN?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by viiv on 2007-10-11
I am looking for a GUI application that manages a connection to a Windows LAN. I'm running UBUNTU 7. As far as I can tell, SAMBA only runs in terminal?

---

### Post by HermanAB on 2007-10-11
Swat.

However, you'll likely find that using Swat is even more difficult than using the command line.  The trouble with a GUI is that the error messages are hidden, so it is fine when it works, and worse than useless when it doesn't.

Cheers,

Herman

---

### Post by tgm4883 on 2007-10-11
Are you trying to connect to shared folders or just access the internet.  Have you looked in Places > Network?

---

### Post by viiv on 2007-10-13
> **HermanAB said:**
> Swat.

However, you'll likely find that using Swat is even more difficult than using the command line.  The trouble with a GUI is that the error messages are hidden, so it is fine when it works, and worse than useless when it doesn't.

Cheers,
Herman

Thanks Herman. I'll check it out. 
Eventually I would like to be able to do more with command line, but I'm just recovering from a lifelong dependency on windows ;)

> **tgm4883 said:**
> Are you trying to connect to shared folders or just access the internet.  Have you looked in Places > Network?

tgm.
That sounds logical... but I'm not sure where I'm supposed to go to find "Places". Are you talking gui or command line?

---

### Post by tgm4883 on 2007-10-13
GUI, next to Applications

---

### Post by HermanAB on 2007-10-13
BTW, if you install KDE, then you can run Konqueror (Konq works in Gnome too).  With Konqueror, you have pretty much all file protocols ever invented right at your finger tips.  To connect to a Windows file share, just type:
smb://servernameoripaddress/sharename

and there you go.

You can expand that to include all the parameters:
smb://username%password:workgroup@servername/sharename

Turn that into a bookmark and then you just point and click.

Here is a Samba debug guide:
[http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

---

### Post by steve.horsley on 2007-10-13
Same is true in nautilus too. I made a set of desktop launchers, one per server, that launch the command:
nautilus smb://domain;user@server/C$

I should point out that this behaves like an FTP connection in that you can drag/drop files, but the remote is not mounted into the local filesystem and you can't cd there with a command prompt or open files in situ by File->Open in applications.

---

### Post by viiv on 2007-10-13
> **HermanAB said:**
> BTW, if you install KDE, then you can run Konqueror (Konq works in Gnome too).  With Konqueror, you have pretty much all file protocols ever invented right at your finger tips.  To connect to a Windows file share, just type:
smb://servernameoripaddress/sharename

and there you go.

You can expand that to include all the parameters:
smb://username%password:workgroup@servername/sharename

Turn that into a bookmark and then you just point and click.

Here is a Samba debug guide:
[http://www.aeronetworks.ca/samba-debug-howto.html](http://www.aeronetworks.ca/samba-debug-howto.html)

Cheers,

H.

I forgot to mention that I'm running XFCE (I barely know what that means). It looks like I've been able to run KDE programs on this machine. would I have to switch to KDE (am I even referring to this stuff correctly?) to run something like Konq?

> **steve.horsley said:**
> Same is true in nautilus too. I made a set of desktop launchers, one per server, that launch the command:
nautilus smb://domain;user@server/C$

I should point out that this behaves like an FTP connection in that you can drag/drop files, but the remote is not mounted into the local filesystem and you can't cd there with a command prompt or open files in situ by File->Open in applications.

I looked at Nautilus. It looks pretty similar to my Thunar file manager. Am I correct in this assumption? Could Thunar do the same things?

> **tgm4883 said:**
> GUI, next to Applications
I'm not finding it. Under APPLICATIONS I have (starting from the bottom up): QUIT, ABOUT XFCE, SYSTEM, OFFICE, NETWORK, MULTIMEDIA, GRAPHICS, GAMES, FILE SYSTEM, ACCESSORIES, SETTINGS. Under NETWORK I just find a few programs that I've installed: firefox, gaim, thunderbird, kwifi, & wifi radar.


{TO EVERYONE}
I appreciate all the responses.
I just found the shared folders app in my APPLICATIONS menu (it was under my SYSTEM folder) I opened it and it promts me to ADD a shared folder. I'm not currently in my office, so I can't try it out till monday, but I'm guessing I'm on the right track?

I installed SWAT, but I got the same results as for SAMBA... nothing... I install it but I can't find an icon for it anywhere (I know I know, still recovering from the windows environment). I tried to guess on a few command lines to execute, but nothing happened...

---

### Post by steve.horsley on 2007-10-13
I've never seen thunar, but I know it's a file manager like nautilus or konqueror. So it is well worth trying putting smb://servername/C$ into the location bar (assuming it has one) and see what it says.

---

### Post by viiv on 2007-10-14
> **steve.horsley said:**
> I've never seen thunar, but I know it's a file manager like nautilus or konqueror. So it is well worth trying putting smb://servername/C$ into the location bar (assuming it has one) and see what it says.

I'll give it a try on Monday, when I'm back at the office.
I don't know why I didn't think of that. It's the same for windows.. basically.
thanks

---

### Post by viiv on 2007-10-16
Problem solved.
I installed Konqueror and it works great. Thanks everyone!

---

