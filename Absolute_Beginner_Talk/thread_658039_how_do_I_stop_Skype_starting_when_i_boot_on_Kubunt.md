---
title: "how do I stop Skype starting when i boot on Kubuntu?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Ruthie_J on 2008-01-04
I feel pretty stupid - I want to stop Skype starting up when I boot up my laptop.. I've searched other posts about this but they all say to go to system>preferences>startup, and I'm on Kubuntu, and can't seem to find a system preferences menu or similar. I know it's probably staring me in the face, can someone tell me where please?

---

### Post by hyper_ch on 2008-01-04
do you save the session when shutting down? If so and if skype is running at that point, it will be autostarted the next boot up.

So if the above applies:

(1) Disable auto-session save (and resume)

(2) Add the programs you want to the  System -> preferences -> startup

---

### Post by Ruthie_J on 2008-01-04
No, don't save me sessions, and there is no system>preferences>startup on Kubuntu! (not on mine, anyway) Any other ideas?

---

### Post by hyper_ch on 2008-01-04
> **Ruthie_J said:**
> No, don't save me sessions

Are you sure? I think Kubuntu does that by default. Open an application you normally don't have open and then restart the computer. If it will be opened again, sessions are auto-saved.

---

### Post by ajgreeny on 2008-01-04
Make sure hidden files are showing in konqueror or dolphin and then go to ~/.kde/Autostart (or something similar, I can't now remember properly) look for the link to skype and remove it.  You should not now have skype start at boot up.  Do check however that you start with an empty session as the default is to start up the last session.

---

### Post by Ruthie_J on 2008-01-04
yep, definitely don't save my sessions. Sorted it through Konqueror, never ceases to amaze me how much you can do with it! Thank you very much :)

---

### Post by sumguy231 on 2008-01-04
Edit: Never mind. Stupid page caching.

---

