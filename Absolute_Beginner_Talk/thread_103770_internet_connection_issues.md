---
title: "internet connection issues"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by STORMBRINGER69 on 2005-12-14
Hello everyone,
I am new to Linux and have just I believe sucessfully installed it. .....Now for the catch. I can't seem to connect to the internet. I have aol broadband but whenever I navigate to a site using firefox i get a cannot find site messeage. Any help getting my connection configured properly would be greatly appreciated.
thanks in advance

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=STORMBRINGER69]Hello everyone,
I am new to Linux and have just I believe sucessfully installed it. .....Now for the catch. I can't seem to connect to the internet. I have aol broadband but whenever I navigate to a site using firefox i get a cannot find site messeage. Any help getting my connection configured properly would be greatly appreciated.
thanks in advance[/QUOTE]
Try out these steps:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

### Post by kshep92 on 2007-11-13
Can you update that link please? I'm not getting through to the post. I too have the same problem.

---

### Post by bumanie on 2007-11-13
Hi guys, 
Noticed no-one has helped you for a long time. I am far from an expert on this but if you are using gutsy, there apparently has been a problem for many people with the ipv6 internet stack released a few months ago. Check out this link [http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/](http://www.lockergnome.com/linux/2007/10/24/ubuntu-gutsy-internet-help/)

If you don't want to blacklist something, maybe your modem/router needs a firmware upgrade.
Hope this helps.

---

### Post by white_sox_fan_82 on 2007-11-13
Also, make sure your NIC is not being disabled by Windows (if you are dual-booting)...

---

### Post by kshep92 on 2007-11-13
Well to tell you the truth, my internet worked fine until a few days ago. Firefox was working like a charm, I didn't change anything - the most I did was install build-essentials and installed a webcam (which still doesn't work). Can anybody tell me what's going on in this case?

---

### Post by kshep92 on 2007-11-16
OK I solved the problem! *gives pat on back* I followed the steps for enabling OpenDNS, but instead of using their DNS addresses, I used the ones that my ISP gave me. 
I still have ipv6 disabled in Firefox and it's still blacklisted from the tutorial on lockergnome.com. If my internet goes down again, I still have 2 things to reverse (the ipv6 thing) and if all else fails then i'll have to resort to OpenDNS again :( (Sorry, that came out wrong, OpenDNS really is awesome ;-))

Thanks for all your help guys, so chalk this up as yet ANOTHER way of solving the internet connection issues.

Here's my configuration in step form:

1. Disable ipv6 in Firefox
2. Blacklist ipv6 (follow instructions from tutorial on lockergnome.com posted by bumanie)
3. Go to OpenDNS's website and go to the set-up instructions page.
4. Follow their steps, but plug in your ISP-issued DNS addresses instead of theirs.

You can skip straight to the 3rd step if you want, but i'm too afraid of messing up this thing again to try re-enabling ipv6 in both instances. If anybody skips to step 3 and their connection works, then let me know pls. Thanks.

Hope this helps!

---

