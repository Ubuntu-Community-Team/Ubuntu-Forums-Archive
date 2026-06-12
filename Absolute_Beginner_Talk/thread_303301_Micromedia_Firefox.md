---
title: "Micromedia Firefox"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by 0m3n on 2006-11-20
hey im completley new to linux and i just got it installed and everything on my computer like 10min ago... well my problem is when i went to myspace... firefox asked (at the top of the page) if i wanted to install a new plug in for micromedia... i clicked install and it restarted firefox, so when i try to go into myspace now it crashes firefox... anyone know how i can fix this? thanks in advance

---

### Post by DigitalAxis on 2006-11-20
Ok, first I'm going to try to help you fix it, then I'm going to tell you how to avoid this happening again.

-----------------------------------------------------------

Open Synaptic (I'm using Xubuntu so this is probably the hardest part of my instructions).  I think it's in administration, may be called 'add/remove programs' and you may have to click on the 'advanced' tab...

If you can't find it, try hitting Alt-F2 to bring up a 'run' command, and type **gksu synaptic** and hit enter.  You'll get a prompt asking you for your username and password.  Enter them and go on.

Now, once Synaptic has loaded, you need to go to Settings, then 'repositories', then on the 'internet' tab, check the box marked 'software restricted by copyright or legal issues (multiverse) and hit CLOSE (not revert)

It will tell you you have to reload.  Hit the reload button at the top.

Then hit the search button, and search for **flashplugin**.  Find the thing marked 'flashplugin-nonfree', right-click it and select 'mark for installation'.  Once you've gone through that, click the apply button at the top.  This may (will?) ask you a question about downloading the flash plugin from Macromedia.

Now exit Synaptic, and try Firefox.


If that doesn't work, re-enter Synaptic ( Alt-F2, gksu synaptic) and search for firefox.  There should be an installed one, version 2.0+0dfsg(etc).

Right-click on it and select 'Mark for reinstallation'.  Then click apply again, and try again.


-----------------------------------

The problem here is that Ubuntu prefers working from its own software repositories.  You may have noticed a lot of options in Synaptic- there are THOUSANDS of programs available for Ubuntu, all accessible through Synaptic, and all freely installable.

This is a different way of doing things compared to Windows; it means you can't (usually) wander around the internet downloading programs, and install them later... but on the other hand most of the time you won't need to.  

As an added bonus, if there are any updates to your programs you don't have to go hunting for them; the Update Manager will let you know, and generally all you have to do is click 'apply' and it will update your system.

This is sorta like Windows Update, but for *all* software.

What I did have you activate another software repository that happens to have a version of Macromedia's Flash plugin available for install.  There's another one, Universe, you also might want to activate.  That repository contains *thousands* of extra programs.

---

### Post by 0m3n on 2006-11-20
do i check the box that says "Do you accept the License and do you want to download the flash plugin now?"

---

### Post by DigitalAxis on 2006-11-20
Yes.

---

### Post by 0m3n on 2006-11-20
i did everything u said and i even reinstalled it and it did the same thing :(

---

### Post by 3rdalbum on 2006-11-20
If you have any bookmarks that you want to save, copy down their URLs now.

Go into the terminal and type:

```

rm -rf .firefox
rm -rf .mozilla

```

(there's a GUI way to do it, but it's just easier to give commands)

Then open Firefox again. You may need to install the Flash plugin again from the repositories; do that and try Myspace again.

---

### Post by 0m3n on 2006-11-20
did what u said and that also didnt work :( my bookmarks were gone but the problem is still happening... could the micromedia be on my computer instead of firefox itself?

---

### Post by navneeth on 2006-11-20
I just solved this problem about a half an hour ago on my computer. I have Automatix installed, and I installed the Flash plugin for Firefox available in it. Now, all Flash-pages works fine.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

