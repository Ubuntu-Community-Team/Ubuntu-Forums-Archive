---
title: "ARGHHH!!! Can Ubuntu connect to a UNSECURED wireless network???"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-15
Hi there,

I've spent half a day trying to connect to an unsecured wireless network but I still can't get it to work! I've been reading hundreads of pages of Ubuntu and/or Debian documentation and dozens of threads and I can't find anything wrong with what I'm doing! I've tried editing the /etc/network/interfaces, I've added and removed star-up scripts, etc...

Do you want to know what's the most irritating thing after all this? Well, guess waht, it works just fine with a WEP secured wireless network but not with an unsecured one!!!

W H Y ? ? ?

](*,)  ](*,)  ](*,)

---

### Post by fhqwhgads on 2006-07-15
Heh, that's weird. I have the exact opposite problem: [http://www.ubuntuforums.org/showthread.php?t=216484](http://www.ubuntuforums.org/showthread.php?t=216484)

---

### Post by verbatim210 on 2006-07-15
i also had the same problem, but it was using windows.  good chance ubuntu is not the culprit.

---

### Post by ovimunt on 2006-07-15
Windows is a completely different story for me... I had loads of problems there as well with absolutely NO reason! I mean it worked one day and it didn't the next, with the exact same configuration! I'm starting to think that I might actually have a hardware problem but it just doesn't make any sense! :confused:

---

### Post by verbatim210 on 2006-07-15
doesnt make any sense?  it does to me, sounds like a networking issue.  another possibility, hardware compatibility.

---

### Post by Engnome on 2006-07-15
> **ovimunt said:**
> 
W H Y ? ? ?

](*,)  ](*,)  ](*,)

Because it's insecure? I've had this problem with windows aswell, just that it told me: This is not safe. And then refused to connect.

---

### Post by verbatim210 on 2006-07-15
if windows has that feature i am unaware.  i stand by the "unsafe wireless is ok" statement.  i used it at home and work still uses it.  i cant remember exactly what my problem was, but i remember it was specific to the new wireless that i introduced, because the existing wireless was able to connect without problems.  back then, i believe wep was troublesome and uneccessary.  my point of view changed when an external unauthorized host connected sapping alot of my bandwidth.

---

### Post by MarkSheely on 2006-07-15
I'd really like to help you with this, but you're not giving enough information.  Which wireless card do you have?  What error messages are you getting when trying to connect?

--Mark

---

### Post by hkq35 on 2006-11-15
Speaking from a my own personal experience...
I have noticed that if you look at the networks in 
system>administration>networking
wireless connection properties network name(ESSID)

and compare them to networks you can see if you use the  'Wireless Assistant' app. ( another repository application )

That many of the same networks appear unsecured in one and secure in the other ( and visa-versa )

If I am roaming around and want to hook in to a random unsecured network, then I have to open both apps and cross check whats unsecured in both.


It may have something to do with different encryption (WEP/WPA/WAP etc) types that are not recognised.

---

