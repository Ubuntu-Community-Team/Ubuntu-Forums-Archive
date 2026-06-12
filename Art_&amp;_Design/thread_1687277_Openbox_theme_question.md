---
title: "Openbox theme question"
date: 2011-02-13
forum: Art &amp; Design
---

### Post by ufuser1 on 2011-02-13
Hello, I'm hoping Im posting this in the right place.
Is it not possible to have a titlebar button raised and have a border around the raised bg at the same time?I'm saying this because No matter what I do or what I change in the themerc It will either have one of those but never both at the same time. This was achievable in windows using blackbox, but I'm wondering why its not working with openbox which are supposed to be extremely similar.

---

### Post by urukrama on 2011-02-13
From the [Openbox Documentation]("http://openbox.org/wiki/Help:Themes#Border"):

> **Border **

Borders can be used on both solid and gradient textures. Valid options for the border are Flat, Raised and Sunken. When a border is not specified, Raised is assumed.

Flat, by default, means no border at all. To add a flat solid border, use Flat Border. When using a flat border, the texture must be accompanied by a border color. 

Example: 
```
window.active.button.unpressed.bg: Gradient Vertical Flat Border
window.active.button.unpressed.bg.border.color: #3d4c5a
```

Raised and Sunken have two bevel options available to them. By default, a bevel is drawn around the very outside of the texture. If Bevel2 is specified, then the bevel is drawn slightly in from the edge. This can be used to animate button presses/toggled states. 

The strength of the bevel highlights can also be determined by the theme, by using the highlight and shadow fields: 

The highlight field specifies the strength of the light bevel. It is a value above or equal to 0, where 0 makes no highlight at all, 256 makes the highlight color 100% brighter, 512 makes the highlight color 200% brighter, and so on. The default highlight is 128 (which is a 50% increase in brightness). 

The shadow field specifies the strength of the dark bevel. It is a value between 0 and 256, where 0 makes no shadow at all, and 256 makes a completely black shadow (100% decreased brightness). The default shadow is 64 (which is a 25% decrease in brightness). 

Example: 
```
window.inactive.button.disabled.bg: Gradient Diagonal Raised
window.inactive.button.disabled.bg.color: rgb:50/54/58
window.inactive.button.disabled.bg.colorTo: black
window.inactive.button.disabled.bg.highlight: 128
window.inactive.button.disabled.bg.shadow: 64

window.inactive.button.toggled.pressed.bg: Gradient Diagonal Raised Bevel2
window.inactive.button.toggled.pressed.bg.color:    rgb:50/54/58
window.inactive.button.toggled.pressed.bg.colorTo:  black
```


In other words, unless you use *Flat border*, *raised* is assumed whenever you use *border*.

---

### Post by ufuser1 on 2011-02-14
> **urukrama said:**
> From the [Openbox Documentation]("http://openbox.org/wiki/Help:Themes#Border"):

In other words, unless you use *Flat border*, *raised* is assumed whenever you use *border*.

I dont want just a black border, I want a raised button with a black border. Now That I've look close enough at the documentation I dont think its possible. For some reason raised is classified as a border so I can't even have both at the same time. I might be wrong though but I tried all possible combinations ushc as: Solid Raised flat border;Solid Raised border; Border flat raised border and so on..

---

