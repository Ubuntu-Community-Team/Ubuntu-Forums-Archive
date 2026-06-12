---
title: "Beryl problems are user-rights related"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by medley on 2007-01-19
Well, I think after a couple weeks of trying, I've found a clue as to why beryl won't run consistently on my machine.

Today there was a new update for beryl released on the distros. I installed it, and after at least 2 weeks of trying to get this damn app to run, all of a sudden BERYL IS RUNNING!

But wait. What would happen if I ended the session and started again? I ask myself. Well, son of a gun, Beryl no longer runs. correctly. The windows no longer have frames/controls on them.

So, here is what I've concluded. I'm using Kubuntu, which is known to lock down root priveleges. I'm also using an NVidia card, which is know to have driver problems (or so people say). The fact that Berly ran after the initial says that the NV drivers are not a problem. The fact that Beryl no longer ran after I ended the (working) session and restarted means that somewhere, there is a configuration file or something that Beryl can access the first time it is installed buy is no longer accessible/writable after the very first session ends.

Does this make any sense to anyone? Don't blame it on the NV drivers, because Beryl ran fine for several hours until I decided to see what would happen after I ended/restarted the session.

Can someone PLEASE help me with this? I'v been working on it for weeks. It clearly is boiling down  to a user rights issue.

---

### Post by jordanmthomas on 2007-01-19
> I'm using Kubuntu, which is known to lock down root priveleges.
huh?  I'm not sure what you mean here.  It shouldn't do any more than Ubuntu or anything else for that matter.

Anyway, try running beryl-manager from a konsole
```
beryl-manager
```
It should report any errors so we can get down to the problem

---

### Post by medley on 2007-01-19
> **jordanmthomas said:**
> huh?  I'm not sure what you mean here.  It shouldn't do any more than Ubuntu or anything else for that matter.

Anyway, try running beryl-manager from a konsole
```
beryl-manager
```
It should report any errors so we can get down to the problem

I don't get any errors at the konsole. It says 'trying 'home/phil/.xcompmgrrc' as configfile

then a separate line that says 'finished parsing the config file'

These are the only two messages in konsole. At the desktop I get an error message that says 'the composite manager has crashed twice in one minute and will be disabled for this session'

The ruby icon for beryl-manager is present in the taskbar after this, and because I've got it set to default back to the previous desktop manager after a beryl crash' kde restarts. This is the behavior I was experiencing prior to the beryl update of yesterday as well. It seems that the very first time Beryl is installed it will run, but after that no joy. I did see a from a guy somewhere saying that if he was having similar problems, and that if he uninstalled beryl, deleted /usr/.beryl and another file (can't remember the exact location of the files) and then reinstalled beryl, he could get it to run once as well. I tried this earlier and had found it to work. 

So, I'm pretty sure it's not a driver problem, or it should never work. And like I said, I was fooling around with it for several hours and it ran flawlessly. I was only after I logged out of the session and logged back in that it failed (and continues to without exception since then).

---

### Post by jordanmthomas on 2007-01-19
try deleting .beryl and .emerald from your home directory
```
sudo rm -r ~/.beryl
sudo rm -r ~/.emerald
rm ~/.xcompmgrrc
```
the sudo is just so it won't ask you about every single file

Which window decorator are you trying to use (emerald, heliodor, aquamarine)?

Also, post the output of 
```
cat /etc/X11/xorg.conf
```
Back in the pre-compiz days composite managers would crash if there was not the following at the end of xorg.conf
```

Section "Extensions"
   Option "Composite" "Enable"
EndSection

```

After ensuring that is in xorg.conf, try running beryl-manager again

---

