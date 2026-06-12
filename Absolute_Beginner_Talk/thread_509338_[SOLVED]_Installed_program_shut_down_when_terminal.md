---
title: "[SOLVED] Installed program shut down when terminal is closed"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by srhue on 2007-07-25
I installed a few programs using the sudo apt-get command (such as checkgmail and a firewall program), however when I close the terminal, the program that is running closes too. How can I keep the program running after I close the terminal? Does this have to do with the programs location or user priveleges? This is a Feisty 7.04 install by the way.

---

### Post by Mornedhel on 2007-07-25
I suppose you are running the program from within the terminal. In that case, the program is ran as a child of bash (the command line). When bash is terminated, every child of his is terminated as well. This is normal. What you would want to do is run them as you normally would, but add a & (ampersand) sign at the end of the commands you want to keep running once the terminal is closed. This asks bash to have them run in the background, in a subshell. The & * has * to be at the end of the line, otherwise it may have another meaning.

---

### Post by srhue on 2007-07-25
Thank you Mornedhel for the info. Is it correct to start these programs from the terminal or is there a better way to start them so they won't be a child of Bash?

---

### Post by eentonig on 2007-07-25
You could start them from the starter promt. Type <Alt>+<F2> and enter the command.

Or you could create a startup script for them (if you want them to start everytime you start the computer.) and activate that under Administration\Sessions

---

### Post by Mornedhel on 2007-07-25
It is correct to start them from the command line, yes, but if you don't need the console output (and you don't, since you wanted to close the console), eentonig is correct.

---

### Post by Malta paul on 2007-07-25
Its not a bad idea to install your packages (programmes) using System >Administration > Synaptic Package Manager. As it will also install for you with any dependent programmes that may be required. You have a large choice and a short description also.
 Check out: [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
 Have fun and post again if you need help :guitar:

---

