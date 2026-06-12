---
title: "How do I get a list of pacakges I have installed since after installing the OS?"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by kevlaur on 2007-12-06
Not just dpkg-query -l
I want a list of what I personally have installed after installing the OS, so that when I upgrade, I can easily write an apt-get script to get my system up to date.  The full list is not good because there might be older packages that the new version of Ubuntu doesnt need.  I dont even want the dependent libs because they will get picked up again automatically, just the ones I choose and clicked on to install.  Is there a way?  If not, is there at least a way to see them ordered by date of installation?  Thanks in advance.

---

### Post by steven0451 on 2007-12-06
I would also like to know this, mostly because I like to try other linux distros then swap back to a production Ubuntu afterwards.
So having a list of what I normally install after the OS is installed would be extremely helpful.

---

### Post by Don Cox on 2007-12-06
Sytem > Administration > Synaptic Package Manager > File > History

-- 
Don Cox

---

### Post by steven0451 on 2007-12-07
> **Don Cox said:**
> Sytem > Administration > Synaptic Package Manager > File > History

-- 
Don Cox
Awesome, thank you! :mrgreen:

---

### Post by kevlaur on 2007-12-07
But I used Adept to install them.  Synaptic history is blank.  *sigh*  
So, dpkg doesnt keep this information?  :confused:
   -Kevin

---

### Post by ptn107 on 2007-12-07
dpkg does keep that information.

From your home folder in a terminal...
```
dpkg --get-selections | grep "install" > list.txt
```
This dumps a list of installed packages to **list.txt** in your home folder.

If you open the file you'll notice that the word 'install' appears on every line.  That's just the dpkg-status.  We can remove it.

To remove the word 'install' from every line:
```
sed -i 's/install$//g' list.txt
```

Your **list.txt** now contains just a list of packages.

---

### Post by Scarath on 2007-12-07
Almost the same as above:

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

### Post by mahiyar on 2007-12-07
From the synaptic package manager if want to draw a text file of the history is there a way?

---

### Post by Joe Moren on 2007-12-07
kevlaur, Check out ' aptoncd ' in synaptics! Joe

---

