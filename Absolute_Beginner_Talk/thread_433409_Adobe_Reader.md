---
title: "Adobe Reader"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by funzero on 2007-05-04
I have forms that are pdf files.  I am able to fill in blanks in windows but not in ubuntu.  any ideas what the problem is?

---

### Post by imdidactic on 2007-05-04
Use [PDFedit]("http://sourceforge.net/projects/pdfedit").  It's an open source program that will allow you to change the entire document, let alone fill in the blanks.

---

### Post by teddybairs1 on 2007-05-04
Can you open the forms with OpenOffice?

Are you using Adobe Reader (acroread), Evince, or KPDF? Adobe Reader doesn't come preloaded, you have to get it either from the medibuntu repos or by running alien on the Adobe .rpm package.

---

### Post by teddybairs1 on 2007-05-05
Hey, just checked it. Install the acroread-plugins package. It will give you the ability to edit forms in pdf (at least that's what it tells me).

---

### Post by funzero on 2007-05-05
I use adobe reader & evince.  Cannot open in open office, all I get is characters.  where is the plug-in info?

---

### Post by teddybairs1 on 2007-05-05
Assuming you downloaded acroread from the medibuntu repos, search in Synaptic for acroread. You should turn up acrobat reader as well as all related packages including acroread-plugins and the mozilla plugins for acrobat reader.

---

### Post by funzero on 2007-05-05
Thanks, works perfectly now.

---

### Post by teddybairs1 on 2007-05-06
No problem.

---

