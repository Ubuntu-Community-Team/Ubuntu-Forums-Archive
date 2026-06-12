---
title: "session and wireless problem"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-11-16
i have opened 2 threads couple of weeks ago about my problems but no one helped.. so here i am again and please someone help me

1. i got my wireless to work from the help of a thread from here.. but whenever i turn it on after awhile my computer freezes.

2. i cant save any sessions.. whenever i restart it goes back to default.. what can i do ?

please someone help !!

---

### Post by KentS on 2007-11-16
Have you tried Ndiswrapper?
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by HunkieChan on 2007-11-16
ys bro.. i have tried that..but it still freezes..uh, its been a month.. why isnt anyone helping me :(

---

### Post by KentS on 2007-11-16
I think you haven't gotten any help because no one knows where to begin. Your problem sounds really strange. In the worst case, it might be a bug with no easy fix. In this case you should post it as a bug. But I think you should consider a few things first.
Are you doing anything specific when your system freezes? Maybe you should check your memory usage with a system monitor, or
```
free -m
```
Have you tried both ndiswrapper and bcm43xx seperately, without the other one being installed, or blacklisted?
Have you tried your hardware in a different OS? Is it working there?
Have you checked [http://ubuntuforums.org/showthread.php?t=405990?](http://ubuntuforums.org/showthread.php?t=405990?) There are some people having problems with their system freezing. And some possible solutions have been posted. You might also consider posting your problem in that thread, or making a new thread in the Networking and Wireless forum.

As for your other problem. Can you be more specific? In some cases you need to change several things to make sure your settings aren't changed when you reboot.

---

### Post by Inxsible on 2007-11-16
Are you sure its only because of you network manager and not any other app that you are running?
What network card do you have ?

---

### Post by HunkieChan on 2007-11-16
i dont know why or how but since i removed the wep key for my wireless network.. my computer doesnt freeze..which is weird.. one thing that still happens to me is -- when my wireless button is turned on and i try to restart/start/shutdown my computer freezes.. 

sessions: lets say i save pidgin there to be started when i turn on computer.. then i restart/start my computer , my pidgin doesnt open..i check the session and pidgin isnt listed there.. tahts what i meant by session problem

thanks

---

### Post by HunkieChan on 2007-11-16
yes, i used that thread to fix my wifi.. i have broadcom 4310.. i think its my network manager that is freezing my computer because when i turn on my computer and if my wifi is turned on then my computer freezes when its loading at grub menu .. and if i restart the comp with the wifi being turned off then my computer doesnt freeze..

---

