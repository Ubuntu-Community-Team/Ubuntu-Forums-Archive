---
title: "Multiple Commands in Alacarte"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2006-10-13
I need to run "sudo mount -a" before running Amarok (to access my desktop's files via samba). Is there a way to do that through Alacarte?

---

### Post by mahy on 2006-10-13
> **tonyr1988 said:**
> I need to run "sudo mount -a" before running Amarok (to access my desktop's files via samba). Is there a way to do that through Alacarte?

Whoa, it took me some time to realize what you mean! Open Alacarte, select the item you want (Amarok), and put this as a command:

gksudo mount -a && amarok

I never tried it myself, so just let me know if it doesn't work. However, is it really necessary to do mount -a each time you start Amarok? Can't you just schedule it to happen once, at startup?

---

### Post by hajk on 2006-10-13
I don't know whether Alacarte can be tuned like that, but the usual Linux way of executing multiple command is by making an executable script. In your case, this script could read something like this:

```
#!/bin/bash
##
## Some explanatory text
 
mount -a 
....

....

```

where the ... dots indicate some further commands, one per line.

Call this script amarok-start (for example), put it in /usr/local/bin
(as root) and make it executable with 
```
sudo chmod +x /usr/bin/amarok-start
```
then make sure that this script is started when you want to start Amarok.

---

### Post by tonyr1988 on 2006-10-13
The && method seems to have worked fine. Thanks hajk - I may mess with the script method later (especially if I need to do more than one command).

Also, sorry for the ambiguity in my first post. And I do have an entry in my /etc/fstab, but sometimes I'm in this situation:

1) My laptop's already booted up, and then
2) I turn on my desktop to access my music

So...I don't want to restart my laptop just to mount my music across the samba network. So I usually just pop open a terminal, "sudo mount -a" and run Amarok.

This way seems to be easier :)

Thanks everyone.

---

