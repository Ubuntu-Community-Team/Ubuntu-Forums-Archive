---
title: "Install application error : configure error"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Rajith on 2007-03-04
Hi frndz

I'm really a newbie not only in ubuntu but also in linux....
Well , i'm using ubuntu 5.10 .... as my os...
When i completed installation i tried to install and application with extension ,tar.gz..
i successfully extracted that file and open terminal and access that particular folder where i extracted...
i type ./configure.....

It shows c compiler error : configure : error .... like this....
My friend told me to install c compiler from synaptic manager... i installed that via cd ie mark as gcc and installed....

But still its having probs ...
Dont know how to step forward.......
Shall i know wat the reason is ......

---

### Post by annda on 2007-03-04
try installing the build-essential package. you may need more than gcc.

also, have you looked around and made sure the application you are trying to compile is not available in the repositories or somewhere else as a precompiled .deb package?

---

### Post by Rajith on 2007-03-04
repositories or somewhere else as a precompiled .deb package?

I didnt understand wat it is and where did i get these things...
Would you please make it clear.....

---

### Post by annda on 2007-03-04
the first step when you try installing new software is running synaptic. it's in system > administration menu.

then go to settings > repositories and check all options for software sources.

then hit Reload. after synaptic finishes downloading information on installable programs, you can browse or search for the application you need.

if you still can't find it, google for name_of_the_program.deb
if you find it, download to your desktop and double-click the file.

---

### Post by Rajith on 2007-03-04
Hi annda

Would you mean to download directly from net...
Or shall i put that ubuntu cd in to cdrom...

---

### Post by annda on 2007-03-04
go to synaptic first. when you select the sources where your system should look for software, the ubuntu cd is one of them (it's mentioned on the repositories list in synaptic). but remember, the cd only has essential software, the rest of the repositories (software sources) are online. there are literally thousands of programs you can download and install.

as i said, go to synaptic and look around.

---

