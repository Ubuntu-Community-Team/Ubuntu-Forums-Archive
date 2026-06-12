---
title: "graphic service off, terminal qccess only"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by peterj on 2006-11-02
Hi,
I was messing about in admin-services and I turned off graphics at start-up. Immediately the box went into tty and I can't un-do the setting. the command servicesgives me a warning 'gtk-warning can't open display.
thanks in advance,
Peter

---

### Post by chuckyp on 2006-11-02
Make sure you are booting in multiple user mode.  Use update-rc.d to add gdm back to the runlevel you want.

---

### Post by peterj on 2006-11-02
hmm, Im kinda new to this, I can sudo -i for root, but when I key in that command im not sure on  the coding.

---

### Post by NeoLithium on 2006-11-02
```
sudo update-rc add gdm defaults
```

---

### Post by peterj on 2006-11-02
update-rc.d: /etc/init.d/add: file does not exist

---

### Post by NeoLithium on 2006-11-02
My bad for it being so late. Here is what you REALLY should type.
```
update-rc.d -f gdm defaults
```

I guess it's bed time for me ;)

---

### Post by peterj on 2006-11-02
noo! dont go to bed pleease lol!

it says start-up links for etc/init.d/gdm already exist

---

### Post by peterj on 2006-11-02
apparently he went to bed.. anyone else? I really need it to work urgently!!

---

### Post by NeoLithium on 2006-11-02
Are you able to run ```
/etc/init.d/gdm start
```

---

### Post by peterj on 2006-11-02
yes!! now it says when i tried to access services the configuration could not be loaded; i think i deleted them using the updat command.

---

### Post by NeoLithium on 2006-11-02
gdmsetup should be able to work now; and will help you get it up and running (I HOPE :)

---

### Post by peterj on 2006-11-02
sorted, thanks a million, really appreciate it.

---

### Post by NeoLithium on 2006-11-02
No problemo :) Sorry it took a little while; but I'm glad you're all up and running again!

---

### Post by peterj on 2006-11-02
on a kind of irrelavant subject I got rid of windows and im loving it! you dont realize how little use it has till its gone. I hope eventually Ill have learnt enough to give back to the community.
Thanks again.

---

