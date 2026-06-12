---
title: "Removal code"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by toasted on 2006-08-30
Suppose I got something with this:

```
 sudo aptitude something 
```

Is this what I would use to remove it? (the -r that is)

```
 sudo aptitude -r something 
```

---

### Post by jpeddicord on 2006-08-30
You can use:
```
sudo aptitude remove something
```but if you want to use standard apt-get, you would use```
sudo apt-get remove something
```
You can also go to System > Admin > Synaptic and search for any packages you want to change/remomve/install.

---

### Post by croak77 on 2006-08-30
It's sudo aptitude install and sudo aptitude remove.

---

### Post by toasted on 2006-08-31
Alrighty, thanks

---

### Post by Titus A Duxass on 2006-08-31
aptitude man or aptitude help 

Will show you what you can do.

---

### Post by toasted on 2006-08-31
Duh, I should have thought of that! Thanks

---

