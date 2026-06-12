---
title: "Remote Desktop, Ubutu to Ubuntu"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-07-14
I have enabled Remote Desktop via System --> Preferences --> Remote Desktop

Every thread then suggest that I use vncviewer to connect to that machine. But I can't find it anywhere to install. Do I have to download it from the net since synaptic can't find it (I have most repositories enabled) or is xvncviewer (which is found) the one I should use?

When I connect to any Windows box, I simply use tsclient. Isn't there any way to use tsclient in order to connect to your other computer and see the remote desktop?

---

### Post by steve8track on 2007-07-14
I think tsclient and xdmcp are related.  This would allow each person to remotely access the computer as different users (maybe not what you had in mind, though I guess end result may be the same).  I am thinking of using it instead of vnc so that I can log in on startup, since I don't know if you can access the computer before login using vnc.

This is what I used when I set up remote access (Edgy):

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Remote_Access")

I looked on Synaptic, and it looks like I don't have vncviewer installed, only xvncviewer, xtightvncviewer, and vnc-common.  I think you're right, **xvncviewer is what you want**.  Don't forget that if you are accessing the computer from outside of your local network, you need to set your router to forward port 5900 (unless you set it to a different port).

Good luck.

---

### Post by SirGrant on 2007-07-14
VNCviewer is accessed by going to commandline and simply typing vncviewer

I use ultraVNC which runs very well in WINE.  I just use it because I'm familiar with it and it works when I want to connect to either my brother or grandparents ubuntu machines.

---

### Post by steve8track on 2007-07-15
I thought I would add that despite using xvncviewer, the terminal command line is still vncviewer, and a place you can read about passwords for vnc is here:

[https://help.ubuntu.com/community/x11vnc]("https://help.ubuntu.com/community/x11vnc")

That way you can use a script or a icon shortcut to view your remote desktop, without risking others getting your password.

---

### Post by steve8track on 2007-07-31
I've tried xdmcp, and it works way better for me than vnc did, though you have to use it from your ubuntu login.  Also, for security reasons, it is used on a local network only (though I guess you could port forward).  It looks and feels like I'm on the other computer, only with the graphics card of this one, which is fine by me.  It seems to use local graphics, while using the remote hard drive and remote processor.

Good luck.

---

### Post by medley on 2007-07-31
> **MockY said:**
> I have enabled Remote Desktop via System --> Preferences --> Remote Desktop

Every thread then suggest that I use vncviewer to connect to that machine. But I can't find it anywhere to install. Do I have to download it from the net since synaptic can't find it (I have most repositories enabled) or is xvncviewer (which is found) the one I should use?

When I connect to any Windows box, I simply use tsclient. Isn't there any way to use tsclient in order to connect to your other computer and see the remote desktop?

If you're using Ubuntu, you should find an app called 'Krdc Remote Desktop Connection' under 'Internet' in your K-menu (equivalent to the start menu in XP). This is actually a VNC client and works well enough for me. I have 7 computers on my home network (3 of which run Kubuntu), and I use this to access any of them. Right underneath that you'll find 'krdc' which is the server and can be used to set up your Ubuntu machines to allow remote connections to them. On my XP machines I use UltraVNC both as server and viewer. From any machine on my network I can access any other system this way.

Cheers and hope this helps.

---

