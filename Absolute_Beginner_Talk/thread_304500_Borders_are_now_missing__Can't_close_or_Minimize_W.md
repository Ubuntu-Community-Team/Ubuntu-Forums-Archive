---
title: "Borders are now missing \ Can't close or Minimize Windows"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by kd7swh on 2006-11-21
This makes me feel like a total n00b :( 

I tried installing compiz but after executing it, the window borders in gnome disappeared. Now there aren't buttons to close, maximize, or minimize windows.

I tried changing themes to no avail. Can anyone help me restore that little X to its rightful home in the corner of my windows? ](*,)

and Alt+Tab isn't working either.

---

### Post by IYY on 2006-11-21
Typing 'metacity' in a terminal should fix it.

---

### Post by kd7swh on 2006-11-22
I didn't even think to see if it was running. Thanks, it was metacity. 
The strange part is though that when I logged in via GNOME Failsafe it tells me that the dbus settings daemon failed to start. is this related to metacity or is this a different issue?

---

### Post by IYY on 2006-11-22
I think the dbus issue has to do with the failsafe, not metacity. You could try to restart it with /etc/init.d/dbus restart

---

### Post by kd7swh on 2006-11-23
No Matter, I just install beryl and I really like it. But it wont start at login. just like metacity.

I add them to the startup list in the gnome session manager but they aren't there upon reboot.

I am quite sure this is a bug in Gnome

---

### Post by Ilon on 2006-11-26
Hi!

My husband installed Ubuntu to my laptop. In the first days it worked ok (I get used to the fact that internet is much slowlier than it was with Windows.    :???:  And also to the surprising effect that I always lose 2 letters, when I am typing. In every sentence, and always different ones.)
But after a few days [B]the minimze button started not working on the windows. When I click it, the window disappears. 
What should I do?[/B]
(Please do not suggest to ask my husband. He is testing Ubuntu on my laptop, bacause he has not installed it to his laptop yet :)  )
Thanks

---

### Post by Portable_Jim on 2006-11-30
Thanks typing 
```
metacity
```
worked well. :KS

---

### Post by Ilon on 2006-11-30
Thanks, we found the answer. It was on the panel. 
By

---

### Post by Dr. Nick on 2006-11-30
It looks like some problems have been resolved, but ill toss in my 2 cents

If windows disappear when minimized or they don't go to the tray when closed then right click a panel and push "add to panel" and add "Window List" and "Notification Area"

If you lose window borders then open a terminal or push alt+f2 and type
[B]
metacity --replace[/B]

If you are trying to get beryl to start up and boot then add "beryl manager" to the Startup tab of the session preferences, You should see the red diamond if you have the notification area, right click it and make sure beryl is set as the window manager and not metacity

---

### Post by compmodder26 on 2006-11-30
> **Ilon said:**
> Hi!

My husband installed Ubuntu to my laptop. In the first days it worked ok (I get used to the fact that internet is much slowlier than it was with Windows.    :???:  And also to the surprising effect that I always lose 2 letters, when I am typing. In every sentence, and always different ones.)
But after a few days [B]the minimze button started not working on the windows. When I click it, the window disappears. 
What should I do?[/B]
(Please do not suggest to ask my husband. He is testing Ubuntu on my laptop, bacause he has not installed it to his laptop yet :)  )
Thanks

These things you described above should not be happening.  Have you tried asking for help here in the forums for these issues?

---

### Post by buddah3618 on 2007-07-22
> **Portable_Jim said:**
> Thanks typing 
```
metacity
```
worked well. :KS

YES - Thanks - typing "metacity"  worked like a charm. I knew that if I searched these forums long enough I'd find the answer.

Thanks Again
buddah3618

---

### Post by TranceWarp on 2008-03-17
Thanks for this...I was having the same problem.  Oddly, metacity was NOT on.  I used the replace option, went back to custom effects using xgl and evetything's fine now. :)

---

