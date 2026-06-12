---
title: "Mozilla packages downloaded from mozilla.com won't run,suspected shell script problem"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by clevin on 2007-04-07
Im running Ubuntu 7.04 beta

the repositories only have Thunderbird 1.5.10, so I download 2.0 RC1 from ftp.mozilla.org, its a tar.gz, extracted in my /home/username/thunderbird/

it works fine (running the shell script) until this morning.
first when i click the shortcut of thunderbird. netscape crash feedback pops up, when I get rid of it. 

next time, whenever I click thunderbird icon, no window would be created. and no thunderbird session can be observed in system monitor (however, if i delete the profile folder for TB (folder ./thunderbird in my home folder), it will create new profile folder.).

I then tested tar.gz version of firefox, it does not work neither. This make me wonder if all the shell script suddenly stopped working.

any suggestion would be greatly appreciated.

---

### Post by kerry_s on 2007-04-07
You have to install libstdc++5.
sudo apt-get install libstdc++5

---

### Post by clevin on 2007-04-07
when I do as u suggested, it told me I already have newest version installed. 

Thanks.

---

### Post by Bachstelze on 2007-04-07
```
ls -l /bin/sh
```

What does that give you ?

---

### Post by clevin on 2007-04-07
> lrwxrwxrwx 1 root root 4 2007-04-07 14:19 /bin/sh -> bash


now I kinda suspect its my newly installed scim's problem. ?

---

### Post by kerry_s on 2007-04-08
Have you tried starting the programs from terminal to see the errors?

---

