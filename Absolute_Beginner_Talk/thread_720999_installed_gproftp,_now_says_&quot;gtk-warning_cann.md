---
title: "installed gproftp, now says &quot;gtk-warning: cannot open display&quot;"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by thepiston on 2008-03-10
noob here, how do i start gproftp?  I get this warning: 

```
(gproftp:6346): Gtk-warning **: cannot open display:
```

---

### Post by glennric on 2008-03-10
Try 
```
gksu gproftpd
```

---

### Post by neurostu on 2008-03-10
Are you trying to open gproftp locally or remotely?

The only time I see this message is when I SSH into a remote machine and try to start an X session without having used the '-X' command line arg in my ssh command

---

### Post by thepiston on 2008-03-11
gksu gives me a "comand not found" error

I'm local - on the machine

---

