---
title: "Trying to install but can't due to errors?!"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by nu2this on 2006-06-21
the program I'm tyring to install is gtapecalc-1.1.1 it can be found here:
[http://www.tucows.com/preview/59525](http://www.tucows.com/preview/59525)
This is a tar.gz & I followed the instructions in Aysiu's page [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php) as well as "How To Install Anything In Ubuntu" in [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)  but instead of getting things going I got this in terminal the 1st time I did this Ihad an error that said I needed gtk something I went to Synaptic found it(about 4-5 apps), installed same.
When I tried the 2nd I got the errors listed there went to Synaptic & found an awful lot of things especially for recursives!! now surely it cant't mean install everything! one of the items under data got me some sort of server app(I think) called Roxen3 which I got out of.
So what does those install data-local,install-am,install-recursive mean?
What data,am, or recursive?  What goofy noob thing have I done now?

---

### Post by halfvolle melk on 2006-06-21
It  says you don't have the right permissions to do that. Try 'sudo make install'.

---

### Post by nu2this on 2006-06-21
I did that & the same thing shows up anyone else help. Does having Automatix  installed cause this?

---

### Post by Jasper Houtman on 2006-06-21
Looks like you have a lot of dependencies missing.
Look at the errors and try to apt-get the packages it's reporting by using:

sudo apt-get install packagename

in the terminal.

---

### Post by nu2this on 2006-06-24
It has been a while other things & all. Since then I tried apt-get for the errors,aptitude too & got command not found.

---

### Post by nu2this on 2006-06-24
here's the view from terminal hope this'll help in diagnosing the problem.

---

### Post by nu2this on 2006-06-24
bump

---

### Post by bohboh on 2006-06-24
Try aptitude instead of apt-get. Handles dependancies better.

Edit:Seen that you have already tried.

---

### Post by raptros-v76 on 2006-06-24
you may need the gtk development packages.

---

