---
title: "gnumeric-gtk"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by michael37 on 2007-07-26
What is a difference between packages that I see in Synaptic:

gnumeric-gtk and gnumeric.  

The package descriptions are identical.

I am running 64-bit Ubuntu Fiesty 7.04.

---

### Post by Foxmike on 2007-07-27
I am not sure, but I think they both refer to the same package, but I guess one is there as a transitionnal package (it has been officially renamed, but still there as a link or something).  I am sure you can install anyone and the result will be exactly the same.

---

### Post by michael37 on 2007-07-27
> **Foxmike said:**
> I am not sure, but I think they both refer to the same package, but I guess one is there as a transitionnal package (it has been officially renamed, but still there as a link or something).  I am sure you can install anyone and the result will be exactly the same.

Thanks.  I installed gnumeric (without -gtk) and it works fine.

---

### Post by hardyn on 2007-07-28
gtk allows for theme integration in to gnome and gtk, its probably grey and ugly... gtk will make it look a little prettier.

---

### Post by michael37 on 2007-07-28
> **hardyn said:**
> gtk allows for theme integration in to gnome and gtk, its probably grey and ugly... gtk will make it look a little prettier.

I selected gnumeric-gtk, it automatically deselected gnumeric (non-gtk) and it looks exactly the same...   but then I am not using any dark themes, so I can't really tell.

---

### Post by michael37 on 2007-07-30
Oh.  What a pleasant surprise.  I just discovered that gnumeric-gtk CANNOT operate on XLS files.  Upon opening, gnumeric-gtk reports "unsupported file format".

Of course, gnumeric-gtk description forgets to mention this little detail:

> 
The following formats can be imported and exported:
 * Microsoft Excel (tm) 97/2000/XP (.xls)
...


Uninstalled gnumeric-gtk and installed regular gnumeric back.  XLS file format works again.

---

