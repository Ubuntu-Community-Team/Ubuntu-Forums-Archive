---
title: "How to run something as a service?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by Schammy on 2006-11-21
I successfully installed [mt-daap]("http://www.mt-daapd.org/") and have my iTunes being served to my LAN from my ubuntu box -- sweet!

Every time I reboot though, I have to manually start the service again via the terminal.  Is there a way to have it start automatically as a service?  How?

Thanks!

---

### Post by taurus on 2006-11-21
You could either move it to /etc/init.d/ or create a link to it from /etc/init.d!

---

### Post by seijuro on 2006-11-21
EDIT: oops wrong post

---

### Post by Schammy on 2006-11-21
Thanks, but I need some clarity...

When you say move "it" to /etc/init.d/.  Is it a file?  Which one?  Is there a place in the directory to move "it"?  Does a shortcut work just as well?  How do I make a shortcut?  Can I do all of this in the GUI file manager?

Thanks.  Sorry for all the Qs but I'm still new at this.

---

### Post by seijuro on 2006-11-21
I'd use a symlink if it were me in /etc/init.d do
```

sudo ln -s /path/to/program

```

---

### Post by Schammy on 2006-11-21
I went back to my machine to try and get a symlink in the init.d directory but see that there's already a file named mt-daapd there!

So it was there in the first place.  Can anyone figure out why mt-daapd doesn't start as a service then? 

Any trouble shooting advice?  Other things I could try?

Thanks.

---

