---
title: "irexec at startup"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by dysphasi on 2007-10-30
Ok, my remote is working great in mythtv, but I would like to set a button on it to load myth in the first place.

To do this I understand I need to be using irexec. I've managed this up to the point that I can run irexec from the terminal and all's hunkydory

...but when I add the --daemon or -d switch, it loads (I can see it under processes), but none of the buttons work at all.

...HOWEVER, if I run sudo irexec -d, everything works again.

Now first off, I thought there's no need to run irexec -d from sudo (if it works without within the terminal, why doesn't it as a daemon?)

Secondly, if I resigned myself to the need to use sudo, firing it up at startup becomes so much more complicated. 
I've tried adding it to rc.local and even within init.d (with appropriate sym links etc.. to the rc.d folders) but neither approach would work.

Pray help!:(

---

### Post by jfsylvain on 2007-10-30
I had a similar problem.  I wanted to launch mythfrontend from the power button on my remote.  It wouldn't work until I set the DISPLAY variable in the .lircrc file.

Here is the irexec section from my .lircrc

```

# Power
begin
prog = irexec
button = Power
config = DISPLAY=:0 /usr/bin/mythfrontend
end

```

---

### Post by dysphasi on 2007-10-31
hmm, thanks, I'll give it a go and report back later

---

### Post by pointone on 2007-10-31
When starting it as root (i.e., from rc.local), you either need to have your .lircrc file in /root or specify the location of your .lircrc explicitly.

I start the irexec daemon from rc.local with the command:

```
/usr/bin/irexec -d /home/me/.lircrc
```

---

### Post by jfsylvain on 2007-10-31
You could also launch irexec from rc.local, but run it as a non-root user:

```
su -c '/usr/bin/irexec -d /home/jfsylvain/.lircrc' -l jfsylvain
```

---

