---
title: "[SOLVED] Configuration error"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-03-10
I have come across the following error.
When trying access a number of area in the 'Systen/administration area I get a "The configuration could not be loaded" You are not allowed........
Could someone please tell me what I've done wrong.

---

### Post by neurostu on 2008-03-10
Are you the only system user? It sounds like you don't have permission to "administer" the system.  If you share the system then talk to the sysadmin about getting admin privledges, if you are the only person using the system it sounds like you have broken your sudoers file.

---

### Post by jken146 on 2008-03-10
It could be that your user isn't in the admin group.  Are you using the first user that was created when Ubuntu was installed on your computer?

---

### Post by newbeeman on 2008-03-10
> **jken146 said:**
> It could be that your user isn't in the admin group.  Are you using the first user that was created when Ubuntu was installed on your computer?

As far as I'm aware. I haven't changed anything. Where would I check?

---

### Post by neurostu on 2008-03-10
try a simple command like:
```

sudo apt-get install pingus

```

if that works then you still can sudo for Super User powers!

If it doesn't then that is a good sign that we are getting close to the problem...


---
pingus is a free linux clone of lemmings....

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> try a simple command like:
```

sudo apt-get install pingus

```

if that works then you still can sudo for Super User powers!

If it doesn't then that is a good sign that we are getting close to the problem...---
pingus is a free linux clone of lemmings....

I ran the command, ended up with "This apt has Super Cow Powers" If that means anything to you, doesn't help,  still get the same error.

---

### Post by neurostu on 2008-03-10
did you type that command exactly?  you might have forgotten the install & pingus

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> did you type that command exactly?  you might have forgotten the install & pingus

As you quoted. But I tried it again and noticed "Cannot resolve 'archive Ubuntu.com'"
Tried 'sudo apt-get update' got the same error as above. Would this suggest the repository is down?
Where to from here?

---

### Post by neurostu on 2008-03-10
try this:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

```

Tell me if it pops up an error

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> try this:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup

```
Tell me if it pops up an error

Ran it as quoted checked it 3 times got "no such file or directory"

---

### Post by neurostu on 2008-03-10
did you type /etc/  or  /ect/  ?  its a really common mistake

B/c you have that file, its a system file used by X server, you wouldn't have a GUI without that file.

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> did you type /etc/  or  /ect/  ?  its a really common mistake

B/c you have that file, its a system file used by X server, you wouldn't have a GUI without that file.

Yes as quoted "etc"

---

### Post by neurostu on 2008-03-10
hmmm....

Ok then lets try something else....
try something simple like ```

sudo gedit blah.txt 
```

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> hmmm....

Ok then lets try something else....
try something simple like ```

sudo gedit blah.txt 
```

Yes, that opened  a txt file window

---

### Post by neurostu on 2008-03-10
hm... then you are in the sudoers file....
Have you previously been able to Administer the system without these errors?

Did you recently edited any files or install new software?

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> hm... then you are in the sudoers file....
Have you previously been able to Administer the system without these errors?

Did you recently edited any files or install new software?

That's my problem. This is a new install, things were going well till I noticed my internet connection went down. Which program I loaded that caused the problem? There are so many I wouldn't know where to start, suppose I should have used pen and paper!!!
If it gets too bad I'll rip it oiut and start again.
Got any ideas before I turn in, in which case it can wait till tomorrow?

---

### Post by neurostu on 2008-03-10
If your install is fresh, I would just reinstall as you don't have many settings to reconfigure...


Ubuntu reinstalls (for me) take like 30-40 minutes.  Trying to hack out a fix to a problem RARELY takes me less then an hour. 

It all depends on my mood, do I want to learn about linux, if yes then I hack it out.
If no then I reinstall.

---

### Post by newbeeman on 2008-03-10
> **neurostu said:**
> If your install is fresh, I would just reinstall as you don't have many settings to reconfigure...

Ubuntu reinstalls (for me) take like 30-40 minutes.  Trying to hack out a fix to a problem RARELY takes me less then an hour. 
It all depends on my mood, do I want to learn about linux, if yes then I hack it out.
If no then I reinstall.

OK. I'll take your advice. Thank you for your efforts.
Please, briefly advice on a re-install, never done that yet.

---

### Post by neurostu on 2008-03-10
Re-install = same as fresh install, 

put in liveCd and click INSTALL!

> Thank you for your efforts. No problem... and if you feel like I deserve it feel free to click the little star in the bottom right of my post to publicaly thank me.

We are all learning and (me especially) and I learn a lot trying to help people with their problems.

---

