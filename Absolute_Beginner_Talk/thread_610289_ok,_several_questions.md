---
title: "ok, several questions"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by dlbrando on 2007-11-11
Ok several questions

Cant get sound to run on an emachines N-10, sound is onboad and comes up with a generic display when I tell it to display the cards installed.  Does anybody happen to know which app I need to install to get it to play?

I am also having a strange problem with my wireless router and wireless in general.  It seems that whenever I try to connect to my router, wep enabled, it freezes and my caps lock key starts blinking.  Also no matter where I connect to it always has only 30percet of a signal, whats up with this.  I am gonna try to reset the router and see what I can do from there.

I am also having problems with getting a dvd to play, says the codec is not installed, and it then searches and finds one, I download it, and from then I cannot get it to install.  

If you know the answers and have a minut it would be appreciated.  Or if you have a thread bookmarked that helped you with these problems and can link it that would be great.  

Thanks
Dave

---

### Post by rudeboyskunk on 2007-11-11
Sorry, I can only help you with the dvd.  You probably need to install a file called "libdvdcss."  You can get it [here]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb").

When it asks you what to do with it, just save it to your desktop (or home folder or where ever you told firefox to save downloaded files), then when it's finished downloading, double click on it.  You will have to enter your password.  It should do everything else for you.

Also, make sure all of your repositories are enabled by going to System>Administration>Software Sources.

---

### Post by DutyDuty on 2007-11-11
I can only answer the 30% question. My FiOS can only reach 50% if I stand with my laptop litterallty on top of the airport. I've connected to a T3 network and only got 75%. I'm not sure what the standard of 100% is, but you won't get it.

---

### Post by dlbrando on 2007-11-11
awsome thanks guys

---

### Post by dlbrando on 2007-11-11
what do you mean by enabling repositories, check all the boxes?

---

### Post by jw5801 on 2007-11-11
I can shed a bit more light. If your caps/scroll lock lights start flashing, then your kernel has crashed/is panicing. You'll probably want to debug that, so as soon as you reboot take a look at the output from "dmesg" and have a look around the logs in /var/log/ to see if you can find anything suspicious.

---

### Post by SpiritIsReality on 2007-11-11
howdy
here's some links [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
trails

if it's w32codecs this works for me [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+codecs&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+codecs&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+w32codecs&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Ahelp.ubuntu.com+w32codecs&btnG=Google+Search&meta=)
I think VLC is great too.

---

### Post by peterjohn on 2007-11-11
about the dvd thing, you can also go and install VLC and you don't have to mess around with codecs or anything, its all integrated.  Or at least for myself, I have never had a problem watching any dvd so...

---

### Post by dlbrando on 2007-11-11
sweet, so i got some new stuff installed by checking the boxes in the system menue, and I got my dvd to play so thats good now.  The main thing that I am wondering about is why trying to connect wirelessly to my secured router makes the kernel crash.  

Still no sound, im gonne try to contact nvidia tomorrow to see what is up.  The tech support person at emachines seriously asked me what linux was....

---

