---
title: "My password is not being accepted"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by solo1 on 2008-03-12
Hello to all....

When I try to select my printer as the default printer, a message pops up saying "Password required"  and also "Password for cindy (that's me) on localhost?"  I put in my password, but it won't accept it.  Please help...

---

### Post by PeterJS on 2008-03-12
Are you getting an error message?

If it looks like nothing is happening, it is in fact accepting your password, it's just not giving you and visual feed back. This is a hold over security measure from the old old days of unix.

---

### Post by PeterJS on 2008-03-12
[QUOTE=solo1]Thank you so much for your help.  I need to further explain the problem.  When I closed out that window that looked like it wasn't doing anything, a new window popped up saying "Not authorized" and "The password may be incorrect."  So I guess it really insn't taking the password.....oh my.....[/QUOTE]

The not authorized one is caused by the fact that, because you closed the prompt, clearly it didn't get your password to authorize you, and I'm pretty sure that password may be incorrect one always comes up with the not authorized message.  Give it another go, if the error message shows up in the same console as the password prompt, then you know that it's a problem with it accepting your password. Any other errors could be legitimately cause by you closing the password prompt, which the system sees as canceling or intentionally not authorizing it.

---

### Post by Yumb on 2008-03-21
I'm having this same issue.  It's giving me this error from the New Printer Wizard (same as the original poster apparently).  I am most assuredly entering the password correctly, the wizard just isn't taking it.

It's my development machine at work, and I use it 8 hours a day or so, so the password is one thing I won't forget.  It's just this particular feature (printer wizard) that's the problem and it's driving me insane.

---

### Post by Trail on 2008-03-21
What if you launch the wizard with sudo/gksu? You might be already authorized, thus not ask you again for password.

---

### Post by Yumb on 2008-03-21
Thanks for the quick reply!

Thanks to the magic of Google (oddly enough it didn't come up in the forum search), I actually found the solution RIGHT after I posted that inquery.  Apparently there's a bug with the user-admin tool, as described here:

[http://ubuntuforums.org/showthread.php?t=590366](http://ubuntuforums.org/showthread.php?t=590366)

which caused my account to be removed from the lpadmin group.  I re-added myself, and the problem is solved.

Thanks for your help!

---

