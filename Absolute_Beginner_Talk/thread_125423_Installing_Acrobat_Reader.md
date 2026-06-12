---
title: "Installing Acrobat Reader"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by Hereford on 2006-02-03
I downloaded Acrobat7.0 Reader (tar.gz) from the Gnomefiles web page and installed according to directions in /usr/local/Adobe/...etc.  Then I made a symbolic link in /usr/bin to *acroread* in the installed bin directory.  But when I try to execute from the command line it just flashes the Adobe start-up logo for a second and then quits.  What have I done wrong?  Supposing I can get it to run, how would I go about adding this or any other such non-.deb application to the launch panel or desktop?

Thanks.

---

### Post by mcmillan on 2006-02-03
If there's any error messages coming with in the console post them here.

I thought Acrobat reader was in the repositories, just make sure you've enabled extra ones. If you don't know how to do that go [here]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")

Even if it's not there are alternatives to reader that can work, unless you're really set on Adobe's program. I thought gpdf was installed by default, which works though I think it was bit minimal. I really like evince, which is a bit simpler than Acrobat reader, but still gives decent functionality.

---

### Post by Mitush on 2006-02-05
Well... I seem to have a problem with acroread too and I don't know how do I feel about trying to install one of the standard programs in my brand new Ubuntu (breezy) and failing so quickly. I've installed acroread into /usr/local/packages and the acroread cannot find libXp.so.6 for some reason. libXp.so.6 is in /usr/lib allright, and I've tried putting it into LD_LIBRARY_PATH and using ldconfig and editing that file which ldconfig uses (I don't remember the name). Nothing helped. ldd acroread was showing that it doesn't find libXp.so.6 although it was right there. That kind of unpredictable "hidden" behavior I was usually associating with the other popular OS.

And I did multiverse unsupported options to that sources.list file. It doesn't find acroread anyway. I just feel uneasy about not being able in the future to install some linux package I may need which dosn't show up in the deb lists.

---

### Post by mcmillan on 2006-02-05
Mitush, your problem is seeming a bit above my knowledge right now. I notice there is a package in my repository list called libxp6 Might try reinstalling. Might be worthwhile to try reinstalling it. Sorry to not be of much help.

---

### Post by dinesh01 on 2006-11-08
getting following problem in updating repositories


E: Malformed line 32 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by rlozano on 2006-11-08
this one should be in synaptics, right? you dont have to install it manually, or if ever you do, its pretty straight forward...

---

### Post by bigken on 2006-11-08
just go to add/remove and select office then select adobe ;)

---

