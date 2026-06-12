---
title: "playing .rm files"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2008-04-10
Hi,
I'm having a problem playing .rm files in Ubuntu.  Usually Ubuntu searches for the codecs and downloads them but in this case that doesn't happen. Any help? Thanks

---

### Post by Inxsible on 2008-04-10
you need to install real player. Let me search for a tutorial for you.

---

### Post by SteelCore on 2008-04-10
Isn't that the same as Helix player?

---

### Post by lizzard on 2008-04-10
mplayer should be capable to play rm-files.

---

### Post by Inxsible on 2008-04-10
Well I couldn't find a tutorial, so I thought I will tell you myself

1) Download the realplayer bin file from [http://www.real.com/linux](http://www.real.com/linux)
2) then make it executable:```
chmod +x filename
```
3) then run it using ```
./filename
```

---

### Post by SteelCore on 2008-04-10
I followed your guide and it did start installation but then it stopped and asked me to give it the complete path to the directory where I want Realplayer to be installed and I'm not sure what the answer should be.  Thanks

---

### Post by PhilJ on 2008-04-10
when you do 
sudo ./ RealPlayer10GOLD.bin
and it asks you for the path write
/opt/real/
then when it asks you about links and offers  /usr  accept it, just hit return

Philj

download win32 codecs from  repositories or mplayer site install to /usr/lib/codecs  to enable mplayer to run rm files

---

### Post by SteelCore on 2008-04-10
It worked.  Thanks to all

---

