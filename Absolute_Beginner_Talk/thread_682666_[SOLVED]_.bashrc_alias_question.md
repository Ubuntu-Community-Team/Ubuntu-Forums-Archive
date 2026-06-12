---
title: "[SOLVED] .bashrc alias question"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by rbc on 2008-01-30
After looking at some previous posts, I created a *.bash_aliases* in my home directory and adding the following to it:

[I]alias ll='ls -al'
alias m usb='pmount /dev/sdb1 /media/sdb1'
alias um usb='pumount /dev/sdb1'[/I]

I then opened the *.bashrc.* file and uncommented these lines:

[I]if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi[/I]
 If i then open terminal, without typing anything, i get this:

[I]bash: alias: pmount: not found
bash: alias: pumount: not found
bobbyc@DNLaptop:~$[/I]

In terminal, the *ll* command will work and displays the correct results, but if I type the same command again, and hit Return, it erases the command. Did I totally screw up the procedure or mistype something, or is this some quirk?

---

### Post by p_quarles on 2008-01-30
You need a space between the pmount commands and the device name.

---

### Post by mali2297 on 2008-01-30
> **rbc said:**
> After looking at some previous posts, I created a *.bash_aliases* in my home directory and adding the following to it:

[I]alias ll='ls -al'
alias m usb='pmount /dev/sdb1 /media/sdb1'
alias um usb='pumount /dev/sdb1'[/I]

I then opened the *.bashrc.* file and uncommented these lines:

[I]if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi[/I]
 If i then open terminal, without typing anything, i get this:

[I]bash: alias: pmount: not found
bash: alias: pumount: not found
bobbyc@DNLaptop:~$[/I]

In terminal, the *ll* command will work and displays the correct results, but if I type the same command again, and hit Return, it erases the command. Did I totally screw up the procedure or mistype something, or is this some quirk?

Replace the spaces in **m usb** and **um usb**. For example, make it
```

alias m_usb='pmount /dev/sdb1 /media/sdb1'
alias um_usb='pumount /dev/sdb1'

```

---

### Post by rbc on 2008-01-30
Thanks mali2297. That did it.

---

