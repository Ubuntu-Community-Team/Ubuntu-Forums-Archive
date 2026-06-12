---
title: "Weird Terminal look....screenshot inside"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by xcafeus on 2007-10-16
Hi guys,

I did a bit of searching but failed to find any relevant info..

Why is it not like "user@ubuntu"???... when I login as root (I enabled that function) it shows "root@ubuntu" but not when logged in as me...

[[IMG]http://img80.imageshack.us/img80/6158/weirdterminallx9.th.png[/IMG]](http://img80.imageshack.us/my.php?image=weirdterminallx9.png)

---

### Post by Beggar on 2007-10-16
The reason it is different is because in your ~/.bashrc file, there is an entry like the following

```
PS1="$"
```

As opposed to the usual (something like the following).

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

---

### Post by xcafeus on 2007-10-17
> **Beggar said:**
> The reason it is different is because in your ~/.bashrc file, there is an entry like the following

```
PS1="$"
```

As opposed to the usual (something like the following).

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

can I fix this by copying your text above to the corresponding file?

EDIT: how did this happen? (I upgraded to Gutsy earlier - had some problems due to FakeRaid - followed the Fakeraid guide to reinstall grub and fix menu.lst using the 7.10 livecd this time)

---

### Post by xcafeus on 2007-10-17
can you please confirm before I start messing things again? :) cheers

---

### Post by Dr Small on 2007-10-17
Make a backup just in case :D
```
cp .bashrc .bashrc_bak
```

Open .bashrc
```
gedit .bashrc
```

Press CTRL + F to "Find" and enter this string:
```
PS1="$"
```

If it finds it, replace it with:
```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```

Dr Small

---

### Post by Beggar on 2007-10-17
As small said, that was copied directly out of my own bashrc file, so you should be fine, always make a backup however.

---

### Post by llamakc on 2007-10-17
And after you have edited the file you do not need to reboot or relogin. Just run:

source ~/.bashrc

and you should recognize the change immediately.

---

### Post by xcafeus on 2007-10-17
much appreciated I will try that now..

---

### Post by xcafeus on 2007-10-17
guys I opened /etc/.bashrc (which was located at two places: /etc and /root) and found it empty. I then cd /root and copied the good one to /etc. I tried the source command but couldnt find it so I rebooted and I still get only the $ sign at the terminal. I think something else is wrong...

see screenshot

[[IMG]http://img81.imageshack.us/img81/6529/screenshotterminal1kl6.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotterminal1kl6.png)

the arrow keys produce this:

[[IMG]http://img85.imageshack.us/img85/8228/screenshotterminal2so2.th.png[/IMG]](http://img85.imageshack.us/my.php?image=screenshotterminal2so2.png)

---

### Post by llamakc on 2007-10-17
You want to edit the .bashrc in YOUR home directory.

This would be at ~/.bashrc

---

### Post by xcafeus on 2007-10-17
i tried that too to no avail... something got messed up during the upgrade from 7.04 to 7.10 having fakeraid. I must perform a clean install tommorow... it seems that there is a deeper problem with the system. I just finished installing gutsy on my laptop (im typing using it now) and since there was no raid everything works fine... I only got a gnome error on first boot which disappeared after a second reboot.

I think a clean install is the solution to this thread.

thanks for all the help.

---

