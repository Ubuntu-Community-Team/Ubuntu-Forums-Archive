---
title: "synaptic/proftpd won't work anymore! also samba!"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by juicymixx on 2006-08-20
I'm not sure what happened to my Dapper install.   I think it was running one of the updates that caused this problem:

I'm having numerous problems now:
1) proftpd is doing something odd, I can't connect from any windows machines in my network
2) apt-get install samba fails while installing

so I thought to use the synaptic package manager, but it's failing now!   When I try sudo synaptic from the terminal I get the error:
synaptic:error while loadingshared libraries: libvte.so.4: cannot open shared object file: No such file or directory

I have no idea what this means!

I tried apt-get install libvte , but it says:
E: Couldn't find package libvte
!!!

Please help!   I can no longer get files into or our of Dapper through the network;  And it's really irritating that synaptic doesn't work!:( 

Thanks!

---

### Post by krang on 2006-08-20
I think, you could fix your synptic with [this hint]("http://www.ubuntuforums.org/showthread.php?t=239238"). ;)

---

### Post by Uncle Spellbinder on 2006-08-20
See the "sticky" thread in *Desktop Support*: [**_Fix for Synaptic problems after libvte updates_**](http://www.ubuntuforums.org/showthread.php?t=239238)

**EDIT:**
*krang* beat me to it. ;)

---

### Post by jimmygoon on 2006-08-20
Here.. I think this is what I did:

"sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4"

That should work for you hopefully.

---

### Post by juicymixx on 2006-08-22
Thanks everyone for your help!   It got synaptic up and running, then I went ahead and reinstalled proftpd and samba.   Now everything is going great!
=D>

---

