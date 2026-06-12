---
title: "Remove StartUp Sessions entry using terminal"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-04-03
I already posted on this in another forum but as yet have not received a reply.

I have placed Beryl-Manager in my Startup Sessions through System>Preferences>Sessions>Startup.
Nothing wrong with that, you say.
Well, there is if Beryl doesn't actually work and keeps bring me back to a login page.

So, to extricate myself from this dilemma, I need to take Beryl-Manager out of my Startup Sessions list from the TTY1 console/terminal.

Can somebody please tell me how to do this?
Thanks 
Paul

---

### Post by sisco311 on 2007-04-03
```
rm ~/.config/autostart/beryl-manager.desktop
```

---

### Post by PaulFXH on 2007-04-03
Thanks sisco311
That worked very nicely.

---

