---
title: "Delay Startup of Program"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-25
How can I delay the startup of gmail-notifier? It launches before my wifi connects. I was wondering if I can delay the launch of the program by 30 seconds after Ubuntu boots? Thanks!

---

### Post by TitusDalwards on 2006-10-25
for delaying programs you can use sleep command for example if you type  ```
sleep 15; xmms
``` in terminal, xmms program starts after 15 second.

you can use the same thing for your startup programs.

---

### Post by amitroy5 on 2006-10-26
I entered this:

sleep 15; gmail-notify 

Into Startup Programs under Sessions.

But it does not launch after 15 seconds after booting up Ubuntu.

What did I do wrong? Thanks!

---

### Post by toorima on 2006-10-26
Try with 
sleep 15 && gmail-notify

---

### Post by amitroy5 on 2006-10-30
That did not start the program either.

---

### Post by sean222 on 2007-01-30
Hey **amitroy5**, both methods you suggested worked great FROM THE TERMINAL.

However they aren't working from System -> Prefs -> Session.

Is there anywhere else I can place **sleep 10; kiba-dock**?

---

### Post by sean222 on 2007-01-30
Fixed it myself :) I placed the code in a file then added it to System -> Prefs -> Sessions as **sh <filename>**

---

