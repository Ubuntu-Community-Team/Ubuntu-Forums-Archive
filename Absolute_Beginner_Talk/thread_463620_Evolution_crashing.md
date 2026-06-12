---
title: "Evolution crashing"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by p_quarles on 2007-06-03
For whatever reason, Evolution is very unstable on my system. By and large, it works okay, but I've found that during some sessions it crashes after I hit "reply." This is easily fixed by forcing a quit and restarting. Today, however, one of my accounts (IMAP server) seems to be having problems, and Evolution completely freezes when it tries to check in. Completely freezes = I have to restart GNOME to quit Evolution. 

I'm currently switching back to Thunderbird (which I used under Windows), but I do like Evolution because it comes preconfigured much more to my liking. The only other things I saw on the forums had to do with Evolution crashing instantaneously, every single time, and that is definitely not happening here. 

(Specs, FWIW: 2 Pentium M 2.8Ghz processors, 1G memory, Intel graphics controller)

---

### Post by jiminycricket on 2007-06-03
Does the crash reporter apport start when Evolution crashes? (and do you let it report to Launchpad)?  Do you see any specific errors if you run Evolution from a terminal?

---

### Post by p_quarles on 2007-06-03
To the first question, no: it just freezes and doesn't do anything. Nothing else happens after I do a force quit.

And I've never run Evolution from terminal. I'll try that, though, after the IMAP connection gets fixed. For now, I'll just wade through the extensions and get Thunderbird working like it should (grumble).

---

### Post by p_quarles on 2007-06-04
Okay, I ran Evo from the terminal, and did in fact get a couple error messages:
> (evolution-2.10:22445): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:22445): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'

Both have to do with junk filters, I'm guessing. Could either of these things make the entire program so prone to freezing up? Thanks in advance.

---

