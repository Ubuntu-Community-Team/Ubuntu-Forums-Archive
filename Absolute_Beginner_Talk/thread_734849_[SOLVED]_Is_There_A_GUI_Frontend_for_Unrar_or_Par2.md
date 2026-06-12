---
title: "[SOLVED] Is There A GUI Frontend for Unrar or Par2?"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-25
I've learned how do verify and unpack .rar files from the terminal, but after a while, it gets tiresome to have to do it that way, especially when you are used to being able to do it from the context menu within Windows.

So, my question is if there is a GUI frontend for either one of those programs, unrar or par2?  If not, would anyone have any suggestions to make doing those things easier/faster?

Thanks!

FwF

---

### Post by jan quark on 2008-03-25
try this
[http://peazip.sourceforge.net/free-unrar-utility.html](http://peazip.sourceforge.net/free-unrar-utility.html)

---

### Post by hyper_ch on 2008-03-25
there is for rar in gnome and kde... it's the normal archiver in each desktop environment... you just need to add support for rar and other packagers...

---

### Post by Squish on 2008-03-25
what bout 7z?
I hear thats supposed to be the best?

---

### Post by jan quark on 2008-03-25
i guess peazip is somehow based in 7z, isn't it?

or did I misunderstood the info on the page...

---

### Post by FreewareFan on 2008-03-25
Thank you, jan quark, I believe peazip will do fine for the unpacking.  

That just leaves a gui for par2, and I'll be all set.  Anyone have any suggestions for par2 frontends?

---

### Post by billgoldberg on 2008-03-25
I don't know about you guys, but when I installed p7zip-full, I could use the archive manager to unpack stuff (and the right-click "extract here").

I don't think that will have changed from the time I installed it.

---

### Post by FreewareFan on 2008-03-25
> **billgoldberg said:**
> I don't know about you guys, but when I installed p7zip-full, I could use the archive manager to unpack stuff (and the right-click "extract here").

I don't think that will have changed from the time I installed it.

Archive Manager works great for single rar files, no problem.

My experience with it this morning was that it would not unpack all the split .rar files, only the one that was right-clicked on.  That's what started my search for these front-ends that would work.  

Peazip handles the split files fine, so I'm good with that, but still looking for a frontend for par2 now...

---

### Post by kellemes on 2008-03-25
> **FreewareFan said:**
>  but still looking for a frontend for par2 now...

[Pypar2]("http://pypar2.silent-blade.org/")

---

### Post by billgoldberg on 2008-03-25
> **FreewareFan said:**
> Archive Manager works great for single rar files, no problem.

My experience with it this morning was that it would not unpack all the split .rar files, only the one that was right-clicked on.  That's what started my search for these front-ends that would work.  

Peazip handles the split files fine, so I'm good with that, but still looking for a frontend for par2 now...

On my computer it handles split archives without a problem. Unpack the first one, like with winrar on windows, and it will work.

---

### Post by FreewareFan on 2008-03-25
> **billgoldberg said:**
> On my computer it handles split archives without a problem. Unpack the first one, like with winrar on windows, and it will work.

As I said, it would not work that way for .001, .002, etc....     It only unpacked the first file, otherwise I would have used it...   Perhaps there is something different with my installation of Gutsy 7.10, that's all I can think of...

---

### Post by FreewareFan on 2008-03-25
> **kellemes said:**
> [Pypar2]("http://pypar2.silent-blade.org/")

Excellent!  Don't know how I missed it in the repository.  Many thanks!

---

