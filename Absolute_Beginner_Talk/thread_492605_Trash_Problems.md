---
title: "Trash Problems"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-07-04
I needed to reinstall Steam using Wine so I just deleted my .wine folder. Simple enough, got Steam working after all, but when I went to empty my trash I got that I could not delete that as I did not have permission to. How can I really trash that? I want to as it is about 5 gigs. Any ideas?

---

### Post by greg_g on 2007-07-04
Well, one way would be to use your terminal.

```

cd .Trash
ls

```
then, from that list of stuff in there, 
```

sudo rm filename

```

if that doesn't work, try to force rm by
```

sudo rm -f filename

```

---

### Post by toasty_ghosty on 2007-07-05
Thanks..but when I try I get this:

[email]theking@OptimusPrimeTheSecond:~/.Tras[/email]h$ sudo rm -f .wine
rm: cannot remove `.wine': Is a directory

---

### Post by CaptainInsaneO on 2007-07-05
Add -d right before the directory name. (So, after the -f but before .wine)

---

### Post by toasty_ghosty on 2007-07-05
It still won't let me:

theking@OptimusPrimeTheSecond:~$ sudo rm -f -d .wine
rm: cannot remove `.wine': Is a directory

---

### Post by cwood06 on 2007-07-05
do sudo rm -r ~/.trash/.wine

r stands for recursive and that will remove the directory and all its files

---

### Post by toasty_ghosty on 2007-07-05
theking@OptimusPrimeTheSecond:~/Desktop$ sudo rm -r ~/.trash/.wine
rm: cannot remove `/home/theking/.trash/.wine': No such file or directory

---

### Post by CaptainInsaneO on 2007-07-05
The last one you posted is being executed from the desktop, therefore it won't work. Execute that command from the directory that .Trash is in.

---

### Post by scragar on 2007-07-05
> do sudo rm -r ~/.trash/.wine

you forgot the capital T, that's why it wouldn't work, fix that and everything should run smoothly.

---

### Post by toasty_ghosty on 2007-07-05
Thank you. My trash is FINALLY empty.

---

