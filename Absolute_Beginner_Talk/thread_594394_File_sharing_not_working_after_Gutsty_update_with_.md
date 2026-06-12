---
title: "File sharing not working after Gutsty update with samba."
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by WaffleLove on 2007-10-27
Something tells me it's an simple solution but I haven't found it , or really know where to even begin.

My Xbox use to be able to see my comp no problem, then I upgraded to gutsty. Now I can't even file share between the two.

I've tried installing the Samba program in add/remove, i've searched google for things like samba set up, file sharing, these forums, nothing seems to have helped so far.

Sambas website I cant make heads or tails of it since I'm still learning about linux, but what I understood I tried like editing my smb.conf and looking too see if workgroup was right in there. I've made sure the workgroup is the same on my xbox and compy, and yet my xbox will not even detect the files/workgroup, and at times my computer doesn't even seem to be saving the settings, example. I right click on an file, I want to share then click share restart my comp, then go to System>Admin>Share and nothing is listed.

What gives? It went from being as simple as right clicking on the file I wanted, and hitting share folder, to no longer working in any shape or form. AT some point even after the update it wouldn't let me do that.

Any information that needed for this please tell me commands and I'll post it.

---

### Post by Cato2 on 2007-10-28
Some things to try:

- can your Samba shares be seen from a Windows PC?  Try "net use" on Windows command line.

- can you boot Ubuntu from a Live CD on another PC?  Try connecting to your shares, then go into /var/log/samba on both PCs and see if you get some useful messages - the samba logs are organised by client IP address so use ifconfig on client to check IP.

See also [http://ubuntuforums.org/showthread.php?t=585202](http://ubuntuforums.org/showthread.php?t=585202) where there are some similar problems.

---

