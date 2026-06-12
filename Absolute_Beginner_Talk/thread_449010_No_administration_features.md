---
title: "No administration features"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by thunderkyss on 2007-05-19
Hey guys. first, let me say this is an awesome Forum. I especially like the little check if already posted thing next to my new Thread title(when creating the new thread).

I used it, found some interesting reading, but no solution.

So. 

I've just installed Ubuntu 7.04 on two of my computers. A laptop, and a dual powered AMD 64 bit monster.

Now, on the laptop, I'm not allowed to install any programs, plug-ins, or anything. when I go to install something, Ubuntu asks me for a password, I give it the password for my log-in(there's only one account on this machine). but it gives me an error, saying "The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

I've also tried to examine my wireless settings, to help me get my AMD machine "connected", but I'm not allowed. I get the same kind of error message.

So I go to system->administration, and I don't have the same options on the laptop, as I do on my desktop(the AMD machine). No network settings, no user groups, etc...

So, I've come to the conclusion that Ubuntu was installed without an adminstrator account. 

How do I get one, without reinstalling??

---

### Post by overdrank on 2007-05-19
> **thunderkyss said:**
> Hey guys. first, let me say this is an awesome Forum. I especially like the little check if already posted thing next to my new Thread title(when creating the new thread).

I used it, found some interesting reading, but no solution.

So. 

I've just installed Ubuntu 7.04 on two of my computers. A laptop, and a dual powered AMD 64 bit monster.

Now, on the laptop, I'm not allowed to install any programs, plug-ins, or anything. when I go to install something, Ubuntu asks me for a password, I give it the password for my log-in(there's only one account on this machine). but it gives me an error, saying "The underlying authorization mechanism(sudo) does not allow you to run this program. Contact the system administrator."

I've also tried to examine my wireless settings, to help me get my AMD machine "connected", but I'm not allowed. I get the same kind of error message.

So I go to system->administration, and I don't have the same options on the laptop, as I do on my desktop(the AMD machine). No network settings, no user groups, etc...

So, I've come to the conclusion that Ubuntu was installed without an adminstrator account. 

How do I get one, without reinstalling??

Hi just a thought did you install as oem on the system?

---

### Post by thunderkyss on 2007-05-19
I don't think so, that doesn't sound familiar.

Thanks for the quick response.

---

### Post by taurus on 2007-05-19
What's the output of this command from a terminal?

```
id
```

---

### Post by thunderkyss on 2007-05-19
**output of id:**
> uid=1001(cj) gid-1001(cj) groups=4(adm), 20(dialout), 24(cdrom), 25(floppy), 29(audio), 30(dip), 44(video), 46(plugdev), 104 scanner), 113(lpadmin), 1001(cj) cj@ElwoodUbuntu:~$

---

### Post by taurus on 2007-05-19
You also need to belong to group admin (besides adm) if you want to use sudo.  Therefore, boot into recovery mode from GRUB menu and add your login name, cj, to group admin.

```
nano -B /etc/group
```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then reboot.

```
shutdown -r now
```
Now, see if you can run these two commands from a terminal

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by thunderkyss on 2007-05-19
Code:
> nano -B /etc/group

I did this. I wasn't expecting my whole screen to be highjacked.

But that's ok. 

After I changed my shorts, It looks like cj is listed in the admin group.

> adm:x:4:cj

---

### Post by thunderkyss on 2007-05-19
hey guys, please don't be mad at me, but I think I lied to you.

I actually created two accounts when I installed Ubuntu.

I didn't think I did, but I did. I typed in "cjhoward" in the user name field, and edited it in the log on name field to "cj"

I thought it was just one account, but it was in fact two. 

I signed in as cjhoward, and I was able to do everything I wanted to do, including upgrading cj's priveledges 

thanks guys.

---

### Post by overdrank on 2007-05-19
> **thunderkyss said:**
> hey guys, please don't be mad at me, but I think I lied to you.

I actually created two accounts when I installed Ubuntu.

I didn't think I did, but I did. I typed in "cjhoward" in the user name field, and edited it in the log on name field to "cj"

I thought it was just one account, but it was in fact two. 

I signed in as cjhoward, and I was able to do everything I wanted to do, including upgrading cj's priveledges 

thanks guys.

:^o
thanks tarurs:lolflag:

---

### Post by thunderkyss on 2007-05-19
I beg your mercy.

---

### Post by thunderkyss on 2007-05-19
hey guys, I did a quick search, and didn't find a quick and easy answer.

Ctrl+Alt+Del

Does linux(Ubuntu) have an equivalent??

---

### Post by overdrank on 2007-05-19
> **thunderkyss said:**
> hey guys, I did a quick search, and didn't find a quick and easy answer.

Ctrl+Alt+Del

Does linux(Ubuntu) have an equivalent??

Well what are you trying to do?
ctrl,alt,backspace restarts X and ctrl,alt,F1 get you in the terminal, and ctrl,atl,F6 or F7 returns you t desktop. :(

---

### Post by thunderkyss on 2007-05-19
> **thunderkyss said:**
> **output of id:**
> uid=1001(cj) gid-1001(cj) groups=4(adm), 20(dialout), 24(cdrom), 25(floppy), 29(audio), 30(dip), 44(video), 46(plugdev), 104 scanner), 113(lpadmin), 1001(cj) cj@ElwoodUbuntu:~$




Taurus, thanks for your help.

Can anyone explain to me what the "id" command does??

and what that info the command spit out meant??

---

### Post by overdrank on 2007-05-19
> **thunderkyss said:**
> Taurus, thanks for your help.

Can anyone explain to me what the "id" command does??

and what that info the command spit out meant??

Hi these may help
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
Good luck!:popcorn:

---

### Post by trak87 on 2007-05-19
To know what any command does, just type:

```
man <progname>
```

"man" is the command to look at the manual page.

So running "man id" will give you info about the id program.

---

### Post by thunderkyss on 2007-05-19
> **overdrank said:**
> Well what are you trying to do?
ctrl,alt,backspace restarts X and ctrl,alt,F1 get you in the terminal, and ctrl,atl,F6 or F7 returns you t desktop. :(

I think the system manager is what I'm looking for.

Let's say a program hangs, and I want to stop it, end it, whatever. 

ctrl,alt,backspace looks like it'll do what I want. 

Or, if a program is running, and I can't see it in the taskbar, or anywhere else.... happens sometimes in Windows.

---

