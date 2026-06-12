---
title: "run a command upon log in?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by DecemberWinds on 2008-01-14
Every time I log in I type in compiz --version into terminal to make my window title bar normal size.

Is there a way I can make this just run when I start up. I tried adding something to sessions where the "command" box is "compiz --version" but there is no change.

Any help would be much appreciated! :)

---

### Post by HermanAB on 2008-01-14
Add the command to the bottom of ~/.bash_profile

Cheers,

Herman

---

### Post by DecemberWinds on 2008-01-14
hmm... when I do sudo gedit ~/.bash_profile I get a blank text editor...?

---

### Post by santiagoward2000 on 2008-01-14
> **DecemberWinds said:**
> Every time I log in I type in compiz --version into terminal to make my window title bar normal size.

Is there a way I can make this just run when I start up. I tried adding something to sessions where the "command" box is "compiz --version" but there is no change.

Any help would be much appreciated! :)

Hi!
What flavor of Ubuntu are you using? In Xubuntu, all you need to do is go to **Applications/Settings/Autostarted Applications**. I think in Ubuntu is somewhere like **System/Sessions**, but I'm not really sure right now. Sorry.

---

### Post by DecemberWinds on 2008-01-14
It's ubuntu 7.10 gutsy gibbon

---

### Post by DecemberWinds on 2008-01-14
bump for help! ;n;

---

### Post by Mansfieldatron on 2008-01-14
> **DecemberWinds said:**
> hmm... when I do sudo gedit ~/.bash_profile I get a blank text editor...?

Did you add it anyway and try it out?

---

### Post by Rocket2DMn on 2008-01-14
You should be able to add a program from System->Preferences->Sessions.  Here you can Add a startup program.  Just name it something suitable and place "compiz --version" in the command line, and leave any comment you would like (for your own reference).  Then logout and log back in to see if it works.

---

### Post by jordanmthomas on 2008-01-14
> **DecemberWinds said:**
> hmm... when I do sudo gedit ~/.bash_profile I get a blank text editor...?

First off, don't use sudo to launch graphical programs (use gksudo instead)
Second, you don't need root privileges to edit your own file.

```
gedit ~/.bash_profile
```
If it's blank that simply means it doesn't exist (or is empty)
It's not a problem.  Edit away and save as usual.


Lastly, compiz --version doesn't actually DO anything except print what version of compiz you run.  How on earth can this possibly fix a problem.  I'm not denying it works for you, but it is certainly odd.

---

### Post by Rocket2DMn on 2008-01-14
It is odd, but I have heard people use it before.  Seems like "compiz --replace" would make more sense.  Is the bash stuff executed at a GUI login?  Otherwise "~/.profile" might do it, too.  I would recommend going through the GUI like I suggested with Sessions, but use whatever you're most comfortable with.

---

### Post by jordanmthomas on 2008-01-14
> **Rocket2DMn said:**
> It is odd, but I have heard people use it before.  Seems like "compiz --replace" would make more sense.  Is the bash stuff executed at a GUI login?  Otherwise "~/.profile" might do it, too.  I would recommend going through the GUI like I suggested with Sessions, but use whatever you're most comfortable with.

No, I don't think the suff in .bash_profile will run like expected.
I'd go with the session properties as well if I was using gnome.

Usually I use startx to start x, so it's a bit easier there.  :)

I was just trying to save him some trouble he'd have later if he tried editing his .bash_profile.

---

### Post by nikoPSK on 2008-01-14
in the bash text file?

---

### Post by Rocket2DMn on 2008-01-14
> **nikoPSK said:**
> in the bash text file?

One of them.  There can be .bashrc, .bash_login, .bash_logout, .bash_profile, .bash_history, and possibly some others.  Let's stop talking here so the OP can fix his problem and not have to filter through this stuff :)

---

