---
title: "Can't run exe application from visual basic"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by omeng on 2007-04-19
Good afternoon,
I just recently able to successfully installed Ubuntu and now able to connect to our LAN, open xls files from network, print to network printer, and surf the internet. I wanted to open an application compiled from visual basic but was unable to open it. Is Ubuntu capable of running applications or programs that are windows based? If yes, how to? I have no idea, simple instruction on how to do it will be of great help.

Salamat po. (Thank you)

Omeng

---

### Post by Jussi Kukkonen on 2007-04-19
Generally speaking .exe-files are windows executables and you can't run them on Linux. If you really need to, take a look at Wine ([https://help.ubuntu.com/community/Wine)](https://help.ubuntu.com/community/Wine)). It should be available in your package manager.

---

### Post by delphiguy on 2007-04-19
pareng omeng.

You have to install wine first to have your Windows Application run in Ubuntu.
You can install it from synaptic just search for "wine"

or from terminal
sudo apt-get install wine

i think you have to enable the universe repositories for that.

After you have installed wine you can now run your Windows applications, well most of it i guess.
To run your application you can do this from the terminal:
wine /home/user/myapp.exe

But with VB apps there are runtime dll's that needs to be installed first, if memory serves me.

you can refer to this site for some more pointers. 
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by omeng on 2007-04-19
Thank you for your help. Is it true that if I install wine, there is a possibility that viruses designed for windows can infect my system? If it is, then I'll have to forget about installing wine and enjoy Ubuntu without worrying about viruses.
"Don't let the things you want, let you forget the good things you already have". Ubuntu is a good thing.

---

### Post by eentonig on 2007-04-19
Someone once tried to run windows virii under Ubuntu/Wine. It failed. So even with Wine enabled, you won't have to worry about that.

As long as you only type your sudo password for trusted apps, you'll always be safe anyway.

---

### Post by hagabaka on 2007-04-19
> **eentonig said:**
> Someone once tried to run windows virii under Ubuntu/Wine. It failed. So even with Wine enabled, you won't have to worry about that. As long as you only type your sudo password for trusted apps, you'll always be safe anyway.


That doesn't mean that other Windows virii cannot run under wine. If the windows program is "normal", even if it's malicious, it would probably be able to run in wine, or will be in the future. On the other hand, it's perfectly possible to write a native Linux "virus" or a malicious program in general. Lots of security tips that Windows users should know also work in Linux.

---

### Post by Nik_Doof on 2007-04-19
> **eentonig said:**
> Someone once tried to run windows virii under Ubuntu/Wine. It failed. 

Iirc, didnt the virus the guy ran work well under wine? I remember reading it filled up a few areas of his install with various exe files, but no major damage was done.

---

