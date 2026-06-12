---
title: "Problems with adding package to LaTeX-path"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by janki on 2006-03-24
**Beginner's question:** I want to use a package IEEEtran in LaTeX (it's basically a cls-file called IEEEtran). I found all the other installed LaTeX-packages in the directory /usr/share/texmf/tex/latex/. So I put the file IEEEtran.cls in a sub-directory IEEEtran. But when I try to compile my LaTeX-file with the inclusion of the IEEEtran-package I get the following error:
----
[I]LaTeX2e <2001/06/01>
Babel <v3.7h> and hyphenation patterns for american, french, german, ngerman, b
ahasa, basque, catalan, croatian, czech, danish, dutch, finnish, greek, iceland
ic, irish, italian, latin, magyar, norsk, norsk, portuges, romanian, russian, s
lovak, slovene, spanish, swedish, turkish, ukrainian, nohyphenation, loaded.

! LaTeX Error: File `IEEEtran.cls' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: cls)

Enter file name:[/I]
----

Obviously my LaTeX-path doesn't containt the directory where I placed IEEEtran.cls. How can I update the LaTeX-path so that it finds the cls-file? I have done many searches on web to find the correct way to install a LaTeX-package, but so far nothing that I have been able to use.

Thanks!

---

### Post by Leif on 2006-03-25
This is how I do it : [http://velourfog.blogspot.com/2005/11/how-to-setup-local-texmf-for-latex.html](http://velourfog.blogspot.com/2005/11/how-to-setup-local-texmf-for-latex.html)

---

### Post by janki on 2006-03-25
[QUOTE=Leif]This is how I do it : [http://velourfog.blogspot.com/2005/11/how-to-setup-local-texmf-for-latex.html](http://velourfog.blogspot.com/2005/11/how-to-setup-local-texmf-for-latex.html)[/QUOTE]
Thanks! Works like a charm now.

---

### Post by perigee on 2007-12-11
The only thing u should do is : 

# texhash

to update the latex database

---

