---
title: "Install a New Font"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Crumpets and Jam on 2008-02-22
I've downloaded a few new fonts for my system that I'd love to be able to use. In Windows, I had to add them to a fonts folder. Do i have to do something similar in Ubuntu?

Please can you help me? Cheers.

---

### Post by banewman on 2008-02-22
Yes, you add the new fonts to a folder.
If you open the control center, click fonts, then click the help button there is simple instructions.
:)

---

### Post by forestpixie on 2008-02-22
believe there are a few ways - I make a hidden folder in my /home - .fonts

then put the fonts in that and run

sudo fc-cache -f -v

seems to work ok for me

---

### Post by Crumpets and Jam on 2008-02-22
> **forestpixie said:**
> believe there are a few ways - I make a hidden folder in my /home - .fonts

then put the fonts in that and run

sudo fc-cache -f -v

seems to work ok for me

I don't seem to have a .fonts folder (yes, I know it is hidden). The closes thing I have is a *.fontconfig* folder.

Any ideas?

---

### Post by forestpixie on 2008-02-22
indeed - as I said I make one :)

- make sure you put the . in front so it's a hidden folder

---

### Post by Crumpets and Jam on 2008-02-22
> **forestpixie said:**
> indeed - as I said I make one :)

- make sure you put the . in front so it's a hidden folder

Ah, thanks for that mate.

---

