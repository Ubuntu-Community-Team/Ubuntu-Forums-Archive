---
title: "stop firefox3 from auto loading tabs at launch"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by lenticular on 2008-04-17
Ok, this has to be some easy switch that is staring me in the face.

Under Gutsy, firefox3 used to ask about restoring an old session or starting a new one at launch.  Now, it just automatically reloads my last session, tabs and all.  I have firefox (v3 beta4) set to show a blank page at launch.

The "restore previous session" dialog box was semi-annoying, but seeing my old sessions restored without being asked goes beyond that.

Can someone give me a pointer to how to change this, please?

Thanks,
  John

---

### Post by joshrobinson on 2008-04-17
so you want it to ALWAYS start a new session? and never load tabs?
and not ask you what you want to do at start?

---

### Post by lenticular on 2008-04-17
Yes, that would be ideal.  Once every 50 launches or so it is convenient to have the option to restore, but I would rather do without it.  Worse still is having a forced restore and having to kill all the tabs that I no longer care about.

Thanks,
 John

---

### Post by joshrobinson on 2008-04-17
type this into your address bar

about:config

click the "ill be careful i promise" button

scroll down and find this line
browser.sessionstore.enabled   at the end of the line where it says true double click it so it switches to false

close your browser and re-open it
open a bunch of tabs, close it and open it back up to make sure its what you want

---

### Post by lenticular on 2008-04-17
Wonderful!  That's just what I was looking for.  Thanks so much.

-John

---

### Post by joshrobinson on 2008-04-17
> **lenticular said:**
> Wonderful!  That's just what I was looking for.  Thanks so much.

-John

your welcome

---

