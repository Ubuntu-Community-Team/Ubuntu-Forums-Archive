---
title: "How do I remove the sda1 icon from the desktop?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Ulfursson on 2007-10-20
I'm allergic to desktop icons, and I'd like to remove the particularly useless windows' partition icon (even if I wanted to access it and somehow decided I need it on my desktop, it still displays my windows partition as empty). So how do I get rid of it?

---

### Post by Kosimo on 2007-10-20
alt+f2
gconf-editor


Then search this tree:

apps \ nautilus \ desktop

just disable  (volumes visible)

---

### Post by floke on 2007-10-20
Use gconf-editor

Apps/Nautilus/Desktop - uncheck 'volumes visible'

---

### Post by Marc Hoffman on 2007-10-20
only problem doing it that way is that other mounted drives are seen - like my IPOD or the flash drive i inserted.

---

### Post by Brian Kendig on 2007-10-21
Is there not a more "proper" way to remove the icons? A checkbox to uncheck in some settings dialog from the System menu, for example?

---

### Post by corney91 on 2007-10-21
> **Brian Kendig said:**
> Is there not a more "proper" way to remove the icons? A checkbox to uncheck in some settings dialog from the System menu, for example?

I believe it's either through gconf-editor or you can mount it in a different folder to /media, which I'm sure someone more knowledgeable can explain how to do (I'm afraid I don't know how myself, but would be interested to find out)

---

### Post by jingo811 on 2007-10-23
> **Brian Kendig said:**
> Is there not a more "proper" way to remove the icons? **A checkbox to uncheck in some settings** dialog from the System menu, for example?



Answer: 
This seems like the proper way.  You get to untick a checkbox with this method.  It worked for me.

> **Kosimo said:**
> alt+f2
gconf-editor


Then search this tree:

apps \ nautilus \ desktop

just disable  (volumes visible)

---

