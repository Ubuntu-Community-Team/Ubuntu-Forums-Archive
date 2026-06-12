---
title: "Installing LMMS in Kubuntu"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-04-01
Hey all, I'm trying to install LMMS for Kubuntu (is this even possible?) but I can't figure out the right file to download from their website. I look in Adept Package Manager but it's not there either. Any help?

---

### Post by rubbsdecvik on 2007-04-02
It should be possible.  I haven't used Kubuntu in a while, but I know I got it working on there before.  Do you have all your repositories selected and uncommented?

You can do that by doing this:

```
sudo gedit /etc/apt/sources.list
```

Then removing all the "#"s before the lines that have deb in them.

Save the file then do this:

```
sudo apt-get update

sudo apt-get install lmms
```

Let me know if that works or doesn't.  I'll try to help out as best as I can.

---

### Post by rubbsdecvik on 2007-04-02
PS... if you want you can try this equivalent.  It's called Hydrogen.

```
sudo apt-get install hydrogen
```

---

### Post by rubbsdecvik on 2007-04-02
Just curious to see if any of that worked for you.

---

### Post by hackle577 on 2007-04-02
I think it did, but there's no shortcut to it in the "Sound and Video" category.

---

