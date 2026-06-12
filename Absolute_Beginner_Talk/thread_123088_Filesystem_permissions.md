---
title: "Filesystem permissions?"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by djgenesis on 2006-01-29
I want to copy some skins from my windows machine to "/usr/share/bmp/Skins" lets say..... and i DON'T want to use the terminal.. Everytime i try to copy something in there it says i don't have access. 

Is there any way ji could get access with my current account (not root) in the GUI and copy my skins to the folder above without having to use the command?

---

### Post by timetunnel on 2006-01-29
> Is there any way ji could get access with my current account (not root) in the GUI and copy my skins to the folder above without having to use the command?
Well, no (and yes). Of course you can't write to /usr/share/bmp/skins as a normal user, because if you could you'd bypass the file permissions and make them unnecessary. To write there, you **must** do it with the right permissions. If you really DON'T want to use the terminal, you can open a terminal  :o , type
```
sudo nautilus
``` 
enter the root password and nautilus will be started for ROOT (!!!). Be **very very very very very** careful doing that,  because you then have full access to the whole file system in Nautilus and can accidently mess up you whole system by moving or deleting the wrong files. So I'd rather stick with the terminal and copy the files from there:
```
sudo cp -v -R /windows/somewhere/skins/* /usr/share/bmp/skins
```
What it does is: copy ("cp") all files and subfolders in "/windows/somewhere/skins" recursively ("-R") to folder "/usr/share/bmp/skins", giving feedback for each file that's copied ("-v"). All this is done with root permissions ("sudo").

This is **much** safer than using Nautilus as root because it only does this one specific action as root and (almost) nothing can happen accidently.

Jens

---

### Post by djgenesis on 2006-01-29
I'd rather NOT type ```
smb://192.168.0.2./D/installations/windows/audio/players/winamp/all_versions/Skins

```
and just use the window... You can tell i am still hooked up huh?? :P 
Thanks for your reply, it solved my problem :D

---

