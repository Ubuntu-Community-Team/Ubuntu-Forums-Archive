---
title: "Map a drive from Windows?"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-05-05
Hello Ubuntu gurus ;)

I was wondering if someone could give me a quick run-through of how to map a student drive that's on an XP server.  What programs and information will I need?

Thanks :)

---

### Post by ScreemingBlue on 2006-05-05
You will need smbfs, so go ahead and install it. > sudo apt-get install smbfs You will then need to create a mount point on your linux box...something like > sudo mkdir /mnt/winxp Now all we have to do is mount the windows share to the mount point using a command like this > mount -t cifs -o username=*username*,password=*password* //xpserver/share /mnt/winxp Make sure the windows firewall allows File Sharing. Username and password should have at least read access to the share you are mounting.

Hope this helps.

---

