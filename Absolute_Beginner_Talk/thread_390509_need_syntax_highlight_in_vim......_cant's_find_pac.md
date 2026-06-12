---
title: "need syntax highlight in vim...... cant's find package"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jcolo on 2007-03-22
Hi,

I installed recently the server CD. I need to have syntax highlight in Vim using a terminal. I am running it out of a vmware installation and I connect via putty.

Its is driving me nuts. It seems there is no binary package with syntax highligh enable and the only option seems to me to ( as I tried) to download the full version and do an ad-hoc compilation/installation in my system ( which incidentally does not have a compiler ... and I wish I do not have to install one.).

Can somebody suggest me a package with vim/syntax on ??

Many thanks.

JCG

---

### Post by jtibau on 2007-03-22
I'm not sure what you mean by not wanting to compile the full vim... What I've done to get sintax highlighting from vim is this:

sudo apt-get install vim-full

then edit the .vimrc file to whatever things I want it to have. I usually just use the example file provided by vimtutor.

You don't need to compile anything :) just a regular apt-get

---

### Post by Bachstelze on 2007-03-22
No additional package needed. The syntax highlighting is disaled by default but you just need to edit the vim config to enable it.

```
echo "syntax on" > ~/.vimrc
```

This will enable the syntax highlighting in vim just for you. If you want to enable it system-wide, do the same with /etc/vimrc (as root).

---

### Post by jcolo on 2007-03-22
Hi,

thanks for the comments.

Vim by default in the server installation is compiled without syntax support

Vim --version reports  

Included patches: 1-35
Compiled by [email]buildd@rothera.buil[/email]dd
Small version without GUI.  Features included (+) or not (-):

 -syntax

if I do a apt-get install vim-full

I get this....

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package vim-full is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  [COLOR="Blue"]vim-runtime vim-gui-common vim-gnome vim vim-common[/COLOR]
E: Package vim-full has no installation candidate


I have as well downloaded vim-full_7.0-035+1ubuntu5_i386.deb manually and moved to  /var/cache/apt/archives

same result.

dpkg -l gives me these lines.

ii  vim-common        7.0-035+1ubuntu5  Vi IMproved - Common files
ii  vim-runtime       7.0-035+1ubuntu5  Vi IMproved - Runtime files
ii  vim-tiny          7.0-035+1ubuntu5  Vi IMproved - enhanced vi editor - compact version

I have then installed all the packages that are suggested in the failed vim-full installation but the vim-gnome ( sorry ... on dialup plus just using terminal )... that is

[COLOR="Blue"]vim and vim-gui-common.[/COLOR]

Result is syntax works now. Don't know  which one make the magic .

Cheers.

JCG




Thanks.

JCG

---

