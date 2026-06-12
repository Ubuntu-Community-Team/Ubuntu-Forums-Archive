---
title: "absolute basic help needed installing drivers"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by going_diamond on 2007-07-15
Hi guys.

having no understanding of compiling source etc, I need help to install a couple of drivers. I am using feisty fawn, with synaptic package manager or add/remove. The drivers in question are firstly for wifi d link usb card, DWL-G122 Hardware vers C1, downloaded the driver  rt73-cvs-daily.tar.gz from  the douments site i was directed to. It went into what I presume is my 'home' directory. What do I do now?

2nd driver is for a Canon LBP 3200 laser printer mono. The detect printer can find it, but the correct driver is not there. I have downloaded a driver that I was directed to again, and the same thing, only this time its a rpm package that apparantly is not supported on this version. 

I am a real newbie, knowing absolutely nothing about linux and terminals etc, but I do not ever want to go back to windows so would greatlt apreciate some patient help. (like grade one instructions :) )

Thanks for all replies. 

Doug

---

### Post by RomeReactor on 2007-07-15
Hi. I think [this guide]("http://ubuntuforums.org/showthread.php?t=400236") can help you with your DWL-G122. As for your printer driver, do a search on on these forums for the name of your driver and see if anything turns up.

---

### Post by scrooge_74 on 2007-07-15
For your wireless do I little search until you find a howto that works for you, example

[http://ubuntuforums.org/showthread.php?t=442517&highlight=DWL-G122](http://ubuntuforums.org/showthread.php?t=442517&highlight=DWL-G122)

what you downloaded is compress file double click on it to get the drivers 

The rpm for Cannon is for use under Redhat or Suse. There is a tool call alien to convert the rpm package into a deb package

Canon is know for having a bad support for linux

when in doubt [http://www.google.com/linux](http://www.google.com/linux) will take you a long way

---

### Post by going_diamond on 2007-07-17
Thanks guys, now working through the installation. I have another question. I open a particular web site, and a popup comes that tells me I need a flashplayer plugin. I downlode the tar, unpack it, and give it the install command and this error comes up

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

If I need this plug in for the web site, but feisty fawn won't install it, what can I do?

Thanks :(

---

### Post by scrooge_74 on 2007-07-17
Check this on the community docs

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by RomeReactor on 2007-07-17
Here's a link to the [specific page]("https://help.ubuntu.com/community/RestrictedFormats/Flash#amd64andppc"). Unfortunatley, there's still no Flash for the 64-bit architecture; you can, however, use a workaround to use the 32-bit Flash in your 64-bit Ubuntu. You'll have to do some work to get it going, though.

---

### Post by going_diamond on 2007-07-17
Thanks Scrooge, I think it worked. It takes some getting around all this new stuff, but I am hoping that once I get the hang of it, I will apreciate it much better than that other frustrating and unstable platform, windows vista. 

Thanks agin.

---

### Post by going_diamond on 2007-07-17
Hmm Rome reactor

your reply made me think, I did follow installing the restricted codecs etc, and that all went well, when I went back to the site, I got the same pop up re installing the plug in, but it then disappeared. Does this mean that the browser is now handling the stuff on the site, or what? 

Thanks again.

---

### Post by RomeReactor on 2007-07-17
You could try going to YouTube or another site that requires flash to see if it's working correctly; the [test on Adobe's site]("http://www.adobe.com/shockwave/welcome/") tells me I need to install the plugin, but I have no problems with YouTube or any other site that uses flash.

On a semi-related not, you could also check if you have the [Java plugins]("http://www.java.com/en/download/help/testvm.xml") working correctly.

---

