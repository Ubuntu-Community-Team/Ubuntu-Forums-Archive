---
title: "&quot;The system administrator has disabled your account&quot;."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2007-09-19
Hi.

When I now try to log into my regular user account I get the following message, **"The system administrator has disabled your account."** I have checked the permissions and they seem ok: user is read-write, group is access, others no access. 

I run a home LAN and I was successfully accessing the Linux box from an XP box.  However, sometime this afternoon, after I "shared" some files (SMB) and changed permissions, I no longer had access to the regular user account (just the SU acct.)  Strangely, I can still access the regular user (Ubuntu 7.04) files from the XP box even though I can't log into it.  I believe I changed all the permissions back to what they were prior to this problem.

I searched this forum and googled the error message. The very few hits did not apply to my situation.  Does anyone have any thoughts on this issue?   Should I just create another user and transfer the files to this account? 

Thanks,
Ian.

---

### Post by nonewmsgs on 2007-09-25
i would make a new account copy and paste everything over and delete the old one just like you suggested.

don't know why though...

---

### Post by Ian-on-the-Trent on 2007-09-26
Thanks for your suggestion nonewmsgs.

I was just about to do that but something twigged in my brain. This might be a solution:

I clicked through System>Adminsitration>User and Groups>User Settings>username>Properties. I then clicked on the Advanced tab and under the Advanced Setting, Shell showed *bin/true*. I changed it to *bin/bash*. Not sure if I had inadvertently messed the setting up in the first place. And I'm not sure why I did what I did  although something I read in the past may have twigged my action.

Not an easy solution and totally lucky. Unless of course what I did will work for now but pose problems later on.

*...After a 1/2 day of use with several shutdowns/logins: Just to let you know...the change I made is so far stable and I've been able the user account fully.  Very strange indeed.*

---

### Post by nizate on 2008-05-05
Is there a way to enable that User? I have the same problem with a newly created user that I am using to run a Teamspeak Server... Is there a way to enable it??? I am using Hardy...
Thanks.

---

