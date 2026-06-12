---
title: "clamAv"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by mwanafunzi on 2006-02-24
Hi all,
I just discovered that I have clamAv on my system. How do I get it running. I tried typing clamav in the terminal; but no success.


cheers

---

### Post by kent41 on 2006-02-24
[QUOTE=mwanafunzi]Hi all,
I just discovered that I have clamAv on my system. How do I get it running. I tried typing clamav in the terminal; but no success.


cheers[/QUOTE]


to run Clamav   enter clamscan

go to this site.

[https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29](https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29)

Also what version of clamav do you have?

---

### Post by mwanafunzi on 2006-02-24
Thanks for the thread.
After running freshclam, i get 0.87 as my version. Plus another message telling me that I should update. The thing is though, I run clamscan and I get "cmd not found"....
Why would this be?

edit: sudo apt-get install clamav-base, clamav-daemon, and clamav-freshclam. It seems that I still have version 0.87 (although it says that there is a newer version). I think I will check out the clamav site in the morning, maybe it will make a little more sense after I have caught some sleep.

---

### Post by kent41 on 2006-02-24
[QUOTE=mwanafunzi]Thanks for the thread.
After running freshclam, i get 0.87 as my version. Plus another message telling me that I should update. The thing is though, I run clamscan and I get "cmd not found"....
Why would this be?[/QUOTE]

When I run freshclam i must enter sudo -s -H  first then enter freshclam.

I have been trying for 1 day to get some help on how to install ver .88 but i guess we will have to use ver .87

---

