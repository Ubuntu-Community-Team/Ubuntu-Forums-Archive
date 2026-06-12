---
title: "[SOLVED] Need help with vi"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-04-26
I am having an issue with the vi editor.  When trying to navigate threw a file with the arrow keys letters appear.  I go into insert mode using i or the insert key then when the up arrow key is pressed an A appears.

---

### Post by taurus on 2007-04-26
Try to install the vim-full first.

```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by wormser on 2007-04-26
> **taurus said:**
> Try to install the vim-full first.

```
sudo aptitude update
sudo aptitude install vim-full
```


That did the trick.  Thank you.  

What is the deal with the default vi package?  It seems weird that it does not work?  Is it just an old school version of vi that does not support many things that vim does?

---

### Post by bluedog800 on 2007-05-01
Awesome that fixed me up - I had that problem in 6.10 and never got around to looking into it!

Thanks

---

### Post by adam s on 2007-05-01
Hi,

Vi uses specific characters to certain jobs. 

Below are a list of scroll commands :

h - left
j  - down
k  - up
l  - right
ctrl f  - forward one screen
ctrl b - backward 1 screen
ctrl d - scroll down half a screen
ctrl u - scroll up  half a screen
0 - Beginning of line
$ - end of lie
G - last line in file
:0 - first line in file


These commands are useful as they can be used within linux command line (eg man, cat, more  , head, tail etc)

If you can get the O'Reilly Vi book it is very useful (especially the attached Quick Reference Guide.

Hope this is useful,

Adam

One of the reasons that I moved to linux was to use vi as I had got fed up of poor functionality in windows text editors (I will probably now be flamed by people who have not used even 2% of Vi's capabilities)

---

### Post by andrew.46 on 2007-06-11
Hi,

 I was searching for vim material:

> **taurus said:**
> Try to install the vim-full first.

```
sudo aptitude update
sudo aptitude install vim-full
```

 Is there a different package name under Dapper? I get the following message:

```
andrew@ilium:~$ sudo apt-get install vim-full
Reading package lists... Done
Building dependency tree... Done
Package vim-full is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  vim-tcl vim-ruby vim-python vim-perl vim-gtk vim-runtime vim-gui-common
  vim-gnome vim-common vim
E: Package vim-full has no installation candidate

```

 Do I simply have to install all of these compnents? I imaging 'vim-full' is a meta package.

  Andrew

---

### Post by taurus on 2007-06-11
> **andrew.46 said:**
> Hi,

 I was searching for vim material:



 Is there a different package name under Dapper? I get the following message:

```
andrew@ilium:~$ sudo apt-get install vim-full
Reading package lists... Done
Building dependency tree... Done
Package vim-full is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  vim-tcl vim-ruby vim-python vim-perl vim-gtk vim-runtime vim-gui-common
  vim-gnome vim-common vim
E: Package vim-full has no installation candidate

```

 Do I simply have to install all of these compnents? I imaging 'vim-full' is a meta package.

  Andrew

I would go with the last three.

```
sudo apt-get install vim-gnome vim-common vim
```

---

