---
title: "Create shortcut to Home Folder on Desktop"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Ghost_Dog on 2008-02-01
I've always had shortcuts to Computer and Home folder on the desktop on previous versions but I am unable to place the Home Folder on the desktop in Gutsy Gibbon (some error about placing something in the same folder).

---

### Post by Het Irv on 2008-02-01
Your desktop is located in your home folder, that is why you are getting the error.  The quickest way I know is though the places menu.  

Edit: learn somethine new every day. See Below

---

### Post by LowSky on 2008-02-01
there is a way, for some reason ubuntu hides them..

in terminal type ```
gconf-editor
```

then scroll through

/apps/nautilus/desktop
check the box  home_icon_visible

---

### Post by emarkd on 2008-02-01
You can have Nautilus place that icon on your desktop for you.  In Synaptic, install gconf-editor.  Run it and under Apps > Nautilus > Desktop there's a checkbox for that functionality

---

### Post by hyper_ch on 2008-02-01
```

sudo ln -s /home/USER/ /home/USER/Desktop/Home

```

---

### Post by froy02 on 2008-02-02
If it does have to be on the desktop you could click on the folder and drag it to either the top or the bottom tool bar. It is just as easily accessible as the desktop.

---

### Post by maximilion on 2008-02-08
> **hyper_ch said:**
> ```

sudo ln -s /home/USER/ /home/USER/Desktop/Home

```

I *love* your sig :) :D

---

### Post by stchman on 2008-02-08
> **Ghost_Dog said:**
> I've always had shortcuts to Computer and Home folder on the desktop on previous versions but I am unable to place the Home Folder on the desktop in Gutsy Gibbon (some error about placing something in the same folder).

Use the mouse to drag the home folder from Places menu.

You can also bring up Nautilus and highlight your home folder and use the middle mouse button and drag it out to your desktop.

---

### Post by hyper_ch on 2008-02-08
> **maximilion said:**
> I *love* your sig :) :D

I didn't come up with any of those... and it's not my usual sig. My usual sig is an image with random quotes.

---

### Post by PhrygianCat on 2008-03-11
Is it possible to make a shortcut on the desktop and make it so that any user logging to this computer be able to see & execute it? I'm a noob and am thinking about doing something similar to putting shortcut in the c:\documents and settings\all users\desktop folder. Thanks for the help.

---

### Post by Omnios on 2008-03-11
k look in menu 
 
/Applications // System Tools // Configuration Edotor ..
 
This launches the editor.
 
In the editor choose 
 
apps 
nautilus
desktop.
 
Now on the right there will be names and values, check off what you want displayedon the desktop. Also volumes visable will show all mounted partitions on the desktop.
 
Edit: If usefull please give a thanks.

---

### Post by xgermx on 2008-05-17
Thanks! Being a windows "power user", gconf-editor is just the thing I needed to tweak my desktop.:KS

---

