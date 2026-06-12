---
title: "Number of PATH entries?..."
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by goodrich on 2005-11-22
Is there a maximum number of path entries you can have in Linux? I have /bin, but i would like to add /bin/apps, /bin/other, /bin/more...etc...

Is there a disadvantage or limit to doing things this way?

Thanks

---

### Post by unixfudotnet on 2005-11-22
You can have a ton. Not sure of an exact number, but I have had some huge environment variables (what path is) and have populated path with a ton of paths and never ran into a problem.

There is nothing wrong with adding your own extra paths to $PATH. If you desire it, do it. It will be ok :)

Realize though, that when searching for a program (without absolute path), the order of directories in your PATH variable will be searched from left to right.

So, if you are looking for a program called "monkey" and your path was "/usr/local/zoo:/usr/local/animal_hospital:/usr/local/showbiz", it would search /usr/local/zoo/monkey, /usr/local/animal_hospital/monkey, /usr/local/showbiz/monkey and whichever one exists and is executable first will be executed.

---

