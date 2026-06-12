---
title: "Rockboxin' Blues"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by deez on 2007-04-29
So I"m trying to Rockbox my 5th G, Ipod.  I"m following the instructions from the rockbox page, but I'm running into some problems.  

I'm supposed to exract a zip file into the root directory of my player.  When I do that from my Desktop, nothing happens.  When I drag the zip file to the player and then extract it, I get an empty folder.  How can I extract the contents of a zip file to my player?

2nd, I downloaded the 2nd file I needed, the 'ipodpatcher', it's a boot loader.  I'm supposed to be able to just click  it and let it do its magic, but nothing happens.  It says it's an executable file, but is it really?  It doesn't execute much that I can see.  Any advice?

Thanks a lot.  Keep on Ubuntuing.

---

### Post by nixclusive on 2007-04-29
I don't know that desktop environment you are on but entering these commands should unzip your zip file:```
unzip file.zip
```The contents of the zip file are placed in the current directory. You can then copy the extracted files to your player.

About executing the other file, make it executable:```
chmod +x <exec-file>
```And then execute it:```
./exec-file
```

---

### Post by deez on 2007-04-29
Thanks a lot.  Worked like a charm.  I appreciate it.  Peace.

Deez

---

