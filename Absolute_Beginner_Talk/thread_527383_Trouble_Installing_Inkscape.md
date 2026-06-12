---
title: "Trouble Installing Inkscape"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Fully216 on 2007-08-16
I was under the impression that Inkscape is available through the repos.  I would rather install it there compared to compiling from source.

I do have the main, universe, restricted, and multiverse repos enabled.

When I try to install it, I get a strange message.  I type $ sudo apt-get install inkscape

And I get the following back:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package inkscape is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package inkscape has no installation candidate

What other package would Inkscape be 'reffered to?'  Any ideas?

---

### Post by annda on 2007-08-16
this is strange... it looks like at this point inkscape isn't in any of the feisty repositories
[http://packages.ubuntu.com/feisty/graphics/](http://packages.ubuntu.com/feisty/graphics/)

you can get the package from here but you will have problems with dependencies:
[http://packages.ubuntu.com/feisty/graphics/inkscape](http://packages.ubuntu.com/feisty/graphics/inkscape)

or you can **temporarily** use the gutsy main repository (mine is: deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy main) - NOT A VERY GOOD IDEA, since some dependencies you install might not be right for feisty. if you want to take that risk, remember to remove the gutsy repository right after install or bad things may happen.

---

### Post by Seisen on 2007-08-16
Try downloading it from the second link that he gave you, then use Gdebi to install and it will pull the dependicies that you need if you need any and if they are available.

---

### Post by steve.horsley on 2007-08-16
Odd - I just installed Inkscape (on Feisty) using Synaptic. I use "Server for the UK" ans my repo in the Synaptic properties.

---

### Post by Fully216 on 2007-08-17
Thanks for everyone's suggestions.  I love the fact people are so helpful here!

I am still not exactly sure what happened with the repos.  Before I was going to go through the list of suggestions offered, I decided to use apt-get install inkscape again to see if it would work.  Low and behold:

"The following NEW packages will be installed:  inkscape"

Looks like the repos were possibly updated?  Still, it was very strange what happened.  I wonder if it was related to this article about the ubuntu servers being hacked.

[http://it.slashdot.org/article.pl?sid=07/08/15/1341224](http://it.slashdot.org/article.pl?sid=07/08/15/1341224)

Again, thanks for all the help everyone.  :D

---

