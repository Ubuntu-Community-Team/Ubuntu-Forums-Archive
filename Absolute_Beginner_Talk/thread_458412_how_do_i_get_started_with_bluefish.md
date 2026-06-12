---
title: "how do i get started with bluefish"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-05-29
I downloaded bluefish last night, and it opens when I type "bluefish" in the terminal.  However, when I close the terminal it goes off.

How can I get an icon in the top panel to start bluefish?

Also, the bluefish page says it requires gtk version 2.0 or newer.  Do I need to download that too, even though bluefish is already opening?

---

### Post by meng on 2007-05-29
Ordinarily, there would be a bluefish entry in the menu, probably under Applications > Programming (or possibly Applications > Internet). If it's there you can drag (or right-click) to add to the Panel.

---

### Post by Ek0nomik on 2007-05-29
You also can right click on your panel and add a custom item.

You would just type:  "bluefish" in for your command.

---

### Post by GoneWithTheWind on 2007-05-29
That is very cool - thanks!  :)

Do I need to get gtk version 2.0?

Now I've pasted in a bunch of source code, and have the bluefish manual.  Are there any other bluefish manuals or guideline pages around?

---

### Post by meng on 2007-05-29
Anything that was required was installed when you installed bluefish. Such is the beauty of package management.

---

### Post by Ek0nomik on 2007-05-29
Are you just looking for some guides on how to use the program?

---

### Post by Medieval_Creations on 2007-05-29
if you put a & when running any application from the terminal it runs it in the background and you can close the terminal without closing the app too.

Example:
```
bluefish &
```

---

### Post by GoneWithTheWind on 2007-05-29
Thank you very much.

> **Ek0nomik said:**
> Are you just looking for some guides on how to use the program?

Yes.

---

### Post by init1 on 2007-05-29
No, if it works, you don't need to worry about the gtk. I have had times where I tried to install a deb package and it gave a result=1 because of my dependencies. When I told it to ignore the dependencies, it installed and ran fine.

---

### Post by Ek0nomik on 2007-05-29
> **Medieval_Creations said:**
> if you put a & when running any application from the terminal it runs it in the background and you can close the terminal without closing the app too.

Example:
```
bluefish &
```

Sometimes closing the terminal will kill the program too.

I think mozilla dies if you close the terminal.

Regarding Bluefish guides, I would personally just spam Google for some.  That's what I would do.  ;)

---

