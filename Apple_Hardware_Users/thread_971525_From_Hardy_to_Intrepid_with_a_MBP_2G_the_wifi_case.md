---
title: "From Hardy to Intrepid with a MBP 2G: the wifi case"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by Romu on 2008-11-05
Dear all,
I've been using exclusively Ubuntu on a 2G Macbook Pro since 2006, it's a Core 2 Duo (Merom) with an ATI X1600 graphic card and the AR5008 Atheros wifi chipset.

On hardy, I used an early madwifi driver (20080103), compiled by myself, and this allows me to get the plain benefit of my Internet connection with a speed between 7 and 10 Mb...yes in France, we have some very good speeds.

Newer madwifi didn't work so well, drivers newer than March 2008 didn't perform as expected.

Intrepid is the first release with an Out Of The Box working Wifi thanks to the Ath9k driver. But my connection was sssooooo sssssllllloooooooowwwww, never more than 1,5 Mb, not usable to watch the TV on the computer for instance.

So, for the last days, I went to this forum searching for a fix. Here are my results:
- backports package to get the ath5k driver: the installation seems ok, the module is well registered, and the wifi doesn't work at all, a "iwconfig" returns "no wireless found", end of story
- compiling the compat-wireless package is the same, "no wireless found", same result: end of story
- I finally got a madwifi-hal package which I compiled and it works pretty well with the ath_pci driver.

Ok the speed is still not enough, but around 4 Mb is not so bad. I didn't had the time to make heavy tests with the TV but it seems usable.

I hope this could help some people swimming in the wifi drivers jungle...good luck

---

### Post by Romu on 2008-11-05
After some further searches, it seems we need to activate the ath5k driver through the "Proprietary driver" GUI to make it works.

Cany anyone confirm? If yes, I'll give another try to ath5k.

Thanks.

---

### Post by cyberdork33 on 2008-11-05
ath9k is for the 802.11n capable cards. ath5k is for other atheros cards. With a MBP2,1 you can probably try both.

---

### Post by Romu on 2008-11-05
Ok thanks.

But once installed, should I activate the driver through the Proprietary Driver application?

Because, to me, ath5k doesn't work at all, it doesn't even detect my chipset.

I'll give it a last try and if it doesn't work, I'll keep the madwifi-hal.

---

### Post by cyberdork33 on 2008-11-05
> **Romu said:**
> Ok thanks.

But once installed, should I activate the driver through the Proprietary Driver application?

Because, to me, ath5k doesn't work at all, it doesn't even detect my chipset.

I'll give it a last try and if it doesn't work, I'll keep the madwifi-hal.
it depends. you can activate it other ways depending on what driver you are using / how you install it. If ath5k doesn't detect your chipset, then it is obviously not the right driver, ath9k is.

ath9k is still in early developement, there are bugs. If you'd like, you can file a bug report in launchpad.

---

### Post by Romu on 2008-11-05
Ok, I made the last tests and here are my conclusions regarding the AR5008 in Intrepid:
- the ath5k driver definitely doesn't work, even if the module starts there is no wireless interface detected, I tested this with both the backports packages and by compiling the compat-wireless by myself,
- the ath9k works with a pretty bad speed
- the madwifi-hal compiled from sources is pretty much better and works well, the speed is 3 times faster than with the ath9k and even if this is 2 times slower than my normal connection speed.

This means that ath9k is 6 timer slower than my normal connection speed.

My mac is 2 years old, as well as the Atheros AR5008, I don't understand why we can't get a good connection quality after all these times.

Here I stop the tests, hope this helps.

---

### Post by Be.Free on 2008-11-08
Yo..

I've experiencing same problems.. macbook pro santa rosa with intrepid 32bit. Ath9k worked with wpa2 (eap with tkip) but didn't work with wep. So I go back to madwifi hal. But is already unstable... I'm trying different snapshot.. Which version are you using?

Thx!
Vince

---

### Post by Romu on 2008-11-12
Hi and sorry for this late,
I'm using the madwifi-ng-r3111-20080301.

I'm not sure about the "r" value. But you won't find this package among the madwifi archives, they begin at May 2008. Indeed, I kept my March version for a while and I don't want to give it up, as it is the only one to provide me the plain benefit of my Internet connection speed.

So since this week-end, I downgraded my Mac to Hardy to get a full working wifi. To me, let's wait for 9.04, I won't use Intrepid anymore.

---

