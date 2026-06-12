---
title: "ubuntu update problem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by dellboy on 2007-05-30
ubuntu is telling me there is updates i start to do some of them i need to trun of my computer now it tell me there is update so i click it then is says 


only one software management tool is allowed 


please close the other application eg appitiude or synaptic 

but 


can any one help me ;)

i dont think any app is running

---

### Post by taurus on 2007-05-30
I guess you forgot the pic.

Meanwhile, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Ek0nomik on 2007-05-30
Your picture isn't working.  :)

---

### Post by dellboy on 2007-05-30
here is the pic 

[IMG]http://supermegadownloads.co.uk/image-host/images/7953Screenshot.jpeg[/IMG]

---

### Post by Nythain on 2007-05-30
open up terminal and type
```

sudo dpkg --configure -a
sudo aptitude clean

```

---

