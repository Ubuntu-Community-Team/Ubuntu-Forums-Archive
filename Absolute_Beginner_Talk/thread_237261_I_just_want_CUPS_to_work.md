---
title: "I just want CUPS to work"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by theStorminMormon on 2006-08-15
I have recently installed Dapper Drake on a desktop.  I managed to configure my Dell 720.  I want to be able to print from my two windows xp laptops to the printer attached to my ubuntu desktop without having to go through Samba or stuff like that.

I know it's important to have a static IP assigned to the desktop to make things easier, so I took care of that too.

However, I have no idea how to actually get CUPS set up on the desktop OR how to connect to it from the windows xp laptops.

I have tried adminstering CUPS through firefox (localhost:631) but I can't even set the damn printer preferences.  Most. Annoying. Experiene. Ever.  Keeps asking for my username/password, which I dutifully supply in infinite variation to no avail.  I figure if I can't even get CUPS to realize my printer uses letter paper instead of A4 there's no way I can get it to network properly.

Sigh.  I like Linux, but now I know why so few people use it.  I have a life, you know.  This took like 5 minutes in Windows.

Let me know if you can fix this.

---

### Post by VirtuAlex on 2006-08-15
People say that changing A4 to letter in /etc/papersize and then reinstalling the printer fixes the problem. If you want to activate cups interface you should add the user cupsys to the group shadow. And yes, unfortunately you have to invest time in linux. Nothing is absolutely for free.

---

### Post by goatflyer on 2006-08-15
My understanding is that running samba on your linux box is the only way to be seen by a windows machine.

---

### Post by VirtuAlex on 2006-08-15
That's right. Just install samba package and you're all set. I believe printers are shared by default. You may have to adjust your workgroup name if it is something other than MSHOME, but otherwise it is usually painless.

---

