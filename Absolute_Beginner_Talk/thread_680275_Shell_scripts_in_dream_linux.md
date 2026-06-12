---
title: "Shell scripts in dream linux?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by aznpride93 on 2008-01-27
how do i run them?

---

### Post by Majorix on 2008-01-27
What is a "dream linux"?

---

### Post by aznpride93 on 2008-01-27
> **Majorix said:**
> What is a "dream linux"?
it's a build of linux thats looks like the mac os
it's pretty cool

---

### Post by LaRoza on 2008-01-27
> **aznpride93 said:**
> how do i run them?

Mark them as executable, put the shebang line in, and run them.

See the notes on [http://ubuntuprogramming.wikidot.com](http://ubuntuprogramming.wikidot.com)

---

### Post by Majorix on 2008-01-27
Example:
[php]#!/bin/bash
#Filename script.sh
#Your script goes here[/php]
```
chmod a+x script.sh; ./script.sh
```

---

### Post by aznpride93 on 2008-01-27
> **Majorix said:**
> Example:
[php]#!/bin/bash
#Filename script.sh
#Your script goes here[/php]
```
chmod a+x script.sh; ./script.sh
```
okay the name of the file is "FretsOnFire"
can you please insert the file name in there for me and make it make sense so i can just copy-paste into terminal?
thnx!

---

### Post by Majorix on 2008-01-27
You have to make sure your terminal's working directory is the same as the folder that contains that file ie Desktop or ~ or whatever. Best is, move the file to your home folder and run the terminal, then do this:
```
chmod a+x FretsOnFire; ./FretsOnFire
```

---

### Post by aznpride93 on 2008-01-27
OOPS! my video card doesn't have glx feature or whatever, so it wouldn't run, thanks for the help though, at least now i know the problem

---

