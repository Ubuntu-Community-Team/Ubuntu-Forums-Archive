---
title: "[SOLVED] help - everything looks &amp;quot;old school&amp;quot; Windows"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Abacab on 2008-02-19
Hi.

New to Linux and Ubuntu and in need of some help. This is a little hard to describe but all of a sudden  a couple of days ago everything in Gutsy has taken on what I can only describe as an old Windows 98 type appearance with buttons and radio buttons etc. To see what I mean take a look at the picture kepos posted here (post #5):

[http://ubuntuforums.org/showthread.php?t=394251&highlight=flat+buttons](http://ubuntuforums.org/showthread.php?t=394251&highlight=flat+buttons)

That's the same problem I'm having and it applies to websites (not just in Firefox but also Epiphany and Opera) and applications. I didn't have the problem before, everything looked nice with rounded instead of flat buttons etc. I've searched the boards and Google and though I've come across several people with the same problem I haven't found a way to fix it. Even stranger is that out of curiosity I tried the live disc and that was the same despite not being like that when I installed Ubuntu. I dual boot with Vista and although it probably is irrelevant, everything is fine there.

If anyone can help solve this it would be greatly appreciated. Keep in mind I'm new to Linux. 
Thanks.

---

### Post by Superkoop on 2008-02-19
Your theme has probably been changed. 
Go to: System > Preferences > Appearances 

On the theme tab, check to see what theme you have enabled.

---

### Post by teamkiller87 on 2008-02-19
From the picture in that link I would have to say the control theme you are using is Raleigh, or Redmond or smth like that. You can change it by going in System-Preferences-Appearance and clicking on the Customize button. In the "Control" tab just choose a different control theme, default Glossy or Clearlooks have rounded up buttons so that should tell if you this was the problem or something else.

---

### Post by Abacab on 2008-02-19
Hi. That was the first thing I tried. I'm using Clearlooks and have tried every theme and get the same problem.

---

### Post by Abacab on 2008-02-19
From what I can gather from searching other posts it may have something to do with gnome-settings-daemon if that helps anyone as it means little to me.

---

### Post by timbounceback on 2008-02-19
Alt+F2, then enter```
gnome-settings-daemon
```

---

### Post by Abacab on 2008-02-19
I've read that somewhere else but what is supposed to happen? I tried it and nothing happened and the problem is just the same.

---

### Post by timbounceback on 2008-02-19
OK, and (just doublechecking), you've checked your themes? Try logging out then back in again

---

### Post by Abacab on 2008-02-19
Yes I've checked all themes and I log out and back in after every check in the hope of solving it but so far nothing. It's driving me mad as everything looks terrible whereas it did look great.

---

### Post by Abacab on 2008-02-21
I found the thread below and it sorted the problem in Firefox for me which is the only place it was really bothering me so I guess it's solved.

[http://ubuntuforums.org/showthread.php?t=369596](http://ubuntuforums.org/showthread.php?t=369596)

---

