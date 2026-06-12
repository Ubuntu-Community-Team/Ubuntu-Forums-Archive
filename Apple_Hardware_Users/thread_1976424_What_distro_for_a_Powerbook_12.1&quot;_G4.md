---
title: "What distro for a Powerbook 12.1&quot; G4?"
date: 2012-05-08
forum: Apple Hardware Users
---

### Post by humanizer on 2012-05-08
Hi guys, i looked everywhere on the forums, but can't seem to find a good solution for my recently aquired powerbook laptop. It works very well with Mac OS X 10.4, but that sistem is really outdated. I have managed to install debian squeeze-netinst, but i would like to make it to work with as less hassle as possible :D I tried lubuntu 12.04 too, the install went fine, but it just wont boot. (The partitions were all set like with debian, so there's nothing wrong with that. Any advice?

---

### Post by gwjvan on 2012-05-10
Where does the Ubuntu installation hang? (You can press escape when the ubuntu splash screen appears, to see more output).

On mine (15" G4 1.67ghz), it hung when looking for wireless firmware that isn't there- so I had to prevent it from trying to load the wireless (not sure the best way to do that, but I just moved the wireless driver directories to my home directory), boot to 12.04, set things back to original settings (moved the driver directories back), install the firmware, and then it worked.

---

### Post by EuroCity on 2012-05-10
The best way to do this is probably to boot with this parameter (hitting the TAB key at the second yaboot prompt):

**live b43.blacklist=yes**

... or:

**Linux b43.blacklist=yes**

More info here (in general, not only for this particular problem):

[https://wiki.ubuntu.com/PowerPC](https://wiki.ubuntu.com/PowerPC)

Especially, the *FAQ* and *Known Issues* pages: very useful, indeed...

---

### Post by humanizer on 2012-05-10
Thanks for the reply guys.
I haven't had any luck hitting the esc key, i cannot say where it hangs. Meanwhile i made some experiments with ArchLinux PPC, but didnt really achieve much.

I would like to go with Lubuntu 12.04, because its way more up-to-date than any other available PPC disto, afaik. 

@EuroCity, thanks, will try that these days. 

Otherwise, any more experiences with 12.04 on a G4, how's everything working?

---

### Post by gwjvan on 2012-05-10
Lubuntu with no compositing effects runs pretty quickly.

I haven't run 12.04 on this thoroughly, but it seems to be working reasonably well.

---

### Post by humanizer on 2012-05-16
Thanks for the feedback. I've succeeded in installing ubuntu 10.04 lts on my powerbook, so far it works great. I did the install from the alternate cd. I have only minor issues with the splash (not showing on the entire screen, just in the upper left) and with the screen brightness keys (F1-F2) which are not working with the Fn modifier - but will get to that issue ASAP.

In summation, i'm really satisfied with 10.04 LTS, looks like i'm gonna stay :)

---

