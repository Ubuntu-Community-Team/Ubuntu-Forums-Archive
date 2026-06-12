---
title: "Quick shrt qstns tht need to be ansrd"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-03-30
What is the repository list?
What is the Source.list ?
What are packages?
Why do Is it recommended that I need to update any of them?
_and let's say, I decide to install a program in Synaptic, will everything needed for that program be in one file? or do I have to go searching for pieces of that file?_

and what are these ? 

    * warty
    * hoary
    * hoary-backports
    * breezy
    * breezy-backports
    * dapper
    * dapper-backports
    * edgy
    * edgy-backports
    * feisty
backports?

I know there's google, but I cant seem to get a stable site that tells you EVERYTHING you need to know about Ubuntu :[

---

### Post by mrmonday on 2007-03-30
The repositories list is stored in sources.list, and is a list of locations for downloading packages. Packages are programs or files for programs. It is recommende you update them, so you have the latest and most secure versions of software. They can also add new capabilitys. If you choose to install a program in synaptic, it will automatically select all the other packages you need to install, so you have no problems. You can also use Add/Remove, which is more user friendly.

As for your list, warty, hoary, breezy, dapper, edgy and fiesty are the codenames for each version of Ubuntu. Fiesty is still in development, and Edgy is the latest stable version. Dapper includes long term support. I can not remember what backports are... I will have a look.

---

### Post by NicoleM on 2007-03-30
i can address part of your question.

i'm not sure of all the things you listed other than the names are versions of ubuntu.  not sure what the backport refers to or in what context that list was originally found.

when you install using synaptic you select an application for installation.  if this application requires any dependencies it will notfy you at this time and say something lik e"hey you want to install this? well you also need this, this, and this...want me to install all of it?" you say "sure go for it" and it automatically does it for you.

i hope that helped a little.

---

### Post by compmodder26 on 2007-03-30
Backports are packages that have been PORTED from the development release BACK to the current release.  In the current instance, backports is a repository that contains packages PORTED from Feisty BACK to Edgy.

In essence, it offers users a chance to have the most recent software available.

edit: that post may not be entirely accurate.  The backports don't have to come from Feisty.  They can just be newer versions of software from anywhere.  For a better explanation look here:[http://www.ubuntuforums.org/showpost.php?p=204596&postcount=1](http://www.ubuntuforums.org/showpost.php?p=204596&postcount=1)

---

