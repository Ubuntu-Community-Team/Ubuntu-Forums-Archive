---
title: "[SOLVED] Why does my workspaces disapear?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-24
I currently have 4 workspaces without desktop effects ( on Ubuntu 7.10)

When I enable desktop effects, it goes to 2 workspaces.


**Keep in mine, for some reason, my CompizConfig Settings Manager won't load up/start up so if someone could tell me something about that, it will be great!**

Merry Christmas!

Make this my Christmas present because I got no presents so far... :(

---

### Post by ~LoKe on 2007-12-24
The only way I know of to change that is to change the horizontal desktop number to 4.  Since you can't open up the settings panel, we'll have to figure that part out.

Type this into a terminal and tell me what error it gives:
```
ccsm
```

---

### Post by hilariousness16 on 2007-12-24
Alright, here you  go:)

```
brandon@brandon-laptop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

---

### Post by ~LoKe on 2007-12-24
Looks like you're using a 3rd party repository (trevino's?).  Try downloading the source and compiling it that way.

```
cd ~/ && wget http://releases.compiz-fusion.org/0.5.2/ccsm-0.5.2.tar.gz && tar xvf *0.5.2.tar.gz && cd ccsm* && make && sudo make install
```

Or you could comment out line #45 in /usr/bin/ccsm.

---

### Post by hilariousness16 on 2007-12-24
Hmm...I ran tat link through the terminal and still getting nothing...Should I restart?


and I don't really get that 2nd option that you were saying...:\

---

### Post by hilariousness16 on 2007-12-25
someone help plz?

---

### Post by hilariousness16 on 2007-12-25
bump

---

### Post by shareMenaPeace on 2007-12-25
Go to Compiz Settings Manager and to General and there to Appearance and choose 4 workspace?

---

### Post by shareMenaPeace on 2007-12-25
Oos i Mean Go to 

Administration - Advanced Desktop Effects Settings - General  Options - Desktop Size and make sure you have 4 set. ... oh ok ok you cannot start :)

Hmmm Do you added 

> Section "Extensions"
    Option "Composite" "1"
EndSection

Section "ServerFlags"
    Option "AIGLX" "on"
EndSection

Section "DRI"
    Mode         0666
EndSection

to the config.xorg?

(he has same grafic card than me ... xpress ati 200 m)

Or maybe what i did was install GL Desktop  with synaptic .... than use this tool to edit compiz ... see if this works

---

### Post by lamalex on 2007-12-25
HIllariousness16, are you just using desktop effects from Ubuntu? I'm not sure how Loke deduced you were using a 3rd party repo.

Install the compiz configuration tool
```
sudo aptitude install compizconfig-settings-manager
```
Under general you can set virtual desktop size.

---

### Post by hilariousness16 on 2007-12-25
Mena, do you want me to insert that code? :popcorn:

---

### Post by hilariousness16 on 2007-12-25
OOOOOO WTF IT WORKS


hold on:popcorn:

---

### Post by hilariousness16 on 2007-12-25
thank you everyone, just one little thing

when I went to the compiz thing like sharemena told me, when I go to 5 desktops, it shows 4 so idk if u really got that but oh well, thx for the code too ian

---

### Post by hilariousness16 on 2007-12-25
ugh nvm im still having problems

---

