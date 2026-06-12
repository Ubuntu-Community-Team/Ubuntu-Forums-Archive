---
title: "Same program running twice?"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-15
hey, ive been using scim for a little while and did a lot of tweaks to it i think following a couple threads around here. Right now, i see two keyboard icons in the upper right corner on the taskbar. they both seem identical and say "English/Keyboard" when i hover my mouse over it. When i press shift+spacebar to switch the languuage input, only one of them changes to the other icon, the other keyboard stays the same. Did i install scim twice or is it supposed to be this way?

thanks

---

### Post by seshomaru samma on 2007-02-15
it's not supposed to be like that
is scim working properly ?
you can delete one icon by right-clicking on it

---

### Post by The55Gon on 2007-02-15
> **seshomaru samma said:**
> it's not supposed to be like that
is scim working properly ?
you can delete one icon by right-clicking on it

by hiding the icon? i dont see an option to delete it, only to hide it
how do i uninstall one of them?

---

### Post by seshomaru samma on 2007-02-15
what's the output of 
```
 ps aux | grep scim
```

it's unlikely that you installed scim twice or have two instances of scim running at the same time

---

### Post by The55Gon on 2007-02-15
This is what it outputs:

the55gon 13305  0.0  0.4  27752 10240 ?        Ss   Feb13   0:04 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
the55gon 13308  0.0  0.0   5072  1000 ?        Ss   Feb13   0:00 /usr/lib/scim-1.0/scim-helper-manager
the55gon 13309  0.0  0.3  28444  7828 ?        Ssl  Feb13   0:06 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
root     17821  0.0  0.4  27568 10096 ?        Ss   Feb14   0:00 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
root     17828  0.0  0.0   5076  1004 ?        Ss   Feb14   0:00 /usr/lib/scim-1.0/scim-helper-manager
root     17829  0.0  0.3  51972  7552 ?        Ssl  Feb14   0:00 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
the55gon 19785  0.0  0.1  13032  3608 ?        Ss   Feb14   0:00 /usr/lib/scim-1.0/scim-helper-launcher --daemon --config socket --display :0.0 anthy-imengine-helper 24a65e2b-10a8-4d4c-adc9-266678cb1a38
the55gon 12811  0.0  0.0   2804   768 pts/0    S+   10:17   0:00 grep scim
the55gon@the55gon-laptop:~$

---

### Post by The55Gon on 2007-02-15
does anyone see a problem with this?

---

### Post by seshomaru samma on 2007-02-16
it looks like you are running one instance of scim with maybe two icons
this is my ps aux |grep scim

```
sesho@desktop:~$ ps aux | grep scim
sesho     8619  0.0  1.8  29176 19352 ?        Ss   Feb07   0:16 /usr/lib/scim-1.0/scim-launcher -d -c simple -e all -f socket --no-stay
sesho     8627  0.0  0.1   5096  1036 ?        Ss   Feb07   0:00 /usr/lib/scim-1.0/scim-helper-manager
sesho     8628  0.0  1.4  65644 15164 ?        Ssl  Feb07   0:43 /usr/lib/scim-1.0/scim-panel-gtk --display :0.0 -c socket -d --no-stay
sesho     8630  0.0  0.1   7988  1280 ?        Ss   Feb07   0:01 /usr/lib/scim-1.0/scim-launcher -d -c socket -e socket -f x11
sesho    31504  0.0  0.3  12548  3536 ?        Ss   Feb08   0:02 /usr/lib/scim-1.0/scim-helper-launcher --daemon --config socket --display :0.0 anthy-imengine-helper 24a65e2b-10a8-4d4c-adc9-266678cb1a38
sesho    31506  0.0  0.3  12548  3548 ?        Ss   Feb08   0:01 /usr/lib/scim-1.0/scim-helper-launcher --daemon --config socket --display :0.0 anthy-imengine-helper 24a65e2b-10a8-4d4c-adc9-266678cb1a38
sesho     3477  0.0  0.0   2888   808 pts/0    R+   18:04   0:00 grep scim
```

i think that if scim is working properly then you dont have to worry
just hide the extra icon

---

