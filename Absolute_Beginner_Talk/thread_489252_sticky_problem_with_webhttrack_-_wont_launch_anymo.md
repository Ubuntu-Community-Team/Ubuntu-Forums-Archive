---
title: "sticky problem with webhttrack - wont launch anymore"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by fsando on 2007-07-01
I can't get webhttrack to work without opera.
I had everything working - I could click on webhttrack in the menu - it would start up in firefox. Then I installed opera some time ago. I noticed webhttrack started to use opera instead. Now uninstalled opera and webhttrack stopped working.
starting from console a strange text based browser comes up, complaining about no javascript.
After stopping it this is left in the console:
(had to use ctrl-c after 'waiting for browser to terminate')
```
$ webhttrack
/usr/bin/webhttrack(2329): launching /usr/bin/www-browser
/usr/bin/webhttrack(2329): spawning regular browser..
Can't open history
/usr/bin/webhttrack(2329): waiting for browser to terminate..

/usr/bin/webhttrack(2486): nasty signal caught, cleaning up..
/usr/bin/webhttrack: line 152:  2501 Killed                  ${BINPATH}/htsserver "${DISTPATH}/" path "${HOME}/websites" lang "${LANGN}" $@
/usr/bin/webhttrack(2486): ..done

```

---

### Post by rapolas on 2007-07-01
I think you should go to system -> preferences -> prefered applications and then choose your browser...

---

### Post by fsando on 2007-07-02
> **rapolas said:**
> I think you should go to system -> preferences -> prefered applications and then choose your browser...
Yes I thought about this but it's been set to firefox all the time - it never was set to opera - rather strange.
Is there a way to change configuration for webhttrack? I can't seem to find its configuration files anywhere.

---

### Post by daktari on 2007-07-21
I don't use webhttrack often enough to give even precise timing info, but it stopped working on my box* within the past four to six months following one of several lts auto-updates.  Tried uninstalling and reinstalling webhttrack but with no effect (synaptic / add-remove), in both firefox 1.x AND 2.x environments.  I've never used another browser on this box, so that may at least narrow the field a bit.

As mentioned above, webhttrack - when it was working - opened in a firefox window ( its listed in my GUI Applications->Internet menu ).  Clicking on the icon since it went gimpy now produces only a flicker of the HD idiot light - no other observable system reaction.

/

*my box =
dapper lts (only - no other OS on the box)
firefox (only - versions 1.x and 2.x - no other browser on the box)

---

