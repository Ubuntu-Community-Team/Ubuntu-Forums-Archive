---
title: "Advanced usage of pacman, tips, tricks &amp; reference resources wanted?"
date: 2009-02-08
forum: Arch and derivatives
---

### Post by handy on 2009-02-08
The title says it all. :-)

$ man pacman 

Brings plenty of options, it really is the intelligent usage of these options that I'm sure can do wonderful things for an Arch system.

I'm also sure that the unintelligent combination of pacman's command options can absolutely ruin an Arch install.

Seeing as I'm not intelligent enough to work out the wonders & treasures laying hidden in the pacman man pages, I'm asking for those that are to pass on their knowledge in this thread.

All tips, tricks & links to reference resources welcome. :-D

---

### Post by smartboyathome on 2009-02-08
My list of aliases, which help me remember everything (english is easier to remember than obscure commands ;)).
```
alias install='yaourt -S'
alias update='yaourt -Sy'
alias upgrade='yaourt -Syu --aur'
alias remove='yaourt -R'
alias search='yaourt -Ss'
alias pkg-info='yaourt -Qi'
alias repo-pkg-info='yaourt -Si'
alias fetch='yaourt -G'
alias list-files='yaourt -Ql'
alias install-local='sudo pacman -U'
```

---

### Post by Rokurosv on 2009-02-08
I do the same thing but with normal pacman. Another usefull commands:
pacman -Scc = Cleans cache and unused repositories
pacman -Qs = Search in the installed packages
pacman -Qqdt = Check for unneeded dependencies
You can also pass the result of one command to another
pacman -Rsn $(pacman -Qqdt)
That's the best I can do.....I'm a noob

---

### Post by dannytatom on 2009-02-08
My aliases so far, a couple taken from smartboyathome a while back:

```

alias yogurt="yaourt"
alias pacs="pacsearch"
pacsearch () {
       echo -e "$(pacman -Ss $@ | sed \
       -e 's#core/.*#\\033[1;31m&\\033[0;37m#g' \
       -e 's#extra/.*#\\033[0;32m&\\033[0;37m#g' \
       -e 's#community/.*#\\033[1;35m&\\033[0;37m#g' \
       -e 's#^.*/.* [0-9].*#\\033[0;36m&\\033[0;37m#g' )"
}
alias install='yaourt -S'
alias update='yaourt -Syu --aur'
alias remove='yaourt -R'
alias lsorhpans='pacman -Qdt'
alias rmorphans='sudo pacman -Rs $(pacman -Qtdq)'
alias search='yaourt -Ss'
alias pkg-info='yaourt -Si'
alias fetch='yaourt -G'
alias list-files='yaourt -Ql'

```

---

### Post by handy on 2009-02-08
The ability to safely remove orphan files would be nice.  

Especially if you got to ok every one of them individually; it would be useful if you could point pacman at specified directory(s) for this process.



As far as the .bashrc is concerned the only thing I can add is the following:

Using the ***pacman -Sc*** command when you are sure that you have installed no problems in your last -Syu is a good way to keep your cache size down, but still gives you a quick & easy way out if your next -Syu brings unexpected trouble.

Which means you can always [*_downgrade your way out of trouble_*]("http://ubuntuforums.org/showpost.php?p=6283883&postcount=3") at the cost of keeping a copy of the last known good packages in your cache.  

*If you use _pacman -Scc_ you remove the easy way out, as I see it.*

---

### Post by will1911a1 on 2009-02-09
> **Rokurosv said:**
> 
pacman -Qqdt = Check for unneeded dependencies


This is something I think about figuring out and then forget while I'm actually at the computer.  Thanks!

---

### Post by kerry_s on 2009-02-09
i just stick to standard repos,no testing, no yaourt, right now i just want stable.

my bashrc:

```
export MOZ_DISABLE_PANGO=1
export OOO_FORCE_DESKTOP=gnome


# Check for an interactive session
[ -z "$PS1" ] && return

eval `dircolors -b`
alias ls='ls -a --color=auto'
PS1='\n[Command @ \w]\n$ '

alias !='sudo'
alias x='exit'
alias ch='history -c'
alias u='sudo pacman -Syu'
alias s='search'
alias i='sudo pacman -S'
alias r='sudo pacman -Rsn'
alias ?='installed'
alias c='sudo pacman -Sc --noconfirm'
alias unp='extract'

search() {
   echo -e "$(pacman -Ss "$@" | sed \
     -e 's#^core/.*#\\033[1;31m&\\033[0;37m#g' \
     -e 's#^extra/.*#\\033[0;32m&\\033[0;37m#g' \
     -e 's#^community/.*#\\033[1;35m&\\033[0;37m#g' \
     -e 's#^.*/.* [0-9].*#\\033[0;36m&\\033[0;37m#g' ) \
     \033[0m"
}

installed() {
   echo -e "$(pacman -Qs "$@" | sed \
     -e 's#^core/.*#\\033[1;31m&\\033[0;37m#g' \
     -e 's#^extra/.*#\\033[0;32m&\\033[0;37m#g' \
     -e 's#^community/.*#\\033[1;35m&\\033[0;37m#g' \
     -e 's#^.*/.* [0-9].*#\\033[0;36m&\\033[0;37m#g' ) \
     \033[0m"
}

 extract () {
   if [ -f $1 ] ; then
       case $1 in
           *.tar.bz2)   tar xvjf $1    ;;
           *.tar.gz)    tar xvzf $1    ;;
           *.bz2)       bunzip2 $1     ;;
           *.rar)       unrar x $1     ;;
           *.gz)        gunzip $1      ;;
           *.tar)       tar xvf $1     ;;
           *.tbz2)      tar xvjf $1    ;;
           *.tgz)       tar xvzf $1    ;;
           *.zip)       unzip $1       ;;
           *.Z)         uncompress $1  ;;
           *.7z)        7z x $1        ;;
           *)           echo "don't know how to extract '$1'..." ;;
       esac
   else
       echo "'$1' is not a valid file!"
   fi
 }


```

[http://wiki.archlinux.org/index.php/Improve_Pacman_Performance](http://wiki.archlinux.org/index.php/Improve_Pacman_Performance)

---

### Post by smartboyathome on 2009-02-09
kerry_s, you know pacman-color does the same thing that you do with installed and search.

---

### Post by kerry_s on 2009-02-10
> **smartboyathome said:**
> kerry_s, you know pacman-color does the same thing that you do with installed and search.

yes, i know, but pacman-color is in yaourt, not the standard repos, i used it on the last install. this install i'm only using the standard repos.

---

### Post by handy on 2009-02-10
> **kerry_s said:**
> yes, i know, but pacman-color is in yaourt, not the standard repos, i used it on the last install. this install i'm only using the standard repos.

You don't like AUR?

---

### Post by kerry_s on 2009-02-10
> **handy said:**
> You don't like AUR?

i don't mind it, just prefer to use only the standard repos this time. i played with it on my last install, till i broke it. :lolflag:
ended up with kernel panic and had no way to undo the damage, cause i had fully cleaned. :(

i always try something different on each install, i'm working right now, so i really don't want to end up with a reinstall or have to fix things.
on this install i'm shooting for full stability, very little tweaking, no messing around. :)

i work as a welder in the ship yard they call me when it gets busy, jobs almost done, after that i can mess around all i want.
i don't usually work, cause i'm partially disabled, had a accident in the dry dock, i fell, messed me up good. i get paid whether i work or not, so they only call me when there really shorthanded or need the job done fast.

---

### Post by handy on 2009-02-10
> **kerry_s said:**
> i don't mind it, just prefer to use only the standard repos this time. i played with it on my last install, till i broke it. :lolflag:
ended up with kernel panic and had no way to undo the damage, cause i had fully cleaned. :(

i always try something different on each install, i'm working right now, so i really don't want to end up with a reinstall or have to fix things.
on this install i'm shooting for full stability, very little tweaking, no messing around. :)

i work as a welder in the ship yard they call me when it gets busy, jobs almost done, after that i can mess around all i want.
i don't usually work, cause i'm partially disabled, had a accident in the dry dock, i fell, messed me up good. i get paid whether i work or not, so they only call me when there really shorthanded or need the job done fast.

I'm very sorry to hear that you got hurt.  Though I know sympathy isn't going to make anything better. :-)

There are a few of us who have been dissabled one way or another through accident &/or disease who are regulars on the forum.

Computers offer such a broad range of mental stimulation they are perfect for those that can't do what they otherwise would be doing. 

Well, that's how it is for me anywhay. :-)

---

### Post by kerry_s on 2009-02-10
i know exactly what you mean, if i didn't have a computer i would go crazy with boredom. :lolflag:

---

### Post by handy on 2009-02-11
> **kerry_s said:**
> i know exactly what you mean, if i didn't have a computer i would go crazy with boredom. :lolflag:

The last thing in the world that I am is religious.

BUT:

Amen brother.

:-D

---

### Post by &#32 Greg on 2009-02-11
It would probably be a good idea for someone to wikify this thread. I'd do it myself, but I'm not sure if I know enough to determine what commands would go in.

---

### Post by smartboyathome on 2009-02-11
> **  Greg said:**
> It would probably be a good idea for someone to wikify this thread. I'd do it myself, but I'm not sure if I know enough to determine what commands would go in.

[Already done]("http://wiki.archlinux.org/index.php/Pacman_Aliases"). :popcorn:

---

### Post by handy on 2009-02-11
> **  Greg said:**
> It would probably be a good idea for someone to wikify this thread. I'd do it myself, but I'm not sure if I know enough to determine what commands would go in.

If you make additions to the Arch wiki pacman page, tell us, & we can all work at refining the page.

Many heads can make light work of a job like that.

---

### Post by handy on 2009-02-14
I'm very interested in pacman usage tips.  

Making aliases is easy once you know how.

Safely cleaning up an Arch installation that has been around for a while, that the user has learned Arch on & made mistakes in their usage of installing & uninstalling packages, which leaves debris (orphan files) which accumulates.

It is part of the Arch way, (rolling release) for these orphans to accumulate & remain until the user finds & removes them, or the HDD fails.

What safe ways do people use to find & remove orphans?

---

### Post by fwojciec on 2009-02-14
> **handy said:**
> What safe ways do people use to find & remove orphans?

"pacman -Qdt" will give you a list of packages installed as dependency for another package that are no longer required, i.e. "orphans".

You can automatically remove them, along with their dependencies, with something like: "pacman -Rs $(pacman -Qqdt)"

I think someone already mentioned this earlier in this thread.

Beyond that, in order to keep the system clean, you might have to remove all the leftover *.pacsave files.  You can find them with "find / -type f -name *.pacsave" or more simply with "locate *.pacsave".  It's also a good idea to keep an eye on the /var/log directory, in case some logs are growing too large.

---

### Post by handy on 2009-02-14
> **fwojciec said:**
> 
"pacman -Qdt" will give you a list of packages installed as dependency for another package that are no longer required, i.e. "orphans".

You can automatically remove them, along with their dependencies, with something like: "pacman -Rs $(pacman -Qqdt)"

I think someone already mentioned this earlier in this thread. 

Thanks, for that fwojciec.  

I just looked & the above was listed a couple of times; your post has finally drummed it into my thick head. :-) 

> **fwojciec said:**
> 
Beyond that, in order to keep the system clean, you might have to remove all the leftover *.pacsave files.  You can find them with "find / -type f -name *.pacsave" or more simply with "locate *.pacsave".  It's also a good idea to keep an eye on the /var/log directory, in case some logs are growing too large.

I have manually found & removed .pacsave files, I'll use your suggestions in the future.

I do keep an eye on the /var/log/ & have prune the size of some log files from time to time.

Thanks again for your post.

---

