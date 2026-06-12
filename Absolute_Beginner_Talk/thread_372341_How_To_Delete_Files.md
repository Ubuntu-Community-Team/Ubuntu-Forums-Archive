---
title: "How To Delete Files?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by the_nomad on 2007-02-28
hello there... ive noticed that folders created with mkdir cant be deleted with nautilus. it says i dont have the permission... how do i delete it through terminal??! :mad: :mad: :mad: 

thanx.

---

### Post by Quillz on 2007-02-28
```
sudo rm FILE NAME
```

---

### Post by JermainWijnhard on 2007-02-28
If you're doing it from the comman line interface, it wont delete folders unless they are empty. Try to delete the content first and try again.

---

### Post by the_nomad on 2007-02-28
> **JermainWijnhard said:**
> If you're doing it from the comman line interface, it wont delete folders unless they are empty. Try to delete the content first and try again.

Not really.. actually i was trying to make a folder so i can mount the windows partition but i've made the folder in a location where i wasnt feeling confortable with so i wanted to delete it through nautilus but it said that i dont have the permission :|

it worked with 'sudo rmdir file' :) thanx for the hint.

---

### Post by Ek0nomik on 2007-02-28
If you want to do it with nautilus, you may.

```
sudo nautilus
```

Hope that helps!

---

### Post by the_nomad on 2007-02-28
yeah that worked too :) thanx. i now can see where half of my installed files were :P
i guess i forgot to say i used 'sudo mkdir' when making the folder :)

thanx for replying dudes.

---

### Post by Ek0nomik on 2007-02-28
The community around here can be good at replying once in awhile.  ;)

Cheers!

---

### Post by DirtDawg on 2007-02-28
You may also be interested to know you can remove non-empty (or empty) folders with 
```
 rm -r FOLDERNAME 
```
Careful, though, because it won't ask to confirm first. Don't accidentally erase your /home folder, for example. For confirmation use:
```
 rm -r -i FOLDERNAME 
```

---

### Post by jvc26 on 2007-02-28
You should use:
```

gksudo nautilus

```
As you should always use gksudo for graphical apps, and sudo for CLI: [Running Sudo Graphically]("http://psychocats.net/ubuntu/graphicalsudo")
Il

---

