---
title: "[SOLVED] Password prompt"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Ryutatsu on 2008-04-20
I'm trying to make a launcher for encfs but it won't work because encfs requires a special password (not the root password so gksu or sudo won't work) is there any way I can make the launcher create a dialog box to enter the password?

---

### Post by sdennie on 2008-04-20
You can actually use gksudo I think.  Doing this prints a gksudo style dialog on the screen and then prints the password to stdout.

```

gksudo --print-pass --message "Enter password for some application"

```

If you are using some command that accepts a password on the commandline, you could use it like this:

```

some_command --password `gksudo --print-pass --message "Enter password for some application"`

```

I've never used that in practice but, I just tried it from the commandline and it seems to work as expected.

---

### Post by Ryutatsu on 2008-04-20
Sorry, that doesn't quite work. It asks for a password but only from the command line, the dialog box doesn't show up from the launcher. Even when it does show up encfs doesn't recognise the --password as a valid option and simply asks for the password again in the command line.

---

### Post by sdennie on 2008-04-20
You may have to make a script and have the launcher use that script.  I don't know what the command line arguments are for encfs (I just guessed about the --password) but, `gksudo --print-pass --message "Enter password for some application"` will evaluate to whatever password you enter in the dialog so, you can just put that in the spot where you would have normally hardcoded a password in.  Hope that helps.

---

### Post by Ryutatsu on 2008-04-21
Thanks for all of your help. What I've ended up doing is actually create two .sh files. One calls encfs with the -extpass=progarm option set to get the password from the other .sh file that contains your gksudo command.

---

