---
title: "java+flash+firefox"
date: 2007-08-26
forum: Apple PPC Users
---

### Post by frog_pilot on 2007-08-26
OK, here is what I did:

I installed Gnash 0.8.0 and ibm-j2re1.5,
libflash-mozplugin,
libflash-swfplayer,
libgnash0,
totem-mozilla,
vlc,
mozilla-pugin-vlc,
vlc-plugin-alsa,
x264-bin,
(ppc-codecs, libdvdcss2, realplayer... the whole multimedia-support-progs).

First: while getting java to run, I mentioned the following:

There was no java support at all after installing ibm-j2re1.5. I found, that the symbolic link to the java-plugin-library in /usr/lib/mozilla-firefox/plugins points to /usr/lib/j2re1.5-ibm/jre/bin/ns7/libjavaplugin.so. But there is no such folder /ns7/ and there is also no such library libjavaplugin. In the java-doc is written, that the right plugin-lib for firefox is libjavaplugin_oji.so. You can find it in /usr/lib/j2re1.5-ibm/jre/bin/. I think, this is a major bug, because this was a default installation of  ibm-j2re1.5. To fix this problem, you have to run in a terminal: ```
sudo rm /usr/lib/mozilla-firefox/plugins/libjavaplugin.so
cd /usr/lib/mozilla-firefox/plugins
sudo ln -s /usr/lib/j2re1.5-ibm/jre/bin/libjavaplugin_oji.so
```After this procedure you can test your java-install at the java-test site [www.java.com/download/en/installed.jsp ]("www.java.com/en/download/installed.jsp")
It will tell you, that you have JRE 1.5.0 from IBM Corp. And > You don't use the newest version of Java. The newest is JRE6 Update 2 ---> download now but i think there is no package for debian-ppc.

After all, I got Java running. Flash films are also running, but there is a sound-problem. It shows me the flash-animation in my browser window, but the sound is white noise... Is it because of compatibility-problems with flash and gnash?

And when I open the youtube-site, it tells me > Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player.  What's the matter???

**To point out my questions:**
1. Is there anybody who can play flash-animations in the browser-window with sound, tell the url and how you got it running (I tested with this flash animations: [http://www.couchkartoffelsalat.de/]("http://www.couchkartoffelsalat.de/"). Can you listen the sound here?)

2. Can anybody play youtube-videos in the browser-window? How did you manage this?

3. When I am on a flash-website and I want to get to another site (for instance when I am on youtube.com and I type in ubuntuforums.org, firefox crashes/closes during loading ubuntuforums.org). Does anybody mention similar problems?

---

