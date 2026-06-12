---
title: "Debian downloads"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by niko663 on 2006-09-23
Hello

I am extremely new to Ubuntu (and loving it). I want to install a maths package from Debian (specifically xmaxima).

I downloaded the package installer but it said Error: Dependency not satisfied: maxima

I assumed this mean't download maxima package installer (which I did) and got a similar message, Error: Dependency not satisfied: libgmp3

Following in a similar vain I downloaded libgmp3. This time package installer said All dependencies are satisfied. Great, I am on my way. 

I pressed install package but I failed to install the package, reason conflicting packages (libgmp3c2).

I am stuck. Can Debian packages normally be installed in Ubuntu? Any help would be greatly appreciated. 

Thanks

---

### Post by christhemonkey on 2006-09-23
Why are you trying to install off debian?

It is in the ubuntu repository.
To install xmaxima:
```
sudo apt-get install xmaxima 
```

---

### Post by niko663 on 2006-09-23
Thankyou

I tried searching for it in add/remove programs and synaptic with no success, hence tried the Debian website.

I will try from the Ubuntu repository

Thanks again

---

### Post by lamego on 2006-09-23
Please be carefull when trying to install .debs from Debian on Ubuntu, you may break your system.

---

### Post by ubuntuuser on 2006-09-23
You will need to enable the universe repository. You probably don't have them enabled and that's why you were unable to find it. Look [here]("http://ubuntuforums.org/showthread.php?t=263339&highlight=enable+repositories") to see how.

---

