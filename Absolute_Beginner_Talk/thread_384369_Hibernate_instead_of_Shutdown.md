---
title: "Hibernate instead of Shutdown ?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by herbster on 2007-03-14
I typically use my PC during the day/evening, shut it down at night and turn on again in morning to check stuff before I go out, and leave it on all day. So it's basically on all day/off at night. I'm wondering if I even need to shut it down? Couldn't I just put it in Hibernate through the night, hit power button in the morning and I'm back in?

Do I ever even need to turn it off? (of course technical situations excluded).

---

### Post by davmac on 2007-03-14
I very rarely shutdown my laptop - I just hibernate. Once it has hibernated the machine is off (i.e. in exactly the same state as if you'd shutdown) it is just that when you power on again it'll pick up exactly where it left off.

Hope this helps,

Dave Mac

---

### Post by SoggyCornflake on 2007-03-14
> **herbster said:**
> I typically use my PC during the day/evening, shut it down at night and turn on again in morning to check stuff before I go out, and leave it on all day. So it's basically on all day/off at night. I'm wondering if I even need to shut it down? Couldn't I just put it in Hibernate through the night, hit power button in the morning and I'm back in?

Do I ever even need to turn it off? (of course technical situations excluded).

I used to test BIOS releases for a laptop manufacturer.  I found that Hibernate and suspend tended to have more problems than rebooting.  When a unit is hibernating, it has to save configuration information just prior to shutting down the computer/laptop.  There are ocassions where the computer locked up becuase something didn't store quite right so it couldn't recover from a hibernation.

Granted my experience was in testing Windows Installations rather than Linux your results my vary, but as for me, I don't trust suspend/resume or hibernate/restore very much

---

### Post by herbster on 2007-03-14
I just remembered that the last few times I used Hibernate and came home, my USB wasn't working. What is up with that? An Ubuntu bug or something wrong with my configuration?

---

### Post by SoggyCornflake on 2007-03-14
> **herbster said:**
> I just remembered that the last few times I used Hibernate and came home, my USB wasn't working. What is up with that? An Ubuntu bug or something wrong with my configuration?

My vote is to blame it on the BIOS.  See my previous post.  USB got the meaning "Usually System's Broken"  at that company.  We found that USB devices typically would lock up about 1 out of 10 times.  There were better devices and sometimes a new BIOS would fix it, but we would do 50 suspend/resumes followed by 50 hibernatios/restores to weed out those kind of problems.

---

### Post by V-600 on 2007-03-14
In normal use I only hibernate my laptop as its so slow to boot up. It has never had any problems with this. My desktop PC has never hibernated successfully.

in my experience you should have no probs using hibernate rather than turning your comp off....if it works successfully. This depends a lot on your hardware but good luck with it if you can do it.

I still turn laptop off from time to time to let programs like fsck do their thing but that also has no more problems on the laptop in constant use than the desktop.

---

