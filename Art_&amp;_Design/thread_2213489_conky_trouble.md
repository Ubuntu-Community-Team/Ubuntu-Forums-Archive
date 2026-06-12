---
title: "conky trouble"
date: 2014-03-26
forum: Art &amp; Design
---

### Post by achtyl on 2014-03-26
So I have spent about two hours working on getting conky to work 100% correctly and i am pretty close to where I started. 
Things i want to fix
       conky disapears when I click the go to desktop button. How can I make it stay.
       conky turns white (fixed already)
       conky disapears when I click the desktop

---

### Post by Portaro on 2014-03-26
I think only you need is put this line code on your file ->

> own_window_type override

---

### Post by grumblebum2 on 2014-03-27
When using **own_window_type override**
[COLOR="#FF0000"]disable[/COLOR] argb transparency...
```
own_window yes
own_window_type **override**
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
[COLOR="#FF0000"]#[/COLOR]own_window_argb_visual yes
[COLOR="#FF0000"]#[/COLOR]own_window_argb_value 0
```
Override windows are not under the control of the window manager....own_window_hints are ignored.

[SIZE=3]OR[/SIZE]
 
you could use...
```
own_window yes
own_window_type **normal**
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_argb_visual yes
own_window_argb_value 0
```
Normal windows **are** under the control of the window manager.
So you need to use ccsm to disable shadow to the conky window
```
(any) & !(class=Conky)
```
[ATTACH=CONFIG]251499[/ATTACH]


and also stop the conky window from being minimized when you show the desktop.
[ATTACH=CONFIG]251500[/ATTACH]

---

### Post by achtyl on 2014-03-27
That seams to have fixed it. I tried changing it to override and conky became black. So I used normal with making the settings change in compizConfig.

---

