---
title: "X Windows"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by AaronLS on 2007-12-07
I have setup the SSH server on my Ubuntu machine, and would like to be able to be able to open X windows over SSH from a WinXP machine.  

My client is a WinXP box with a SSH Secure Shell version 3.2.9.
My Ubuntu installation is version 7.04.

I have not really setup anything else other than firestarter and the SSH server.  I also changed the default SSH port.  I am able to successfully connect to the Ubuntu machine from winXp with the SSH Secure Shell client.  I have enabled "Tunnel X11 Connections" in the SSH Secure Shell client.

From there I am mostly lost.  I have tried to read guides, but I get lost because because sometimes they aren't clear on whether the steps they are describing should be performed on the client or server.

Thanks in advance.

---

### Post by Dr Small on 2007-12-07
You can't tunnel X applications over SSH to a Windows machine that doesn't have Xorg installed. Your best bet would be to do this on a Ubuntu machine, and then you could tunnel the X display of Firestarter directly to your destkop.

---

### Post by AaronLS on 2007-12-07
> **Dr Small said:**
> You can't tunnel X applications over SSH to a Windows machine that doesn't have Xorg installed. Your best bet would be to do this on a Ubuntu machine, and then you could tunnel the X display of Firestarter directly to your destkop.

Thanks, X.Org goes on the Ubuntu machine.

Do I also need some sort of emulator on my WinXP machine, such as X-Win32?  This is what is called X Windows Server, correct?

---

### Post by Dr Small on 2007-12-07
Xming may be what you need:
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

If you get that to work, make sure X11 Forwarding is ON in your sshd_config

Dr Small

---

### Post by AaronLS on 2007-12-11
I discovered I didn't need to install anything on the server, but did need to run GDM.  ?I'll have to figure out how to set it up for automatic startup or as a service.

I installed xming and the Portable Putty download that comes with xming, and installed them both.  I tried to follow a tutorial on using XLaunch but when I compelted the tutorial it just makes this chime sound in windows and nothing happens.

If I start xming.exe, then run putty and connect to the server, I can then run things like xterm or gedit and the graphical window pops up.

I'm not sure what the deal is with Xlaunch, but I can't find any forums for support.  I kind of hoped I could get it working on a thumb drive.

Anyway, thanks for the help.  I am having alot of fun with this box.

---

### Post by AaronLS on 2007-12-11
This is my log from Xming if it means anything to someone here.  When I run XLaunch I see a grey window and hear one or sometimes two chimes and then the window disappears.  I think this might have something to do with it: "winClipboardProc - winClipboardFlushWindowsMessageQueue trapped WM_QUIT message, exiting main loop."

I've tried this on two different computers with the same behavior.  I'm not sure if the logs are the same on the other though.  



Welcome to the Xming X Server
Vendor: Colin Harrison
Release: 6.9.0.31
FreeType2: 2.3.4
Contact: [http://sourceforge.net/forum/?group_id=156984](http://sourceforge.net/forum/?group_id=156984)

Xming :0 -clipboard 

XdmcpRegisterConnection: newAddress 192.168.1.100
(--) 5 mouse buttons found
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
Could not init font path element C:\WINDOWS\Fonts, removing from list!
winProcEstablishConnection - Hello
winInitClipboard ()
winProcEstablishConnection - winInitClipboard returned.
winClipboardProc - Hello
DetectUnicodeSupport - Windows XP
winClipboardProc - DISPLAY=127.0.0.1:0.0
winClipboardProc - XOpenDisplay () returned and successfully opened the display.
winDeleteNotifyIcon
winClipboardProc - winClipboardFlushWindowsMessageQueue trapped WM_QUIT message, exiting main loop.
winClipboardProc - XDestroyWindow succeeded.
winDeleteNotifyIcon
FreeFontPath: FPE "built-ins" refcount is 2, should be 1; fixing.
winDeinitMultiWindowWM - Noting shutdown in progress

---

