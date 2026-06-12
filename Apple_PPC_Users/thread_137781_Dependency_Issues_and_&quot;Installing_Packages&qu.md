---
title: "Dependency Issues and &quot;Installing Packages&quot;"
date: 2006-02-28
forum: Apple PPC Users
---

### Post by jelyon on 2006-02-28
First, I have successfuly installed Kubunto on an OldWorld G3. But this has been my typical computing experience with Kubuntu so far:

-  Power on the box

-  Boots, and loads KDE, and I login.

-  Before it gets the desktop fully loaded (and Toolbar or menu bar, however
it's known in the KDE world), it kills KDE, and returns to the text based
Ubuntu Configuration. It tells me it's "Installing Packages."

At 5% it fails. Over on the 4th console, it shows:

The following packages have unmet dependencies
Libesd-alsa0: conflicts: libesd0 but 0.2.36.1ubuntu5 is to be installed.

I've gone through apt-get -f upgrage and apt-get -f install, to no avail.

The odd thing is that for a while, yesterday, it was working fine, until I decided to install mysql server. That broke it again, and brought back some mysql dependencies (again!) which I solved with a "sudo apt-get remove mysql-common". The libesd0 issues remain, however.

I even tried swearing at it with the strongest curse words I know, some even in French.

My concern, aside from getting beyond this show stopper, is that any time I
install or remove some package, that I'll end up with a system that isn't
useful because of these dependencies. I thought the package managers were
supposed to, you know, manage dependencies?

Is there something I'm missing, or something stupid I'm doing? 

I'm always ready to admit to my own stupidity.

---

### Post by Xian on 2006-02-28
Well, it's been a while and you don't have a response (and I don't know from your description what the problem is either), so perhaps you could post something relevant from your 'apt-get -f install' command. From what you are illustrating it sounds like a conflict problem but I don't understand why it is not be resolved via apt.

---

### Post by sarcasticfrench on 2006-03-09
Well, I can't say I actually know the answer, but here are a couple of things you could try. If after it fails you are able to type, try typing "startx". That should start the GUI back up, but then of course you could just end up right back where you started. If it just totally freezes, you could try pressing ctrl-option f1, which should take you into the console from which you might be able to do something usefull. In the console you could type "ps -aux | more" to get a list of I've installed quite a few packages, and I haven't had any problems like this, so maybe you should just try reinstalling. I tried to install Opera (which I later found out doesn't support KDE) and then I had to reinstall because I couldn't get into the GUI (graphical user interface), and the console was not working.

---

