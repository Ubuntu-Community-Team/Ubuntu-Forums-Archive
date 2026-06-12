---
title: "Virtual machine"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by barbedsaber on 2008-01-10
There are quite a few things I no how to do in linux, this is not one of them.


 I**need** to set up a virtual machine. I **need** to run [[COLOR="Navy"]This[/COLOR]]("http://home.exetel.com.au/trappett/teds/") peice of software, in order to comunicate with my pvr (which is kind of like a hard drive tv recorder, I think it is similar to teevo)
even if you can just tell me where I have to save it so that it will work with wine, (which I already have) or if that dosn't work, which virtual machine I should use and how to set it up. sorry that I had to ask such a big question.

---

### Post by aktiwers on 2008-01-10
I have no idea about that specific app, but VirtualBox is great (VM).

---

### Post by daniel_szollosi-nagy on 2008-01-10
Tricky question. I don't know the application but from the screenshots it seems that it should have not problems under wine. Install the application to wine by running "wine installer.exe" or whatever is the name of your installer. Once that's set up, change to the application folder (generally ~/.wine/drive_c/Program\ Files/Application\ Name) and run your app from there: wine myapp.exe

From there on it all depends on how your app communicates with your PVR over USB... it may or may not work out. WineHQ has no information on this application.

If you decide to give VirtualBox a try for running a virtual machine, make sure you do not pick the Open Source Edition, as USB support in that one is flakey or non existent.

---

