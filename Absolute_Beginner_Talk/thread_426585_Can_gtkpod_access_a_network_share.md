---
title: "Can gtkpod access a network share?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by shutrbug on 2007-04-28
I currently have all of my music stored on a PC running the beta of Windows Home Server.  I can view all the files by navigating there through Places, Network, Windows Network, Workgroup, SERVER, Music (the folder name on the server).  Right clicking on the folder shows the address as smb://server.

What I want to do is manage my iPod using gtkpod but when I try to add files, it only shows local folders, not network shares.  When I click Add Files in gtkpod, then navigate to the folder starting at smb://server and try to open it, I get the error message "The folder contents could not be displayed.  Cannot change to folder because it isn't local."  Is there any workaround for this limitation?

---

### Post by misconfiguration on 2007-04-30
I know this is an old thread but I was able to access my shared media VIA GTKpod. What I would do first is; mount your smb:// share to a local folder such as /media/shared_media and within GTKpod add the files and use the GUI to locate your music to add. This has worked for me, just throwing out a suggestion.

---

### Post by shutrbug on 2007-05-01
> **misconfiguration said:**
> I know this is an old thread but I was able to access my shared media VIA GTKpod. What I would do first is; mount your smb:// share to a local folder such as /media/shared_media and within GTKpod add the files and use the GUI to locate your music to add. This has worked for me, just throwing out a suggestion.
Thanks for the tip.  I used the [instructions here]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently") to mount the share permanently at /usr/shared_media.  Not sure why I couldn't mount it at /media/shared_media though.  I've successfully loaded a few CD's worth of MP3s using gtkpod just now.

---

### Post by misconfiguration on 2007-05-04
Great news buddy!

---

