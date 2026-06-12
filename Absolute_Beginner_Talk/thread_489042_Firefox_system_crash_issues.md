---
title: "Firefox system crash issues"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by nothinghead on 2007-06-30
I posted [this thread ]("http://ubuntuforums.org/showthread.php?t=483886") regarding my problem the other day, but I have more info and new questions.

I'm running firefox 2.0.0.4 on an AMD64 Fiesty.  Sometimes, when changing tabs, loading a site, closing a tab, or closing the browser my system instantly restarts.  I get booted to a black screen with text, a normal screen in the boot process (nothing apparently related to the error) and am back at my login screen within seconds.

Firefox's "error console" doesn't give me any hints.  I've disabled greasemonkey but use the following extensions:
Adblock
Adblock Plus
Chatzilla
Conquery
Download Statusbar

If anyone has a clue about what to do to stop this, I'd like your help.  But, is there any way to really specifically log what's happening?  Because the restart is so instantaneous I don't know what will work.  The error seems random, but the longer I deal with it, I've figured out things that will cause the error repeatedly, so if there was a way to log errors instantly and save to a log even on a shutdown, that might be able to help diagnose what's going on.  

For example, I know that if I visit one specific website anytime during my browsing I will get the error when I either A) download a file or B) exit the browser.

help?

---

### Post by pyros on 2007-06-30
> **nothinghead said:**
> I posted [this thread ]("http://ubuntuforums.org/showthread.php?t=483886") regarding my problem the other day, but I have more info and new questions.

I'm running firefox 2.0.0.4 on an AMD64 Fiesty.  Sometimes, when changing tabs, loading a site, closing a tab, or closing the browser my system instantly restarts.  I get booted to a black screen with text, a normal screen in the boot process (nothing apparently related to the error) and am back at my login screen within seconds.

Firefox's "error console" doesn't give me any hints.  I've disabled greasemonkey but use the following extensions:
Adblock
Adblock Plus
Chatzilla
Conquery
Download Statusbar

If anyone has a clue about what to do to stop this, I'd like your help.  But, is there any way to really specifically log what's happening?  Because the restart is so instantaneous I don't know what will work.  The error seems random, but the longer I deal with it, I've figured out things that will cause the error repeatedly, so if there was a way to log errors instantly and save to a log even on a shutdown, that might be able to help diagnose what's going on.  

For example, I know that if I visit one specific website anytime during my browsing I will get the error when I either A) download a file or B) exit the browser.

help?

sounds like it is crashing x.org

I'd look under /var/log/ for Xorg.log files. beyond that though, I'm not sure what to suggest. does the page that reliably cause crashes have flash elements?

---

### Post by nothinghead on 2007-06-30
Yes, the page that causes eventual errors has some flash elements.

I do have a xorg.0.log and a xorg.0.log.old files, but they're big files, is there something specific I'm looking for?  The only thing that jumps out at me is this in the "old" file

> Fatal server error:
Caught signal 11.  Server aborting


---

### Post by pyros on 2007-06-30
> **nothinghead said:**
> Yes, the page that causes eventual errors has some flash elements.

I do have a xorg.0.log and a xorg.0.log.old files, but they're big files, is there something specific I'm looking for?  The only thing that jumps out at me is this in the "old" file

sounds like the right item, but like I said, I'm not really sure what to tell you.

Personally, I would uninstall flash (or whatever the free alternative is) and see if it still happens.

I also know that compiz and beryl can cause this sort of behavior.

Other than that, I'd try reposting the problem in the multimedia and video area ([http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)) since it's a problem with the xserver crashing.

---

