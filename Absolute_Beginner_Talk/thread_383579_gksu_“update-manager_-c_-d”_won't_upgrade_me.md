---
title: "gksu “update-manager -c -d” won't upgrade me"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Toadmund on 2007-03-13
Why when I follow the the instruction on this page:
[http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-606-dapper-drake-to-ubuntu-10-edgy-eft.html")
To put this in terminal: ```
gksu “update-manager -c -d”
```
Why does it spit this out:
```
toad@toad-desktop:~$ gksu “update-manager -c -d”
gksu: invalid option -- c
GKsu version 1.3.7

Usage: gksu [-u <user>] [-k] [-l] <command>

  --always-ask-password, -a
    Do not try to check if a password is really
    needed for running the command, or if there
    are other means of obtaining it: simply ask for it.
  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.
  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --icon <icon>, -i <icon>
    Replace the default window icon with the argument.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --ssh-fwd, -s
    Strip the host part of the $DISPLAY variable, so that
    GKSu will work on SSH X11 Forwarding.
  --sudo-mode, -S
    Make GKSu use sudo instead of su, as if it had been
    run as "gksudo".
  --title <title>, -t <title>
    Replace the default title with the argument.
  --user <user>, -u <user>
    Call <command> as the specified user.
  --desktop <file>, -D <file>
    Use a .desktop file to get the name of the application
    and the icon from.

  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!


toad@toad-desktop:~$

```
And when I go to update manager it says there is no updates, why can't I get to edgy from dapper?:confused:

---

### Post by taurus on 2007-03-13
It's

```
gksu "update-manager -c" 
```

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by Toadmund on 2007-03-13
I knew someone would say that, however it doesn't help either, update manager tells me it's upgrading me, yet ultimately doesn't :(

---

### Post by taurus on 2007-03-13
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Toadmund on 2007-03-13
Here ya go, hot and fresh, for your perusing pleasure!
```
...om the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://flomertens.keo.in/ubuntu/ dapper main main-all

```

---

### Post by taurus on 2007-03-13
What happens to the rest of it, top half?  I would recommend you edit /etc/apt/sources.list and place a # in front of the last line to comment it out.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Toadmund on 2007-03-13
I left the top half out as everyone has the same stuff their, (I guess), I put the # in like you suggested.

---

