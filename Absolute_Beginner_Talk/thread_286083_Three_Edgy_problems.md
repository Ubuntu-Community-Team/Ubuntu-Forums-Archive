---
title: "Three Edgy problems"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by BarFly on 2006-10-27
Here is a screenshot of what I get in the update manager:  [http://img108.imageshack.us/img108/8360/screenshotlb1.png](http://img108.imageshack.us/img108/8360/screenshotlb1.png)
Why does it list two items which I cannot select but says my system is up to date?

Also, and unrelated, I did not get FF 2.0 with the upgrade.  Perhaps this is because I ditched the Ubuntu version for the real version via Automatix (which is no longer installed).  I have the tarball, can extract it and it works ok.  Just I want to update the old one and do not know how.  I don't really want it in my home directory and cannot figure out how to install it anywhere else.  "which firefox" reveals /usr/bin/firefox.  When I "sudo firefox" and try to update, it says FF is up to date.

And, FF 1.5.07 keeps crashing on me.  This happens when I choose "save link as."  This never happened in Breezy or Dapper.  Maybe if I found a way to install 2.0 this would be solved.  I don't know.

Any help would be appreciated.  Besides these issues, I am happy with Edgy.

---

### Post by BarFly on 2006-10-27
I hate to do this as it is annoying, but here it goes:
Bump.

---

### Post by bulldog on 2006-10-27
Try ```
sudo aptitude dist-upgrade
``` and see if you get some error messages.

When updates where hold back it's mostly a dependency problem.
Maybe will aptitude give you the opportunity to see whatis wrong and maybe an option to repair.

---

### Post by BarFly on 2006-10-27
Thanks!!!  Your solution worked for the update problem.  The two things listed got replaced.  I guess when I upgraded it didn't take all the way.  I don't know as I am not a Linux guru, just a user.  Now I am down to the FF problem.  I checked and it still won't upgrade.  Thanks again!

---

### Post by Metacarpal on 2006-10-27
In Synaptic (System > Administration menu) do you see Firefox listed?  It may be that the Automatix-installed version is superceding the official Edgy package.  If you see your version of Firefox in there, uninstall it.  Then you should be able to get the Edgy Firefox 2.0 from the repos.

---

### Post by BarFly on 2006-10-27
> **Metacarpal said:**
> In Synaptic (System > Administration menu) do you see Firefox listed?  It may be that the Automatix-installed version is superceding the official Edgy package.  If you see your version of Firefox in there, uninstall it.  Then you should be able to get the Edgy Firefox 2.0 from the repos.

Yeah, that does not seem to work.  I uninstalled FF through Synaptic.  Oh, what is still there?  Take a wild guess.  I can start to install FF 2.0 from the untarred version from Mozilla, and it starts installing.  Then it hangs forever on checking compatibility of add-ons (extenstions).  Ok, I got rid of my extenstions (blah will be removed once you restart Firefox).  Guess what?  All the extensions are still there.

What the hell is going on?  Do I have some sort of Linux virus?  I am very annoyed, but at least this box still works (somewhat).

---

### Post by bulldog on 2006-10-27
Uuuuuhmmm you did install your new firefox,but your menu just points to the old one.

Look where you installed the new one and make a starter for it,I bet you get the new one.

---

### Post by BarFly on 2006-10-27
bulldog, I am not trying to be an ***.  FF 2.0 is /usr/bin/firefox.ubuntu.  1.5.07 is in the same directory, but just named firefox.  I can open up 2.0 from that directory.  However, it still hangs on the checking for compatability of add-ons thing.  I went out for dinner, hoping I was just being impatient.  I came back to find a message saying "Firefox is not responding."  Note that although I was able to disable all extenstions, I cannot remove them.  Something is wrong.  And I write this with 2.0.  This sucks.

---

### Post by bulldog on 2006-10-27
Make a new profile and don't use the old one.

So you have a clean start.

---

### Post by BarFly on 2006-10-27
> **bulldog said:**
> Make a new profile and don't use the old one.

So you have a clean start.

Yeah, that worked!!!  Thanks, buddy!  Jeez, this was a frustrating experience.  The FF problem annoyed me more than the ubuntu update manager saying "Your system is up-to-date" while listing two upgrades...  Ach der leiben.  Or in English, "Ah, that is life."

If I had a place to throw all of my data and my roommate's data, I would wipe the HDD and start fresh as I get the feeling I have a bunch of garbage on my HDD that I could do without.  Ach der leiben.

---

