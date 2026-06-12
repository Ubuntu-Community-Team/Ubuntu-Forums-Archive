---
title: "Screen Accidentally Blacked Out And Inaccessible"
date: 2011-04-20
forum: Apple Hardware Users
---

### Post by jimwg on 2011-04-20
Greetings:

One of our home school students, toying with the Power Management panel on our 700mHz iMac since there are no brightness control keys that work on it, set it for full display blackout and now can't get the screen back since we can't see the controls. We turned the machine off and on but his account keeps blacking out on log-in though it doesn't happen with other accounts. How can we fix this to retrieve all his work?

Thanks!

JimWG

---

### Post by stealth. on 2011-04-20
> **jimwg said:**
> Greetings:

One of our home school students, toying with the Power Management panel on our 700mHz iMac since there are no brightness control keys that work on it, set it for full display blackout and now can't get the screen back since we can't see the controls. We turned the machine off and on but his account keeps blacking out on log-in though it doesn't happen with other accounts. How can we fix this to retrieve all his work?

Thanks!

JimWG


**EDIT: I noticed you said that it doesn't happen with other accounts, so I think my answer will not help. **


Ubuntu right?, AFAIK you can boot up select the "recovery console" option, and then select the "root shell" option.

There should be some kind of "X" program installed, I think its called X11 but I'm recalling this from memory.  Type in "whereis X11" or "whereis X" and post the output, if you can't find either one type "ls /etc/ | grep X" and post the results. Once you find that directory there should be some kind of backup of your settings. 

The last time I had a black screen this is how I fixed it. But as I said I'm recalling this from memory, but I'll try to help. 


Post the result of these commands, take a pic, something...

---

### Post by jimwg on 2011-04-20
> **stealth. said:**
> **EDIT: I noticed you said that it doesn't happen with other accounts, so I think my answer will not help. **


Ubuntu right?, AFAIK you can boot up select the "recovery console" option, and then select the "root shell" option.

There should be some kind of "X" program installed, I think its called X11 but I'm recalling this from memory.  Type in "whereis X11" or "whereis X" and post the output, if you can't find either one type "ls /etc/ | grep X" and post the results. Once you find that directory there should be some kind of backup of your settings. 

The last time I had a black screen this is how I fixed it. But as I said I'm recalling this from memory, but I'll try to help. 


Post the result of these commands, take a pic, something...


Thanks for your fast answer and offer to help! You don't know how much a rescuer's appreciated here!

Yes, though this is a Mint machine with the problem, we just learned Ubuntu machines on "Lamp" iMacs and G3 iBooks are prone to the very same problem because the screen brightness keyboard keys don't function as they're "not laid out" according another Ubuntu page. So it seems to us that a single remedy on any machine should fix them all. 

Is there a way to find and target the specific power/display configuration file and change the power entry or delete the file itself without taking all the configurations down? Also, a teacher here asked whether we can kill two birds with one stone by fixing the keyboard key brightness controls problem. 

 Just asking since we're all just teachers here and not techies but are struggling to learn thanks to help like yours!

JimWG

---

### Post by stealth. on 2011-04-20
> **jimwg said:**
> Thanks for your fast answer and offer to help! You don't know how much a rescuer's appreciated here!

Yes, though this is a Mint machine with the problem, we just learned Ubuntu machines on "Lamp" iMacs and G3 iBooks are prone to the very same problem because the screen brightness keyboard keys don't function as they're "not laid out" according another Ubuntu page. So it seems to us that a single remedy on any machine should fix them all. 

Is there a way to find and target the specific power/display configuration file and change the power entry or delete the file itself without taking all the configurations down? Also, a teacher here asked whether we can kill two birds with one stone by fixing the keyboard key brightness controls problem. 

 Just asking since we're all just teachers here and not techies but are struggling to learn thanks to help like yours!

JimWG

Well its my bedtime, hang in there we will get it fixed, surely you have tried the recovery console? You have GRUB installed right, if not what method of installation have you followed?

---

### Post by avtolle on 2011-04-20
Since the OP is on PPC, to get to a recovery console will require typing "Linux single" (w/o the quote marks) at stage two of the Yaboot boot process (or perhaps Linux 1 w/Debian, as the OP is using mintppc; when I tried Linux 1 on Ubuntu PPC, it didn't work). Reportedly, in 8.04 and 8.10, there was a bug in the process which caused a problem with the recovery menu, which hopefully has been fixed. 

Good luck; I've no experience with this problem, but wanted to aid a bit.

---

### Post by stealth. on 2011-04-21
OP check this link: 
[http://www.google.com/url?sa=t&source=web&cd=2&ved=0CBsQFjAB&url=http%3A%2F%2Fwww.linuxscrew.com%2F2007%2F10%2F25%2Fajust-lcd-brightness-from-command-line-works-at-dell-1501%2F&rct=j&q=gconf%20change%20brightness%20command%20line&ei=aMWvTYSWD8jGtAbSpoXyCw&usg=AFQjCNEHO5HrlD8mMq7hGbB19XkFj-5DxQ&cad=rja](http://www.google.com/url?sa=t&source=web&cd=2&ved=0CBsQFjAB&url=http%3A%2F%2Fwww.linuxscrew.com%2F2007%2F10%2F25%2Fajust-lcd-brightness-from-command-line-works-at-dell-1501%2F&rct=j&q=gconf%20change%20brightness%20command%20line&ei=aMWvTYSWD8jGtAbSpoXyCw&usg=AFQjCNEHO5HrlD8mMq7hGbB19XkFj-5DxQ&cad=rja)

---

