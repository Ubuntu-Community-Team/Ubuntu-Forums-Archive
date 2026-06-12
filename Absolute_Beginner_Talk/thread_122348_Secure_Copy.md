---
title: "Secure Copy"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by jgrantham on 2006-01-27
Does anyone,know of a secure copy or secure ftp client for ubuntu? I would love to find one that works like WinSCP for windows in that it allows you to only copy the newer files if you want to.

Does anyone know of anything like this?

---

### Post by earobinson on 2006-01-27
have you searched in synaptic for secure ftp, I would but im not at my linux box :(

---

### Post by twisted_steel on 2006-01-27
While this may not be as robust as WinSCP, you can drag and drop files over a secure connection from within GNOME, assuming that is your desktop.  Just go to the Places menu, then Connect to Server.  Select SSH in the drop down list, and enter the information.  You will see the new location in the Places menu and on your desktop.  Just open that up, enter your password, and you should be all set.

---

### Post by pelle.k on 2006-01-29
I recently installed gftp, for making changes to files on websites i create. There can be quite a lot of files wich should be owerwritten / skipped. gftp seems to qo a quick analysis and shows you a list of actions.

Even though you will have to go through ssh to get it secure, is this what you need? It sounds like you want to do some sort of synchronisation...

Let us now if you managed to find something that fits you bill...

---

