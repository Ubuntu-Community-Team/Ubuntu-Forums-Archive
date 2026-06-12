---
title: "Removed home directory..."
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-05-31
This was really stupid...

While logged in and all my drives mounted in Gnome I tried to move my Home directory. I could not do so, so I switched to a text base shell, logged in as root(removed the safety pin) and moved my home directory to a different location(BOOM!). Upon switching back to the GNOME shell I noticed my desktop blank:confused: ... I realized my mistake(not logging out) and moved back to a text base shell and put my Home directory back in the /home/ folder. My icons are back but Firefox has lost all it's settings, Evolution needs to be re setup and my emails are probably toast, screen resolution and background are back to default ect....

So, for future reference: Where are my settings stored? I thought it was in your Home folder? Which folder(s) contain these settings so that I can back them up before I try this again?

If you where wondering I was going to remount a portition of my drive as my home folder. Too late have I went searching on the we and found:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

It's not critical to restore/recover these settings as I'm still playing around in Ubuntu and expected myself to destroy the system long before now! It has proved itself very idiot proof!

I'll really appreciate any help you guys can give! Thanks!

---

### Post by meng on 2006-05-31
Many settings are stored in hidden directories within your $HOME. Use "ls -a" (or "view hidden files" options in a GUI) to see them.

e.g.
~/.mozilla
~/.evolution

Depending on what you did, you may yet be able to save your stuff!

---

### Post by RudolfMDLT on 2006-05-31
[QUOTE=meng]Many settings are stored in hidden directories within your $HOME. Use "ls -a" (or "view hidden files" options in a GUI) to see them.

e.g.
~/.mozilla
~/.evolution

Depending on what you did, you may yet be able to save your stuff![/QUOTE]

Using the mv command in the shell, would this have moved  the hidden files as well?

---

### Post by meng on 2006-05-31
No, so they should be wherever you last left them ... please don't say that you deleted them.

---

### Post by RudolfMDLT on 2006-05-31
I just went and looked; There are hidden evolution and firefox folders but the mail directory inside .evolution is 23kb big, so it seems like the originals are gone... but again, using the mv command to move my entire HOME directory, surely it should move the hidden contents aswell?

---

### Post by meng on 2006-05-31
Oh well, then yes.
I thought you must have been inside ~ and done a "mv *". Don't know why I thought that. Can't explain why it didn't move things back though.

---

### Post by RudolfMDLT on 2006-05-31
Thanks meng! I didn't think of the hidden files! 

It's getting late this side of the world! Tomorrow, i'll download emails and on purpose go and muck things up and see exactly how these folders are affected until I get a perfect restore routine going! I just HAVE to see how the nuts and bolts of Ubuntu fit together! :)

Appreciate your help, Thanks!:D

---

