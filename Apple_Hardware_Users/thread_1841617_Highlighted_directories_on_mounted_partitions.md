---
title: "Highlighted directories on mounted partitions"
date: 2011-09-09
forum: Apple Hardware Users
---

### Post by Anstice on 2011-09-09
Hey guys,

I have two partitions that I have auto-mounted using /etc/fstab and that works fine. The only slightly annoying thing is that whenever I 'cd' to these locations the directories and files are highlighted which makes them a bit difficult to see sometimes. 

I was wondering if anyone knows if there is a way to remove the highlighting.

For reference here are the lines my fstab that mount the partitions:

/dev/sda5	/media/Dickens	vfat	user,fmask=0111,dmask=0000    0    0
/dev/sda3	/media/Capote	ntfs-3g	user,fmask=0111,dmask=0000    0    0

---

### Post by Toz on 2011-09-16
If you're referring to the syntax highlighting in a terminal window, you can disable all highlighting by editing ~/.bashrc and deleting or commenting-out the lines:
```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

```

You'll then need to close that terminal window and re-open if for it to take effect.

---

