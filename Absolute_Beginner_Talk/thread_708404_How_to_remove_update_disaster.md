---
title: "How to remove update disaster?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by pointyblue on 2008-02-26
Aaargh!

My Ubuntu 7.10 just autoupdated and now Evolution email doesn't work! (It opens, then closes again instantly...) :confused:

Haven't got the faintest idea what was updated, I just accepted the prompt to update the system and continued working on something else.

How can I find out what was updated - and how do I restore the computer to the state it was in prior to this update?

**If only Ubuntu had a System Restore option like MS Windows'!** (Probably should have kept XP... :( )

---

### Post by Joeb454 on 2008-02-26
Open up a terminal from Applications>Accessories>Terminal

And then type ```
evolution
``` when it exits, it will give some output back to the terminal. Could you copy this onto a new post back here :) It might help us figure out what's wrong.

Also make sure to check your updates next time ;)

---

### Post by pointyblue on 2008-02-26
From terminal:

> sm@sm-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:14729): DEBUG: mailto URL command: evolution %s
** (evolution:14729): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)
sm@sm-desktop:~$ 


I think it might have been a language update. (Danish.)

Thanks for helping out!

---

### Post by philinux on 2008-02-26
The updates were language packs today.

I'd reinstall spamassasin via synaptic.

---

### Post by TVu on 2008-02-26
That same update switched my system default language to English, without the possibility going back to my native Finnish. Go figure.

---

### Post by pointyblue on 2008-02-28
Hmmm... Removed Spamassassin via Synaptic, restarted computer and Evolution still didn't work.
Then I reinstalled Spamassassin, restarted - and Evolition still shut down instantly.
Changed the language of the computer from Danish to US English, restarted - and it still doesn't work.

**Please **share all your ideas on what is wrong and how to fix it.

In the quarter of a second Evolution is open before closing down again I can see my inbox an all the mails in it. So I guess they're ok and stored somewhere on the computer.

I really need to gain acces to those emails, do any of you know where on the machine they are stored? Thought I'd backup the folder containing the emails, then remove and reinstall Evolution and restore the back up

 Do you think I'd be able to access the emails from the "new" Evolution?


Oh, by the way, even after removing Spamassassin via Synaptic I still get

```
sm@sm-desktop:~$ evolution
CalDAV Eplugin starting up ...
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:5720): DEBUG: mailto URL command: evolution %s
** (evolution:5720): DEBUG: mailto URL program: evolution
Segmentation fault (core dumped)
sm@sm-desktop:~$ 

```

in a terminal, so I guess Evolution still tries to start Spamassassin... Strange.

---

### Post by pointyblue on 2008-03-02
Anyone?

---

### Post by TVu on 2008-03-03
I'm pretty sure this won't help you at all, but my problem with that particular update was fixed by reinstalling locales-package.```
sudo apt-get install --reinstall locales
```

---

### Post by pointyblue on 2008-03-09
Thanks for trying to help out.

I decided to go with Vista on this machine in stead of Ubuntu. I feel linux isn't safe enough for important data until there is a system restore option as MS Windows'.

Still running Ubuntu on my other PC though - just not on the one for important data.

---

### Post by handydan918 on 2008-03-09
If it's not too late, I would suggest either re-installing (via synaptic) your evolution package, or maybe try sudo dpkg-reconfigure evolution

---

