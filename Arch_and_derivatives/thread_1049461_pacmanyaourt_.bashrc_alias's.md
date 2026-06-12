---
title: "pacman/yaourt .bashrc alias's"
date: 2009-01-24
forum: Arch and derivatives
---

### Post by kerry_s on 2009-01-24
hey guy's i'm still trying to understand the package management in arch.

i installed the yaourt which seems to do some of the pacman stuff at the same time, so instead of separate aliais's i just mixed it in with the pacman 1's.
question:
is it safe/okay to do that?

this is what i got for alias's:
```
alias !='sudo'
alias ch-='history -c'
alias u='sudo yaourt -Syu --aur'
alias i='sudo pacman -S'
alias yi='sudo yaourt -S'
alias r='sudo pacman -Rsn'
alias s='yaourt -Ss'
alias c='sudo pacman -Scc --noconfirm;sudo yaourt -Cc --noconfirm'
alias a='yaourt -Qs'
alias o='sudo pacman-optimize && sync'

```


questions:
did i miss any of the important 1's?
what do you have for your alias's?

thanks

---

### Post by fwojciec on 2009-01-24
```
alias pacman="sudo powerpill"
```
[Powerpill](http://xyne.archlinux.ca/info/powerpill) uses aria2c for downloading simultaneously from multiple mirrors, so that you can max out your connection when you're downloading updates.  You can also use it as a downloader for yaourt.

---

### Post by kerry_s on 2009-01-24
thanks, not really big on aria, i tried it already though, just prefer to stick with wget. my machine is low spec 450mhz 256mb, if i make things to fast it can't keep up and will slow down anyway, so i try and keep it simple, just with in the limits. my dsl is a max 3mb's shared between 5 computers and xbox, i've learned to wait. ;)

so is my alias's okay, safe to use with out problems?

---

### Post by fwojciec on 2009-01-24
> alias c='sudo pacman -Scc --noconfirm
That should be sufficient, no need to make yaourt do the same, since yaourt will only pass this request on to pacman.  Same goes for your "i" and "yi" aliases -- yaourt will simply use pacman to install stuff from regular repos.

---

### Post by kerry_s on 2009-01-24
so then i can just use yaourt for those?

```
alias !='sudo'
alias ch-='history -c'
alias u='sudo yaourt -Syu --aur'
alias i='sudo yaourt -S'
alias r='sudo pacman -Rsn'
alias s='yaourt -Ss'
alias c='sudo yaourt -Cc --noconfirm'
alias a='yaourt -Qs'
alias o='sudo pacman-optimize && sync'

```

---

### Post by smartboyathome on 2009-01-24
```
$ cat .zshrc-additions
##Helpful Arch Linux Aliases
alias install='yaourt -S'
alias update='yaourt -Sy'
alias upgrade='yaourt -Syu --aur'
alias remove='yaourt -R'
alias search='yaourt -Ss'
alias pkg-info='yaourt -Si'
alias fetch='yaourt -G'
alias list-files='yaourt -Ql'
alias group-install='sudo pacman -S'
alias install-local='sudo pacman -U'
```

There you go. Just replace yaourt with sudo pacman where needed. group-install and install-local are there because yaourt doesn't do those. :)

---

### Post by kerry_s on 2009-01-24
> alias group-install='sudo pacman -S'

so yaourt doesn't do dependency's or is "group" something different in pacman?

added the local install, thanks.

---

### Post by smartboyathome on 2009-01-24
> **kerry_s said:**
> so yaourt doesn't do dependency's or is "group" something different in pacman?

added the local install, thanks.

yaourt can't install package groups, such as "gnome" or "e17".

---

### Post by kerry_s on 2009-01-24
> **smartboyathome said:**
> yaourt can't install package groups, such as "gnome" or "e17".

oh okay, your talking metapackages. 
are you sure? see pic

---

### Post by smartboyathome on 2009-01-24
Well, it didn't use to. I guess it does now. :P

---

### Post by kerry_s on 2009-01-24
> **smartboyathome said:**
> Well, it didn't use to. I guess it does now. :P

:lolflag: that's linux for ya, just gets better with time.

---

### Post by kerry_s on 2009-01-24
okay, i decided to separate it to use only when needed, yaourt repos are just to big, which slows things down when i'm just looking/installing the basic things.

so this is what i got:
```

alias !='sudo'
alias ch='history -c'
alias u='sudo yaourt -Syu --aur'
alias i='sudo pacman -S'
alias yi='sudo yaourt -S'
alias l='sudo pacman -U'
alias r='sudo pacman -Rsn'
alias s='pacman-color -Ss'
alias ys='yaourt -Ss'
alias c='sudo pacman -Scc --noconfirm'
alias yc='sudo yaourt -Cc'
alias a='yaourt -Qs'
alias o='sudo pacman-optimize && sync'


```

---

### Post by fwojciec on 2009-01-24
This is a nice function to have in .bashrc if you want to just search through the official repos:
> pcs () 
{
  echo -e "$(pacman -Ss $@ | sed \
  -e 's#core/.*#\\033[1;31m&\\033[0m#g' \
  -e 's#extra/.*#\\033[1;32m&\\033[0m#g' \
  -e 's#community/.*#\\033[1;35m&\\033[0m#g' \
  -e 's#^.*/.* [0-9].*#\\033[1;36m&\\033[0m#g' )"
}
This basically does pacman search, but colorizes the output.

There used to be something called "tupac" that performed cached searches of AUR -- it worked very fast when I tried it.

---

### Post by kerry_s on 2009-01-24
> **fwojciec said:**
> This is a nice function to have in .bashrc if you want to just search through the official repos:

This basically does pacman search, but colorizes the output.

There used to be something called "tupac" that performed cached searches of AUR -- it worked very fast when I tried it.

i've got "pacman-color" which does that exact thing.

---

