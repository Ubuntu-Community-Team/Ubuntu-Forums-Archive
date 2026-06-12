---
title: "failed to open winecfg (of latest wine)"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by tk92 on 2006-10-28
i have installed wine, by downloading deb pakage from the wine hq site.

AFter installing, whenever i try to run winecfg i get this message, also when i try with sudo, i get the same message too.

```
wine: creating configuration directory '/home/thomas/.wine'...
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
```

I tried countless times of re installing, yet no luck.



HELP PLS!!

---

### Post by tk92 on 2006-10-28
update. I created the .wine folder in my home folder manually.
now i get this
```
thomas@thomas-desktop:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/thomas', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.

```
and this window pops up, but it doesnt respond, nor function.

---

### Post by tk92 on 2006-10-28
Please I Need Help!!!!!

---

### Post by janmartin on 2006-10-28
My 2 cent:

Delete the ~/.wine folder etc.
Then reinstall using Synaptic:
In the Panel: 
System -> Administration -> Synaptic Package Manager
search for wine and install it.
Then in the Terminal run winecfg to configure it. 

You might also want to read this:
[http://whirlpool.net.au/forum-replies-archive.cfm/613653.html](http://whirlpool.net.au/forum-replies-archive.cfm/613653.html)

Use the search function of this forum and read a lot.

---

### Post by The Headhunter on 2006-10-29
I also have the same problem and I tried what you did, janmartin, and it still didn't work.

---

