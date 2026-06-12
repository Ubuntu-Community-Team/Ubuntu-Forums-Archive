---
title: "[SOLVED] latex math question"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2008-02-26
I just installed kile on my new computer and I am trying to compile a file that contains the environment {equation*} in order for my equations not to appear numbered. However I get an error: 
Environment equation* undefined.
 Does anybody know what packages I need to install in order to fix this? (I have already installed the basic ones, meaning tetex-base, tetex-bin, tetex-extra...)

Thanks in advance

---

### Post by Origin415 on 2008-02-26
Have you tried installing texlive-latex-extra, texlive-latex-recommended, and texlive-math-extra?

---

### Post by glennric on 2008-02-26
I think you want
```
\begin{equation}\notag .... \end{equation}
```

Edit: Although
```
\begin{equation*} ... \end{equation*}
```
works for me.  I will figure out which package this is in.

---

### Post by glennric on 2008-02-26
What documentclass are you using?  It depends on that.  If you are using amsart you don't need any other packages, otherwise you need to include amsmath with
```
\usepackage{amsmath}
```

---

### Post by christina_svats on 2008-02-27
By using the package amsmath I did get {equation*} to be recognized, however now it doesn't seem to be able to keep the equations embedded, instead it places them in separate lines.

What puzzles me is that this exact file I was compiling before, without any problems, in both ubuntu 7.04 and ubuntu 7.10 without using the amsmath package and with my equations becoming part of the text flow...

Anyway, if anyone knows how to make them go back into text, please help! The paper is due in a few days!!!!

Thanks!

---

### Post by Whiffle on 2008-02-27
I always just do $$equation$$ for things in the text, and \[equation\] for stuff thats supposed to have its own line...

---

### Post by christina_svats on 2008-02-27
I tried this and it still goes to its own line...What am I doing wrong?

I am writing:
```
...is the mean square error (eq. \ref{err}), where $$d^{p}$$ is the desired-output vector and...
```

---

### Post by Whiffle on 2008-02-27
doh I'm sorry, its single $'s, not double.

---

### Post by christina_svats on 2008-02-27
ok, problem solved, thanks very much!

I still don't get it though, what ever changed from the beginning and it keeps compiling with errors?...
Nevermind, my work is done, thanks again!!

---

