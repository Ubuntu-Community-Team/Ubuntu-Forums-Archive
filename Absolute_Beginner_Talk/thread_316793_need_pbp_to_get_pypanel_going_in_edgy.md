---
title: "need pbp to get pypanel going in edgy"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-12-11
i've tried everything i can figure out and i've read a bunch of stuff i don't understand. please hold my hand while you call my mom.

---

### Post by K.Mandla on 2006-12-11
fuscia, you're such a noob. :biggrin: It's installed, right? and you have a .pypanelrc file set up? and you're cueing it in .xsession or .xinitrc with a "pypanel &" command line?

Welcome to Ubuntu! :biggrin:

---

### Post by fuscia on 2006-12-11
> **K.Mandla said:**
>  It's installed, right? and you have a .pypanelrc file set up? and you're cueing it in .xsession or .xinitrc with a "pypanel &" command line?

i've installed it from synaptic (over and over again) and each time i type 'pypanel' into the terminal, i get "command not found". i've tried installing it from source but get an error when trying to run "python setup.py.install".  and there's no .pypanelrc to be found.

> fuscia, you're such a noob. :biggrin:

i'm waiting for a short bus forum.

> Welcome to Ubuntu! :biggrin:

gosh! thanks!

---

### Post by K.Mandla on 2006-12-11
That's bizarre. Let me install it on my Openbox machine and see what's happening. If it's not running from a terminal then it might be a bug. I could've sworn I tried this under Edgy a while ago, though. ...

---

### Post by K.Mandla on 2006-12-11
Well I'll be darned. You're right. pypanel from the command line gives me *bash: command pypanel not found*. 

I'll have to poke around and see what the story is. I noticed when I installed it, it put python2.5 into place (I don't use python on that machine otherwise). 

Could it be a dash issue?

---

### Post by fuscia on 2006-12-11
> **K.Mandla said:**
> Well I'll be darned. You're right. pypanel from the command line gives me *bash: command pypanel not found*. 

I'll have to poke around and see what the story is. I noticed when I installed it, it put python2.5 into place (I don't use python on that machine otherwise). 

Could it be a dash issue?

i think a bunch of people have had the same problem. there is even a thread about pypanel being possibly busted in universe. some of the solutions were over my head and i didn't want to do a bunch of stuff that might not work for me.:-k

---

### Post by K.Mandla on 2006-12-11
Do you have a link for that? You've sparked my interest on this. I don't know why; I don't even use pypanel. Maybe I'm just bored of playing Temple of Elemental Evil. :biggrin:

---

### Post by fuscia on 2006-12-11
> **K.Mandla said:**
> Do you have a link for that? You've sparked my interest on this. I don't know why; I don't even use pypanel.

[http://ubuntuforums.org/showthread.php?t=103418&highlight=pypanel](http://ubuntuforums.org/showthread.php?t=103418&highlight=pypanel)

> Maybe I'm just bored of playing Temple of Elemental Evil. :biggrin:

pypanel's just like it, only better.

---

### Post by K.Mandla on 2006-12-11
> **fuscia said:**
> pypanel's just like it, only better.
At least pypanel doesn't kill off my entire party with the first giant toad. Sheesh!

---

### Post by fuscia on 2006-12-11
> **K.Mandla said:**
> At least pypanel doesn't kill off my entire party with the first giant toad. Sheesh!

oh, you mean like e17?

---

### Post by maximegb on 2006-12-23
Pypanel is broken in edgy because of this bug [https://bugs.launchpad.net/distros/ubuntu/+source/python-xlib/+bug/66511](https://bugs.launchpad.net/distros/ubuntu/+source/python-xlib/+bug/66511)

To get pypanel in edgy, I installed these dapper packages :
python-xlib_0.12-5_all.deb
python2.4-xlib_0.12-5_all.deb
pypanel_2.4-1ubuntu1_i386.deb

Hope this help.

---

### Post by fuscia on 2006-12-23
> **maximegb said:**
> Pypanel is broken in edgy because of this bug [https://bugs.launchpad.net/distros/ubuntu/+source/python-xlib/+bug/66511](https://bugs.launchpad.net/distros/ubuntu/+source/python-xlib/+bug/66511)

To get pypanel in edgy, I installed these dapper packages :
python-xlib_0.12-5_all.deb
python2.4-xlib_0.12-5_all.deb
pypanel_2.4-1ubuntu1_i386.deb

Hope this help.

thanks for trying. i got an error, which i would try to figure out, but i've been using xfce4-panel instead and it has filled my needs. i appreciate your efforts, just the same.

---

