---
title: "[SOLVED] Firefox problems"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Dylock on 2008-01-24
My system has been struggling with a kernel panic problem for a few weeks now (still haven't figured out why but it seems to only happen once a week)
Anyway, this last one required me to hard boot the system. Once I got back in, i noticed something  strange with Firefox

[http://img148.imageshack.us/img148/4435/firefoxproblemti0.jpg](http://img148.imageshack.us/img148/4435/firefoxproblemti0.jpg)

It doesn't load any of my 'profile', and it always seems to be 'Transferring' in the status bar.

I have done a complete removal via synaptic and reinstalled but it did nothing.

I'm totally out of ideas, does anyone have any suggestions?

Thanks,
Dylock

---

### Post by Zeroangel on 2008-01-24
I would try and remove the user profile folder from:
/home/$USER/.mozilla/firefox

If you have bookmarks and other things you want to restore later, I highly recommend that you do not delete the folder permanently, just move it out of its parent folder.

Start firefox, and it should then start in its vanilla state, with all defaults, and it will recreate the profile folder.

You can then restore things manually by moving things into the new profile folder, from the old one.

---

### Post by Dylock on 2008-01-24
I tried your suggestion just now, it seems to have had no effect.

I notice however that the help menu has been missing (was still missing before i deleted the folder). man this is weird.

---

### Post by Zeroangel on 2008-01-24
ah, damn. OK, well another thing I would try then is
sudo aptitude purge firefox

This should completely remove firefox from your system (not leaving behind any residual configurations and such) then you can try to reinstall it.

Failing that, try downloading an alternate firefox version such as swiftfox (based on FF3, and optimized for specific architectures) and see if that floats your boat.

---

### Post by Dylock on 2008-01-24
I tried the purge as you suggested however still nothing, I'm beginning to wonder if the problem is something bigger then firefox.

I'll look into the alternate firefox versoins, thanks a lot for your help zero

---

### Post by Dylock on 2008-01-24
i think ill also try reinstalling of the dependecies of firefox, there are a lot of them so it will probably take a while :/

---

### Post by y-lee on 2008-01-24
I think Zeroangel meant [Swiftweasel]("http://swiftweasel.tuxfamily.org/about.php"). It is a firefox build compiled for speed. [download a deb here]("http://sourceforge.net/project/showfiles.php?group_id=195473"), just don't confuse Swiftdove for Swiftweasel, I did the first time i downloaded it. haha

BTW It is noticeably faster:popcorn:

---

### Post by Dylock on 2008-01-24
Woohoo, resolved, according to the firefox support that greybar on the bottom indicates a faulty addon, just disabled them all and im good to go. Hopefully this will help someone else that has the same problem. 

Thanks for everyones help.

---

### Post by Zeroangel on 2008-01-24
Hmm that was odd. Removing the profile folder should have removed the installed addons. But no matter. Glad to hear that your problem is solved.


---

### Post by y-lee on 2008-01-24
Learn something every day. Thanks Zeroangel :)

> Swiftfox is an optimized build of Mozilla Firefox. Swiftfox has builds for both AMD and Intel processors and is based on the most cutting edge Firefox source code available.

[Swiftfox]("http://www.getswiftfox.com/")

---

