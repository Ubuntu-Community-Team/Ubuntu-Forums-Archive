---
title: "Openc++ ????"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Lilla on 2007-06-30
hi,

Can you please tell me how to open the openc++ (c++ compiler)? I am looking for it but still cannot find :(

---

### Post by Lilla on 2007-06-30
:-|

---

### Post by Taliskerd on 2007-06-30
try the OpenC++ [Reference manual]("http://www.csg.is.titech.ac.jp/~chiba/opencxx/html/index.html")
and the command reference link for help.

Or google 'openc++'

---

### Post by loell on 2007-06-30
actually its g++  :)

to install.. in the command line type


```
sudo apt-get install build-essential
```

---

### Post by Lilla on 2007-06-30
I cannot install build-essential because it says that I already have the newest version eventhough I didn't install it yet :(

---

### Post by loell on 2007-06-30
strange, anyhow, now that you have g++, you can compile c++ programs by

ie

```
g++ MyCode.cc -o MyCode 
```

---

### Post by tarek on 2007-06-30
I can compile c++ by just installing g++ not build-essential.

```
sudo aptitude install g++
```

should do it.

---

### Post by Lilla on 2007-06-30
but it still doesn't show what I expect.. I expect a console window like it is when you compile c++ codes in Windows.. 

I've found that there is a dev c++ for linux, but I don't know how to install it correctly after I download it from:
[http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=12148&release_id=46016](http://sourceforge.net/project/showfiles.php?group_id=10639&package_id=12148&release_id=46016)

please help me :(

---

### Post by loell on 2007-06-30
you can copy and paste the output here, so anybody can see the problem.

also if you notice devc++ was dated back in 2001 , most of the C++ projects these days in linux land whether its big or small, 
uses g++ and auto-tools.

---

### Post by tarek on 2007-06-30
The terminal is the console window in Windows. If I'm not mistaken you are talking about Visual Studio, where when you run a c++ program it starts a console window.

In linux just type g++ [nameOfFile].cpp and the output is a.out, to run it enter ./a.out and it'll run like it does in windows.

tk

---

### Post by Lilla on 2007-06-30
oh, finally it works! thanks, tarek :)

---

### Post by tarek on 2007-06-30
> **Lilla said:**
> oh, finally it works! thanks, tarek :)

You're welcome. 

By the way, as loell suggested you can do the following (I modified it a bit)
```
g++ MyCode.cpp -o MyCode.out
```

Which is good if you are compiling more than one file, this way you don't overwrite the output a.out.

tk

---

