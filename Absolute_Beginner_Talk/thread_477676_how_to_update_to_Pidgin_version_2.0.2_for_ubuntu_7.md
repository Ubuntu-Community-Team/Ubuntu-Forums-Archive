---
title: "how to update to Pidgin version 2.0.2 for ubuntu 7.04 ?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-18
Hi
thank you for reading my post
I have Pidgin version 2 and now i know that verion 2.0.2 is available, is there any update center which i can use to update Pidgin?

Thanks

---

### Post by brennydoogles on 2007-06-18
> **legolas_w said:**
> Hi
thank you for reading my post
I have Pidgin version 2 and now i know that verion 2.0.2 is available, is there any update center which i can use to update Pidgin?

Thanks

I am not sure, but i created a .deb from the source which should work for you.  [Here it is!!]("http://www.fileden.com/files/2007/6/6/1150141/pidgin_2.0.2-1_i386.deb")

---

### Post by zvacet on 2007-06-18
[http://www.getdeb.net/search.php?keywords=pidgin]("http://www.getdeb.net/search.php?keywords=pidgin")

---

### Post by legolas_w on 2007-06-18
Hi
Thank you for your replys.
I tried and installed your created deb file and it does not updates the pidgin to 2.0.2, can you please tell me where it installs the pidgin?

does my last shortcuts point to new version or old version?


thanks

---

### Post by RonB123123 on 2007-06-18
Once the new pidgin is installed, you can access it through Applications > Internet > Pidgin. 

Once in Pidgin, click on Help > About to verify that it is version 2.0.2. 

That's what I did. Though, I think I uninstalled my previous version of pidgin first. Hope this was helpful.

---

### Post by fatray on 2007-07-10
There is no uninstaller that I could find on my system for Pidgin?  It's not listed in "Add/Remove" or "Automatrix".
I tried to use your installer and it didn't work.  I guess because I don't now how to remove Pidgin first?

---

### Post by zvacet on 2007-07-10
If you installed Pidgin from source go to the Pidgin folder and type 

```
sudo make uninstall
```

If you installed deb file you should be able to remove it with synaptic.

---

### Post by fatray on 2007-07-10
LOL, I've searched and searched and can't find where it was installed.  Where do things in general get installed in Ubuntu?  Using the Search on my taskbar, I find Pidgin that I downloaded in my DOWNLOAD folder.  The install folder is MIA.

---

### Post by cyberdork33 on 2007-07-11
if you installed from source (compiled) then you need to go to the source directory (wherever it might be that you unpacked the source) and use the command listed above to uninstall.

---

