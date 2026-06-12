---
title: "Real Player 10 on AMD 64 Athalon 3700"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by tooCanad on 2007-01-27
Trying to install Real Player 10 on my pc. Its an AMD 64  Athlon 3700. No luck.

The text below outlines my steps:


1.     In terminal:  cd to download directory.
2.     Entered the following:    *chmod a+x RealPlayer10GOLD.bin*

          No issue with this.

3.      Next enter the command:  *sudo ./RealPlayer10GOLD.bin*

4.      Next I get a  password prompt.   I enter the password and the result below is returned:
           
             *unable to execute ./RealPlayer10GOLD.bin: No such file or directory*

Any suggestions?

---

### Post by antiwindows798 on 2007-01-27
Exactly, I would want to know that as well. I also have an AMD processor (X2 and 64 bit of course).

---

### Post by antiwindows798 on 2007-01-27
Here's what I did:

chmod +x RealPlayer10GOLD.bin
.  RealPlayer10GOLD.bin

And that produced the following error:

bash: ELF: command not found

---

### Post by ludepu on 2007-12-20
I too am having a problem. i have amd turion 64. i get error: not supported.

any help would be much appreciated:)

---

### Post by LowSky on 2007-12-20
are you guys running 64 bit ubuntu or x86 ubuntu?

do you really need real player or could helix (a linux modified real player) be good enough?

Helix is in the repositories

---

### Post by dwblas on 2007-12-20
The problem usually revolves around dash vs. bash.  if /bin/sh points to /bin/dash, delete the link and create /bin/bash --> /bin/sh.  I have realplayer 10.0.9.809 installed on my AMD 64 with no problems.  Realplayer must require bash for some reason.  I automatically change the link when first installing so didn't have these problems.  To help others who search for this, please reply with a go or no-go regarding the dash to bash fix.
Edit: Synaptic doesn't come up with a hit for Helix.  What repository would I want to add to find it for 64 bit?
        Also you could probably use "/bin/bash RealPlayer10GOLD.bin" instead of changing the link.

---

