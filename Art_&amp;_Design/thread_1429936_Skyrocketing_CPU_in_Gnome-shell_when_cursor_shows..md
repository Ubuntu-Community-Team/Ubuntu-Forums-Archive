---
title: "Skyrocketing CPU in Gnome-shell when cursor shows."
date: 2010-03-14
forum: Art &amp; Design
---

### Post by hxcobd on 2010-03-14
This problem is rather weird, and I don't recall it happening before I reformatted my computer.

I've installed Gnome-shell and used a few different techniques to boot into it directly, without needing to open a terminal to start it.

However, all of the techniques that boot directly into Gnome-shell leave my mouse cursor invisible when I mouseover the Activities menu or top menu bar. 

Then, when I Alt+F2 and run a Restart, the cursor becomes visible, but my CPU usage skyrockets to 85% or higher and stays there for the entire session.

Anyone had this same issue?

---

### Post by hxcobd on 2010-03-14
Problem solved yet again... God, I am a genius.

The two following methods did NOT work properly, and on my particular setup, caused CPU usage issues:

1.) [http://ubuntuforums.org/showpost.php?p=8158674&postcount=7](http://ubuntuforums.org/showpost.php?p=8158674&postcount=7)

2.) [http://live.gnome.org/GnomeShell/DistributionPackages](http://live.gnome.org/GnomeShell/DistributionPackages)

However, what DID work was a combination of the following:

1.) [http://ubuntuforums.org/showpost.php?p=8155154&postcount=6](http://ubuntuforums.org/showpost.php?p=8155154&postcount=6)

2.) Upon rebooting, Gnome-Shell DID load, but the cursor was still invisible. However, after running an Alt+F2 'Restart' this time, the cursor became visible and CPU usage remains low.

I'm led to conclude that as long as you're using the 'gnome-shell --replace' command at some point in your Gnome-shell login process, you shouldn't have any problems with CPU usage. This might be because without using this particular command, Gnome-WM is still running in the background? Not sure.

One thing I noticed between using the 2 non-working techniques and my 2-step technique is that if you open System Monitor while in Gnome-shell using the 2 non-working ones, right under Mutter, there seem to be 3-4 blank-named processes turning on and off randomly.

However, if you use the 'gnome-shell --replace' command, these unnamed processes never start at all.

---

