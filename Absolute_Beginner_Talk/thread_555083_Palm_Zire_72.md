---
title: "Palm Zire 72"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by coasterman777 on 2007-09-19
I am a real Newbie to Linux based sytems. I LOVE Ubuntu, but for the life of me, I cannot get my Palm Zire 72 to sync. I would like it to sync to Avantgo. It is sync via USB.  Can anyone help me in plain language that newbie like me can understand?

---

### Post by heinig on 2007-09-19
I'm not sure if the same is true for the Zire 72 but I was able to sync my palm  after I loaded the visor module..
Did you do that?
If not, go to a terminal and type "sudo nano /etc/modules"
Add "visor" to that file
Save and exit
Restart the computer

Now try to sync using gnome-pilot (add the applet to your panel)

Good luck!

---

