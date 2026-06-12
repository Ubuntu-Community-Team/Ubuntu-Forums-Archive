---
title: "how do you add keys"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by fminmexico on 2007-09-29
Just where am I supposed to import the key file from, I can copy the key to a document but that does not work.I have the keys what do I do to import them to synaptic. 
   fminmexico.

---

### Post by michael37 on 2007-09-29
Exit Synaptic.

Open terminal.

If you have a link to the file, type
```

wget http://www.some.site.ws/key.gpg -O- | sudo apt-key add -

```
or if you saved the file on your hard drive, type
```

sudo apt-key add /path/to/file/key.gpg 

```

Start Synaptic.  It will now recognize the key.

---

### Post by Arthur Archnix on 2007-09-29
Most of us here aren't running crystal-ball until a more reliable version is released, so if you want some replies your going to have to explain what you're trying to do, what steps you've taken, and what's gone wrong.

For example, "I'm trying to install program X. I added the repository to my sources.list but need to add the key. I can download the key using wget blahblahblah, but now what do I do with it? I was following the instructions I found at www.getprogramX.com"

EDIT: Michael is apparently running crystal-ball.:-k

---

