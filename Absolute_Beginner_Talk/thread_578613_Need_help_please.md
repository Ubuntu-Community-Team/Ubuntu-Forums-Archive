---
title: "Need help please"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by xjrockx on 2007-10-17
I had no idea how to title this, either way my problem is pretty simple.  I just installed Ubuntu Server 6.06 and everything loaded and booted just fine.  I hit enter to get the log in prompt, yet I am unable to see anything I type.  I understand that the password does not show but neither does my user name.

I can successfully log in to the account but the same problem persists.  I get the typical username@root$ prompt but regardless of what I press on the keyboard it will not show on the screen; however, if I type something like say "asdf" then press enter what I typed appears on the previous line.  Its as if it is masking everything I type until I press enter.

Please please please, any help is greatly appreciated.  I have tried to do a search, but I either am not very good at searching or there isn't a good response to my question.  Sorry if this sounds like a stupid question but it's driving me nuts.

---

### Post by mlind on 2007-10-17
sounds weird ,, You could reconfigure console-setup and make sure its settings are correct
```

sudo dpkg-reconfigure console-setup

```

you may need to run *setupcon* or reboot to make any changes apply.

---

### Post by xjrockx on 2007-10-17
Thank you very much, Ill try this as soon as I get home from work.  Anyone else? Or is my problem really just that weird?  Maybe I should try to re-install if the above does not work?

Also I would be more then happy to try to explain my problem better if anyone is not able to follow.

---

### Post by mlind on 2007-10-17
> **xjrockx said:**
> Thank you very much, Ill try this as soon as I get home from work.  Anyone else? Or is my problem really just that weird?  Maybe I should try to re-install if the above does not work?

Also I would be more then happy to try to explain my problem better if anyone is not able to follow.

Does this also happen on other tty's (Ctrl+Alt+F2, Ctrl+Alt+F3, ..) ?

---

### Post by xjrockx on 2007-10-17
Umm not that I know of, but I am @ home now and I can check.  Give me a few min to boot up and try some things.  Ill get right back to ya.

---

### Post by xjrockx on 2007-10-17
Ok, I just ran the command you posted.  I get an error when doing so.

Package 'console-setup' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbing/dpkg-reconfigure: console-setup is not installed
user@name:~$

As far as the other tty's working they seem to.  I also wanna add though, if I use the command exit to log out then attempt to log back in I can read all that I type.  Using Ctrl+Alt+F2 seems to simulate the exit command thus being the reason why it seems to work.  Keep in mind though I am completely new to Ubuntu/Linux so I am not completely sure what I am talking about haha.

Also one more thing to add.  Even after doing the small exit work around I have been using, If I use any of the sudo commands to change directories or make new ones, I wind up back at square one.  Thanks again for your help.

---

### Post by xjrockx on 2007-10-18
Anyone else?

---

### Post by xjrockx on 2007-10-18
Please, this problem is driving me nuts.  I am determined to find an answer.

I have tried re-installing several times still the same problem.  Google doesn't show anything, and no one on this forum seems to know what I am talking about.

---

