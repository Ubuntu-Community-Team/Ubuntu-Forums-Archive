---
title: "ATI installation and libGL.so.1 woes"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by mithbuntu on 2007-10-14
Hello.  I am trying to set up my Ubuntu installation and I am having some trouble installing the video card drivers.

I am following the guide [here](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually) to the letter so please do not refer me to it.

I believe that I do not have the libGL.so.1 file on my computer.   Or at the least, not in the correct /usr/lib location.   I went there and it was absent but I haven't found any info on how to install this file.

Further more to back this claim up, if I try to run fglrxinfo I get this:
```

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

I've been looking for three hours on possible solutions, but nothing has been helping and they only set me back further -- I've killed my X so many times.

---

### Post by mithbuntu on 2007-10-14
I am going to try copying libGL.so.1.2 over to libGL.so.1 and see what happens.

```

 sudo cp /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

```

Either way I am still curious as to why the original method would not work.

**

Well it seemed to have worked.  I guess this is solved.

---

### Post by iLoVe.cF- on 2007-10-14
havnt worked for me yet :S well, ohh my god, this is really annoying :S

---

### Post by mithbuntu on 2007-10-14
Well, if you need help you should post some info on your problem.  It's too much to try and help if I have no idea what is going on specifically.   Just dont forget I have been using nix for like a week :P

---

