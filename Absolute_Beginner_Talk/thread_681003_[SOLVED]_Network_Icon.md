---
title: "[SOLVED] Network Icon"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-01-28
Hello!
I'm using a wired network and i can see it's icon (two computers) on top left side. In windows one was for send and the other for receive and they became lighter (shinier) when I was sending or receiving can I have it in my ubuntu too?
+++
By double clicking on that icon in windows I could see how much did I send or receive. Here I can just see my ip and servers and something like this. Can I see how much did I send or receive?
Thank you.

---

### Post by Cypher on 2008-01-28
Type
```

/sbin/ifconfig

```
at the prompt and you will get packets and bytes RX'ed and TX'ed..and any errors..

---

### Post by Hoom@n on 2008-01-28
Thank you but I couldent find prompt. (I know msdos and I know cmd in windows, but today is my first day in Linux.) Please tell me where it is.
+++
And can I make the icon like windows' to see is my computer transferring files or not? I mean see the icon's monitors in different colors when receiving or sending files (like gray and blue in windows xp)
Thank you.

---

### Post by emarkd on 2008-01-28
the prompt is at Applications > Accessories > Terminal.

If you want a nice monitor for your desktop, do a search for conky.  You can see my Conky monitor in the bottom corners of this screenshot.  The network activity is in red and green.

---

### Post by Hoom@n on 2008-01-28
Thanks alot for your help and the picture. I just wanted to have an animated network icon like windows. Please tell me if it's impossible to have that, Thank you.

---

### Post by emarkd on 2008-01-28
The Gnome network icon is not animated.  Instead of trying to make Ubuntu like Windows, why don't you try it Ubuntu's way?  You may find, as many of us do, that this way is better after all ;)

---

### Post by Hoom@n on 2008-01-28
Thank you for the help. I just wanted to have a view of my transfers. Now I think you are right.
Thank you.

---

### Post by emarkd on 2008-01-28
Maybe you misunderstand me.  In that screenshot I posted, the red and green graphs in the botton right are for network activity.  Download activity is in red, upload is in green.

---

### Post by Hoom@n on 2008-01-28
Thank you but i just wanted to see can i make it like windows or not. thanks again.

---

### Post by whitethorn on 2008-01-28
Hi I'm not sure if this is really what you want, but you can right click on the top bar and add an applet called system monitor.  Then you can right click on it and add network.  It'll give you a graph on ur taskbar (top bar whatever it's called).  You can also always try corky (looks really nice) or gdesklets (small desktop plugins).

---

### Post by Hoom@n on 2008-01-28
Thank you but could you please show me a screenshot?

---

### Post by Hoom@n on 2008-01-30
I've to add:
By going to add to panel under the system and hardware there is network monitor which was the exact thing I needed! I found it myself!
Again thanks!

---

