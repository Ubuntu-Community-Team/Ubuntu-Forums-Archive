---
title: "can anyone reccommend a &quot;code traversal&quot; program?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-02-11
On windows, I preferred "Understand for C++". 

With it, one can "surf" code, right click on any token and its usage will show up in a pane to the left.

Is there a similar thing for Linux?

All this gediting is starting to get cumbersome, esp for the bigger code packages.

---

### Post by bvanpelt on 2008-02-11
I'm sure I'll start a religious war, but...

I think what you want is an Integrated Development Environment (IDE). I think the best available IDE for C++ is the MS Visual Studio IDE. SO, when I'm developing in C++, I develop and test under Windows and then port to unix. Under Unix I just use vim & make.

I'm using Java much more heavily now, even for Windows-based apps. For java I like Eclipse the best.

I just don't see Unix-based C++ IDEs that have the power of Visual Studio.

And, I'm open to suggestions!

Brooks

---

### Post by asmoore82 on 2008-02-11
This is the classic arguement:
Some say heavy development is better when relying on a strong IDE because
of the little things it does "for you."
Others, like me, say that IDEs are terrible for exactly the same reason.

That's just philosophy, so the only tangible things that I can offer to this thread are:
1. in gedit, click "View -> Highlight Mode -> Sources -> Whichever You Desire"
2. for ViM, create a ``.vimrc'' file in your home directory with all the customizations you want,
see the vim manual and online vim help for endless possiblities
mine is like this:
```
$ cat .vimrc 
syntax on
filetype on

filetype indent off

set bg=dark
```

---

### Post by shadow_slicer on 2008-02-11
You could try [Anjuta]("http://anjuta.sourceforge.net/"). I think it has the features you need. I have it installed on my Ubuntu box, but I haven't had a chance to try it out. It's in the Ubuntu repositories, so you can check it out.

---

### Post by raul_ on 2008-02-11
Really? I hated Visual Studio. I thought it was the worst IDE ever. Oh well, tastes are tastes :)

I use Geany. It's called an IDE, I just see it as a neat editor with some extra functions. Eclipse is one of the most powerful IDE's, it has lot of support.

---

