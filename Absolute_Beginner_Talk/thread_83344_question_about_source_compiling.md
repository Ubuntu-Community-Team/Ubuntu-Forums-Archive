---
title: "question about source compiling"
date: 2005-10-28
forum: Absolute Beginner Talk
---

### Post by teaker1s on 2005-10-28
up until now I've followed the readme instructions and with luck and ./configure I've installed some source code the bit that confuses me is when there are no help or read me's how to go about compiling and installing the source? is there a simple bullet proof method and if possible a gui based app? as a couple of source there isn't any clues or script

thanks

---

### Post by John.Michael.Kane on 2005-10-28
This maybe what your looking for [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

also you may need  build-essential package which is in synaptic

---

### Post by az on 2005-10-28
What do you need to compile?

---

### Post by Kyral on 2005-10-28
a good 90% of compiling stuff from source follows this procedure

[LIST=1]
[*]Download the Tarball   
[*]Extract the Tarball   
[*]Change into the directory that the Tarball should have made   
[*]run ./configure   
[*]run make   
[*]run sudo make install [/LIST] Of course its always good to read the README file to find out any quirks with the package.

But ALWAYS try to Apt-Get it first ;P

---

### Post by teaker1s on 2005-10-28
hi guys I've installed several things from source forge and some of them have needed autoconf or automake but others there is no indication of what to use and while the configure comand works on certain source it refuses the make comand. being a little new to this I'm guessing there is source code that will work on some os and other source that either I don't know what to compile it with or it just doesn't like ubuntu. as configure gives no clues.

---

### Post by Kyral on 2005-10-28
Do they come with READMEs?

Thats what I meant about quirks ;P

---

### Post by teaker1s on 2005-10-28
no readme- I've finally found problem the code is offered as source code and I mistakenly thought it would be x86 compile your self for linux or ms
buried in the documentation it's source but for Ms quite why It doesn't state this as i understand it most source can be compiled either for ms or linux with the correct  compiler as they both use x86 processor.
thank you for your help I've emailed the developer asking if he could make it clear before you download it's ms only source

---

### Post by Kyral on 2005-10-28
It actually CAN be MS only source...like if it uses System calls to things that only Windows has, or any number of things really *cough DIRECTX cough*

---

### Post by teaker1s on 2005-10-28
being green to this is there any traits if there is no readme that I can check if it's linux ms or for both?

thanks

---

### Post by Kyral on 2005-10-28
Not unless you examine the source code....or try to compile it ;P

---

