---
title: "Make an executable file"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by finwe on 2006-09-18
Hi,
I'm trying to install Ampl (a mathematical optimization program).

I followed instructions from this site, [http://www.ampl.com/DOWNLOADS/index.html#Unix](http://www.ampl.com/DOWNLOADS/index.html#Unix), which looked like this:

"The downloaded file must be decompressed by gzip to produce a file named ampl. This file must be made executable, by a Unix command such as chmod +x ampl, after which it may be executed from any directory in your search path."

However, the chmod command doesn't seem to work since i get this error-message:

mange@mange-desktop:~/Optimering$ chmod +x ampl
mange@mange-desktop:~/Optimering$ ampl
bash: ampl: command not found

](*,) 


I hope someone can help me with this!

Regards

---

### Post by buffy^ on 2006-09-18
you need to enter the full file name.

---

### Post by bensexson on 2006-09-18
The directory you are in is not in the path.  You need to run the command like this:
./ampl

---

### Post by finwe on 2006-09-18
> **bensexson said:**
> The directory you are in is not in the path.  You need to run the command like this:
./ampl

Thanks, that made it possible to run the file :)
Is it possible execute the script (or whatever it is) without the './' in front? And what exactly was chmod needed for in this case?

---

