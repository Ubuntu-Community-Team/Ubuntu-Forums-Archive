---
title: "Record Video &amp; Audio from Android Phone?"
date: 2016-04-19
forum: Any Other OS
---

### Post by The Bright Side on 2016-04-19
Hey folks! I just started a new job that requires me to record video clips from mobile games. I did several hours of research into this, and I simply can't find any easy way to capture both video and audio from my Android phone using Linux. I did find:

[LIST]
[*]adb command to record only video
[*]Android apps to record using a *rooted* phone
[/LIST]

I really don't want to try rooting my phone because of the danger of bricking it. And I do need audio, not just video. So my question is: with Android being Linux-based, there has to be some Linux app that grabs audio and video, right?

What am I not seeing?

Hope you can help me. :-)

---

### Post by TheFu on 2016-04-19
Interesting problem.  Device audio seems to be the issue.

Maybe ask this question on some android support forums? What do they do?  Google found this: [http://www.howtogeek.com/232674/how-to-record-gameplay-on-your-android-phone-iphone-or-ipad/](http://www.howtogeek.com/232674/how-to-record-gameplay-on-your-android-phone-iphone-or-ipad/) , but the games need to have support for this (according to the article).

If there is an android app that can be like a remote desktop with audio for Android, you can use simplescreenrecorder to capture just that window from Ubuntu. Don't think any of the remote-desktop-apps are good enough to stream gameplay, but I could be wrong.

Another option .... 
My android tablet has HDMI output which carries both video and audio.  My smartphone does not.  You can connect any HDMI recording device to that port and record as you like - provided HDCP isn't involved.  Amazon sells a stand-alone device for $75-$80 that will do this.  [http://www.amazon.com/AGPtek-YPBPR-Recorder-Capture-Device/dp/B00MXK8SGS](http://www.amazon.com/AGPtek-YPBPR-Recorder-Capture-Device/dp/B00MXK8SGS) is one for $74.  Just connect USB2 storage (not USB3) with a single FAT32 or NTFS partition and press the only button on the machine to record.  Simple is better. It makes h.264/AAC files inside an mp4 container.  The AAC is limited to stereo.   There is a microphone jack too, but it only works with analog video input (Component cables), not HDMI.

If you must have Linux involved, then you'll need an HDMI capture device that is supported by Linux. I don't know of any for less than $500. Had a Hauppauge 1512, but it didn't have any Linux drivers at the time.  Alpha drivers are available from Hauppauge, but they didn't work with the exact version of the 1512 I had. Seems they make 3 different versions of the 1512.  Burned out 2 of those devices (bad HDMI switch).  I **don't** love the smell of burning electronics in the morning. ;(

Anyway, some ideas for consideration.

---

### Post by The Bright Side on 2016-04-19
Wow, thanks for all this information, TheFu. I've been doing some more research to see whether, if I don't get it done in Linux, I could succeed in Windows. It wouldn't be ideal, but I do have a Windows 10 partition and a VM as well.

Turns out that the software my colleagues are using to capture from iOS (Reflector 2) theoretically works with Android, but it utilizes Android's own "Screen Cast" function. My Moto G doesn't have that function, even though I have the right version of Android installed. It seems like my phone simply doesn't support it for some reason. Perhaps it will in a future update.

---

### Post by Bucky Ball on 2016-04-19
*Thread moved to **Any Other OS**.*

Good luck, but unless you are running Ubuntu I doubt these forums are the best place for support. We are specifically focused on the distribution Linux Ubuntu, not Linux generally (or Windows).

---

### Post by MartyBuntu on 2016-04-19
Run an Android installation as a virtual machine.
Use any number of screen capture option (Kazam...etc...)

---

### Post by mc4man on 2016-04-19
My sony tablet has a/v screen recording built-in, on nexus the 1st one I tried from google play store worked fine - AZ screen recorder.

---

