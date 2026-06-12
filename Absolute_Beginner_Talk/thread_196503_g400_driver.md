---
title: "g400 driver"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by DirkvdM on 2006-06-14
I just installed Ubuntu 6.06 and am amazed at how simple it all looks. I don't see any way to install a driver for my Matrox G400 graphics card. My experience with Linux is limited to Suse (before which I used msWindows). In Suse I couldn't get the graphics stuff to work properly, but at least it didn't look too bad. Now, I'm looking at 800x600 on a 24" monitor, which of course will not do. 
But I haven't a clue where to start. 'screen resolution' doesn't give any options other than 800x600@61Hz. And I don't see anything like Suse's Yast or anything else that could help. How does one install drivers in Ubuntu?
To complicate matters, it's a wide-screen monitor, so something like 1600x1000 (or 1600x1024) would be preferable, but I'd be happy if I'd get a somewhat higher screen size, if not over the entire width.
I tried mga_xorg7_installer.run, which seemed to be the answer, but I can't get it to run because of an 'authentication failure' when I try 'su root'. During installation, no root password was asked for, so what gives? I don't quite get the 'sudo' thing yet, but I'd prefer a graphical solution anyway (I'm not too familiar with the use of a terminal)
By the way, I switched to Ubuntuy because it's based on Debian, which supposedly automaticaly resolves dependencies (which drove me nuts in Suse). Is this true?
Many questions, because I wasn't sure which ones to ask. I hope someone can get me started. 
Thanks.

---

### Post by jitesh on 2006-06-14
Out of curiosity, do you have a Linux driver for it?

---

### Post by DirkvdM on 2006-06-14
Ah, yes, that's one of the questions I forgot to ask. I remember once searching for a Linux driver (I bought this card because I heard that the Linux community was focusing on it), but not finding one. At the Matrox site I found a driver-page that said there wasn't one, so I made do with the what Suse offered 'out of the box', which wasn't too bad (1152x900@75Hz). But now I can't even find that Matrox page (that site really is horrible - why don't they just put all the drivers on one page?).

---

### Post by DirkvdM on 2006-06-14
Ah, I've found a driver, at [http://www.matrox.com/mga/support/drivers/latest/home.cfm](http://www.matrox.com/mga/support/drivers/latest/home.cfm). This is only for the Milennium, not the Marvel, so I'll have to do without the tv function, but that's not that essential. I unpacked it, but running it from the file browser doesn't seem to have any effect. So I went back to the terminal and ran into the same problem - I can't login as root (authentication failure). However, I think I get the sudo thing now - just add 'sudo' before every command. Right? A bit awkward, but I suppose there's a reason for it. 
So I typed 'sudo sh install.sh', but that gave the message "the X server drivers included in this installation package do not support the current version of your X server." That sounded like that script I had previously downloaded, so I went there and typed 'sudo sh mga_xorg7_installer.run'. Which seemed to work (although there was an error "C++ preprocessor '/lib/cpp' fails sanity check"). So I tried installing the matrox driver again, but got the same error message. And the screen resolution still doesn't give any further options.
Still stuck....

---

