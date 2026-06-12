---
title: "SSH = Text only?"
date: 2005-06-22
forum: Absolute Beginner Talk
---

### Post by Trojan1313 on 2005-06-22
I thought I was going to get a look at me beautiful desktop with putty connection to SSH, but oh, the disappointment when I found myself in the X-less Ubuntu where I can do nothing! :(

Now tell me, can I start X.org remotely or do I need to use another tools for graphical remote administration?

---

### Post by TravisNewman on 2005-06-22
FreeNX or things like that would be what you want, or remote gdm logins. 
FreeNX: [http://freenx.berlios.de/](http://freenx.berlios.de/)
FreeNX is in the backports repositories. See the third party section on the forums.

Happy remoting! ;)

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=panickedthumb]FreeNX or things like that would be what you want, or remote gdm logins. 
FreeNX: [http://freenx.berlios.de/](http://freenx.berlios.de/)
FreeNX is in the backports repositories. See the third party section on the forums.

Happy remoting! ;)[/QUOTE]
Lucky me, I found the program on synaptic. :)
How do I configure it? I can't find it anywhere in the menu.

Thanks a million. :)

EDIT: Is there any client wich doesn't require install (Windows client)? Not neccesery, but since I will be using it from school mainly it would be good.

But I can probably sneak it in, just a small app anyway, even suspekt I can install it extract it from my home PC when I've installed it there, no registry = no fuss. :)

---

### Post by ltmon on 2005-06-22
I hope to try out freenx pretty soon.... [this blog](http://www.kdedevelopers.org/node/view/1187) makes it sound really nice :)

---

### Post by Jussi Kukkonen on 2005-06-22
[QUOTE=Trojan1313]I thought I was going to get a look at me beautiful desktop with putty connection to SSH, but oh, the disappointment when I found myself in the X-less Ubuntu where I can do nothing! :(

Now tell me, can I start X.org remotely or do I need to use another tools for graphical remote administration?[/QUOTE]

This is not for windows, I believe, but... If you are running X locally then you can tunnel (remote) X over SSH. I think this has to be enabled on the ssh server. This way you can start remote graphical programs seemingly 'on the local desktop'. Like this:

Connect with X tunneling enabled (this is with OpenSSH client):
```
ssh -X user@host
``` 
When you're logged in, start the program you want:
```
openoffice &
```

---

### Post by Trojan1313 on 2005-06-22
There is a Windows Client for it. :)

---

### Post by somuchfortheafter on 2005-06-22
why not use vnc, its cross platform, easy to use, and it works fairly well...

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=somuchfortheafter]why not use vnc, its cross platform, easy to use, and it works fairly well...[/QUOTE]
 Do the free edition work for contact between Linux och Windows?

---

### Post by Poul on 2005-06-22
you can always keep and run it from your usb key.

---

### Post by Trojan1313 on 2005-06-22
[QUOTE=Poul]you can always keep and run it from your usb key.[/QUOTE]
 So I don't need the registry files then? In that case I have other ways to... distrubute it. *evil grin*

*don't have a USB-memory*

---

### Post by somuchfortheafter on 2005-06-22
what do you mean free edition .. does it work.. haha of course it works lol

---

