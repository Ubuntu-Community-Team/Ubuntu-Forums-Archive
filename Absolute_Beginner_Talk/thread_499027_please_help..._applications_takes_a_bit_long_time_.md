---
title: "please help... applications takes a bit long time to start"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-07-12
hello everyone

my applications start a bit late. 

is there any performance tweak which may make my applications start faster...

---

### Post by MikeAlmere on 2007-07-12
I work on an old machine and chose Xubuntu, because it is light on resources. This makes everything work fast. What kind of machine do you use?

---

### Post by cyneuron on 2007-07-12
i have good enough confi....

pentium centrino mobile ; 512 mb ram

---

### Post by felicity on 2007-07-12
If specific applications take too long opening, you can always add them to your session to be automatically started when you boot your computer. You can also use Devilspie to have them open on a specific workspace or minimized.

---

### Post by cyneuron on 2007-07-12
is there any performance tweak required or available....

---

### Post by Ozeuss on 2007-07-12
I don't have real benchmarks, but word on the street
```
sudo apt-get install preload
```
that program should study your work habits and preload some programs you use frequently, thus lowering load time.
and also
```
sudo gedit /etc/hosts
```
and add you hostname to the first line after localhost like this:
```

127.0.0.1 localhost yourhost
127.0.1.1 yourhost

```

also, there are specific tunings you can do or certain applications, like OO, from their GUI.

---

