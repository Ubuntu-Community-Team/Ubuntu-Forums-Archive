---
title: "Add/remove prog and other problems"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by jtclicker on 2008-02-27
I've searched for answers to this but no luck! I have absolutely no experience of ubuntu or linux so I'm going to need some handholding which I must admit hurts as I'm usually solving other folks problems on a pc. I've just installed ubuntu on a wintel machine as a dual boot with ubuntu on a second drive. worked well, had a error 21 problem but after altering the bios settings everything is fine on the install.
But...
In Add/Remove programs everytime I try and 'tick' a box, I get a refresh dialogue and the box refuses to tick, so I can't add an app.
I've sldo got a keybiard issue. I've selected the language and kybd layout correctly - I'm using a spanish Dell keyboard with ubuntu in English, but I can't access my third level characters like the @ which is usually ctrl/alt/2.

Any ideas?

I'm going to be using ubuntu for heavy photowork with cinepaint and other apps, so colour management is going to be a big issue for me and I'm already reading the resources.

Thanks in advance
Julian

---

### Post by jan quark on 2008-02-27
have you enabled the software sources?

check this in system > administration > software sources
check all available sources except source and cd

then run 

```
sudo apt-get update
```

and try to install one more time

---

### Post by jtclicker on 2008-02-27
thanks that solved the add/remove problem. Any ideas about the keyboard?

---

