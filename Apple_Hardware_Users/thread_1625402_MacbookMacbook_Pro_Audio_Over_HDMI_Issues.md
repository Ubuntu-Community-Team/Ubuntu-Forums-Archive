---
title: "Macbook/Macbook Pro Audio Over HDMI Issues"
date: 2010-11-19
forum: Apple Hardware Users
---

### Post by theSuperman on 2010-11-19
I just found out that the new 2010 Macbooks (not just the Pros) can output audio via HDMI. It works fine under OSX, however not so well under Linux. Under the "Hardware" tab in Sound Preferences, I changed my profile to be "Digital Stereo (HDMI)." I then played around with Alsamixer and unmuting S/PDIF 2 appeared to blast distorted sound through my television speakers.  

The audio is very choppy and full of static, and only stays on for a second at a time before cutting out for another few seconds.  I have searched extensively and do not see any other posts relating to the MacBook (there are others regarding audio over HDMI, but none are too relevant). 

Has anyone gotten the new 2010 Macbook/Macbook Pros to have audio over HDMI??

---

### Post by lael on 2010-11-19
I have a mbp 6,1 and haven't tried this yet - but might be able to later this weekend.

What adapter did you use to go from mini displayPort to HDMI?

---

### Post by theSuperman on 2010-11-20
> **lael said:**
> I have a mbp 6,1 and haven't tried this yet - but might be able to later this weekend.

What adapter did you use to go from mini displayPort to HDMI?

[http://www.amazon.com/gp/product/B0025V2VO0/ref=oss_product]("http://www.amazon.com/gp/product/B0025V2VO0/ref=oss_product")

This is the adapter that I bough from Amazon. It has mixed reviews; some people complain that it does not output audio.

---

### Post by theSuperman on 2010-11-20
Manually selecting an audio output sometimes makes the sound work, however the video and audio are all sped up, as if you were fast forwarding. Any ideas what is going on?

---

### Post by itismike on 2010-12-02
same experience with a MBP 6,2. Audio and video work fine for OSX, but under Linux only video passes through.

---

### Post by theSuperman on 2011-01-15
So has anyone been able to get HDMI audio working on Macbooks/MBP?

---

### Post by itismike on 2011-01-15
No luck here. What would a bug report be opened under? Nvidia driver or Sound Preferences?

---

### Post by theSuperman on 2011-01-16
Actually after posting to my thread, I remembered about another that I was subscribed to. I got an email like a month ago about an update saying how pulseaudio does not correctly setup its sinks (maybe due to a udev problem?)  Anyway, I followed giox069's solution [HERE]("http://ubuntuforums.org/showpost.php?p=10298111&postcount=33") and it worked for me. I now have two sound outputs under the "Output" tab in Sound Preferences, with "Internal Audio" being my HDMI output and "Internal Audio Analog Stereo" being my internal speakers.  So its a hack, but it finally works and I am happy about that.

---

### Post by mpall on 2011-01-22
> **theSuperman said:**
> Actually after posting to my thread, I remembered about another that I was subscribed to. I got an email like a month ago about an update saying how pulseaudio does not correctly setup its sinks (maybe due to a udev problem?)  Anyway, I followed giox069's solution [HERE]("http://ubuntuforums.org/showpost.php?p=10298111&postcount=33") and it worked for me. I now have two sound outputs under the "Output" tab in Sound Preferences, with "Internal Audio" being my HDMI output and "Internal Audio Analog Stereo" being my internal speakers.  So its a hack, but it finally works and I am happy about that.

Tried, and it didn't worked. I'm attempting to bitstream DTS/DD 5.1 audio through HDMI to my A/V Receiver, and it seems that Ubuntu cannot start it. In OSX and Windows, my receiver and HDMI output works fine.
If you please can tell us what you did in order to get sound over HDMI it would be much appreciated. I'm using a LINDY MINI-DP-HDMI Adapter and I have a MBP "17 6,1 model.
Thanks

---

### Post by theSuperman on 2011-01-23
> **mpall said:**
> Tried, and it didn't worked. I'm attempting to bitstream DTS/DD 5.1 audio through HDMI to my A/V Receiver, and it seems that Ubuntu cannot start it. In OSX and Windows, my receiver and HDMI output works fine.
If you please can tell us what you did in order to get sound over HDMI it would be much appreciated. I'm using a LINDY MINI-DP-HDMI Adapter and I have a MBP "17 6,1 model.
Thanks

You tried [THIS]("http://ubuntuforums.org/showpost.php?p=10298111&postcount=33") already and it didn't work? Thats the only thing I can suggest, since it worked for me.

---

### Post by mpall on 2011-01-23
> **theSuperman said:**
> You tried [THIS]("http://ubuntuforums.org/showpost.php?p=10298111&postcount=33") already and it didn't work? Thats the only thing I can suggest, since it worked for me.

Yes. I tried almost everything I could find around the web. Even update to latest ALSA and kernel 2.6.36, but nothing. Audio won't pass to my receiver.
Dunno if it's a problem on the x64 architecture or a bug, maybe, on the x64 ALSA drivers. Btw, what value did you put on the  "load-module module-alsa-sink device=hw:X,3"??? I tried with 1,7 & 1,9 with no success.

---

### Post by mpall on 2011-03-13
Anyone know any other working solution to make Ubuntu recognize my receiver??

---

### Post by mishathegoat on 2011-03-24
I'm also having the same issue as the original poster. I have a MacBookPro 6,1 I tried the workaround but it didn't help..

Any other ideas?

Thanks

---

