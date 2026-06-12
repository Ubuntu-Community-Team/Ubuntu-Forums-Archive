---
title: "Help me- user and password"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by mkrc on 2007-08-08
I downloaded the iso image and burned it onto a cd and a few days later, I inserted the disc and booted from it and told it to install ubuntu and turning off the monitor, I went to finish my business. I came back half an hour later and found out that it had failed to load the human interface and when I clicked on OK, it started the standard interface and asked for user and password. I have no idea what there are as I haven't set them. 

Please tell me where can I find these username and passowrd.

P.S. - Do u think that the downloaded image was corrupted or the burn wasn't good? ( Checked WinMD5Sum when downloaded the iso file and it matched!)

---

### Post by arochester on 2007-08-08
Did you use the oem install instead of the text install? Try the username:oem and the password: (either) oem (or)(blank)

If this is what has happened the process is not over until you issue the command > sudo oem-config-prepare 

---

### Post by AlexenderReez on 2007-08-08
as far as i know there is no default username and password...you just need to press enter....

---

### Post by Hospadar on 2007-08-08
well if you did the graphical install off the livecd, then you probably set the username and pass without knowing it, so if you forgot it, you'll probably have to reinstall to reset it.

If that's not the case, I know on some of the installations there is a default username and password "ubuntu" / "ubuntu"

If these don't work for you and you weren't doing the livecd install, I would suggest it, it's very straightforeward and you set your user info during the installation.

---

