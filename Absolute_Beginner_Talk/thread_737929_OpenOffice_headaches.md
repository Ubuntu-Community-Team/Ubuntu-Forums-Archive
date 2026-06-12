---
title: "OpenOffice headaches"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-03-28
I'm trying to view Powerpoint presentations for my upper level physics course, except that I notice that many of the fonts and components to the various equations or symbols are either replaced by an obscure character or missing altogether. Is there a way to install the necessary math characters to be able to view the slides properly?

---

### Post by kpkeerthi on 2008-03-28
Do you have **msttcorefonts ** installed?
Install it  using
```
sudo aptitude install msttcorefonts 
```

You need to have multiverse repository enabled in System -> Admin -> Software Sources

---

### Post by spacefreak86 on 2008-03-28
Yes I do. The majority of the slides have objects created in the equation editor and while some of them work, not all of them do, and to be able to do hw, I kinda need all of them to work.

---

### Post by spiderbatdad on 2008-03-28
Are you using SCIM and Latex input?
You can also right click on the SCIM icon to get an input pad to select symbols from.
Check synaptic for Latex packages.

---

### Post by spacefreak86 on 2008-03-28
Yes, I have LaTeX already on my system, as I use it for laboratory reports and other physics reports.  What is SCIM?

The symbols missing are typically h-bar, the integral (definite and indefinite) and partial derviative symbol, and a few other symbols.

---

### Post by spacefreak86 on 2008-03-28
Mostly solved. Since I'm dual booting, I went ahead and copied all of the fonts from C:/Windows/Fonts folder using the System Settings -> Appearance -> Font Installer in Kubuntu. I realize that's a bit of cheating, but if it got the job done, I'm game.

---

### Post by meindian523 on 2008-03-28
Mostly?What are you still missing?SCIM is Smart Common Input Method.It's enables a common method of input for different languages,etc.(At least,that's how much I know of it)

---

### Post by milton1 on 2008-03-28
you could always beg the person making the slides to learn Beamer. Then the presentation would be a lovely pdf.  :)

---

### Post by spacefreak86 on 2008-03-28
> **milton1 said:**
> you could always beg the person making the slides to learn Beamer. Then the presentation would be a lovely pdf.  :)

I am tempted to ask him to at least make PDF files of the Powerpoint Slides. That might help a bit.

As far as what is missing, I got the h-bar to work, but it still won't show integrals, summations, or the symbol for infinity or aleph. I'm thinking its a problem with the way OOo translates the Microsoft Equation Editor files, but I don't know to be sure.

---

