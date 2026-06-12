---
title: "Installing 6.06 error :("
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Henaro on 2006-05-07
Hi, I am rather new to Linux.  I have installed and used Kubuntu 5.10.  About an hour ago I tried to install Ubuntu 6.06.  I am installing it to a 14 GB(New partition 1) partition with a 378 MB(New partition 2) swap space.  I am getting an error right at the beginning saying "No root file system".  It says this while it is "Formating swap space in partition 2 of IDE1 Master (hda)..".  After I click "Ok" it goes up to 15% then stops.  I left it for about a half an hour then closed out of it.  I have tried installing it 2 times and failed at both attemps.  I deleted GRUB by mistake and now I cannot get back to my Windows XP.  Please help me out.  

Also a side question, is it possible to use the number pad on linux?  I broke the "five" and "six" buttons on my keyboard a few months ago and I am now more accustomed to using the number pad.

---

### Post by moberry on 2006-05-07
The only thing I can think of off the top of my head is your root parition (/) is not being mounted by the installer. One possible reason for this is if you did not REpartition after you put the ubuntu disk in after nuking kubuntu. The default behavior of the installer when it detects linux partitions is to not give them a mount point. You must specify the mount point in the partition options. Also.. maybe you as a new linux user should use ubuntu 5.10 it is the most recent stable version. 6.06 is a development version.

I have never had a problem with my number pad not working.. make sure num-lock is on :-) it is off by default.

---

### Post by Henaro on 2006-05-07
Oh I see.  Well then I will fool around with Kubuntu and Ubuntu 5.10 for alittle while longer then.  Thanks for the help.  And I just realized I never tried putting NumLock on.  565656565656565656! :D

---

### Post by moberry on 2006-05-07
lol. happens to the best of us :-D

---

### Post by Henaro on 2006-05-07
Rather then making a new topic I brought this one up.  I am having some trouble with GStreamer on kubuntu.  I installed gstreamer through Adept.  Whenever I try to play my mp3 file I get this error through AmaroK:  

```
gstmad.c(1206):gst_mad_check_caps_reset: /thread/decode0/mad1: failed to negociate 44100Hz, 2channels
```

---

### Post by Sef on 2006-05-08
Did you follow the directions for enabling MP3s and other formats.

If not, check out this link:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

