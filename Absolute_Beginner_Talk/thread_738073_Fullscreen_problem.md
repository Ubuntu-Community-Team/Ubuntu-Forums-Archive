---
title: "Fullscreen problem"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by AflingZ on 2008-03-28
Hello!

I have a problem. When I open the home folder (file browser in general), it is shown in full screen, without any option to minimize or exit it, as the title bar is not shown. Also the startbar (or panel) is not shown. Only the file browser, and I dont know how to make it normal size again.

Thanks in advance :)

edit:
btw is it called nautilus?

---

### Post by bumanie on 2008-03-28
Have you made any changes to your system such as enabling desktop effects etc.? What type of video card are you running?

---

### Post by AflingZ on 2008-03-28
I have the standard desktop effects enabled, I just tried without, which didnt help :(

video card, its a Geforce 6200LE

I might have enabled that fullscreen thing, but I really dont know how I did it then. :(

---

### Post by bumanie on 2008-03-28
This may fix your problems as something similar to what you are describing occurs with some nvidia cards. 
> sudo nvidia-xconfig --add-argb-glx-visuals -d 24
Hope it works

---

### Post by AflingZ on 2008-03-28
hmm after reset I get this when trying to open filebrowser:
Nautilus kan ikke bruges nu pga. en uventet fejl fra Bonobo ved forsøg på at at finde fabrikken. At afslutte bonobo-activation-server og genstarte Nautilus kan måske løse problemet.
and in english :P
Nautiles cant be used now because of an unexpected error from Bonobo when trying to find the factory. Closing bonobo-activation-server and restarting Nautilus can maybe fix the problem.
I guess I have to do that then? :)

---

### Post by bumanie on 2008-03-28
I have never heard of that happening with that command, as I said it often fixes similar issues with nvidia cards. 
This may help [http://ubuntuforums.org/archive/index.php/t-6140.html](http://ubuntuforums.org/archive/index.php/t-6140.html)

---

### Post by AflingZ on 2008-03-28
okay, I think the bonobo problem is fixed, but now I am back where I started.. Is there a way to go back to the default settings for the file browser maybe? So that the file browser as the same settings as when it was installed .. :)

---

### Post by bumanie on 2008-03-28
Sorry, I am at work and had to do things.
This won't exactly help, but I just saw a discussion with others complaining about thesame thing and putting it down to a bug between nautilus, metacity and compiz. I'll do a bit more searching. This may be something new. May be recent updates have caused some idiosynchratic conflict with your (and the others who are affectted) set up. A suggestion is to use fluxbox or emerald as window managers. That may fix it.

---

### Post by forrestcupp on 2008-03-28
You could try typing this in a terminal
```
sudo dpkg-reconfigure nautilus
```

---

### Post by AflingZ on 2008-03-28
> Sorry, I am at work and had to do things.
No problem, take your time ofcourse :D

> **forrestcupp said:**
> You could try typing this in a terminal
```
sudo dpkg-reconfigure nautilus
```
Thanks that worked ! :D

---

