---
title: "[SOLVED] GNOME problem"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by spai on 2007-12-15
Whenever I start my system (even in failsafe mode) or go to the System>Preference>Appearances tab I get the following message
```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

And I have some weird theme running, that I dont want and I cant change it ,because of the above error message.

Any Ideas?

Thanks in Advance,
Srikanth

---

### Post by jordanmthomas on 2007-12-15
Do you have a custom .gtkrc-2.0?
If so, gnome's complained about this for me in the past.

---

### Post by spai on 2007-12-15
> **jordanmthomas said:**
> Do you have a custom .gtkrc-2.0?
If so, gnome's complained about this for me in the past.

Never heard of that! What is it? And how do I find it?

---

### Post by spai on 2007-12-15
Well I tried searching my home folder, if that is what you mean,
```
srikanth@ubuntu:~$ ls -a| grep gtkrc
.gtkrc-1.2-gnome2

```
Is this what you are talking about?

---

### Post by spai on 2007-12-15
Oh by the way is there any way to kill those hampering KDE applications(if any). Does anyone know how to set GNOME to defaults at least?
I remember some one telling me to move some gconf files in and out. But I dont remember the exact detail. 
Any help is greatly appreciated,
Thank you :)
Srikanth

---

### Post by undine on 2007-12-15
Just delete .gtkrc, and that should fix the problem.

---

### Post by spai on 2007-12-15
> **undine said:**
> Just delete .gtkrc, and that should fix the problem.

YAY, Done that and it worked :guitar:

Thanks a lot :)
Srikanth 
Now for purposes of learning 
1)what is the possible reason for this problem?
2)And what is that file? What did I do by deleting it?

Does .gtkrc remember the configuration or something? If yes how come removing it still has my old settings intact?

Thanks again,
Srikanth

---

### Post by undine on 2007-12-15
> **spai said:**
> YAY, Done that and it worked :guitar:

Thanks a lot :)
Srikanth 
Now for purposes of learning 
1)what is the possible reason for this problem?
2)And what is that file? What did I do by deleting it?

Does .gtkrc remember the configuration or something? If yes how come removing it still has my old settings intact?

Thanks again,
Srikanth

I'm no expert on this, but I believe that .gtkrc is a file created by KDE for the purposes of theming GTK apps that you load into that particular desktop environment. The problem is, that it tends to interfere with the operation of the gnome-settings-daemon -- as you discovered. Therefore, you didn't really do anything (harmful) by deleting it. I hope that it explains it at least tolerably well.

---

### Post by spai on 2007-12-16
Oh :KS
Got it. 


Thanks :)
Srikanth

---

