---
title: "Losing top bar of windows"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by dbaseii on 2007-12-24
Hi all
Any application or window that i open loses the top bar of the screen which stops me being able to close the appilcation/windows. If i right click the window on the bottom taskbar and click maximize the bars come back again.
I have tried various methods to fix the problem without luck
Any ideas?

---

### Post by Znort_Ubern00b on 2007-12-24
do you have compiz running?
what graphics card do you have??

if you answer yes to compiz and nvidia graphics  open terminal and type

**sudo nvidia-xconfig --add-argb-glx-visuals -d 24**

---

### Post by dbaseii on 2007-12-24
Thanks mate

That fixed it

Cheers!

---

### Post by Znort_Ubern00b on 2007-12-24
no worries, don't forget to mark thread solved.

---

### Post by brett611 on 2007-12-26
Hi,
I have this problem with a twist.  I have 3 user accounts -mine, my wife's and guest.  This holiday I had my stone age parents in and they used the computer.  My wife was nice and logged them into her account.  I was not and forced them to use the guest account.  Now, in both my wife's account and the guest account, all applications are missing the top bar (only have file, edit, view, etc in Firefox now), they are 3/4 maximized yet cover the top Ubuntu panel.  Clicking any of the menus will display the menu option but trying to actually select any of the options result in the menu 'drop down' losing focus.  The only exception to this is the File menu, which is how I can close apps.

My account is fine.

I have Ubuntu 7.10, AMD 64, ATI card.  I have previously uninstalled all compiz software as ATI was barfing on it.

Suggestions are most appreciated as I cannot figure out what my parents could have done to make this happen.

Thanks

---

### Post by brett611 on 2007-12-27
metacity --replace 

fixed this problem for me

---

### Post by skaman9876 on 2007-12-28
thanks a lot Brett611


I'm a total Linux noob, just got it as a christmas present with no prior knowledge (besides my Nokia N800) of linux.  I definitely would have never figured this out and the metacity --replace fixed it for me

---

