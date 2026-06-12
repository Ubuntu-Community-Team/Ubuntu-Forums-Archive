---
title: "k9copy keeps crashing"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by royal314 on 2007-04-01
I installed k9copy and every time I try to copy a dvd it crashes, any ideas?

---

### Post by wjston on 2007-04-01
> **royal314 said:**
> I installed k9copy and every time I try to copy a dvd it crashes, any ideas?

Did you install the extra multimedia codecs needed for viewing and accessing dvds in Linux? If not , follow the directions using this url - [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Also, open a terminal and enter the following commands one at a time:
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install libdvdcss2

Hope this helps

---

### Post by royal314 on 2007-04-01
i havn't done this yet, thanks for the suggestion

---

### Post by wjston on 2007-04-01
Your welcome.

If you need more information installing subsequent programs, this is a very useful link that has helped me in the past:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by ramjet_1953 on 2007-04-02
I have a problem with K9Copy, where it goes through the process of converting the DV9 to a DVD5, saves it as an iso and then when I try to auto-burn the new iso, it crashes and as a parting shot, deletes the iso, as well!

I played with it for a while and eventually, just got K9 copy to save it as an iso and not auto-burn.

I then use K3b to burn the iso.

This works for me.

Regards,
Roger :cool:

---

### Post by noremacyug on 2008-02-26
rather than me start a new thread titled exactly "k9copy keeps crashing"  i'll simply resurrect this one.

the problem is just that, k9copy crashes every time i try to open the dvd.  i can play the dvd in totem movie player just fine and installed the codecs wjston listed.  still no go.  any ideas guys or gals?

---

### Post by noremacyug on 2008-02-27
anyone?

---

### Post by noremacyug on 2008-03-07
after fresh o.s. install and reinstall of k9copy, it seems to be working fine.  the issue is no more.

---

### Post by Francis3366 on 2008-03-25
> **wjston said:**
> Did you install the extra multimedia codecs needed for viewing and accessing dvds in Linux? If not , follow the directions using this url - [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Also, open a terminal and enter the following commands one at a time:
sudo aptitude install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo aptitude install libdvdcss2

Hope this helps

I came across your post last night.  I was having the problem with k9copy of sporadic rejection of disks when I attempted to copy DVDs.  I had installed the first two lines in your post but not the third.  After installing libdvdcss2 my problem was solved.  

Many thanks for the information.

Francis

---

