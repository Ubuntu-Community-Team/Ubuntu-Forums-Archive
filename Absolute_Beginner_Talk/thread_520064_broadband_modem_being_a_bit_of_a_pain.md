---
title: "broadband modem being a bit of a pain"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by jasonwatkins on 2007-08-07
my modem has been working fine - it's a sagem fast@600 ( i think ..), but today it's been a real pain in the neck as it keeps dropping the line all the time.

it may just be a one off glitch, but is there any way i can get some sense of if it's actually redialling the connection or just sitting there sulking ??

and if it isn't, what's the best way to kick it into a redial cycle ??

cheers ..

---

### Post by lisati on 2007-08-07
> **jasonwatkins said:**
> my modem has been working fine - it's a sagem fast@600 ( i think ..), but today it's been a real pain in the neck as it keeps dropping the line all the time.

it may just be a one off glitch, but is there any way i can get some sense of if it's actually redialling the connection or just sitting there sulking ??

and if it isn't, what's the best way to kick it into a redial cycle ??

cheers ..

I had some problems a while back with connections being dropped, both with ADSL and dial-up. It turned out that some water had found its way into the underground cables along the street (we'd had some stormy weather) and that was interfering with the signal. One clue was a very faint crackly sound when using the phone, and another clue was that our regular phone calls didn't have the usual quality. Might be a fault with your phone line. Then again, it might not.....

---

### Post by expatCM on 2007-08-07
It seems like there are two possibilities, one that the modem is not performing correctly and the other that the phone lines are not doing so well.

Perhaps you can borrow another modem and put that on your line........   if it works well then you know that that the phone lines are no problem.  That way you can quickly narrow down your focus on the problem ....

---

### Post by jasonwatkins on 2007-08-20
my modem is fine and the line is fine - had them both checked.

the problem is ultimately with my ISP because I think the connection is sporadically dropped to force you to re-connect.

I used [this guide]("http://ubuntuforums.org/showthread.php?t=422683&highlight=eagle") to set up my modem and it worked 100% fine.

I checked for the "adsl" script that supposedly automated the "pppd call ueagle-atm" command and it wasn't there - so i created it and then ran this command ..

"sudo update-rc.d adsl start 50 2 3 4 5 . stop 50 6 0 ."

but it said the rule for adsl was already there - so does anyone think this might have been why the modem didn't automatically re-dial ???

And is the number 50 the amount of re-tries ????

---

