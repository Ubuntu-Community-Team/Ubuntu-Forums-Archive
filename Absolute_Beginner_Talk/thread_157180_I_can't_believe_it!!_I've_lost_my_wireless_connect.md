---
title: "I can't believe it!! I've lost my wireless connection! I can't go back to Windows now"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-04-08
After I first installed Breezy it took me over a week to get my wireless usb adaptor (Inventel UR054g V1.1) to work, mostly with help from you guys (many thanks). It worked absolutely fine for a few weeks but for the last few days it has kept failing on me when I'm in the middle of browsing. Sometimes I can get it to work again by deactivating/activating in Networking, but now I can't get it to work at all.
Even worse my ethernet connection which I never had a problem with isn't working now either. After searching the forums, I decided to uninstall firestarter to see if that would help, but now when I boot up I get "please enter your password to run /usr/sbin/firestarter" There are a lot of questions on the forums about this, but I haven't found many answers :???: none that seem to apply to me, anyway.
I'd really appreciate any help you can give me - I've really enjoyed using ubuntu, I think it's an excellent OS and I'd hate to have to go back to windows, which is where I'm posting this from.:(

---

### Post by x5452 on 2006-04-08
im curious about that firestarter thing too,  I get that enter password prompt every time I boot up, even before I had set firestarter up.  sorry I am brand new and dont know much about internet connections.  did ubuntu stop recognizing you lan connection?  do you have desklets enabled that say anything about your internet up time ect.?

---

### Post by jason.b.c on 2006-04-08
[QUOTE=clareb]After I first installed Breezy it took me over a week to get my wireless usb adaptor (Inventel UR054g V1.1) to work, mostly with help from you guys (many thanks). It worked absolutely fine for a few weeks but for the last few days it has kept failing on me when I'm in the middle of browsing. Sometimes I can get it to work again by deactivating/activating in Networking, but now I can't get it to work at all.
Even worse my ethernet connection which I never had a problem with isn't working now either. After searching the forums, I decided to uninstall firestarter to see if that would help, but now when I boot up I get "please enter your password to run /usr/sbin/firestarter" There are a lot of questions on the forums about this, but I haven't found many answers :???: none that seem to apply to me, anyway.
I'd really appreciate any help you can give me - I've really enjoyed using ubuntu, I think it's an excellent OS and I'd hate to have to go back to windows, which is where I'm posting this from.:([/QUOTE]


>  (Inventel UR054g V1.1) 

That **v1.1**, It dosen't by any chance mean *USB 1.1* , Does it.?

Maybe your wireless adaptor just took a dump.:(    and it's time for a new one.               How old is it.??

---

### Post by clareb on 2006-04-09
Jason b.c. - nope that's what it says on the darn thing, and it works fine with Windows, so it's definitely not the adaptor. It's about a year old, I hate the stupid dangly thing, I'd replace it with a bus card if I could be guaranteed it would work and didn't cost the earth.

x5452 - I don't have gdesklets, according to networking, everything is working fine, the light's on on the adaptor, I just can't access any websites. Very frustrating.

Thanks for your responses, guys. :~)

---

### Post by gordonbrown77 on 2006-06-09
I have a UR054g(R01) v1.1 and got it working using ndiswrapper and the following driver 

[ftp://ftp.inexq.com/Drivers/UR054g(R01)3325.zip](ftp://ftp.inexq.com/Drivers/UR054g(R01)3325.zip) 

Using most up to date ndiswrapper v 1.17, haven't tried with version that comes with breezy

---

### Post by gordonbrown77 on 2006-06-09
Forgot to mention you need to add the following lines to /etc/modprobe.d/blacklist
 to prevent it loading the default modules ubuntu tries to use.

blacklist prism54
blacklist islsm
blacklist islsm_usb
blacklist islsm_device

---

