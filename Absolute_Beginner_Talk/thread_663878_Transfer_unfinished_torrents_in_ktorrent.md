---
title: "Transfer unfinished torrents in ktorrent"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by youthforlinux on 2008-01-10
I have an installation of kubuntu with ktorrent with a lot of unfinished torrents.  I want to know how to transfer them to another kubuntu installation on my other computer because I really don't feel like redownloading them all.

---

### Post by filam on 2008-01-10
I am not a KDE user, but I assume you are downloading to your home directory? Are you moving to a new computer (copying over your entire home directory?). Open the torrents in Ktorrent and it should recognize the files by doing a check. Just like the check a torrenting app must do after restarting. Just make sure that Ktorrent on the new machine is saving your data to the same place as on your original machine.

---

### Post by forestpixie on 2008-01-10
this might help - but then again...

if you open nautilus - and view hidden folders, look for .kde - open that and navigate to 
/share/apps/ktorrent/

Edit just realised you're using kubunut - don't know the location of the kde config files but thats what you're looking for

I at least have in there a folder which corresponds to the last files I was downloading - maybe copy that and also of course the files which are present in the download location

or even copy the whole ktorrent folder /home/*username*/.kde/share/apps/ktorrent/ to the new /home before you install ktorrent - but I think you'll need the files in your download area as well

---

