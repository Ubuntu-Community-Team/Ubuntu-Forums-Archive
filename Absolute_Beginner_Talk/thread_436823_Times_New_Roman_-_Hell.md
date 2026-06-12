---
title: "Times New Roman - Hell"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by JacobRogers on 2007-05-08
I installed "Easy Ubuntu" and it said that it had "many popular Microsoft fonts" in it.  So anyways, I opened a word document I've been working on in Open Office (it was first created in MS Word on my Mac).  The font thing said it was in "Times New Roman".  But it looked a little weird, but I just went with it.

So I typed up about 9 pages and then I mailed it to myself on the Mac to print it out.  But when I opened it on the Mac it only came to like 6 pages.  So I don't think I was really using Times New Roman on my Ubuntu machine.  This made me sad because I had to very quickly pull 3 pages out of thin air.  

So how can I get Times New Roman to actually work on my ubuntu computer?

---

### Post by srt5 on 2007-05-08
That sounds a bit strange. I'm not a Mac user myself but the way I got Times New Roman font working on my Ubuntu laptop was by opening up a terminal window and typing

```
sudo apt-get install msttcorefonts
```

which gets the true type fonts used in Microsoft applications. I'm not sure if easy ubuntu already did this for you, but it is probably worth a shot since It worked first time for me. I hope this answers your question, if not post back and I'm sure that someone here will have an answer for you :)

Edit: For the purposes of just printing the document out, OpenOffice.org exports into PDF format which should look the same on whichever platform you are viewing it on, but it's still much easier to try and solve the font problem that you have on Ubuntu.

---

### Post by JacobRogers on 2007-05-08
Thanks that worked, I was able to see "Times New Roman" as one of the fonts in the pull down menu of Open Office, and it looked right.  After having to write so many papers I can easily tell what Times New Roman looks like.

Thanks again.

---

### Post by kstella on 2007-05-10
I was looking for answers to a similar question. Thanks, I'll try this.

---

