---
title: "Network icon gone"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by Maikelv on 2008-01-12
Hi there,

A silly problem, but I ve been looking for a solution for an hour now, and its really getting on my nerves :P.
My wlan icon on my top panel is gone (The one wich indicates my wlan signal strength, and where I can easily change networks). And in all my ubuntu-noobishness I can't find it back. In "add to panel" there is only the "network monitor" and this is different from the one I had before.

Could anyone give me a quick hand ?

---

### Post by rowanparker on 2008-01-12
```
nm-applet
```
?

---

### Post by Maikelv on 2008-01-12
hmm that command gives me a new line in terminal (without the usual user@.....$) as if its loading, but its been doing that for quite a bit now....

---

### Post by steeleyuk on 2008-01-12
Try ALT + F2 and type nm-applet, see if thats gives you what you want. Seems like the terminal is giving you a seperate problem though :s

---

### Post by Maikelv on 2008-01-12
hmm entering nm-applet doesn't do anything :)

---

### Post by rowanparker on 2008-01-12
There is nothing wrong with his terminal.
It means there is something wrong with nm-applet.
Try running: ```
killall nm-applet
``` and then run: ```
nm-applet
```

---

### Post by Maikelv on 2008-01-12
> **rowanparker said:**
> There is nothing wrong with his terminal.
It means there is something wrong with nm-applet.
Try running: ```
killall nm-applet
``` and then run: ```
nm-applet
```

Hmm, does the same thing :) so new terminal line.

---

### Post by rowanparker on 2008-01-12
Tried a restart?
I know its a Windows-like suggestion but I'm outa ideas.

---

### Post by eolson on 2008-01-12
If I'm understanding correctly,  you now have the terminal icon instead of the signal strenght bars.

If you don't have a wifi card or your wifi card is not working that will happen.

Is your wifi working?

---

### Post by Maikelv on 2008-01-12
I rebooted , and its not back.

My wifi is working perfectly. hmmm, pretty strange :s

---

### Post by Tenken on 2008-01-12
Have to tried adding the applet back to the panel? Right-click the panel -> Add to Panel and scroll down until you find Network Manager (under System and Hardware), select it and click the "Add" button.

---

### Post by Maikelv on 2008-01-12
> **Tenken said:**
> Have to tried adding the applet back to the panel? Right-click the panel -> Add to Panel and scroll down until you find Network Manager (under System and Hardware), select it and click the "Add" button.

well, I tried this, but it only has the "network monitor" wich is quite different from what I had before. It doesn't have "network manager".

---

### Post by Tenken on 2008-01-12
Sorry, I read "Monitor" not "Manager". Network Manager is a start up service, go to System->Preferences->Sessions and make sure Network Manager is checked. It starts up in the "Notification Area", so if it still missing try adding that to your panel. The Notification Area is where your minimized Pidgin/Rhythmbox/Update notifier icons appear.

---

### Post by philinux on 2008-01-12
You might need to add the notification area .

---

### Post by Maikelv on 2008-01-12
> **philinux said:**
> You might need to add the notification area .

That did the trick !! thanks !

---

