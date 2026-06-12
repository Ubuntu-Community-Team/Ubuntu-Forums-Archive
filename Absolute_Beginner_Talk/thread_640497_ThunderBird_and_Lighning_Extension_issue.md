---
title: "ThunderBird and Lighning Extension issue"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-14
Hi.... I'm currently running ThunderBird version 2.0.0.6
and can't seem to get the Lightning Calender Extension
to work correctly.  The Extension installs just fine but doesn't
function properly.  Is anyone else have issues with
ThunderBird version 2.0.0.6 and Lightning Calender Extension
Version 0.7

Both these work fine together in Windows XP Pro 
but we're trying to get away from Windows  :)

---

### Post by philinux on 2007-12-14
I've got the same versions and they're running fine. What is not working. Maybe i can try to replicate whats going on.

---

### Post by Orbital75 on 2007-12-14
Well, for one when Lighning is installed all the View Icon buttons
at the top tool bar do not function. When I use the Mail Calender
button icons at the bottom of the screen they switch the view but
when I come back to the mail portion there is just a column of
Gray instead of my Calender bar.  I can't change views at all
Month, Day, Week, ect...... Here is the bigger I can't add anything,
it seems the calender just doesn't work.  Thanks for your help :)

[IMG]http://img262.imageshack.us/img262/2522/screenshotlightoz5.png[/IMG]

[IMG]http://img262.imageshack.us/img262/6203/screenshotlightiifm7.png[/IMG]

---

### Post by philinux on 2007-12-14
This is how mine looks and it works no bother -for now anyway.

Maybe uninstall and reinstall might help. Have you any other addons that might be conflicting. I've only got webmail .

---

### Post by LowSky on 2007-12-14
try swiftdove... its a linux project that make thunderbird/lightning work better on linux enabled mahines

---

### Post by Orbital75 on 2007-12-14
Well, I have tried reinstalling it but that doesn't seem to help...
I have a few extensions installed that may or may not have caused
an issue.  The extensions I have installed are WebMail with the
Yahoo and an extension called xsearchbar.

 xsearchbar makes the Search Boxes appear like they did
back in version 1.5.  I know this sounds like a bad program
but it not, its in the Mozilla projects. 

I've tried reinstalling Lightning with the xsearchbar disabled
and uninstalled but neither way worked..... I really depend on
Lightning and need to get it working.

---

### Post by tzd on 2007-12-18
I'm having the exact same issues as Orbital75. I'm on Kubuntu Gutsy with latest official release of both lightning and Thunderbird. 
I have a few add-ons such as "signature switch", "currency converter", "foxclocks" and two more which i can't remember now.

I thought I used version 3.0a of thunderbird when I was on my XP pro after this failure with lightning and version 2.x of thunderbird.
Now I'm stuck with 3.0a since I'm currently unable to uninstall it (posted another topic regarding this).

Hopefully someone can help me uninstalling version 3.0a so that I can reinstall 2.x and troubleshoot/help on this matter.

---

### Post by weigh2tall on 2007-12-28
I was having the same problem after doing a fresh install of Gutsy Ubuntu and was being told that 

> Lightning extension for Thunderbird/Icedove cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type

I found this post 
[http://eccentric.cx/wordpress/](http://eccentric.cx/wordpress/)

And ran this command in terminal
```
sudo apt-get install libstdc++5
```

And Lightning at least has the correct appearance.  I haven't fully tested it.  I wish the error description had been a little more accurate.  Hope this helps!

Edit ... w/o restarting I still get the error message from Ubuntu's Add/Remove program, but installing the Lightning available from Mozilla's site seems to have worked fine

---

