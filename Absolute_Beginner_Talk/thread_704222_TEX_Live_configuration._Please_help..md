---
title: "TEX Live configuration. Please help."
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by mordi05 on 2008-02-22
My Ububntu/Linux life is about 4 days old, and there are still a lot of things I don't get. I am installing Tex Live/TEXmaker and need some help.

I read at least two howto's, but they get too technical for me as they discuss different options left and right. So all the CLI code throws me off.

I installed all the packages I need via the synaptic p manager. I also installed TEXmaker  easily with the usual package manager.

However I read that I need to configure TEX live, and that it doesn't work out of the box. I've currently run texconfig, but I don't understand the different option that it wants me to choose. Also, do I need to configure something else after I finish texconfig and configure TEXmaker?

If anyone can help, it will be greatly appreciated. I will be in the middel of this config interface until someone does.

---

### Post by ajeetraj on 2008-02-22
I am assuming that you are using Gutsy...but it doesn't really matter what you use. As for me, I am a big fan of Latex and I had few difficulties with it. One of the easiest way to have latex running your system is just to get one of the packages: either TEXLIVE or TETEX, when you just want latex. I would suggest tetex, which is easy to get. Just write this command in the terminal to install it: ```
sudo apt-get install tetex
``` or to just to be in a safe side do this:
```
sudo apt-get install tetex*
```
After this you just open your favourite editor (I would suggest Kile for beginners and certanily better than texmaker :))and then write your latex document and then compile it with "pdflatex": Usually I do this: 
```
pdflatex <file name>
``` It will ask you to correct the errors and stuff but just keep pressing enter and when you are done, then you will see  <filename.pdf> in the directory where your .tex file is saved. 

I hope this helps. I hope that I answered your question and if you have any other problems then just drop a line here :)

Good luck!

---

### Post by Anicka on 2008-02-22
Sorry ajeetraj, but tetex is obsolete, it now only points to texlive.

mordi05: have you installed texlive? Either you use the synaptic GUI or you run in the terminal```
sudo apt-get install texlive
```it will install the basic system for texlive, if you need any language packs or extras you can search for it in synaptic and install it. If you think you need more, but don't feel like specifying what, you can install texlive-full, but that will install _a lot_ of stuff.

---

### Post by ajeetraj on 2008-02-22
well from my personal experience, it doesn't hurt to get the whole texlive as after that if you have to use any package then you are sorted. As for me, I have both tetex and texlive because without one of them, i was having problems with the package beamer (for the presentation in latex). So i would suggest if you want to use latex for a long time then it wouldn't hurt to get the whole thing. It doesn't take a lot of space either :)

to get the whole thing, i used the terminal: 

```
sudo apt-get install tetex* texlive*
```

hope this helps!

---

### Post by Anicka on 2008-02-22
Yes, you are right, the beamer was until recently (in feisty) dependent on tetex, but now it is depending on either tetex or texlive. However, in gutsy, the tetex packages are only there as transitional packages and to give a sym-link to the corresponding texlive-path since not all packages have updated there dependencies.

The main reason why I said that the texlive-full is not necessary is that it is depending on all texlive-packages, such as doc files and language packages for virtually any language you can think of, but if you have no problems with disk space, then of course it's the easiest way.

---

### Post by mordi05 on 2008-02-22
I'm sorry, I should have been clearer.
I have already installed Tex Live, because I read it was the one that was supported now.
The install went smooth as I used the synaptic p manager. I installed ALL TEX Live packages (except for languages), as space is not an issue, and I think it is easier than getting missing packages later.

I am not new to LaTEX. I have used it a lot before, but that was MIKTEX on a Win XP OS.
I mainly write the code when I use LaTEX so an editor with fancy GUI-buttons is not really important. I chose TEX maker because it was there when I searched.

Now again to my problem:
I read in a guide that all my packages needed to be configured AFTER the install. This is what I need help understanding. MIKTEX was just install and go for my part.

So, I have run the "texconfig", but I really don't understand the options in it. Like metafont etc. Also I need help on anything I will need to configure AFTER running texconfig.

EDIT: And yes, I'm using GUTSY.

---

### Post by ajeetraj on 2008-02-22
I am sorry that I was not being so helpful. Can I ask you what exactly are you doing or planning to do after the texlive install? I mean after the install, you are good to go....Can you please be a bit more specific :)

---

### Post by Anicka on 2008-02-22
I've never ran any "texconfig". I think it is automatically run at install. Is your question about the install or are having troubles using tex as well? Have you tried to run it with one of your old files:```
pdftex file.tex
```

---

### Post by ajeetraj on 2008-02-22
well, for me pdflatex <file name.tex> works fine. Well there are errors which it tries to fix it but if I keep pressing Enter then it gets compiled and i have the pdf I want. I have no idea about "texconfig" files, sorry!

---

### Post by Anicka on 2008-02-22
So the only thing that is not working (in respect to the guide you are following) is the texconfig? In that case, I would say problem is solved, because it never existed, or you disagree?

---

### Post by mordi05 on 2008-02-22
As I read on this forum, the tetex distribution comes readily configured after installation, but the TEX Live dist. does not. I understand that I need to run the command "textconfig" which brings up a configuration interface via the terminal. 

The options in this interface I do not understand. It is about metafonts, hyphenation, dvips, rehash and formats. Also when I look at these options I am told by the program to edit the fmtutil.conf file.

As I am new to Linux I am reluctant to do anything unless I am positive it applies in my exact case. Because of this I havn't really tested a lot, since I read that it had to be configured after install.
Because of trail and error I had to re install Gutsy twice on the first day because I followed some commands for different things that I found on forums, but didn't understand. And of course I messed things up that I didn't know existed, and couldn't identify.

I found this:
[http://ubuntuforums.org/showthread.php?t=131507&highlight=configure+tex+live](http://ubuntuforums.org/showthread.php?t=131507&highlight=configure+tex+live)
but can't find any details about the configuration.

As I understand, the whole configuration issue only applies to TEX Live, as tetex apparently was ready after the install.

EDIT: Also, I have only used LaTEX before to create documents and reports. I never had much to do with install and configuration. As I suspect is the case with much software when one moves from MS to Linux.

---

### Post by Anicka on 2008-02-22
That seems like an old thread, possibly before texlive was available in the repos. How did you install it start with, as in the guide or by apt-get/aptitude/synaptic?

---

### Post by mordi05 on 2008-02-22
No, through the System >> administration >> synaptic package manager.
I chose the tex live-full package (which in turn selected all other TEX Live packages).
Then I unchecked all the language packages. Then I clciked apply.

---

### Post by Anicka on 2008-02-22
As I said before I have never manually ran texconfig, but every time when there is any tex-related update, there is some config-script ran automatically.

You say you get error messages when you run tex. Is it anything that worries you among these, can you give an example or have you tried to google some of them if you don't know what they mean?

---

### Post by mordi05 on 2008-02-22
I have done some testing now with a variety of old documents. I get a lot of errors, but I think they are mostly related to the settings in the editor., font mismatches and the like. I think I will be able to sort them out.

The install of the TEX Live distro seems to be good, as the different commands are running. I guess I have been thrown off a bit by reading that I have to configure several files, without actually testing thoroughly first. Again, the constant fear of doing something wrong is quite distracting.

I will try to ask again about more specific errors if I can not find out on my own.
Thank you to all who helped in this topic. I must say I am enjoying learning Linux so far, and the large helpful community appears to be an incredible resource.

---

### Post by ajeetraj on 2008-02-22
I agree :)

---

