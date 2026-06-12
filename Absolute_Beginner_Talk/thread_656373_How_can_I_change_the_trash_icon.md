---
title: "How can I change the trash icon"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by jryprt on 2008-01-02
How can I change the blue trash icon in the bottom panel . I have a .png I want to use.

---

### Post by shafin on 2008-01-02
Does changing the **Trash** Icon in **/usr/share/icons/Your Icon Theme/24x24/places** work?

---

### Post by jryprt on 2008-01-02
> **shafin said:**
> Does changing the **Trash** Icon in **/usr/share/icons/Your Icon Theme/24x24/places** work?

No: I go to  /usr/share/icons/Crux/24x24  no trash icons
If I go to /usr/shsre/icons/Human/24x24  or 48x48 in /places
or in /status  there are trash icons 4 or 5 empty & full trash icons 
Witch one do I change if any?

---

### Post by shafin on 2008-01-02
Try changing **/usr/share/icons/gnome/24x24/status/user-trash-full.png** and **/usr/share/icons/gnome/24x24/places/user-trash.png**

---

### Post by freesitebuilder on 2008-01-02
[https://help.ubuntu.com/7.10/user-guide/C/prefs.html](https://help.ubuntu.com/7.10/user-guide/C/prefs.html) has full instructions - quick way to the Theme manager is right-click desktop and choose "change background", then choose the Theme tab.

---

### Post by jryprt on 2008-01-02
> **shafin said:**
> Try changing **/usr/share/icons/gnome/24x24/status/user-trash-full.png** and **/usr/share/icons/gnome/24x24/places/user-trash.png**

Tried it did not work.

---

### Post by shafin on 2008-01-02
Oh,I just Did a bit of research on this thing,and the trash applet seems to use svg's instead of png's,so you'll have to change **/usr/share/icons/gnome/scalable/places/user-trash.svg **and
**/usr/share/icons/gnome****/scalable/**[B]status/user-trash-full.svg

[/B]If you really want to use your png,follow these steps:
move **/usr/share/icons/gnome/scalable/places/user-trash.svg **and
**/usr/share/icons/gnome****/scalable/****status/user-trash-full.svg** to some backup place,so that when you need you can restore them

Then backup and change
**/usr/share/icons/gnome/24x24/status/user-trash-full.png** and [B]/usr/share/icons/gnome/24x24/places/user-trash.png

[/B]**/usr/share/icons/gnome/32x32/status/user-trash-full.png** and **/usr/share/icons/gnome/32x32/places/user-trash.png**

and 
**/usr/share/icons/gnome/48x48/status/user-trash-full.png** and **/usr/share/icons/gnome/48x48/places/user-trash.png**
Does it work?

---

### Post by jryprt on 2008-01-02
> **shafin said:**
> Oh,I just Did a bit of research on this thing,and the trash applet seems to use svg's instead of png's,so you'll have to change **/usr/share/icons/gnome/scalable/places/user-trash.svg **and
**/usr/share/icons/gnome****/scalable/**[B]status/user-trash-full.svg


I changed the .png to .svg  and did the above did not work .

---

### Post by shafin on 2008-01-02
Can you change the png's from the gnome icon theme's 22x22, 24x24 and 32x32 folders also?

---

### Post by jryprt on 2008-01-02
> **shafin said:**
> 
]If you really want to use your png,follow these steps:
move **/usr/share/icons/gnome/scalable/places/user-trash.svg **and
**/usr/share/icons/gnome****/scalable/****status/user-trash-full.svg** to some backup place,so that when you need you can restore them

Then backup and change
**/usr/share/icons/gnome/24x24/status/user-trash-full.png** and [B]/usr/share/icons/gnome/24x24/places/user-trash.png

[/B]**/usr/share/icons/gnome/32x32/status/user-trash-full.png** and **/usr/share/icons/gnome/32x32/places/user-trash.png**

and 
**/usr/share/icons/gnome/48x48/status/user-trash-full.png** and **/usr/share/icons/gnome/48x48/places/user-trash.png**
Does it work?

Ok I change them in 16x16 - 22x22 - 24x24 - 32x32 
There is not a /usr/share/icons/gnome/48x48/status/user-trash-full.png and /usr/share/icons/gnome/48x48/places/user-trash.png 
to change. Still did not work , I did see the icons changed in 16x16 - 22x22 - 24x24 - 32x32 area (the 4 or 5 in each area).

---

### Post by jryprt on 2008-01-03
I changed all the .png in 
/usr/share/icons/gnome/16x16 - 22x22 - 24x24 - 32x32/status & places
/usr/share/icons/human/16x16 - 22x22 - 24x24 - 48x48/status & places
changed all the .svg in 
/usr/share/icons/gnome/scalable
/usr/share/icons/human/scalable
all trash icons in these folders have changed to my icon but the same blue trash icon is still there , bottom panel on the right .

---

### Post by jryprt on 2008-01-03
When I change to Human theme, The trash icon has changed to my icon ,
but when I change back to Crux theme is blue trash icon is back.

---

### Post by jryprt on 2008-01-03
> **jryprt said:**
> I changed all the .png in 
/usr/share/icons/gnome/16x16 - 22x22 - 24x24 - 32x32/status & places
/usr/share/icons/human/16x16 - 22x22 - 24x24 - 48x48/status & places
changed all the .svg in 
/usr/share/icons/gnome/scalable
/usr/share/icons/human/scalable
all trash icons in these folders have changed to my icon but the same blue trash  icon is still there , bottom panel on the right .

I have it but its not the right way. I changed the [ user-trash.png ] &                                
 [ user-trash-full.png ] in
/usr/share/icons/gnome/16x16 - 22x22 - 24x24 - 32x32/status & places
/usr/share/icons/human/16x16 - 22x22 - 24x24 - 48x48/status & places
Than changed the [ user-trash.svg ] & [ user-trash-full.svg ] in
/usr/share/icons/gnome/scalable
/usr/share/icons/human/scalable
doing this changed all the icons in these folders.
after backing up the .png & .svg first .
System>Preferences>Appearance chose crux theme than the customize
button than icons tab than chose human icons .
now I have my icon .
I would like to know where crux theme gets its icon from?

---

### Post by shafin on 2008-01-04
There are some Icons which are not included in the crux theme,they are borrowed from the gnome theme.

And about changing all the other Icons,the other files are mere links to the file you changed,not separate files,if you want  separate icons,you can replace the link by an actual file.

---

