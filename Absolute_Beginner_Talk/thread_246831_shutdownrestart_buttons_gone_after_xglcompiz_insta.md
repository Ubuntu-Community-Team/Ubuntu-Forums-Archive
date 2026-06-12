---
title: "shutdown/restart buttons gone after xgl/compiz install"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by cptjaben on 2006-08-29
after installing xgl/compiz using [this]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper") guide , the shutdown and restart buttons seemed to have disappeared and have been replaced by one very large sized hibernate button. does anyone know how to fix this?

Thanks,
cptjaben

---

### Post by Dinerty on 2006-08-29
known bug with xgl/compiz im afraid, only way is to logout then shutdown from gdm screen

---

### Post by Sammi on 2006-08-29
I have the same prob and I'm using Xgl/Compiz too. Followed an other guide though.

---

### Post by Jagot on 2006-08-29
I haven't bothered to try and fix it.  I just shutdown from the commandline.

---

### Post by ~LoKe on 2006-08-29
I believe that's only a problem if you create a new session for XGL.  If you use an existing session, you should still have those buttons.  I certainly do.

---

### Post by Sammi on 2006-08-29
The command "sudo halt" should do it, right? I should just make a launcher icon on the panel for it, or something similar.

---

### Post by Jagot on 2006-08-29
I use:

```
sudo shutdown -h now
```

---

### Post by Sammi on 2006-08-29
What's the difference?

---

### Post by Jagot on 2006-08-30
> **Sammi said:**
> What's the difference?

They're essentially the same, but whith shutdown -h now you can add options, such as to shutdown at a particular time or whatever - useful if you leave the computer downloading a large file or something:

[http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/shutting-down.html](http://www.tldp.org/LDP/GNU-Linux-Tools-Summary/html/shutting-down.html)

---

### Post by Sammi on 2006-08-30
thx!

---

### Post by cptjaben on 2006-08-30
Hmm, okay thanks for the help i guess i will just make some shutdown and restart scripts, thanks for the info/help.

---

