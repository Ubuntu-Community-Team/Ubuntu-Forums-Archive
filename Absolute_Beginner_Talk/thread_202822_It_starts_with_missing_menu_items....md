---
title: "It starts with missing menu items..."
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by WhoDaBear on 2006-06-24
Hi there folks.  Hoping that someone can help out a Newbie to linux.  I've tried the Wiki guide and searching forums and whilst I do find some relevent stuff, it either isn't quite what I'm after, or doesn't work for me.  I'm afraid its probably a laborious walk-through that I'm after!  Thanks in advance.

Problem:
- Lots of important menu items are ticked "visible" in alacarte menu editor, but don't appear in the menu.  
- I uderstand from other posts that this may be because I'm not in the sudoers list.  I tried editing this in /etc/sudoers with nano, but it didn't work.  
- I'm thinking I probably need to asign admin privelleges or somesuch to my account, but without the GUI for user admin (missing from my menu despite ticked visible) I'm stuck.  My only other user account (the one that shares a password with sudo) has the same problem.  Any ideas?  Thanks again.](*,)

---

### Post by Apple 101 on 2006-06-24
Did you do an OEM install?  Anyway, try this:
sudo passwd root
<password>
<password again>
su <password>
gedit /etc/sudoers

---

### Post by WhoDaBear on 2006-06-24
Hi there.  First, thanks for getting back so quickly.

OEM install?  Don't know what that means.  Downloaded ubunto iso and booted from it, then clicked the install app on the desktop.  I've "developed" this problem for myself somehow, having had all the menu items available for a while!

sudo passwd root

Just did that - doesn't ask me for a password, just returns to:

whodabear@Mother:~$


Thanks again.

---

### Post by Apple 101 on 2006-06-24
Okay never mind about those commands then.  Wait for another user to help you - I'm just not sure.

Wait... try in a terminal:
su <your password>
gedit /etc/sudoers

---

### Post by WhoDaBear on 2006-06-24
Ok - I appreciate your trying though.  Thanks again.

I'm going to re-install now.  Haven't done much to system yet, so not much to do to get it back to this point.

---

### Post by Stew2 on 2006-06-24
One more thing you could try if you havent reinstalled already. Try going into you alacarte menu editor, unchecking the programs that arent showing up then close alacarte. Reopen it and recheck the items you want to show up then close it again and see if they show up. I had a similiar problem and this worked for me... kind of a alacarte reset if you will :). Hope this helps (if you havent already reinstalled)

Regards,
Stew2

---

### Post by WhoDaBear on 2006-06-24
Dear all,  thanks for the help.  Re-installed (I know, much lazier than fixing it!) and up and running again.  Cheers.

---

