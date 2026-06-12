---
title: "Thunderbird, Webmail &amp; Permissions"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-17
I'm using thunderbird with the webmail extension to check my yahoo.  In the preferences - it says that in order for it to work it needs "write access to the application folder."

I'm not sure what the application folder is.  I thought it might have been "/usr/share/mozilla-thunderbird" so I gave myself write access to that folder - that didn't work though.

If I open a terminal and run "sudo mozilla-thunderbird" it runs perfectly.  However, if I click my thunderbird launcher which runs the command "mozilla-thunderbird" it doesn't work.

If changed the launcher to run the command "sudo mozilla-thunderbird" but when I click it, nothing happens.

I then changed it to run "gksudo mozilla-thunderbird" but then thunderbird opens without my data.

Anyone know how I can fix this problem?  I think the correct solution would be to modify whatever application folder it's talking about to have write access by my user account - as an alternative, perhaps I can run it as root.  

I'm temporarily running thunderbird from a terminal with sudo access.

---

### Post by solar george on 2007-03-18
Why are you using the webmail addon, yahoo allows you to access you mail through ordinary methods (pop and smtp).

---

### Post by Agent_Nappi on 2007-04-06
Hi atraeyu

I've exactly the same problem as you.
Webmail is only working fine when thunderbird is launched with gksudo.
Did you figure out another fix for that in the meantime?

I've tryed to do
```
sudo chmod -R 777 /usr/lib/mozilla-thunderbird/
```
but that also doesnt fix the isse.

All 3 Online indicators for Imap, POP3 & SMTP (in extension properties of the webmail plugin) remains red and only change status to green when starting thunderbird with gksudo as you allready said.

Any suggestions from anybody else is welcome as well :-)

Best Regards 
Agent

---

### Post by Oby on 2007-04-25
Hmm, I have configured it with ports > 1024, but still it wont work except if I sudo thunderbird.

And if I do so, the prefs.js-file is ****** up if I launch Thunderbird as a non-root again...

This is clearly a permission-error, and I hope someone knows how to fix it :-)

---

### Post by ar2000jp on 2007-04-29
I had the same problem, WebMail always says "Error" on POP3 and SMTP, so I changed the ports from 25 to 2025, and from 110 to 2110, in both WebMail extension and the account settings, and then everything worked fine with my yahoo account.
I use ThunderBird 1.5.0.10 and WebMail extension 1.0.17, and Ubuntu 7.04.

Good luck!

---

### Post by MonsterTrimble on 2007-04-29
Well, I have recently had the same issues, and still having major issues with TB 2 (I hate to say it, but stick with TB 1.5 for now! - especially with webmail+hotmail).

What I ended up doing is sudoing into konqueror - Yeah, I know, bad me - Unhiding the .thunderbird in your home folder and setting the permissions from root to everyone. Not very clean but it worked. What I will say however is to make SURE everything is under your name and not root. Konqueror missed stuff the first time around.

---

### Post by gomets11 on 2007-05-02
> **ar2000jp said:**
> I had the same problem, WebMail always says "Error" on POP3 and SMTP, so I changed the ports from 25 to 2025, and from 110 to 2110, in both WebMail extension and the account settings, and then everything worked fine with my yahoo account.
I use ThunderBird 1.5.0.10 and WebMail extension 1.0.17, and Ubuntu 7.04.

Good luck!

this worked...thanks!

---

