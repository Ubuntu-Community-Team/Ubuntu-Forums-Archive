---
title: "Question about ' sudo '"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2006-10-18
I wanted to run ' lshw ' and remembered that it is recommended that I run it as ' sudo '.

I type ' sudo ', hit enter and get this:-

>>>

four@four-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
four@four-desktop:~$ lshw
WARNING: you should run this program as super-user.
<<<

If someone could explain something about this, I'd really appreciate it.

Thanks.

---

### Post by jordanmthomas on 2006-10-18
prepend sudo to the command you want to run
ie
```
sudo lshw
```

---

### Post by meng on 2006-10-18
sudo lshw
one command, not two.
Search the wiki for RootSudo

---

### Post by Tomosaur on 2006-10-18
You're right, you run it as sudo, but you use it like this:
```

sudo lshw

```

---

### Post by PriceChild on 2006-10-18
Further reading: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) :)

oh and btw you can use code tags: [ code ] code here [ /code ] (without the spaces) to separate code from other text instead of those >>>'s :)

---

### Post by paradj on 2006-10-18
your trying to use sudo as a shell
sudo changes the program you wish to run privilages

usage:

$ sudo lshw

---

### Post by ReaderRat on 2006-10-18
> **L Campbell said:**
> I wanted to run ' lshw ' and remembered that it is recommended that I run it as ' sudo '.

I type ' sudo ', hit enter and get this:-

>>>

four@four-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
four@four-desktop:~$ lshw
WARNING: you should run this program as super-user.
<<<

If someone could explain something about this, I'd really appreciate it.

Thanks.
This may help you understand more about sudo:
[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by L Campbell on 2006-10-18
Many thanks for all the help, here.

I really appreciate it.

Kind regards.

---

