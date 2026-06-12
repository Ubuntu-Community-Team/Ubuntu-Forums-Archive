---
title: "roots wants to make link: &quot;operation not permitted&quot;?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by pixelstuff on 2007-05-30
hi
how can I make a  link to a folder  which is outside of my home directory? So the folder is root-owned but also from the  root browser (file browser (root)) or trying "sudo chown me wantedfolder" I get "operation not permitted" It's probably not possible to change the owner outside the home directory...but why can't the root browser make a link?The folder is on a shared partition, I can't keep all my documents in the home directory :(
Thank you

---

### Post by Cypher on 2007-05-30
If the folder is something like "/shared/stuff" and your home directory is "/home/user", then try the following
```

cd /shared
sudo chown root.root stuff
sudo chmod 777 stuff
cd ~
ln -s /shared/stuff stuff

```
Does that work?

---

### Post by pixelstuff on 2007-05-31
:p thank you! It worked! \\:D/

---

