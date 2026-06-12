---
title: "Compiz, Beryl and GLX"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by guitarist549 on 2006-11-16
Ok, so I've seen several people talk about Compiz, Beryl, and GLX on these forums and, aside from having something to do with effects, I have no idea what the are and would like to know whether it's something that I should mess with? I'm currently trying to customize my desktop so I am curious.

---

### Post by Joe_CoT on 2006-11-16
XGL and AIGLX are two different methods of adding 3d effects to xwindow. They're a back-end if you will, which a window manager would use to show those effects. XGL is a hack, which only people whose video cards (ie ati) don't support aiglx use. Aiglx is an extension to xorg, and is included by default in Edgy Eft.

Compiz and Beryl are two window managers that utilize said 3d effect, and they work with either back end. Beryl is a fork of the Compiz project; many people prefer beryl at this point, and there's discussion of including it in Ubuntu+1

The [Beryl Project Website](http://www.beryl-project.org/) includes more information. I recommend their how tos over anyone else's if you plan on setting it up.

---

### Post by guitarist549 on 2006-11-16
> **Joe_CoT said:**
> XGL and AIGLX are two different methods of adding 3d effects to xwindow. They're a back-end if you will, which a window manager would use to show those effects. XGL is a hack, which only people whose video cards (ie ati) don't support aiglx use. Aiglx is an extension to xorg, and is included by default in Edgy Eft.

Compiz and Beryl are two window managers that utilize said 3d effect, and they work with either back end. Beryl is a fork of the Compiz project; many people prefer beryl at this point, and there's discussion of including it in Ubuntu+1

The [Beryl Project Website](http://www.beryl-project.org/) includes more information. I recommend their how tos over anyone else's if you plan on setting it up.

Which would you recommend? I read somewhere that Beryl is less stable, but I don't know.

---

### Post by Joe_CoT on 2006-11-16
I've used beryl without issue. If your video card will support it, I definately recommend aiglx over xgl, as it's in Edgy Eft by default, requires much fewer changes to the system in dapper, and is much, much more reliable.

Compiz or Beryl? up to you. No one's talking about adding *compiz* to feisty fawn.

---

### Post by guitarist549 on 2006-11-16
Ok, well I have run into a problem. On the page it asks me to install XGL or AIGLX if it is supported. How will I know which is supported? I have an nVidia GeForce 7400 card.

---

### Post by Joe_CoT on 2006-11-16
If you have an nvidia, you can either use the aiglx method, or the nvidia method. Only ati's don't support aiglx

---

