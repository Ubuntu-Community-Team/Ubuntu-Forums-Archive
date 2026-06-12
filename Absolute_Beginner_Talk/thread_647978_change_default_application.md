---
title: "change default application"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by aaronaaron on 2007-12-23
How do I change the default application for running DVDs?  When I put in the DVD totem runs automatically, but I want VLC to start up.  Thanks in advance for the help.

---

### Post by zero-9376 on 2007-12-23
system>preferences > removable drives and media, i think dvd playback is under multimedia or something and you should be able to change the application there

---

### Post by Timbothecat on 2008-04-06
> **zero-9376 said:**
> system>preferences > removable drives and media, i think dvd playback is under multimedia or something and you should be able to change the application there

That's exactly where you have to go. The problem here though is how do you change it? Please excuse my ignorance but when I hit the "Browse" button it takes me to the files in my home system. The thing is that I don't know a) where to find vlc and b) what I need to put into the field in order to make it work.

Any help would be great.

Thanks.

---

### Post by wormser on 2008-04-06
You should be able to just put in vlc.  I am unsure if you need the %m behind it like the default command totem %m.  If you have a problem with it then add the %m.

```
vlc
```

---

### Post by gug@fnal.gov on 2008-04-06
I am a novice at Ubuntu, but have been running Linux since the mid-1990's. First make sure the obvious is true, the package providing vlc is installed. Look at the snaptic package manager. Next from a terminal, you can use either locate or find. If the executable is vlc I would try: 
>  locate vlc
or
> find / -name "vlc"
If you are not sure what the executable is called, I could tell you how to find that out under RedHat, but not yet in Ubuntu. Any most, if not all, user applications that are installed by the automated tools (not by tarring and copying by hand), should have at least a symbolic link in /usr/bin. So try browsing there first. A second place to look might be /usr/local/bin. 

I don't think it would be a system tool, those generally fall under /usr/sbin or /sbin. 

Another trick, if you know the name of the of the command and can call from the command line, then you can use "which" to find the absolute path. I don't have vlc installed, but I have mplayer
> which mplayer
/usr/bin/mplayer
 
I use locate and find mainly for non-executable files or to find executables that are not on my path and need the directory specified to execute.

---

