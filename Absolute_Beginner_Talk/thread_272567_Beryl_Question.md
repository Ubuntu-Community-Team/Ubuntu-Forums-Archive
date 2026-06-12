---
title: "Beryl Question"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by Lopsicle on 2006-10-06
...................................................................................

---

### Post by bulldog on 2006-10-06
I haven't the slicest idea you're talking about :D can you be a little more specific on your probelm?

---

### Post by PriceChild on 2006-10-06
> **Lopsicle said:**
> I just installed Beryl and everything seems to be working fine.The problem is that now I cant click on my desktop and my right hand numbers panel is not working.Is this normal or have I messed up somewhere?I reccomend a reboot.

Could work, could not... let us know.

---

### Post by arsenic23 on 2006-10-06
It is possible that the faq you used had you add this line of code somewhere:
```
xmodmap /usr/share/xmodmap/xmodmap.us
```

After doing this a lost a lot of keyboard mouse functionality.  More then likely my keyboard is not 100% US standard.  Curantly I'm using this line to replace the above:
```
xmodmap -e "keycode 22 = BackSpace Delete"
```

This fixed most of my keyboard issues, though I beleive I still do not have the 'super' key.

---

### Post by Lopsicle on 2006-10-06
.....................................................................................

---

### Post by bulldog on 2006-10-06
> **Lopsicle said:**
> PriceChild... Ok thanks the reboot got my mouse clicking on the desktop, but still my number keys are not working on the right panel.

arsenic23...Yes it is possible I used that code,obviously Im using a UK settings keyboard so how would I change it back?


Make the .us  .uk I think.

Do CTRL ALT BACKSPACE and login again.

If you set your numlock on doesn't they work again?
[if I'm guessing right you have it about your numeric bloc]

---

### Post by jordanmthomas on 2006-10-06
This may (probably is) a stupid question, but is numLock turned on?

---

### Post by Lopsicle on 2006-10-06
.....................................................................................

---

### Post by Lopsicle on 2006-10-07
...............................................................................

---

