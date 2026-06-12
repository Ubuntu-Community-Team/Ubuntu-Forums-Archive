---
title: "problem with installing virtualbox"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-10-08
im installing it through the .deb package and installing with gdebi and im at the agreement thing and read it.
how do i say i agree and install it

---

### Post by Kingsley on 2007-10-08
You probably have to type in 'y' or 'yes'.

---

### Post by antisocialist on 2007-10-08
nope didnt work

---

### Post by n3tfury on 2007-10-08
you need to use the tab and <enter> keys to get through the agreement.

---

### Post by antisocialist on 2007-10-08
im getting this when i try to open synaptics to install virtualbox via synaptics
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by bodhi.zazen on 2007-10-08
Yes, you get that error message when you abort the installation

enter this command in the terminal :

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

OK, now to install Virtualbox see here : [http://doc.gwos.org/doku.php/doc:office:virtualbox#ubuntu_host](http://doc.gwos.org/doku.php/doc:office:virtualbox#ubuntu_host)

*Note as pointed out by n3tfury ; you haev to use the tab key to select "yes" or "ok" and then hit the enter key ...

---

### Post by ~~Tito~~ on 2007-10-09
Once you use the tab key once. You can navigate with the arrow keys and select your answer with enter. I got it to work, its pretty cool. You can set the amount of ram it uses and a lot more things.

---

