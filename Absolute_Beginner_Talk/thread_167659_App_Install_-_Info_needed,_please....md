---
title: "App Install - Info needed, please..."
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by JL_COG on 2006-04-28
Could someone running Breezy Badger please tell me what is in the command section of properties of App Install? It is under system tools, properties in the command box. Thanks, jl

---

### Post by Qrk on 2006-04-28
The command is 

gnome-app-install

---

### Post by JL_COG on 2006-04-28
Now the error is that i need to be root. seems like an improvement. do you know what else needs to be done for the add applications icon to properly perform? wish i knew how i messed thi up. thanks.

---

### Post by Qrk on 2006-04-28
Use the menu editor (smeg) to edit the launcher, and make sure that it launches with:

```
gksudo gnome-app-install
```

You can type this into a terminal to make sure that it works.

I am not sure if smeg will allow you to edit that part of the menus. I know alacarte will, so you may want to try it.

---

### Post by JL_COG on 2006-04-28
I forgot to thank you before, Qrk, but now i REALLY need to: Thank-you, Thank-you, Thank-you, Thank-you, Thank-you, Thank-you, Thank-you, Thank-you, Thank-you, etc. Now i don't have to re-install. It was kind of you to bother to reply. :) jl

---

### Post by Qrk on 2006-04-29
Your welcome. Can Llamas blush?

---

