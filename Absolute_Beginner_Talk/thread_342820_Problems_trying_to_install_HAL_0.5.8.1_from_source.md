---
title: "Problems trying to install HAL 0.5.8.1 from source code"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Alveric on 2007-01-20
Hi there

OK, so I downloaded HAL 0.5.8.1 from the website, to try to install it to see if it sorts out the problems I have been having with gnome power manager under Edgy (separate matter).

I downloaded it, extracted it to a new folder in my Home folder and ran the first of the series of shell commands for preparing and installing it, as follows:

user@linux:~$ cd ~/hal-0.5.8.1
user@linux:~/hal-0.5.8.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Now, the first time I did this I had a look to see what compilers I had installed (yes - I hadn't realised I don't get one installed by default).

So I went to Synaptic and installed gcc-4.1 and all recommended packages.

Deleted all folders relating to this matter, extracted and ran ./configure again and got the same error.

Synaptic says gcc is installed, but if I run

user@linux:~$ gcc

I get

bash: gcc: command not found

PLEASE can somebody handhold me through this and I promise to stop asking stupid questions.

Thanks in advance,

Al.

---

### Post by poningru on 2007-01-21
> **Alveric said:**
> Hi there

OK, so I downloaded HAL 0.5.8.1 from the website, to try to install it to see if it sorts out the problems I have been having with gnome power manager under Edgy (separate matter).

I downloaded it, extracted it to a new folder in my Home folder and ran the first of the series of shell commands for preparing and installing it, as follows:

user@linux:~$ cd ~/hal-0.5.8.1
user@linux:~/hal-0.5.8.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Now, the first time I did this I had a look to see what compilers I had installed (yes - I hadn't realised I don't get one installed by default).

So I went to Synaptic and installed gcc-4.1 and all recommended packages.

Deleted all folders relating to this matter, extracted and ran ./configure again and got the same error.

Synaptic says gcc is installed, but if I run

user@linux:~$ gcc

I get

bash: gcc: command not found

PLEASE can somebody handhold me through this and I promise to stop asking stupid questions.

Thanks in advance,

Al.

hehe just install build-essential

---

### Post by Alveric on 2007-01-21
Thanks for that - I missed the whole build-essential thing.

Question (my promise to stop asking stupid questions will kick in when I successfully wrap up this thing, I promise).

./configure seemed to run fine, but when I type make I get

make: *** No targets specified and no makefile found. Stop.

I tried sudo make (just to be sure) and got

make: *** No targets specified and no makefile found. Stop.

Now, I checked the folder and there is a Makefile.am and a Makefile.in in there.

Any suggestions (cos someone might read this thread in the future and my ignorance may help them :wink: )

Thanks,

Al.

---

### Post by Alveric on 2007-01-22
Hello? Err - help?

(the problems I was experiencing with gnome power manager have been written off as not a g-p-m bug, therefore must be a HAL bug - really need to try and fix this)

Cheers,

Al.

---

