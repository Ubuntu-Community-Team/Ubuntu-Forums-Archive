---
title: "Lost my vsftpd.conf"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by tolle6 on 2006-11-28
Hi all,
Total newbie at this, but you could probably tell from the thread ;) .
When attempting to configure my vsftpd.conf, I found out that it was completely empty.
Is there any way I can re-install vsftpd and get a fresh .conf, or could it be found on the Internet in some way?

Help appreciated

---

### Post by Bachstelze on 2006-11-28
You could try reinstalling vsftpd or extract the .conf file from the DEB and copy it in its right place.

---

### Post by tolle6 on 2006-11-28
I tried "sudo apt-get install vsftpd". That didn't work, is that what you meant by reinstalling?

For the extracting and copying part I'm afraid I might need extra instructions, sorry about that :oops:

---

### Post by Bachstelze on 2006-11-28
You need to pass an extra argument to apt-get if you wand to reinstall a package that is already installed. I don't remember what it is and I'm not on my Debian at the moment so chack the manpage ;)

And for extracting files from a DEB package, just open it in the Archive Manager, it works like a ZIP.

---

### Post by tolle6 on 2006-11-28
HymnToLife: Thanks, i will try it out. Sorry if my questions are answered somewhere else, it's just a bit confusing working without a GUI. (I'm on ubuntu server).

---

### Post by tolle6 on 2006-11-28
Problem solved. 
apt-get remove and then installed it again.

Thanks for putting me on the right track :)

---

