---
title: "grub menu - help"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-07-02
ok guys, in the grub menu .. it shows 4 linux kernel (sp) and windows xp.. now i used only the latest kernel and xp.. how can i hide rest of them.. and can i give them whatever name i want because it looks silly with so amny niumbers ..thanks gusy

---

### Post by splintercellguy on 2007-07-02
You could try using GrubED: [http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

---

### Post by Seisen on 2007-07-02
Post your grub menu if you can.

---

### Post by sebast on 2007-07-02
Yeah, pretty easy to do actually

here is the easiest way:

In the command line type ```
sudo gedit /boot/grub/menu.lst
```

It will open the file that stores the different menu items when you boot in administrator mode so you can edit it (you should probably make a backup file before in case you break it).

In the file, you'll see the different Operating system listed, you can put the "#" before things that you don't want (it will put the items in comments).

You can also change "title" attribute to whatever you like to give prettier names.

Hope this helps

---

### Post by bodhi.zazen on 2007-07-02
Actually, why don't you go under synaptic and remove your old kernels ? Save one old one "just in case".

Then, if you don't want to see the old kernel, comment it out :

[http://users.bigpond.net.au/hermanzone/p15.htm#hide_items](http://users.bigpond.net.au/hermanzone/p15.htm#hide_items)

---

### Post by testube_babies on 2007-07-02
> **sebast said:**
> 

In the command line type ```
sudo gedit /boot/grub/menu.lst
```



I would use "**gksudo** gedit /boot/grub/menu.lst" if you don't want to potentially ruin your user account:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by sebast on 2007-07-03
> **testube_babies said:**
> I would use "**gksudo** gedit /boot/grub/menu.lst" if you don't want to potentially ruin your user account:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Well, I learned something new! Glad you pointed this, this information is not well known I think.

---

### Post by HunkieChan on 2007-07-03
> **sebast said:**
> Yeah, pretty easy to do actually

here is the easiest way:

In the command line type ```
sudo gedit /boot/grub/menu.lst
```

It will open the file that stores the different menu items when you boot in administrator mode so you can edit it (you should probably make a backup file before in case you break it).

In the file, you'll see the different Operating system listed, you can put the "#" before things that you don't want (it will put the items in comments).

You can also change "title" attribute to whatever you like to give prettier names.

Hope this helps

that helped bro, i knew it but i needed clarity to do it.. i was unsure..thankgs guys

---

