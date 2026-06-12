---
title: "[SOLVED] Using Fortunes in Terminal"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by jdimauro on 2007-09-06
Hi folks,

I recently installed Mint on my backup computer to try it out.  It has a neat little feature that when you start up terminal it displays a fortune.  I have fortune installed in Ubuntu but is there a way to get it to automatically display it in terminal?

Thanks!
-John

---

### Post by asmoore82 on 2007-09-06
> **jdimauro said:**
> Hi folks,

I recently installed Mint on my backup computer to try it out.  It has a neat little feature that when you start up terminal it displays a fortune.  I have fortune installed in Ubuntu but is there a way to get it to automatically display it in terminal?

Thanks!
-John

add the 'fortune' command to the end of your .bashrc file

you could quickly do this without even using a text editor like so ...

```
~$ echo "fortune" >> ~/.bashrc
```

---

### Post by asmoore82 on 2007-09-06
if you wanted to get even crazier ... you could make a "fortune" a part of your BASH prompt by
adding this line to the end of your .bashrc file ...

```
export PS1='$(fortune)\n'"$PS1"
```

it would be **extremely** tricky to add this line to the file without a text editor because
you would have to protect all of the special characters from the Shell's interpretation.
that would look like this ...

```
~$ echo "export PS1="\''$(fortune)\n'\'\"'$PS1'\" >> ~/.bashrc
```

---

### Post by asmoore82 on 2007-09-06
A nice happy-medium would be this line, which will display the fortune in red,
at the end of your .bashrc file...

```
echo -ne '\033[01;31m'; fortune; echo -ne '\033[00m'
```

added by ...

```
~$ echo 'echo -ne '\''\033[01;31m'\''; fortune; echo -ne '\''\033[00m'\' >>~/.bashrc
```(all single quotes)

---

### Post by jdimauro on 2007-09-06
Thanks for all of the help folks!  I got it now! :)

-John

---

