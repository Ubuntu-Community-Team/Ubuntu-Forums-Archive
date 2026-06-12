---
title: "AMD64 Gutsy no sound or Java in Firefox"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-10-16
Hi all,
I installed the "sneak preview" of Gutsy last night on my AMD64 Gateway, and I'm pleased to say that ALMOST everything works!  The exceptions are hibernate (not that important right now) and sound and Java in Firefox.  I have Java 5 & 6 installed, and have gone through the steps to install 32 bit Firefox (actually Swiftweasel), but still no Java, and more importantly, no sound from any website.  My soundcard is ATI Radeon Express 1150, and it works fine on any application I've run except Firefox.  I've searched and read through the forums.  At this point I'm thinking of going back to the 32 bit OS, since this seems to be a problem with the 64 bit version.  But I thought I'd try asking here before reinstalling the OS again.  Oops, forgot to mention that I switched last week from 32 bit Feisty to 64 bit and that's when my problems started.  Gutsy actually "fixed" my swf problem, but not the Java or sound.
Thanks!

---

### Post by 001100 on 2007-10-16
you should use the 32bit disto of  ununtu more compadible with more "stuff" I would wait 2 days for the final relese of Gusty, I'm upgrading in 2 days when it comes out.

---

### Post by rsambuca on 2007-10-16
> **001100 said:**
> **you should use the 32bit disto of  ununtu more compadible with more "stuff"** I would wait 2 days for the final relese of Gusty, I'm upgrading in 2 days when it comes out.

To what specifically are you referring?

---

### Post by 001100 on 2007-10-16
I mean usually a 32bit os is more compadible with software and hardware.

---

### Post by Kilz on 2007-10-16
> **Speedoo said:**
> Hi all,
I installed the "sneak preview" of Gutsy last night on my AMD64 Gateway, and I'm pleased to say that ALMOST everything works!  The exceptions are hibernate (not that important right now) and sound and Java in Firefox.  I have Java 5 & 6 installed, and have gone through the steps to install 32 bit Firefox (actually Swiftweasel), but still no Java, and more importantly, no sound from any website.  My soundcard is ATI Radeon Express 1150, and it works fine on any application I've run except Firefox.  I've searched and read through the forums.  At this point I'm thinking of going back to the 32 bit OS, since this seems to be a problem with the 64 bit version.  But I thought I'd try asking here before reinstalling the OS again.  Oops, forgot to mention that I switched last week from 32 bit Feisty to 64 bit and that's when my problems started.  Gutsy actually "fixed" my swf problem, but not the Java or sound.
Thanks!

How did you install 32bit swiftweasel?

> **001100 said:**
> I mean usually a 32bit os is more compadible with software and hardware.
Negative. Are you suggesting that an operating system that is not designed for your hardware (32bit) is better for 64bit hardware than one specifically designed for it? Please produce some facts as to what "software" is not compatible.

---

### Post by rsambuca on 2007-10-16
> **001100 said:**
> I mean usually a 32bit os is more compadible with software and hardware.

What Software and What Hardware are you referring to?  The reason I am asking is because there are very few issues with the 64bit system now.  Please be specific when detailing what software and hardware you are referring to.

---

### Post by Speedoo on 2007-10-16
Kilz,
I used your instructions here:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

Since there's no script for Gutsy, I used the manual install method at the bottom.  I must say I was hesitant about removing linux-utils after the strongly worded warning, but decided to try it anyway.

I agree, just about everything works in 64.  Except sound in the web browser.  And Java (so far.)

---

### Post by justsomedude on 2007-10-16
No idea about your sound problems, but did you create a link from *libjavaplugin_oji.so* to your Swiftweasel plugin directory? Should work something like this:

```
sudo ln -sf /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/swiftweasel/plugins
```

Make sure both paths are correct. Hope this helps....

---

### Post by Speedoo on 2007-10-16
Thanks.  This is the closest I could come up with.  Does it look like it might work?

sudo ln -sf /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/libjava.so  /usr/lib/mozilla/plugins

I'm guessing this is the command to create a symlink?  Getting ready to restart my web browser and try it.

---

### Post by Kilz on 2007-10-16
If you want, run the automated script, use the feisty option. 

[For sound, try this package.]("http://home.comcast.net/~deletebox/ia32-alsa-oss_1.0.10-1_amd64.deb")

---

### Post by Speedoo on 2007-10-17
OK, I ran the script (I see on your site you now have a Gutsy option in the script) and selected Yes=1 to install Java.  I no longer get the "missing plugin" error on Java sites, but I only get a blank window where the Java action should be happening.  To be sure, I went here:
[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)
After 2 tries, I get a blank Java window.
Still no sound in swf.
Also, Swiftweasel froze when I tried to bookmark a (non-Java or swf) site.
So, net result, nothing's fixed, another thing's broken.  Still, the lack of the "missing plugin" notification bar is a good sign.
Thanks!

---

### Post by Speedoo on 2007-10-17
Thanks.  I ran the script and installed 64-bit Swiftweasel.  Still no swf sound.
I tried the sound package you posted, no joy.
I'm going to try to report this as a bug on launchpad.

---

