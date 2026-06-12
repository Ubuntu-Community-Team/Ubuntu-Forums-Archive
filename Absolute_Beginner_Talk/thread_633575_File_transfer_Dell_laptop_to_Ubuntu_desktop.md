---
title: "File transfer: Dell laptop to Ubuntu desktop"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by CBVampyre on 2007-12-06
I have a Dell laptop running Windows XP and I just installed Ubuntu on my desktop. I would like to be able to set up a link between the two to transfer my music, movies, pics, etc. from the laptop to my desktop. I don't have a router and only the desktop is connected to the internet. Is there any way to do this? Possibly a USB connection to recognize one as mass storage? Any help is appreciated.

---

### Post by kelbizzle on 2007-12-06
Do you have a crossover cable? If not you could make a rar, split it and use google pages. They give you 100 megs.

---

### Post by CBVampyre on 2007-12-06
No, I don't have a crossover cable. What is that? I thought of using Google pages or some other online file sharer, but I'm trying to transfer a total of about 7GB. Having to split it that much and then re-download it, it would be worth the cost of getting a router if thats the only other option. I am interested in the crossover cable, though. What is that and how does that work?

---

### Post by iris-n on 2007-12-06
It's a ordinary internet cable with the order of the wires on one of the points mixed. You can find it in any tech store, cheap. Connect the two pcs via the their ethernet ports, configure the net and voilà, you have file share.

Now, I already did it between two windows, but to make windows and linux communicate I honestly don't know how.
Shouldn't be hard, though. Best luck ;)

---

### Post by CBVampyre on 2007-12-06
Thanks for all the help. I'll check for one of those cables tomorrow.

---

### Post by Slim Backwater on 2007-12-06
> **CBVampyre said:**
> ... I don't have a router and only the desktop is connected to the internet.

A router would make the process a lot easier as it would take care of the IP addresses and such (and then your laptop could also get out on the internet - assuming it has an ethernet adapter or wireless).

With a router, share a folder on your Ubuntu desktop, then browse to it from your laptop, copy/paste and your done.  I recommend you use a cable connection to the router for both machines, rather than a wireless one, as it's faster and more reliable.

On the Ubuntu Desktop, System, Administration, Shared Folders.  The first time you go in you'll be prompted for your password, then a dialog about "Sharing services not installed".  Install the Windows Support (SMB), if not both SMB and NFS.

After the service(s) have been installed, Click Add (should default to sharing your home directory), remove the "read-only" checkbox and click Ok.

Right-Click on the network manager at the top right (looks like two little displays, one in front of the other) and click "Connection Information".  Note your IP Address.

On your laptop, Click Start->Run and type \\ipaddress\sharename   replace sharename with your username, or whatever name you used for your shared folder on the desktop.

You may be prompted to login, provide your Desktop username and password, and you should be in.

HTH

._.

---

### Post by kelbizzle on 2007-12-07
Yea I'd get a router. they're all in the $40 - $70  range. or just buy a cheap hardrive and a $5 enclosure.

---

