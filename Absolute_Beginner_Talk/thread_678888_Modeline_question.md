---
title: "Modeline question"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by glaurens on 2008-01-26
Hi,

I've been reading the modeline posts and have been to some of the tools, i.e. xtiming. Everywhere I run into warning about how the wrong modeline can be very bad for you monitor, and would prefer not breaking my plasma.

My questions are:
1. Is there a max length to a vga cable and does it start losing quality at say, 15 metres?
2. Will the modeline make a difference if you are running a S-Video connector?
3. Is there any way to find out what the dot/pixel  clock frequency is for my screen if it is not in the documentation.
4. Exactly how dangerous can an incorrect modeline be?
5. Will a modeline work on plasma, or is it only for LCD?

Thanks in advance.

---

### Post by dcstar on 2008-01-26
> **glaurens said:**
> Hi,

I've been reading the modeline posts and have been to some of the tools, i.e. xtiming. Everywhere I run into warning about how the wrong modeline can be very bad for you monitor, and would prefer not breaking my plasma.

My questions are:
1. Is there a max length to a vga cable and does it start losing quality at say, 15 metres?
2. Will the modeline make a difference if you are running a S-Video connector?
3. Is there any way to find out what the dot/pixel  clock frequency is for my screen if it is not in the documentation.
4. Exactly how dangerous can an incorrect modeline be?
5. Will a modeline work on plasma, or is it only for LCD?

Thanks in advance.

About a million years ago there were **some** badly designed CRT monitors that really didn't like being fed signals that their designers didn't expect, and apparently some of them failed when given incompatible refresh rates etc.

A lot of people now using Ubuntu were either children (or not even born) when this was a current problem, but (as usual, with a lot of things in IT) the "problem" apparently still exists in some people's minds.

If any monitor manufactured in the last 10 years breaks if given an incompatible signal, then I don't know about it.

The command **gtf** generates modeline data, do a **man** on it for further information as it should be all you will need.

---

