---
title: "Deleting Ubuntu Partition"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by amcavoy on 2006-09-14
I have two PC's both running Windows XP and Ubuntu Dapper with the GRUB bootloader at startup.  I recently resized a partition on one of my computers, which ended up basically ruining my whole setup (the tutorials on how to reinstall GRUB didn't work).  What I would like to do on my second PC is to delete Ubuntu completely and work only with Windows XP.  How can I do this without running into the same problem I have with my other PC?

Thank you.

---

### Post by haxer on 2006-09-14
Ooops i did like this ... removed linux then i inserted my windows cd then booted then i choich r=repair then i typed in fixmbr ;)

---

### Post by amcavoy on 2006-09-14
It says that the page cannot be found on the server.

---

### Post by era86 on 2006-09-14
At what point did it say this? While you were booting the Windows repair cd?

---

### Post by haxer on 2006-09-14
double post

---

### Post by haxer on 2006-09-14
Hmm ... i dont remember dont try it maybe it wont work when i looked recently they said to not do it hmm.. try google.com the search for uninstall+ubuntu

or try this 

[http://www.techspot.com/vb/all/windows/t-38428-How-Do-I-Uninstall-Ubuntu-Linux-From-WinXP-Dual-Boot-Machine.html](http://www.techspot.com/vb/all/windows/t-38428-How-Do-I-Uninstall-Ubuntu-Linux-From-WinXP-Dual-Boot-Machine.html)

---

### Post by bulldog on 2006-09-14
Just popin your windows cd and go to the page where you can install,repair or quit.
Choose repair,which brings you to a console.
Login the windows install by following the onscreen command and if you're logt in type fixboot.

If this is not the solution do the same again and  type fixmbr instead of fixboot.
You get some warning but I did this several times and no harm done.

After you can boot in windows you can safely delete your ubuntu partitions in windows.

Hope this what you're looking for.

---

