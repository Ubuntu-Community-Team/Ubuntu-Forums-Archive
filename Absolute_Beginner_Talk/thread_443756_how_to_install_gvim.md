---
title: "how to install gvim"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-14
i remember using gvim a long time ago (i'm basically looking for a text editor that can highlight ruby code) but i have no idea how to install progams.  can someone help me get started?

typing gvim gives me this:

pit@T43:~$ gvim
The program 'gvim' can be found in the following packages:
 * vim
 * vim-perl
 * vim-ruby
 * vim-full
 * vim-python
 * vim-tcl
 * vim-gnome
 * vim-tiny
 * vim-gtk
Try: sudo apt-get install <selected package>

---

### Post by taurus on 2007-05-14
```
sudo aptitude update
sudo aptitude install gvim
gvim
```

---

### Post by sthapit on 2007-05-14
hey, thanks for the fast response!  i get this when i type your commands:

pit@T43:~$ sudo aptitude install gvim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
"gvim" is a virtual package provided by:
  vim-tcl vim-ruby vim-python vim-perl vim-gtk vim-full vim-gnome 
You must choose one to install.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded

---

### Post by taurus on 2007-05-14
Try

```
sudo aptitude install vim-full vim-gnome vim-ruby
```

---

### Post by sthapit on 2007-05-14
thanks, that worked.  gvim still doesn't highlight ruby code though.  any hints?

---

### Post by davidsiegel on 2007-07-05
You'll need to turn syntax highlighting on from the Syntax menu. Alternatively, type,

```
:syn on
```

or put

```
syntax on
```

in a file called .gvimrc in your home folder.

---

### Post by p_quarles on 2007-07-05
For what it's worth, Gedit also highlights ruby code. Just go to View >> Highlight Mode >> Scripts.

---

### Post by GAFFAR on 2007-12-19
Hello ,

I tried using the command

$sudo apt-get install vim-full

system is telling "vim-full" is not there.

Where can I download "gvim" binary package?

And how to install with that binary package?

Any other quick way I can download and install gvim?

Thankx.

Regards,
G.MOHAMMED GAFFAR
mdgaffar@rediffma

---

