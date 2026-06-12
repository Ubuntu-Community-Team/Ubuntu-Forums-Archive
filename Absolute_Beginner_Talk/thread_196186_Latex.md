---
title: "Latex?"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by Trurl on 2006-06-13
Hi everyone,

  What is the recommended LaTex package for Ubuntu? I'm used to MikTex with WinEdt (which I really liked) in XP, but I haven't come across any similar things for linux. Supposing I want to avoid doing all my linux from emacs, is there a good package? 

Thanks for your time!

-Trurl

---

### Post by FryerFox on 2006-06-13
I have the same problem. WinEdt and Scientific Word are great for Windows. There's Kile (an IDE for LaTeX), and Lyx (which takes much of the control away from you to make it simpler). 

Of course, there's also Kate which is a real nice editor once you get the shortcuts down, and it has TeX highlighting.

---

### Post by caldevil on 2006-06-13
kile is the best. Or use texmaker if you don't want to install kde libraries.

---

### Post by Trurl on 2006-06-14
This is a naive question, but...can I use Kile but keep Gnome? Does installing KDE libs imply using KDE or just having the files?

Fryer: Thanks for the suggestions, I'll be checking out Lyx and Kate momentarily.

Thanks,

Trurl

---

### Post by FryerFox on 2006-06-14
[QUOTE=Trurl]This is a naive question, but...can I use Kile but keep Gnome? Does installing KDE libs imply using KDE or just having the files?

Fryer: Thanks for the suggestions, I'll be checking out Lyx and Kate momentarily.

Thanks,

Trurl[/QUOTE]

You're very welcome.

You can use any KDE app and keep GNOME as your desktop. I personally use Kate, KDevelop, KRegExpEditor, Konquest, Kompare, and other KDE apps but have never booted into KDE on this machine.

KDE and GNOME got their act together a few releases ago, and now KDE and GNOME libraries work quite well together. There are a few UI inconsistencies when running KDE apps in GNOME and visa versa - basically slight look-and-feel differences, but nothing major.

---

### Post by harishg on 2006-06-15
Kile is excellent.I tried out lyx recently and it worked very well for smaller documents and was faster than latex once you spend sometime with it.

---

### Post by FryerFox on 2006-06-15
[QUOTE=harishg]Kile is excellent.I tried out lyx recently and it worked very well for smaller documents and was faster than latex once you spend sometime with it.[/QUOTE]

I think Lyx *is* LaTeX (or TeX, at least). It just hides that part from you.

---

### Post by hajk on 2006-06-15
[QUOTE=Trurl]Hi everyone,

  What is the recommended LaTex package for Ubuntu? I'm used to MikTex with WinEdt (which I really liked) in XP, but I haven't come across any similar things for linux. Supposing I want to avoid doing all my linux from emacs, is there a good package? 

Thanks for your time!

-Trurl[/QUOTE]

Two questions really:

1. Which TeX/LaTeX? The current packages in Dapper are based on the tetex
    distribution. However, the maintainer (Thomas Esser) has recently announced
    that he will no longer maintain tetex -- in fact, tetex is already a bit dated.
    Discussions on comp.text.tex show that the TeX/LaTeX community will likely
    move to the TeXLive distribution from TUG ([http://www.tug.com)](http://www.tug.com)). I have myself
    already taken the plunge and installed the TeXLive2005 distribution in my
    /usr/local tree.

2. What editor (or IDE) to use for producing LaTeX documents? This has already
    been answered by others, except that you shouldn't (yet) expect the sort of
    IDE like WinEdt in Linux that you were used to in Windows. You may even lose
    interest in such IDEs once you become more proficient in Linux. 

    You say that you don't care much for learning Emacs -- I can certainly
    understand that, since I use Vim myself.;)  Don't forget that you can also use
    the Gedit editor that comes standard with Gnome/Ubuntu -- it is easy to use
    and has nice LaTeX syntax highlighting. Using it in connection with pdfLaTeX
    would be a good setup.

Good luck!

---

### Post by Trurl on 2006-06-16
Interesting!

I've tried LyX and it's nice but it doesn't teach me basic LaTex (too user friendly) and doesn't read any of my existing .tex files. I'll be trying texmaker and amyedit shortly. 

Three questions back:

1. I've only been introduced to LaTex in an academic context, and I'm not quite sure I understand how the distributions works. In windows, I played around for a long time and eventually got everything work. I didn't realize I was using one type of LaTex over another. What is TexLive vs. tetex? 

2. Supposing I wanted to try kile (or any KDE app): how do I run these within Gnome? 

3. I just tried gedit with a .tex and it opened and highlighted nicely. However, I wasn't sure how to compile (if that's the right word) the tex file into a dvi or a pdf, etc. Any advice would be appreciated. 

Thanks everyone!

Trurl

---

### Post by hajk on 2006-06-16
I think you could benefit from buying one of the many books on LaTeX, I like "The LaTeX Companion" (Addison-Wesley, 2nd Edition 2004). It not only tells you about the many free and commercial TeX/LaTeX distributions for various platforms (Windows, *nix, etc), but also contains a lot of good info on how to produce nice theses and other academic stuff. Most campus bookstores will have it in stock.

Specific to your questions: TeXLive is the granddaddy of distributions, organized by the TeX User Group (or TUG), you can't get a better distribution right now (in my opinion), or a larger one, for that matter. Installing Kile should be done with Synaptic, it takes care of other required packages. And as far as compiling goes: you would first save the edited <your>.tex file; then in a terminal run the command "pdflatex <your>" (without the .tex extension), where you should use the actual file name instead of <your>. There are other commands possible, but at least this one results in a PDF file <your>.pdf, that you can view with a PDF-viewer (like the default viewer Evince, or Xpdf or even Acrobat Reader), and that you can also print directly.

It is customary in the *nix world to do all of these steps separately: editing with Gedit and viewing with Evince can be done by clicking on a .tex or .pdf file; you could also associate running pdflatex with right-clicking on a .tex file (but I can't help you with that).

---

### Post by harishg on 2006-06-17
[QUOTE=Trurl]Interesting!

I've tried LyX and it's nice but it doesn't teach me basic LaTex (too user friendly) and doesn't read any of my existing .tex files. I'll be trying texmaker and amyedit shortly. [/QUOTE]


you have to use the import option and it does a neat job.

Three questions back:

1. I've only been introduced to LaTex in an academic context, and I'm not quite sure I understand how the distributions works. In windows, I played around for a long time and eventually got everything work. I didn't realize I was using one type of LaTex over another. What is TexLive vs. tetex? 

> 
2. Supposing I wanted to try kile (or any KDE app): how do I run these within Gnome? 
If you install it with synaptic it will install the necessary files.

> 
3. I just tried gedit with a .tex and it opened and highlighted nicely. However, I wasn't sure how to compile (if that's the right word) the tex file into a dvi or a pdf, etc. Any advice would be appreciated. 


if you want to produce ps files use 
latex filename.tex 
dvips filename.dvi 

for pdf files
pdflatex filename.tex

---

### Post by dada1958 on 2006-06-18
For some time I thought nothing couldn't beat TeXShop for the Mac. But Gedit is getting closer and closer. I started with this lovely app when I was playing with LaTeX in Hoary, altered the Tag list with my own commands. Then in the times of Breezy I discovered TeXMaker and Kile and I like them, don't understand me wrong. You can define user tags and that's a great thing. But I missed the interactive spellchecker badly.
Now in Dapper, I'm back to Gedit, thanks to two new plugins: External Tools and Snippets I can assign commands to key bindings. See attachments.
Gedit is the front-end editor of my choice, it works amazingly well with TeXLive 2005.

---

