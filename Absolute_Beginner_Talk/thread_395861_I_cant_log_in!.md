---
title: "I cant log in!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-03-28
Ubuntu gets to the login screen but when I type in my username and password I get the error:

User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  Tile should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

I tried changing the session and language in the options but it doesnt work.  When I login it just takes me back to the login screen.  The only session I can log into is the failsafe terminal.

Please help me :(

---

### Post by dfreer on 2007-03-28
From the failsafe terminal try entering this command:
```
sudo chmod 644 -Rv ~/.dmrc
```

---

### Post by Brucey on 2007-03-28
I tried it and it said that the .dmrc was changed but I still get the same error.

---

### Post by ComplexNumber on 2007-03-28
the dmrc error is misleading. it's nothing to do with that file, but usually points to incorrect permissions or ownership on the home directory. login using failsafe terminal (although you may have little option otherwise at the moment) and try the following:
i'll assume that your username is Brucey.
** sudo chown[COLOR=White]....[/COLOR]Brucey:Brucey[COLOR=White] ....[/COLOR]/home/Brucey**

then try logging in. if that doesn't work, try the following (although the above will usually automatically change the permissions anyway):

[B] sudo chmod[COLOR=White]..[/COLOR]700[COLOR=White]...[/COLOR]/home/Brucey


[/B]
it can also be a problem with the root directory, but we'll try the above first.


btw did you change anything significant that may have caused tis?

---

