---
title: "New GPU Installed-Shall I Wait For Hardy"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2008-03-24
Hi All. 
I'm running Vista 64x in a dual boot with Ubuntu 7.10 64x.
I'm loving it mostly but am a noob in both so some stuff hasn't worked out.
Last week I installed a Gigabyte 8800GT OC in Vista assuming it would also work with Gutsy but of course it doesn't. I get a res of 800x600 and Ubuntu cannot see my new card.
This makes Ubuntu virtually unusable. 
I've had a look around and there are various sites outlining complicated (to me) processes to sort this out but I am aware that Hardy Heron is on the verge of release.
So I have a couple of questions:

Is there a simple way to get my new card working in Gutsy ( I mean really simple)?

When Hardy comes out will I be able to install it over Gutsy and will this solve my problem?

I could even try the beta straight away.

Thanks for reading this, John:confused:

---

### Post by FrozenFox on 2008-03-24
There are several easy ways to install the nvidia/ati video drivers.

The best order to try them in, one or another may not work:

1) The restricted drivers manager. Comes with ubuntu, it will alert you after the install from the taskbar program that you have restricted hardware and it can install the drivers for you blah blah. It's stupidly easy to click that and click install.

2) If the above fails, which it does for some, you might try the Envy program from alberto milone. It is unofficial and unsupported, and many people warn against its use since it is not official and some say it causes problems. However, my experience with.. well, just about everyone i've talked to, is it fixed problematic way #1 installs. Including my own. In addition, you must uninstall the drivers through envy every time you update your kernel or xorg (granted, after the official release is out, this shouldnt happen much in the hardy branch) in the update manager or otherwise, or your machine will be (temporarily) unable to boot into anything beyond 800x600 2d. then when the kernel/xorg updates are done, reinstall via envy. The new generation envy, EnvyNG, is supposed to handle this problem, from what I understand, but last I checked it was not available yet. Thus, you still have to uninstall/reinstall via envy when your update manager wants to update the kernel or xorg, linux-modules, releated stuff. Again, this should theoretically be very very seldom (or nonexistent) if you wait until the final release of hardy.

3) If all of the above fails, you can install the binary from the nvidia website, though this is the most difficult way. It has the same "must reinstall for xorg/kernel upgrades" problem as way #2. It is also many more steps that look scary to new users, but it really isnt hard at all. At worst, print out instructions, and you should theoretically be done in about 8 minutes if you just do what they say. If you are forced to this point, there's probably a thread post here somewhere, likely sticky.


As for whether overwriting gutsy with hardy fixing your problem, none of us can answer that question. You'd probably have to find it out by yourself. It shouldn't be too difficult to get working though. Just be sure before you do anything, you have your stuff backed up.

I've also never tried switching out video cards, but I imagine it might necessitate renewing the drivers. Your card -should- work with the 169.x or new beta nvidia drivers though, i think..

---

### Post by Malta paul on 2008-03-24
Yes changing your video card you will need to reinstall the correct video driver.
Just reboot, then go to System>administration>Restricted Drivers manager tick the box and reboot.
If you still have problems install 'Envy'  using Applications>Add/Remove>search 
Have fun:)

---

### Post by Neo0351 on 2008-03-24
The 8800's don't work with the restricted drivers yet, so envy is you're best bet.  Download envy here [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)  You may also lose you splash screen while booting.

---

### Post by LowSky on 2008-03-24
use envy its your best bet and yes you will loose your splash screen, but it still will boot up

---

