---
title: "I can not upgrade to Ubuntu 7.04"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by gsk320 on 2007-04-21
I am currently using Ubuntu 6.10 and when I type gksu “update-manager -c -d” into terminal, it gives me this useless reply, there are no spelling errors or anything in my command:

GTK Accessibility Module initialized
gksu: invalid option -- c
GKsu version 1.9.3

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

---

### Post by marko_4454 on 2007-04-21
> **gsk320 said:**
> I am currently using Ubuntu 6.10 and when I type gksu “update-manager -c -d” into terminal, it gives me this useless reply, there are no spelling errors or anything in my command:

GTK Accessibility Module initialized
gksu: invalid option -- c
GKsu version 1.9.3

Usage: gksu [-u <user>] [options] <command>

  --debug, -d
    Print information on the screen that might be
    useful for diagnosing and/or solving problems.

  --user <user>, -u <user>
    Call <command> as the specified user.

  --disable-grab, -g
    Disable the "locking" of the keyboard, mouse,
    and focus done by the program when asking for
    password.
  --prompt, -P
    Ask the user if they want to have their keyboard
    and mouse grabbed before doing so.
  --preserve-env, -k
    Preserve the current environments, does not set $HOME
    nor $PATH, for example.
  --login, -l
    Make this a login shell. Beware this may cause
    problems with the Xauthority magic. Run xhost
    to allow the target user to open windows on your
    display!

  --description <description|file>, -D <description|file>
    Provide a descriptive name for the command to
    be used in the default message, making it nicer.
    You can also provide the absolute path for a
    .desktop file. The Name key for will be used in
    this case.
  --message <message>, -m <message>
    Replace the standard message shown to ask for
    password for the argument passed to the option.
    Only use this if --description does not suffice.

  --print-pass, -p
    Ask gksu to print the password to stdout, just
    like ssh-askpass. Useful to use in scripts with
    programs that accept receiving the password on
    stdin.

Why dont you use the graphical way?
system-->Administration-->Update Manager

---

### Post by marko_4454 on 2007-04-21
just for reference, the right command is:

```
gksudo 'update-manager -c -d'

```

---

### Post by jiminycricket on 2007-04-21
There's also the command line upgrade-maanger

sudo apt-get install update-manager-core
sudo do-release-upgrade

from: [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by old_geekster on 2007-04-21
I have used the following command to upgrade twice:

sudo update-manager -c -d

It worked great both times.

---

