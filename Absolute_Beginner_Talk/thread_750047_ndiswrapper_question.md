---
title: "ndiswrapper question"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by mike941 on 2008-04-09
If i have the correct driver for my graphics card can i use ndiswrapper to make linux use the driver from the company that made it?

---

### Post by wieman01 on 2008-04-09
"ndiswrapper" is for networking devices only. See this for more:

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

### Post by esttorhe on 2008-04-09
there's also a way to install flash plugin with ndiswrapper or am i wrong?

---

### Post by wieman01 on 2008-04-09
> **esttorhe said:**
> there's also a way to install flash plugin with ndiswrapper or am i wrong?
NDIS stands for "Network Driver Interface Specification" which should answer your question. Read this for more:

[http://ndiswrapper.sourceforge.net/joomla/]("http://ndiswrapper.sourceforge.net/joomla/")

---

### Post by mike941 on 2008-04-09
I'm trying to install my laptop's wifi driver that i DLed from acer's site but it won't let me install it becuase it says i don't have permission. Couls this be because i am storing it in the temporary folder? As far as i know i did everything else correct. O and i believe i am trying to install the .sys file.

---

### Post by esttorhe on 2008-04-09
are you running the command with the word sudo before it?

---

### Post by scraghty604 on 2008-04-09
u need to install the .inf file that is in the bundle of files dl for your driver, thats the only file u need for NDIS

---

### Post by wieman01 on 2008-04-10
> **mike941 said:**
> I'm trying to install my laptop's wifi driver that i DLed from acer's site but it won't let me install it becuase it says i don't have permission. Couls this be because i am storing it in the temporary folder? As far as i know i did everything else correct. O and i believe i am trying to install the .sys file.
Mike, follow my Ralink tutorial (signature). It will guide you through the process.

---

### Post by mike941 on 2008-04-10
Just to update everyone that's trying to help me: I installed the inf file but so far the wifi's not working. I tried to remove the inf file with ndiswrapper but it said i couldn't. I'm going to read that RAlink guide then try more stuff.

---

### Post by joshrobinson on 2008-04-10
whats this code output
```
ndiswrapper -l
```

---

### Post by mike941 on 2008-04-11
I found the broadcom driver at the acer website and installed the inf file and its in the same folder as everything else that's suppose to be there and it's still not working. What else am i suppose to do? 
Now ndiswrappper -l says: ar5211.sys : invalid driver!
bcmwl5 : driver installed
net5211 : invalid driver!

---

### Post by mike941 on 2008-05-17
BUMP. Is that thing about only needing to install the inf files true?

---

### Post by unutbu on 2008-05-17
No, sometimes ndiswrapper needs other files of the form *.sys or *.bin. However, if you keep them all in the same directory and if the .inf file is called 'driver.inf' then

```
sudo ndiswrapper -i /path/to/driver.inf
```

should work.

If you are still getting this error message:
> Now ndiswrappper -l says: ar5211.sys : invalid driver!
bcmwl5 : driver installed
net5211 : invalid driver! 

you might want to remove all the drivers and try again:

```
sudo ndiswrapper -r ar5211.sys
sudo ndiswrapper -r net5211
sudo ndiswrapper -r bcmwl5
sudo ndiswrapper -i /path/to/driver.inf
ndiswrapper -l

```

Look in /etc/ndiswrapper. You should see one directory with the name of your driver. If the 
`ndiswrapper -i /path/to/driver.inf` command worked, you should see exactly what files ndiswrapper is using.

---

