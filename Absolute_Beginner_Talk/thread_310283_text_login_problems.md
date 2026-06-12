---
title: "text login problems"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by richieboy on 2006-11-30
i have my laptop setup to boot to the shell.  as it's booting it stops at:

*Running local boot scripts (/etc/rc.local).

it hangs there until i hit enter, then it gives me the login prompt.  is this bad?  what should i edit in /etc/rc.local to stop it from hanging?

also.  i removed gdm and want to load fluxbox when i enter startx.  what do i do to make fluxbox my default for startx?

i'd appreciate any help.

rich

---

### Post by K.Mandla on 2006-11-30
I believe you should have a file called .xinitrc in your home folder, along with a line in there that triggers fluxbox. I haven't used fluxbox in a while, but I think it looks like this. ...

```
exec fluxbox
```After you log in, type *startx* and fluxbox should start up automatically.

Someone let me know if I'm off the mark here. :)

As far as the funny boot prompt, is there any chance you set your concurrent boot option to *shell*? If so, the screen is spilling messages without regard to the boot sequence, and it looks like the system is hanging on the last one -- rc.local. In fact, you've gotten the login prompt, and it's just been swamped with system messages.

But that's a rather off-the-wall situation, and might not be the reason for that behavior. In which case, you can ignore these comments as mad ravings. ;)

---

### Post by bodhi.zazen on 2006-12-01
Or just type (tab completion) ```
startfluxbox
```Rather then startx.

Or add an alias in ~/.bashrc> alias flux='/usr/bin/startfluxbox'

Then start fluxbox with flux rather then startx or startfluxbox....

---

### Post by richieboy on 2006-12-01
hi.  THANKS for the quick responses.  i have no .xinitrc in home folder, only in a couple of /etc/X11 folders.  and when i enter startfluxbox i get the response "couldn't connect to xserver".  thanks a lot for the help.  my system is almost perfect. 

rich:confused:

---

### Post by K.Mandla on 2006-12-01
> **bodhi.zazen said:**
> Or just type (tab completion) ```
startfluxbox
```Rather then startx.

Or add an alias in ~/.bashrc

Then start fluxbox with flux rather then startx or startfluxbox....
Thanks, bodhi. ;)

---

### Post by K.Mandla on 2006-12-01
> **richieboy said:**
> hi.  THANKS for the quick responses.  i have no .xinitrc in home folder, only in a couple of /etc/X11 folders.  and when i enter startfluxbox i get the response "couldn't connect to xserver".  thanks a lot for the help.  my system is almost perfect. 

rich:confused:

It's hidden, so make sure you're adding the . before the xinitrc. Also, there might be an .xsession file in there that does the same sort of thing.

P.S.: If you don't have one, you can make one with the commands bodhi.zazen suggested, and it should work.

---

### Post by bodhi.zazen on 2006-12-01
K.Mandla: No problem...


richieboy: Hate to ask the obvious, but did you install X ?

---

### Post by richieboy on 2006-12-01
you guys are great!  yes i have x installed.  i'm pretty sure i have all the x stuff.  gnome and fluxbox both work well.  i just liked the idea of booting into the shell; it seems like it would save resources.

i figured out how to show the hidden files.  still no xsession or xinitrc.  if i were to create my own would i just save a file as xsession or xinitrc?
is that all there is to it?

thanks,
rich

---

### Post by K.Mandla on 2006-12-01
Yup. If it's not there, you can make one up from blank, and the system should read it and obey it when X starts. Easy as pie. ;)

---

