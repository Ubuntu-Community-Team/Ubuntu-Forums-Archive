---
title: "More newb questions"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by wych77 on 2006-06-27
1.  When I click on the About Ubuntu icon under the System menu, I get an error stating:   Failed to execute child process "yelp" (No such file or directory)

2.  How do I install Thunderbird or any other program for that matter?  I've done searches in the forums but did not find anything that could help me out.

---

### Post by mlind on 2006-06-27
[QUOTE=wych77]1.  When I click on the About Ubuntu icon under the System menu, I get an error stating:   Failed to execute child process "yelp" (No such file or directory)
[/QUOTE]

launch yelp from terminal and post the output


[QUOTE=wych77]
2.  How do I install Thunderbird or any other program for that matter?  I've done searches in the forums but did not find anything that could help me out.[/QUOTE]

Type this on terminal
```

sudo aptitude update && sudo aptitude install mozilla-thunderbird

```

---

### Post by th3james on 2006-06-27
For future reference the best way to install software (from a GUI) is to go to System -> Administration -> Synaptic package manager

This lets you search for software, and install it with just two clicks!

---

### Post by wych77 on 2006-06-27
Coolness, thanks a bunch guys. :)

---

### Post by Brunellus on 2006-06-27
[QUOTE=th3james]For future reference the best way to install software (from a GUI) is to go to System -> Administration -> Synaptic package manager

This lets you search for software, and install it with just two clicks![/QUOTE]
the command line is very fast and efficient when you know exactly the package that you need.  but if you ever want to search from the command line, it's:

sudo apt-cache search packagename

---

