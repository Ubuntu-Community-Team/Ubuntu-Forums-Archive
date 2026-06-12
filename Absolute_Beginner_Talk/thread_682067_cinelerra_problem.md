---
title: "cinelerra problem"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by lolzlolz on 2008-01-29
cinelerra won't run when i click the icon in apps sound&video it just sits there i installed as suggested and added the thing to the file to give cinelerra the more memory requierd, there is no process called cinelerra in process manager once i start it 
here is the error when i attempted to run it in terminal by typing cinelerra
```
cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory

```
thanks

---

### Post by jan quark on 2008-01-29
ok lets try this
type this into the terminal
```
sudo ln -s /usr/share/fglrx/diversions/libGL.so.1.2 /usr/lib/libGL.so.1
```

I suppose you have a ati 3d card
this code creats a link to the needed library

just a try

---

### Post by lolzlolz on 2008-01-29
i have an nvidia egeforce 8600 gt gfx card technically evga with nvidia chipset anyways ill try that

---

### Post by lolzlolz on 2008-01-29
same error after i did that

---

### Post by lolzlolz on 2008-01-29
so now what ? 
thanks

---

### Post by lolzlolz on 2008-02-08
bump

---

### Post by forrestcupp on 2008-02-08
How did you install it, and which version did you install?  Did you install the official version from Heroine Virtual, or did you install the CV version?

If you didn't install the CV version, I suggest uninstalling Cinelerra and using the CV version.  You can get the apt repository and the authentication key at their [web site](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu).  Doing it this way, you can install everything you need automatically with apt-get or Synaptic and it will be updated for you.

---

### Post by lolzlolz on 2008-02-08
at first i just used synaptic, after adding the key using the terminal command i find no other options for installing cinelerra:confused:

---

### Post by lolzlolz on 2008-02-09
is there a different way i should install?

---

