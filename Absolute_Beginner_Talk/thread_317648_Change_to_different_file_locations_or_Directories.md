---
title: "Change to different file locations or Directories"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by BionicBigfoot on 2006-12-12
I feel like an idiot but I am an old - timer and not that familiar with Linux. I have a file saved to my drive under my "Mike" profile (Cedega Time Demo) and I can't switch to that directory using any commands in the terminal to execute the shell file. I feel like a heel. I am so sorry to bother anybody with this.

---

### Post by PriceChild on 2006-12-12
```
cd <<location>>
```
e.g.```
cd /usr/local/bin
```

---

### Post by BionicBigfoot on 2006-12-12
Ok this is where I am and I want to go to a file I saved on my desktop
When I cd it says there is no such file or directory

mike@mike-desktop:/usr/local/bin$ cd /desktop
bash: cd: /desktop: No such file or directory
mike@mike-desktop:/usr/local/bin$

---

### Post by taurus on 2006-12-12
```
cd ~/Desktop
```
Linux/Unix is case sensitive...

---

### Post by dwblas on 2006-12-12
I use MC (Midnight Commander), which is a GUI to browse dirs, change dirs, edit files, change owner, change permissions, etc.  There was a day when you had to key everything in, but today's computers just contain too much stuff to keep track of it all, so a GUI is very helpful.  [http://www.ibiblio.org/mc/](http://www.ibiblio.org/mc/)

---

### Post by mcglnx on 2006-12-12
May be this link could help: [http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by BionicBigfoot on 2006-12-12
I didn't realize that I had to use [COLOR="Red"]home[/COLOR] in the syntax and that did the trick for what I needed. Thanks.

---

