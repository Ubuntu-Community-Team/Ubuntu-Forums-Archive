---
title: "Remote Desktop Mac yo Linux"
date: 2010-09-07
forum: Apple Hardware Users
---

### Post by DukeBoxer on 2010-09-07
I'm not sure if this is the right place to ask this, but does anyone know why when I try to connect remotely to my linux box with my mac, the mac just hangs on "connecting" while the linux box says someone is connected? I have an old computer with ubuntu 10.04 connected to my tv and I am trying to control it from my mac so that I can run boxee and movies and stuff like that and I don't want to hook up any keyboard or mouse which would defeat the purpose. If i remote in form another linux machine it works fine but it seems like the mac needs a password to log in, which means the linux box makes a password in the keyring, which means I need to unlock it before the mac can connect, which means I need a keyboard connected...you get the idea.

What can I do to get the mac to connect without having to put a password in?

---

### Post by conundrumx on 2010-09-08
It just shows the connecting window indefinitely?  Never asks for a password?

---

### Post by DukeBoxer on 2010-09-08
exactly, it just hangs indefinitely. I have it set on the ubuntu box so that it doesn't ask for a password, but it seems like the only way for the mac to connect is with a password. I did kind of work around what I wanted to do by setting the computer to start boxee on startup and use boxee remote on my palm pre phone (also on iphone and ipod touch) which really takes away the need to remote to it to control boxee..but I am now looking for a way to safely shutdown the computer. I can ssh into it from the mac and then do 'sudo shutdown -h now' but that shuts it off right away, kind of like pulling the plug (thats what it seems to me at least) does anyone know what command to use that makes the computer shut down as if I hit 'shut down' from the pull down menu on the desktop?

---

### Post by conundrumx on 2010-09-09
I'd try using [Jolly'sFastVNC]("http://www.jinx.de/JollysFastVNC.html") to isolate the problem to Screen Sharing or the Ubuntu machine.  As far as your question regarding shutdown...

```
# man shutdown
```

---

### Post by DukeBoxer on 2010-09-10
I was testing the command 'sudo shutdown -h now' on a 10.10 install in virtualbox and I saw it shutoff right away, but when I did it on the box I have connected to the TV it actually went through the same steps as if I went to the menu on the desktop and hit shutdown. Thank you.

I actually worked around everything else by not using the Mac at all. I can use my cell phone for both remote desktop and a remote to control the Boxee UI.

---

