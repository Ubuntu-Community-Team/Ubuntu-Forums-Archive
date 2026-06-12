---
title: "Laptop-mode-tools"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by RandomBloke on 2007-04-20
Hi,

I'm running a really old lappy that I had dapper installed on with laptop-mode-tools.
Hard drive corrupted so now installed with Feisty.
Downloaded laptop-mode-tools and tried to install but get an error mesage telling me I have a newer version installed?
This is a formatted drive.

I need laptop-mode-tools as this BIOS is so old. No power management.
The HDD on this machine keeps it spinning constantly - LMT sorted it out fine.
(as per my previous posts some time ago)

Can anyone give a BIG time newbie simple instructions to get LMT running again?

Many thanks in advance.

---

### Post by Redache on 2007-04-20
It must already be installed.

Open up a terminal and type this
```

sudo apt-cache search laptop-mode-tools

```

and see if it comes up with it installed. 

if it's awkward to read redirect it to a text file by typing 

```

sudo apt-cache search laptop-mode-tools > laptools.txt
```

The file should show up in your home folder.

Hope this helps.

---

### Post by RandomBloke on 2007-04-20
OK, that shows it is indeed installed. Thanks a lot.
:)
I'll try to work out how to implment the app.

---

### Post by Redache on 2007-04-20
Just go to the Terminal again and try typing

```
laptop-mode-tools
```

and see if it loads it. If not use whatever odd name is given to it in Apt :)

---

