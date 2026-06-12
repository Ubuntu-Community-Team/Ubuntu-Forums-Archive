---
title: "Open office Export to pdf problem"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by PreviousN on 2008-02-23
When I export to a pdf, all of the " and - (quotes and dashes) disappear. This means that I can't send my papers to professors, etc when I'm done writing them (because if I don't include quotes I am accused of plagiarism).

I've searched the forums and goggle and can't find reference to this problem at all. The strange thing is that it happens on multiple computers, using different settings.

Any suggestions? -thx :-)

---

### Post by luisito on 2008-02-23
Maybe not the best solution, but have you tried printing to a file and then converting it to pdf with ps2pdf?

(the best solution would be to use LaTeX instead of any type of Office :) )

---

### Post by PreviousN on 2008-02-23
No, I haven't. I'll try it now though...give me a few mins...


EDIT:

Errr..I thought ps2pdf was a program. Turns out its a website. And.I don't really like the idea of having to go to ps2pdf.com every time I want to convert to a pdf. That's not a practical solution.. but thanks anyway.

---

### Post by PreviousN on 2008-02-23
I'm just wondering if anyone else has my problem as well. Is the problem I am having unique?

---

### Post by luisito on 2008-02-23
ps2pdf is a program, and it is very common. It comes with ghostscript. Most people have it installed already.

Try ps2pdf in a console. If it does not work, install ghostscript.

---

### Post by Roger Mudd on 2008-02-23
Could it be a font issue? If you're using a unique font, perhaps OO can't embed it in the PDF.

---

### Post by stoneybroke on 2008-02-23
Hi the answer is go to TOOLS AUTO CORRECT and disable the tick next to DOUBLE QUOTES REPLACE and then replace all your quotes in the document as for the minus sign it must be in the special character set that PDF doesn't understand so try experimenting.

---

### Post by LimCore on 2008-04-02
I have same problem.

It is caused by the fonts.

Using Dejavu * fonts fix this problem...

Reported it as: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/210885](https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/210885)

---

