---
title: "Prevent desktop from starting automatically and VNC questions"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by LorenzoS on 2007-12-20
Hi, very new user here.  I’ve been lurking for the last month getting answers while I got my first installation running.  It’s been great so far but I finally have a problem I can’t find an answer to.  

I successfully got Gutsy Server running and I can SSH into the server using PuTTY.  I also installed the Ubuntu desktop (sudo apt-get install ubuntu-desktop .. sudo apt-get install gdm) and installed VNC server (sudo apt-get install vnc4server) and can successfully remote desktop from my Windows box using VNC, but only if I am already logged into the desktop on the Ubuntu box.  If I reboot the server I can’t VNC into it unless I walk over to the Ubuntu box and log in first.

Since this is primarily a server, I would really appreciate some help knowing how to:

[LIST=1]
[*]Prevent the desktop from starting automatically.
[*]Start the desktop from the command line remotely when I need it.
[*]Be able to remote desktop into the Ubuntu box without having to first log in physically at the box.
[/LIST]

Any help is greatly appreciated.  Thanks.

---

### Post by stalker145 on 2007-12-20
> **LorenzoS said:**
> Since this is primarily a server, I would really appreciate some help knowing how to:

[LIST=1]
[*]Prevent the desktop from starting automatically.
[*]Start the desktop from the command line remotely when I need it.
[*]Be able to remote desktop into the Ubuntu box without having to first log in physically at the box.
[/LIST]

If you really wish the remote desktop capability, there are many ways to do it. One that I found recently and am really enjoying is [NoMachine]("http://www.nomachine.com"). It's free, so easy to set up (3 deb files and no configuration), and uses SSH to tunnel anything from a CLI SSH session to a remote desktop session to a VNC session. It's nice.

Another option is to use the built-in remote desktop capability. Simply go to System ~> Administration ~> Login Window and choose your settings under the remote tab.

Neither of these require your computer to be logged in. It just has to be turned on :D

If you're going to be accessing this from outside your router, make sure you have good pasword security and you forward the appropriate ports.

Check back if there's anything else.

---

### Post by LorenzoS on 2007-12-21
Stalker, thanks for the help but this is not working on my system.  I do have Remote Desktop enabled, but I get an error "Failed to Connect" from UltraVNC Viewer if I attempt to connect when I am not actually logged in at the box.  It works fine if I am already logged in.  

As a test, I enabled automatic login on the desktop so after a reboot, it logs me in and then I can connect to Remote Desktop through VNC.  

Perhaps there is some configuration somewhere that I might be missing?  Note that I installed the desktop on top of the Server installation.  

My ultimate goal here is for the desktop to not automatically start with the system since I will need it infrequently.  If I want to use it, I would like to remotely use SSH or some other remote tool to start it up, use it then shut it down when done to conserve system resources.

---

### Post by stalker145 on 2007-12-21
> **LorenzoS said:**
> Stalker, thanks for the help but this is not working on my system.  I do have Remote Desktop enabled, but I get an error "Failed to Connect" from UltraVNC Viewer if I attempt to connect when I am not actually logged in at the box.  It works fine if I am already logged in.  

As a test, I enabled automatic login on the desktop so after a reboot, it logs me in and then I can connect to Remote Desktop through VNC.  

Perhaps there is some configuration somewhere that I might be missing?  Note that I installed the desktop on top of the Server installation.  

My ultimate goal here is for the desktop to not automatically start with the system since I will need it infrequently.  If I want to use it, I would like to remotely use SSH or some other remote tool to start it up, use it then shut it down when done to conserve system resources.

VNC won't work, in my experience, unless you are logged in - there's no setting that you missed. What you could do is leave the computer turned on and at the GDM/CLI login screen and either SSH or remote login. The nice thing about SSH'ing is that you can forward only the programs you need to your screen. ```
ssh -X user@IP.add.re.ss program-name
```To enable remote login, go to System ~> Administration ~> Login Window ~> Remote.

---

