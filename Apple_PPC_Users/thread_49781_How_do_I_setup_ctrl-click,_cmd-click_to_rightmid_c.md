---
title: "How do I setup ctrl-click, cmd-click to right/mid click for ibook"
date: 2005-07-17
forum: Apple PPC Users
---

### Post by ninotob on 2005-07-17
I have an old graphite ibook setup to dual boot.  The trackpad is of course, a single button monstronsity.  Anyway, in OS X, right click is done by pressing ctrl-click, and middle click by pressing cmd-click.  In ubuntu, middle click is automatically set up as F11 and right click as F12 (all I'll say is:  grrrr).  I want to use the same method for clicking regardless of which OS I'm using.

**Question:**
How can I enable ctrl-click, cmd-click for my single button ibook trackpad? 

**Here's what I've tried:**
After some googling, I ran across this:
 [http://ubuntuforums.org/archive/index.php/t-24868.html](http://ubuntuforums.org/archive/index.php/t-24868.html)

OK, easy enough, I'll just figure out what the code is for ctrl and cmd and modify /etc/sysctl.conf

I tried running "showkey" in the console as suggested, except something goes haywire.  It's as if the enter key is continuously being pressed -- even after the program ends, the prompt scrolled continuously as if I had a weight on the enter key.  The worst part, mousing over things sometimes triggered the application.  Doing a ctrl-alt-backspace was about all I could do to get control back.  

Still wanting the info, I ran showkey but redirected output to a file -- didn't help with the constant enter key problem.  After killing X again, I looked at the file it created -- it told me ctrl=0x9c and cmd=0x9d.  I converted those to decimal (156, 157) and modified sysctl.conf as suggested in the above link.  I rebooted and was sorely dissapointed to find that ctrl-click, cmd-click did absolutely nothing.

I've also tried googling for a table of key values, but my google-fu apparently isn't black belt level.  Any suggestions on what I should try next, or where I went wrong, would be most appreciated.

---

### Post by gruepig on 2005-07-18
I seem to recall "showkey" has to be run in a console (e.g., tty1), not from a terminal within X.  On my system, I can switch to a console with ctrl-option-fn-F1 and back to X with option-F7.

---

### Post by ninotob on 2005-07-18
[QUOTE=gruepig]I seem to recall "showkey" has to be run in a console (e.g., tty1), not from a terminal within X.  On my system, I can switch to a console with ctrl-option-fn-F1 and back to X with option-F7.[/QUOTE]

So that's the issue -- I would presume the character codes I got were ok though.  Sadly, I can't test that out right now -- I ended up tweaking something in a bad way and I have to start over w/ both installs.  To top it off, my CD is dead -- at least I I can install OS X via target disk mode, and I figured out how to setup a netboot server a while back for the ubuntu half.  In any event, it will be a while before I'm back to this question.  :-(

---

