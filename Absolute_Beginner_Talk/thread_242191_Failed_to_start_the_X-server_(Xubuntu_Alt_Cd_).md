---
title: "Failed to start the X-server (Xubuntu Alt Cd )"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Blanka on 2006-08-23
[B][SIZE="3"]Hi there !

I managed to install the Xubuntu but it gives me an error saying the following :


     [INDENT]Failed to start the X-server(your graphical                  interface).
     It is likely that it is not set up correctly.
     Would you like to view the X-server output to diagnose the             
     problem ?
[/INDENT]
Then it the screen comes to :

     [INDENT]Ubuntu 6.06 LTS ubuntu tty2[/INDENT]

     [INDENT]Ubuntu login: [/INDENT]

When I type my login and password it comes to text input but I do not know the commands so please if there is any solutions to this I would be grateful to know them.
As I'm a newbie please tell me exactly what to type as I cannot open my desktop.
I have an old computer 96.0Mb RAM and have managed to get a 10.1Gb hard disk so space is not a problem any more!
I am using the Xubuntu alternate cd as using the live cd gave me enough problems !

[/SIZE]
[/B]

---

### Post by ewl1217 on 2006-08-23
Try the following commands at the terminal, in this order.
```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
```
sudo /etc/init.d/gdm start
```

---

### Post by Blanka on 2006-08-26
[B]This did not work man but i solved the problem by reducing my RAM to 64 and installed it on low memory mode and it worked like a charm !
thanks anyway![/B]

---

