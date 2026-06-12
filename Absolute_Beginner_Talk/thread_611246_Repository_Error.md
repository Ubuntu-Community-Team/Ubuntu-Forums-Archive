---
title: "Repository Error"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by jcouillard on 2007-11-12
How do I make this go away when I reload the Synaptic?? Thanks

[IMG]http://i21.photobucket.com/albums/b263/JCouillard/Screenshot-synaptic.png[/IMG]

---

### Post by NeoLithium on 2007-11-12
Open up a terminal window and type in:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
then
```

sudo apt-get update

```
Should get you nice and good to go again :)

---

### Post by jcouillard on 2007-11-14
I don't know what the hell you did but the error did not pop up. Thanks. I understand the update part but what was the first part about??? I can't wait understand what it is I'm doing rather than just copying and pasting the codes...lol

---

### Post by taurus on 2007-11-14
Adding a key for medibuntu repos.

---

