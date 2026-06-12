---
title: "Got too Click Happy"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by TehMark on 2007-01-24
Hey guys.  First off I'm a newbie on ubuntu and linux in general.  Anywho..

I go too click happy with changing options with Beryl and now my PC freezes after I see the splash screen for the app.  I can get into terminal but I'm not sure how to stop beryl from running on startup via console mode.  I'm sure if I could stop it from auto loading that I could get into its settings to unclick a few of the extra things I turned on.  So I need to get that thing out of my sessions startup section.  Any ideas?

---

### Post by dbbolton on 2007-01-24
does gmd still work ?

if so, from the log-in screen, choose Options > Sessions > Failsafe Gnome
it's a gnome session, but doesn't run any of your start up scripts

if not, you might need to unintall beryl via aptitude, or reset your x configuration.

---

### Post by annda on 2007-01-24
if nothing helps, you can also delete the hidden .beryl directory from your home to remove the wrong settings.

---

### Post by energiya on 2007-01-24
From console write
```

killall beryl

```

or

```

ps -C beryl

```
and remeber the PID
```

sudo kill -9 <PID>

```

or

```

top

```
find beryl and press k. It will ask you for the pid.

The choise is yours.
(I have never installed beryl and don't know if you should be using "beryl" as command name)

---

### Post by autocrosser on 2007-01-24
After logging in as the prior post suggests, trash your .beryl folder in your users folder. This will go back to the default Beryl Settings or in a terminal you can:
 
[LEFT]rm ~/.beryl [/LEFT]
 
[LEFT]to reset Beryl ( this command will trash your preferences folder also)[/LEFT]

---

### Post by TehMark on 2007-01-24
Sweet!  Thanks for all the reply's.  I'll try this when I get home from the office.  Cheers!

---

