---
title: "Upgrading help"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-04-17
I installed Ubuntu 6.06 and now i am trying to upgrade it to 6.10.

I typed in gksu update-manaer -c -d 

and it gave me this:

ashgx@ashgx-laptop:~$ gksu update-manager -c -d
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

Help? lol

---

### Post by Bachstelze on 2007-04-17
All you need is here :

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by toronkusu on 2007-04-23
> **HymnToLife said:**
> All you need is here :

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Yah, i got the same error as him.  Not sure how that URL is going to help us when it tells us to do the exact same thing as what we did before.

gksu: invalid option -- c

That gives us the error that he posted.

---

### Post by Bachstelze on 2007-04-23
> **toronkusu said:**
> Not sure how that URL is going to help us when it tells us to do the exact same thing as what we did before.

No, it doesn't...

---

