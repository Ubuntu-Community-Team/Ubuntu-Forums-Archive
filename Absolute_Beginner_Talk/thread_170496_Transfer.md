---
title: "Transfer"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by GaFFy on 2006-05-04
Is there a easy way to transfer ubuntu settings to a new computer with completely diffferent hardware?
I like how I have this laptop setup and I would like to make my new desktop look and feel the same.  I am using gnome btw.

---

### Post by hw-tph on 2006-05-04
All personal (per user) settings are stored in your home directory. I usually back it all up but you could selectively make a tarball of the files and directories you want and then unpack them on your new computer (I often mail small tarballs to myself so they are stored on my ISP's servers while I need them).

You could use something like this: **tar cfvj dotfiles.tar.bz2 .config .evolution .bashrc .gnupg .gnome2 .gvimrc .vimrc .irssi .mozilla .pftp**

Then simply unpack it on your new computer: **tar xfvj dotfiles.tar.bz2**


Håkan

---

