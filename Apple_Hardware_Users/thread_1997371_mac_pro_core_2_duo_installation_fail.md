---
title: "mac pro core 2 duo installation fail"
date: 2012-06-05
forum: Apple Hardware Users
---

### Post by nicoloparisi on 2012-06-05
hi everybody i have a problem installing ubuntu 12 in dual boot with lion; this is my situation:

-i followed this guide [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)
-so i have 50 gb of free space (not allocated) for ubuntu
-i have installed refit
-i have both 32bit and 64 bit versions

whenever i boot the cd live i can access (with both the versions) to the orange screen with the little keyboard and a little man surrounded by a circle. here if i press f6 i can even access to the screen with the options (do you wanna try ubuntu, or install it)
with both the versions whenever i press or install or try everything blocks so if i want to install it appears a black screen (32 bit), with 64 bit everything stops in the screen with written install the software.

i have read on the guide that i should wait some minutes: well i have waited 15 minutes and nothings happened. 

any suggestion?

thanks

nik

---

### Post by nicoloparisi on 2012-06-05
any suggestion?

---

### Post by nicoloparisi on 2012-06-07
Is there anybody in the forum that can help me?
Any idea, suggestion? Any previous thread that can help me?
Please tell me something!!

---

### Post by jonas2012 on 2012-06-08
I can tell you, that you are not alone and that i have similar problems installing Ubuntu on my MBP 5,3, but i also got no answer as of yet.

---

### Post by nicoloparisi on 2012-06-08
So let's keep asking; i'm sure there is a solution and i wonder why no one in this forum provide something help; in the end linux is supposed to be supported by a great community, but since Now i did not see the great community!!
Please help!!

---

### Post by EuroCity on 2012-06-08
As I also said in the other discussion, you could try to add:

```
nomodeset xforcevesa
```

... to the boot options in the initial screen (the one where you can select the language, etc. etc.).

Only a guess, of course: but sometimes, this setting can solve some graphical boot problems.

The best CD should be the "+mac" one, for 64-bit-capable Macs:

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-amd64+mac.iso)

BTW, very interesting guide, this one:

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

(even if personally I currently prefer to use virtualisation to run Ubuntu on Intel Macs).

---

### Post by nicoloparisi on 2012-06-08
thanks, i'll try tomorrow with the new iso and the setting you suggested me!

---

### Post by EuroCity on 2012-06-08
I would try first with the new ISO without any additional boot parameters; then, if it doesn't work, try first to add only *nomodeset*; and if also this doesn't work, add both parameters: *nomodeset xforcevesa*.

(Of course, there might also be some other boot options worth trying, if necessary...)

---

### Post by jonas2012 on 2012-06-09
Just chiming in here to say, thanks to Euro City, i managed to install it, by using the alternate mac iso with "apsci=off" parameters.

---

### Post by nicoloparisi on 2012-06-11
thanks for the support, it takes me few days to try your solution and i have to say.....WOW.
No problems during the installation and after trying it on my mac i have to say again wow, it is fast and no problems.

tanks 

Nik

---

### Post by jonas2012 on 2012-06-11
Cool, glad it worked out for you. ^^ Incase you used acpi=off, make sure to put it all back to normal in the "grub.conf". I found out it makes the fans stop from working. No good in the long run.

---

