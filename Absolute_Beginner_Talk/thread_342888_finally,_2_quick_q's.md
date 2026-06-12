---
title: "finally, 2 quick q's"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by eschmidt90 on 2007-01-20
So, now that I finally managed to install ubuntu, I am tryinng to install a c/c++ IDE

I tried to download kdevelope, but the add/remove tool says there is conflicting software

what conflicting software?!?!?!?!?

I have no idea what this thing was talking about

so I decided just to go with a text editor and gcc, which was already installed on my machine

the gcc command is recognied, but when I try to compile a simple "hello, world" program, I get the error:

"stdio.h, file not found"

what's going on here?

secondly, is there any way to get support on ubuntu for my apple airport extreme wireless card?

any help appreciated

TIA

-Erik

---

### Post by zaratustra on 2007-01-20
> **eschmidt90 said:**
> So, now that I finally managed to install ubuntu, I am tryinng to install a c/c++ IDE

I tried to download kdevelope, but the add/remove tool says there is conflicting software

what conflicting software?!?!?!?!?

I have no idea what this thing was talking about

so I decided just to go with a text editor and gcc, which was already installed on my machine

the gcc command is recognied, but when I try to compile a simple "hello, world" program, I get the error:

"stdio.h, file not found"

what's going on here?

secondly, is there any way to get support on ubuntu for my apple airport extreme wireless card?

any help appreciated

TIA

-Erik

have glibc? try sudo apt-get install build-essential

---

### Post by meng on 2007-01-20
and if that doesn't do the trick, also install libc6-dev
sudo aptitude install libc6-dev

---

### Post by eschmidt90 on 2007-01-20
I get errors with both of those

---

### Post by zaratustra on 2007-01-20
use Gentoo or at least Sabayon:-) no flame, ubuntu lovers

---

### Post by meng on 2007-01-20
> **eschmidt90 said:**
> I get errors with both of those
Errors with the command itself, or the compilation afterwards?

---

### Post by eschmidt90 on 2007-01-20
errors executing the install commands, as well as errors withthe compilation afterwards

---

### Post by meng on 2007-01-20
Well you'd better tell us what the errors were with the install commands. Obviously if they weren't executed successfully, they wouldn't solve your problem!

---

### Post by eschmidt90 on 2007-01-20
here is the error for the second suggested command:

"No candidate version found for libc6-dev"

here is teh error for the first suggested command:

"Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate"

---

### Post by meng on 2007-01-20
What version of Ubuntu are you using? What architecture?

---

### Post by Lord Illidan on 2007-01-20
It might also be helpful to give us your /etc/apt/sources.list

---

### Post by eschmidt90 on 2007-01-20
I am using 6.10 on ppc

/etc/apt/sources.list - the terminal says this does not exist

---

