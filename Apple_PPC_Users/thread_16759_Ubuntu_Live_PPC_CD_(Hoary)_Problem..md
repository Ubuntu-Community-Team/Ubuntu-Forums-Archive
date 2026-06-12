---
title: "Ubuntu Live PPC CD (Hoary) Problem."
date: 2005-02-23
forum: Apple PPC Users
---

### Post by reyjrar on 2005-02-23
I've downloaded several images for the Ubuntu PPC Live CD, and I'm getting a "No kernel modules found" error which is a fatal error and causes the setup to terminate, leaving me with only the option to abort installation as all other installer prompts result in that message.

I've burned a few CDs, verified checksums, and tried on several Macs.  Has _anyone_ else had this problem?  If not, where can I find a good image?  I've googled and come up dry.  Basically, the message infers that the modules included on the cd were compiled for a different version of the kernel.  For the record, I've tried live, live-powerppc, live-power4, live-expert, live-powerpc-expert, and live-power4-expert.

Ideally, I'd like to get this running on my new 12" Powerbook.

Any suggestions?

---

### Post by JLF65 on 2005-02-24
Where do you find these CD images? All I've found is the Warty (4.10) Install image.

---

### Post by janit on 2005-02-24
[QUOTE=JLF65]Where do you find these CD images? All I've found is the Warty (4.10) Install image.[/QUOTE]

You can download them here: [http://cdimage.ubuntulinux.org/releases/hoary/current/](http://cdimage.ubuntulinux.org/releases/hoary/current/)

The LiveCD didn't boot on my iBook (1GHz, April 2004) though. Complained about a corrupted filesystem. Hope the images work for you  8)

---

### Post by JLF65 on 2005-02-24
Thanks. I'l grab an image or two and give it a try.

---

### Post by Zarniwhoop on 2005-02-24
[QUOTE=janit]
The LiveCD didn't boot on my iBook (1GHz, April 2004) though. Complained about a corrupted filesystem. Hope the images work for you  8)[/QUOTE]

 Just tried one tonight on my new-ish iBook, similar problem.  At the prompt, press the tab key for a list of images.  I think I had to specify linux-powerpc instead of just linux.

HTH

---

### Post by janit on 2005-02-27
[QUOTE=Zarniwhoop]Just tried one tonight on my new-ish iBook, similar problem.  At the prompt, press the tab key for a list of images.  I think I had to specify linux-powerpc instead of just linux.

HTH[/QUOTE]

live-powerpc option worked out fine. Thanks :-D

---

