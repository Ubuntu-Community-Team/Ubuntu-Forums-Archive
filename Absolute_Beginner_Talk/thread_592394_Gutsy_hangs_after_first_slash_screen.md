---
title: "Gutsy hangs after first slash screen"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by nathzenki on 2007-10-26
Hi all,

I upgraded to Gutsy several days ago and everthing was OK. Today I can't boot. Everytime I boot I get the first splash screen followed by the 'load' cursor and that's it. I can't get any further.

Three questions. 

1) How can I use recoverymode to find the problem?

2) In the recovery terminal can I remove Gutsy and get back to where I was?

3) If I re-install Fiesty from the CD, will it wipe existing user files such as email, documents etc that are on the installation partition?

This is doing my head in and stopping me from working. Typing this from Windoze.

---

### Post by nathzenki on 2007-11-04
I solved this problem.

Firstly, I think my problems can be sourced to upgrading via the internet rather than the CD ISO.

I basically downloaded the Gutsy ISO on another pc and burnt a disc.

I then booted with the Gutsy CD. Once in the virtual desktop, I copied my /.evolution folder and other files to another drive via the terminal. I had to use chmod to change the permissions so I could do this. 

Once I had everything copied I then did a clean Gutsy install from the CD. After that, I just copied all my stuff back over.

Gutsy has been fine with this install.

:guitar:

---

