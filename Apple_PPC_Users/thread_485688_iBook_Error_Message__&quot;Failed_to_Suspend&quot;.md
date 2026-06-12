---
title: "iBook Error Message:  &quot;Failed to Suspend&quot;???--What's wrong?"
date: 2007-06-27
forum: Apple PPC Users
---

### Post by reh4c on 2007-06-27
On my iBook G4, I receive a notification after resuming from suspend that "the computer failed to suspend--please see the error log for details."  However, the laptop seems to have come out of suspend properly.  :???:  Does anyone else receive this message?  Is something actually broken?  Please help me get this fixed before Gutsy is released.  How can I track down the cause of this problem?  Thanks!

---

### Post by Sodki on 2007-06-27
What does the logs say?

---

### Post by reh4c on 2007-07-02
Actually, the notification bubble tells me to look in the help file (under gnome power manager) to see what could have caused the issue.  This doesn't help ID the problem.  I'll have to dig some more in the system logs.  Does anyone else with an iBook have this problem?

---

### Post by reh4c on 2007-07-04
There appear to be some issues with gnome power manager.  I added some comments and my syslog to this bug:  [http://bugzilla.gnome.org/show_bug.cgi?id=447319](http://bugzilla.gnome.org/show_bug.cgi?id=447319)
Anyone else have suspend problems/errors?

---

### Post by Sodki on 2007-07-04
> **reh4c said:**
> Anyone else have suspend problems/errors?
I do have suspend problems on my Ibook G4, but I'm on Gentoo PPC. I cannot suspend using GNOME Power Manager, but I can suspend menually or via pbbuttonsd. If I have both pbbuttonsd and GNOME Power Manager active, the computer will suspend and a bubble will appear saying that the computer could not be suspended. This is because they have the same settings and they're trying both to suspend the computer, although GNOME Power Manager is not able to.

---

### Post by reh4c on 2007-07-04
Thanks for the follow-up, Sodki.  Hopefully, the syslog output that I provided in the gnome power manager bug report will help to solve this problem.  Can you check your system logs to see if you get some of the same error messages?  If you discover any additional issues, please add them to the bug report referenced in my last post.  Thanks!

---

### Post by juanitobanana on 2008-07-18
Hello guys,

I had exactly the same problem. I went to system->power management->general and deactivated the "use sound to notify etc.."

after that it came from suspend without even giving an error message.

This might be a bug from the message feature, maybe being activated too soon. Should I post this as a bug on the gnome bug tracker?

---

