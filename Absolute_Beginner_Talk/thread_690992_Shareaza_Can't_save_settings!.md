---
title: "Shareaza Can't save settings!"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by disappearedng on 2008-02-08
Hi everyone
So I downloaded shareaza 2.3 and installed onto my  ubuntu 7.10 machine using wine. The installation went well and I was able to get it running. However, when I try to switch the "save downloaded files in" and "save downloading files in" within the menu and restart Shareaza, everything went "afresh" and all the settings are erased. How could I overcome this problem?

---

### Post by talsemgeest on 2008-02-08
Ive got shareaza running as well. There do seem to be a few problems when running it through wine however; for examply when I try to add files to be shared it closes and then refuses to start back up. Check your /home/*/.wine/ directory to see if your sharaza files are there.

---

### Post by disappearedng on 2008-02-08
yes they are. Is there like a particular .ini file where shareaza save all its settings?

---

### Post by talsemgeest on 2008-02-08
The only config files I could find were in the two data/ folders

---

### Post by jonspraggins on 2008-02-15
Bump.  I'm having the same issues.  Even a normal exit wipes out the settings, I have to redo everything each time I boot it up.

---

### Post by crf on 2008-02-15
I used to use Shareaza when I had windows. But I have not installed wine.
Shareaza uses the registry for most settings. It doesn't use ini files. Settings for shared folders and file information were kept in binary files (.dat files) in the windows user's home directory.

I can't remember whether other users had problems saving their settings when using wine. There is an entry in the wiki. [http://www.shareazasecurity.be/wiki/index.php?title=ShareazaLinux](http://www.shareazasecurity.be/wiki/index.php?title=ShareazaLinux)
You could ask on the forums of that site.

[http://shareaza.sourceforge.net/?id=download](http://shareaza.sourceforge.net/?id=download)

---

### Post by kahlil88 on 2008-05-14
I've only been having this problem since I installed Hardy Heron. It's a nuisance having to change the settings every time, but I can at least resume my downloads if I run Shareaza by entering the following commands in a terminal:
```
cd ~/.wine/drive_c/Program\ Files/Shareaza && wine ./shareaza.exe
```

---

