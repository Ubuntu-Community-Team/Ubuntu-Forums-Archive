---
title: "Some Minor Problems - Gutsy Gibbon"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by BarfBag on 2007-10-21
I installed Gutsy Gibbon on two PC's - a fairly recent AMD Athlon 64 desktop (2 GHz) and my brother's laptop; a Celeron (700 MHz).  This was a clean install on both machines.

The first problem I'm having is probably a bug, as it affects both computers.  On my desktop, the start-up screen is at a massive resolution.  My monitor is from the stone age, so it looks terrible and causes my monitor to act weird.  On the laptop, the start-up screen doesn't even show - just a blank screen.

My second problem is more of a question.  Is there a Compiz Manager (like Beryl Manager) where I can mess with the settings and stuff graphically?

My third problem is the performance on the laptop.  This laptop used to run Feisty Fawn, and performance was never an issue.  With Gutsy Gibbon, packages take longer to start. there's a delay whenever I close a window, and the GNOME desktop takes much longer to start.  I made sure that Compiz wasn't running, stopped the indexing, etc.  None of this made much of a difference.

---

### Post by magli on 2007-10-21
For your second problem/question, you want to install compizconfig-settings-manager. Either search for it using the synaptic package manager, or use the command line:
```
$sudo apt-get install compizconfig-settings-manager
```
You will then fiond it under **System->Preferences**

---

### Post by aktiwers on 2007-10-21
Maybe you should go to System => Preference => Appearance 

And disable your Desktop effects..  I think that will help on question 3.

---

### Post by limac on 2007-10-21
I also am kinda curios about the second problem and if i put that command in this is what is says:

ron@limac:~$ $sudo apt-get install compizconfig-settings-manager
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ron@limac:~$ 

so should I try it using synaptic?

---

### Post by BarfBag on 2007-10-21
Thanks for the help with Compiz.  My question about the start-up screen is still pending, though.

> **limac said:**
> I also am kinda curios about the second problem and if i put that command in this is what is says:

ron@limac:~$ $sudo apt-get install compizconfig-settings-manager
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ron@limac:~$ 

so should I try it using synaptic?

Try restarting.  That happened to me once, and restarting fixed it.

---

### Post by cfaulkner on 2007-10-21
> **BarfBag said:**
> 

My second problem is more of a question.  Is there a Compiz Manager (like Beryl Manager) where I can mess with the settings and stuff graphically?



[http://ubuntuforums.org/showthread.php?t=585996](http://ubuntuforums.org/showthread.php?t=585996)

---

