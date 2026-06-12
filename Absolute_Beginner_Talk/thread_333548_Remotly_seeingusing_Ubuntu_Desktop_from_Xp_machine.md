---
title: "Remotly seeing/using Ubuntu Desktop from Xp machine on same Network?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2007-01-07
Firstly my setup:

Broadband coming in via a Telewest Blueyonder modem, into a DLink Router.

Into this router, I have 2 machines connected via cable.

One a PC running Windows XP home.
The other a PC running Ubuntu (clean fresh install)

What I wish to do is to open a window on the screen of my XP machine and see the desktop of my Ubuntu machine in this window.

Then be able to control the Ubuntu machine (click on icons/run programs etc) then copy files back onto my XP machine.

I have 2 "BIG" Problems:

1: Networking is always a bit of a nightmare getting working even between Windows PC's
2: I know absolutly nothing about Linux and Ununtu.

Someone said about needing a VNC client for the XP machine and a VNC server on the Ununtu machine (which he says may already be there)

Someone else said this is slow, and recommended "NX Client" instead.

The problem is, then we go onto making sure ports are open, starting services, netowrk names, protocols etc etc and I just get lost in seconds.

Is there no way I'm ever going to get working what I want?
I need a very, and I mean VERY basic step by step idiots guide to getting this to work.

Thanks for listening.

---

### Post by halitech on 2007-01-07
here is the guide I used for controlling my ubuntu server from ubuntu but the principle will be the same. just use something like tightvnc on the xp machine to take control

[http://www.ubuntuforums.org/showthread.php?t=191564]("http://www.ubuntuforums.org/showthread.php?t=191564")

edit: far as opening ports, that would only be needed if you are planning on taking control from outside your local network

---

### Post by PiggiePaul on 2007-01-07
> **halitech said:**
> here is the guide I used for controlling my ubuntu server from ubuntu but the principle will be the same. just use something like tightvnc on the xp machine to take control

[http://www.ubuntuforums.org/showthread.php?t=191564]("http://www.ubuntuforums.org/showthread.php?t=191564")

edit: far as opening ports, that would only be needed if you are planning on taking control from outside your local network


Thanks for coming to my rescue.

Amazingly I've just managed to get it working far simpler than I thought possible.

I just ran remote desktop on my Ubuntu machine and installed SAMBA (SMB)
It told me the name I'd need for use with a VNC viewer.

Went to my XP machine, installed TightVNC put in the name it gave me and it worked !!!

My jaw hit the floor as I was just expecting either an error message, or nothing.
The only issue now is how to transfer files between the two machines?

I created a new folder on my Ubuntu machine called "Downloads" and make it shared thru "SMB" Windows Networks, and I put a small test file in this shared folder.

Using TightVNC on my XP machine I can see this shared folder and I can see the file inside, yet I can't work out how I get any files From the Ubuntu machine onto my XP machine or visa versa?

---

### Post by houstonbofh on 2007-01-07
Based on what you have said, skip the NX client.  The main advantage is "over the net" communication, and you don't do that.  Also, don't worry about ports.  Ubuntu doesn't have (or need) a firewall, since it does not listen on a lot of insecure ports.

For remote control, you can use VNC.  I have tightVNC [http://www.tightvnc.com/](http://www.tightvnc.com/) on all my Windows systems.  Remote control both ways.  You will need to enable it in Ubuntu under system preferences to see the Ubuntu desktop.  You will need an exception in your windows firewall to see the Windows desktop.

For file transfer, you can use samba, but windows filesharing is hard.  Even on windows.  I like ftp.  I have ProFTPd on all my Ubuntu machines, and FillZilla client and server on Windows.  (Windows firewall rules again)  Solid file transfer.  On ubuntu under Places, you can "mount" and FTP site and it looks like another drive.  So simple even my mother can do it. :D

Another remote method to look at is SSH/Xtunnels.  This is a little more difficult, but SOOOO nice.  On the Windows side you will need putty and Xming.  On ununtu you will need the ssh server.  Putty is an SSH client.  It is like a secure telnet.  But you can tunnel files and Xwindows over it.  Xming [http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/) is an Xserver for windows.  If you run Xming's xlaunch, and ssh to your system with xtunneling enabled, you can run gui apps from the cli, and they will pop up on your windows system.

Hope this helps.

---

### Post by PiggiePaul on 2007-01-07
Just to update. I did only install the TightVNC Viewer and not the Server.

As I thought I was only using my XP machine (I was installing this on) to VIEW my Ubuntu machine.

Dunno if that was right or not?

---

### Post by PiggiePaul on 2007-01-07
Thanks "houstonbofh" for the advice.

Stupidly (I thought) you would just be able to drag and drop files from the VNC Viewer window onto your XP Desktop (drag and drop)
I now know this aint gonna happen :(

I kinda feel it's "Almost" working.

In my Ubuntu desktop, if I go to the "Places" menu and then to "Network Servers" I can actually see an Icon called "Windows Network"

If I click on this Icon I get another icon with the name of my windows network "pig".

Just 1 step away it feels.

But when I click on this icon I just get an error message "The Folder Contents Could Not Be Displayed - Sorry, couldn't display all the contents of "Windows Network: pig"

---

### Post by gg234 on 2007-01-07
here is [step by step guide ]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")try this 

hope this helps

---

### Post by PiggiePaul on 2007-01-07
> **gg234 said:**
> here is [step by step guide ]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html")try this 

hope this helps

Thanks for that EXCELLENT guide.
That was exactly what I did by guesswork :)


And easy to use guides like that are what I need at the moment.

I have this working (as I explaned above) albeit, I'm using TightVNC though I don't suppose that makes any difference does it?

My next challenge (which seems like its going to be harder) is how do I get files moved between the two machines?

I was hoping for a drag and drop (but I don't think that's going to happen) or even a right click and send to.

I have made a shared folder on my Ubuntu machine and make it shared thru "SMB" Windows Networking.

Yet, I've not been able to find this shared folder from my Windows machine yet.

---

### Post by houstonbofh on 2007-01-07
You might have your Windows Firewall preventing you from connecting.  I can never get Windows filesharing to work with firewalls in place.  Get FileZilla server [http://filezilla.sourceforge.net/](http://filezilla.sourceforge.net/) for Windows, and install it.  Allow it in your Windows firewall.  Start the service when you want to share, and stop it when you don't.  Then in Ubuntu you can connect to it, and it will be a mount on your desktop.  Your FTP server on Windows will be just another drive on Ubuntu.  Now you can drag and drop from within the VNC window.

As to TightVNC server, that is for you seeing the Windows desktop in Ubuntu.

---

