---
title: "How do I get two commands to run together (&amp;&amp; help)"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by petersjm on 2007-02-24
Hi guys,

I've just installed Beryl but find that the only way I can make it work right (without crashing or giving me a white screen) is to run the following two commands:

```
$ beryl-manager --no-force-window-manager
$ beryl-xgl --use-copy
```

Thing is, I don't want to have to type these two commands every time I start my desktop. So I figured I'd put the commands in start-up under sessions. I want the commands to run one after the other, so tried the command:

```
beryl-manager --no-force-window-manager && beryl-xgl --use-copy #note the '&&'
```

but this doesn't work when I restart X. Is there something I'm doing wrong, or is the command correct, but just not working?

Any help would be much appreciated. I love this whole Beryl thing and I'm desperate to show it off :D Thanks

---

### Post by finer recliner on 2007-02-24
try:

```
beryl-manager --no-force-window-manager; beryl-xgl --use-copy
```

(not sure if it will work for ya)

---

### Post by petersjm on 2007-02-24
Thanks, finer, but no, that doesn't work either. What I have done, though, is just put them in Sessions > Startup Programs as two separate entries/commands. That works fine (should have thought of that in the first place, shouldn't I?! LOL).

Now to figure out why using 'beryl-xgl --use-copy' seems to slow everything down to a snail's pace...

---

