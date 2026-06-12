---
title: "shell scripts?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by siterock on 2008-03-02
I'm trying to install two games.  The installers have the file extension .sh which I think I've figured out means they are shell scripts.  Anyway, I opened my terminal and tried the command that was given at the game's website:

sh ./filename.sh

I made certain that I was in the same directory as the installer files, but no go.
Any help?  I hope I described my problem clearly enough.  BTW, I tried sudo, but that didn't work, either.  Thanks in advance for your time and help.

---

### Post by Whiffle on 2008-03-02
One possibility is that the scripts you downloaded aren't marked as executable.  Try this:

chmod +x filename.sh

and then try to run it agan, either with
sh filename.sh

or

./filename.sh

---

### Post by Joeb454 on 2008-03-02
If you don't want to use the terminal you can right click the file in your file browser, and choose permissions>make executable.

Just letting you know the alternative :p

---

### Post by scottro on 2008-03-02
Actually, if you're doing sh filename.sh you probably don't even have to make them executable.  If, while in the same directory, you do ./firename.sh, then you probably do.

Try doing it without the ./.  In other words, just do

sudo sh filename.sh

(I say use sudo because if it's installing something, the chances are that you'll need sudo.)

---

