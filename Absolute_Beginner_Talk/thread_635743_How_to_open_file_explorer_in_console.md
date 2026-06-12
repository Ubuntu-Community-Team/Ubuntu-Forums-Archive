---
title: "How to open file explorer in console"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by GlorytheWIz825 on 2007-12-09
Hi guys,

I am new to Linux and Ubuntu. With my Windows operating system, I set up an alias with 4NT(specialized command prompt) so when I type "explorer" in the command prompt, it will open up a file explorer in the current directory I was in with the console. Is there a way to accomplish this in Ubuntu?

Thanks!

---

### Post by whitenight639 on 2007-12-09
sudo nautilus

---

### Post by kvorion on 2007-12-09
Type 
```
nautilus --browser 
```
on the console.

Try man nautilus for more options

---

### Post by spai on 2007-12-09
why the sudo??
Just typing nautilus in the terminal works fine for me...

---

### Post by kvorion on 2007-12-09
Yup, sudo is not required. Simply invoking the file manager will do the task. With sudo, if you are using nautilus, it will open in /root.

Btw what I forgot is......if you are using Xubuntu, then use thunar instead of nautilus

---

### Post by asmoore82 on 2007-12-09
```
$ nautilus --browser "$PWD"
```

it's a little much to type to get a quick browser window
you can add a custom **alias** in your [hidden] $HOME/.bashrc text file that looks like this...

```
alias explore='nautilus --browser "$PWD"'
``` and then you could just run it like this ...

```
$ explore
```

(after adding that to your .bashrc file, you have to make the shell reload that file like this
```
$ source ~/.bashrc
``` -OR- you could simply close the terminal and open new one ;)

---

### Post by greybirds on 2007-12-09
On my machine, typing
```
nautilus --browser 
```
works, but opens up your home folder, regardless of where you have cd'ed to in the shell/terminal. If you add a space and period to the end, like this
```
nautilus --browser . 
```
it will open up the directory you're currently in. (Period is the shortcut for the current directory, so you're just saying "run nautilus and have it start in the current directory."

You can just as easily replace the period with any path, like
```
nautilus --browser /usr/share/pixmaps
```
will open up the directory where some of your system's pictures are stored and
```
nautilus --browser computer:/// 
```
will open up a browser window with all your storage devices listed.

---

### Post by GlorytheWIz825 on 2007-12-09
> **asmoore82 said:**
> ```
$ nautilus --browser "$PWD"
```

it's a little much to type to get a quick browser window
you can add a custom **alias** in your [hidden] $HOME/.bashrc text file that looks like this...

```
alias explore='nautilus --browser "$PWD"'
``` and then you could just run it like this ...

```
$ explore
```

(after adding that to your .bashrc file, you have to make the shell reload that file like this
```
$ source ~/.bashrc
``` -OR- you could simply close the terminal and open new one ;)

Thanks a lot everyone. That was very helpful. :)

---

