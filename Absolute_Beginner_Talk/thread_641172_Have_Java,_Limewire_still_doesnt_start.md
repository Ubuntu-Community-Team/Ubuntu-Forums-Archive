---
title: "Have Java, Limewire still doesnt start"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by radlations on 2007-12-15
From what I hear. Compiz is responsible for Limewire not running.

Once i turn off compiz's special effect. Limewire works fine. But If i close limewire, I have to reclose compiz for it to work.

Isnt there a way to run limewire without having to turn off compiz everytime?

---

### Post by lespaul_rentals on 2007-12-15
I don't user Compiz, so I wouldn't know.  However, using any eye-candy window manager such as the aforementioned makes it possible to have bad effects.  Sorry I can't be of more help.

---

### Post by mahiyar on 2007-12-15
What happens exactly if you start limewire with compiz? Is it that ther are just frames with blank inside? Give frostwire a try, its the same as limewire, and works OK with compiz on.

---

### Post by radlations on 2007-12-15
It loads just fine

I get to the part where they ask "Hey you wanna try limewire PRO?!"

While the main limewire window in the back is blank. The window bar is there. But its blank, no buttons or search bars.

---

### Post by mahiyar on 2007-12-15
Where did you install limewire from? From repositories or from synaptic?

---

### Post by Perfect Storm on 2007-12-15
Try frostwire instead. It's exactly the same but it's free.

Other than that you need to do this to get limewire working with compiz;

```
sudo nano /usr/lib/LimeWire/runLime.sh

```

delete whhat's inside and replace it with this;

```
#!/bin/bash
java -jar LimeWire.jar
```

---

### Post by radlations on 2007-12-15
Im sure there has got to be an easier way to delete all of this stuff

---

### Post by Perfect Storm on 2007-12-15
Sorry, it should say change, so it says. My fault, havn't my morning coffee yet.

---

### Post by kajillin on 2007-12-15
Limewire sucks, take the next step, and start using bittorrent!

---

### Post by radlations on 2007-12-15
But that would require me to find a good torrent site...

And torrents take forever to finish.

---

