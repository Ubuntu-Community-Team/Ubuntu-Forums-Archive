---
title: "Wireless help for a noob"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by chikimonke on 2006-12-11
To begin, I have tried the 6.10 release, and I am now using the 7.04 release (mainly because I'm a sucker for using "The latest" and I was hoping my problem may have been fixed)  I have gone through the Ubuntu help on connecting to the internet, and have tried the tutorial for setting up an unsupported wireless card.  I have a Dell Truemobile 1350 miniPCI card.  I have installed ndiswrapper and ndisgtk, the latest of both.  When I try to run "Windows Wireless Driver" from the Admin menu, the window comes up, then nothing happens, it's just a blank white window.  I then tried the command line approach, and everything appears to go smoothly in the command line, but when I go to the Network settings, the wireless card is still not showing up.  I try to go into the properties of the card, and the computer thinks for a minute, then closes the network window, with nothing further  happening.  I've pretty much got everything else figured out, this is the last thing (for now) that I need to figure out to be up and running where I want to be.  Thanks for any and all help.

---

### Post by scrooge_74 on 2006-12-11
You should try using 6.06 which is more stable and you may get better results

---

### Post by Kobalt on 2006-12-11
I strongly recommend you to use the Ubuntu 6.10 version : the testing version you are using is VERY unstable at this time, you might only use it if you have very good knowledge of linux/command line. Your problem could be coming from that...

---

### Post by chikimonke on 2006-12-11
Alright, I will try a fresh install when I get home.  Should I be fine using the Desktop version, or should I get the alternate version?  I'm still not 100% clear on what the differences are.  I actually have a few other noob questions, but I'll save those for another post.  Thanks

---

### Post by lyceum on 2006-12-11
Get the desktop version. The alternet is for older machines and server (I think). There is still not promise your wireless will work, but you can get better help with a stable version. I would go with 6.10.

---

### Post by chikimonke on 2006-12-11
Ok, so that's two votes for 6.10 and one for 6.06, 6.10 desktop it is then.  What is the best way to go from 7.04 back to 6.10?  Should I completely remove the partitions and let 6.10 start fresh?  Thanks

---

### Post by lyceum on 2006-12-11
> **chikimonke said:**
> Ok, so that's two votes for 6.10 and one for 6.06, 6.10 desktop it is then.  What is the best way to go from 7.04 back to 6.10?  Should I completely remove the partitions and let 6.10 start fresh?  Thanks

I would start fresh. I don't know of a way to go back to 6.10. And I say 6.10 for 2 reason, 1. You want the latest and greatest. 2. I use 6.10 on my laptop and it runs MUCH better on it than 6.06 did. Some say that 6.06 is more stable, but I couldn't go back to 6.06 now. Just my 2 cents.

---

### Post by Steve S. on 2006-12-11
I honestly couldn't say whether or not 6.10 is better than 6.06, but Dapper (6.06) worked great with wireless, took about 4 minutes to set up (using ra0 instead of eth0) and that was it.

---

### Post by chikimonke on 2006-12-11
Ok, I just did a fresh reinstall of 6.10 and I've gotten further, it appears that the wireless driver was installed, but I still haven't been able to connect (though I might have typed my network key in incorrectly, I'll have to check after work)  So right now I will assume things are working correctly, but I was curious, Steve, when you said that you use ra0 instead of eth0, what does that mean?  Is that something that should be done with wireless?  Thanks

---

### Post by houstonbofh on 2006-12-11
> **lyceum said:**
> Get the desktop version. The alternet is for older machines and server (I think). There is still not promise your wireless will work, but you can get better help with a stable version. I would go with 6.10.
Both install the exact same thing.  The desktop version is a Live CD with a graphical installer.  The Alternate is a text installer.  The Alternate is faster as it doesn't need to load an entire graphics install into ram.  However, the Live CD is good for seeing how well your hardware is supported.

Back to the OP, it seems a lot of people have trouble with that card.  You may want to change to a different one with high power? :D  If not try the steps at [http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html](http://www.antoniocheca.com/wp/content-text/ubuntu-inspiron6000.html) and [http://www.linuxquestions.org/questions/showthread.php?t=373096](http://www.linuxquestions.org/questions/showthread.php?t=373096)

---

### Post by chikimonke on 2006-12-14
Ok, so I tried a completely different distro (openSUSE 10.2) just to see if I would get different results.  And I did, the wireless worked rather painlessly, but I didn't like the layout and feel of the distro.  I'd really like to stick with Ubuntu, but not having wireless is a big deal breaker right now.  I have tried all the tutorials that I can find out there, and they all seem to say the same thing.  I am attempting to use the same driver that worked in openSUSE, and using ndiswrapper, all the same.  I can't help but feel like there's something that I'm missing.  I have enabled the card in the networking setup, I have disabled and unplugged the wired connection. I have even given the system the old restart to see if things would catch.  Nothing seems to work.  If anyone can shed some light on the situation, it would be much appreciated.  Thanks in advance.

---

### Post by chikimonke on 2006-12-14
I don't know what the etiquette for this is, but I'm posting again to bump this back onto the front page, since it's only been an hour and it has already fallen to the third page.  Thanks

---

### Post by dbd on 2006-12-14
Hmm, it should work if you have the driver installed correctly. Did you use this driver?:
[http://ftp.us.dell.com/network/R81433.EXE](http://ftp.us.dell.com/network/R81433.EXE)
Apparently you should use bcmwl5a.inf in directory AR. Or at least that's what it said here:
 [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)
(which I got to from here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported) )

There may be more info here:
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

Sorry I can't be of any more help.

By the way, I don't think there is anything wrong with the occasional bump. Threads can very easily get buried.

---

### Post by chikimonke on 2006-12-14
Thanks for the reply.  Unfortunately that is all stuff that I have already tried.  Tonight I did a full reinstall, so I could start fresh, incase any of my previous tinkering was hindering me. Then I followed the WiFi document help located in that "Read this first" post, which I had conveniently overlooked before , which is the most detailed tutorial I've seen out there.  (note to you better informed people out there, make sure to point links out like that to dense folks like myself :D )  When I got to the point of running "ndiswrapper -l" to check that the driver was installed properly, it told me that it was the wrong driver.  Now normally I would have thought that I was an idiot again and downloaded the wrong driver, but this is the exact same driver that I used in suse that worked, and in previous installs of Ubuntu that I got further in.  What happened?  I feel so close yet so far away...](*,)

---

### Post by c.dric on 2006-12-14
i had problems with ndiswrapper not loading my driver (smc pci card) correctly the other day ... then i've uninstalled the version of ndiswrapper installed by synaptic and manually installed the latest version from sourceforge and it worked fine. 

if you say your driver worked fine with another distro i suspect that may be your problem too.

You can find the instructions in this thread (3rd post from FrodoB)
[http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=315745&highlight=ndiswrapper)

Don't forget to remove the old version with synaptic, and to remove the driver dir in /etc/ndiswrapper/ before going ahead with the manual install.

---

### Post by c.dric on 2006-12-14
Also "Make sure the INF file, SYS file and any BIN files (For example, TI drivers use BIN firmware) files are all in one directory. "

---

### Post by Subw00fer on 2006-12-15
Hey everyone.  I figured I would post here rather than starting another thread about wireless connection problems.

I just got Ubuntu 6.10 installed on a second hard drive and I am having problems connecting to the internet with my wireless Linksys card.  I disabled WEP on my router and I tried connecting by using the SSID that I gave my router in the Network settings under administration but that didn't work.  I couldnt even ping my router so something must be really wrong that I am doing.  Other than that, I am completely lost about this and I can't get my wired card to reach my router so I have to rely only on the wireless.

Please help and thank u!

---

### Post by houstonbofh on 2006-12-15
> **Subw00fer said:**
> Hey everyone.  I figured I would post here rather than starting another thread about wireless connection problems.

I just got Ubuntu 6.10 installed on a second hard drive and I am having problems connecting to the internet with my wireless Linksys card.  I disabled WEP on my router and I tried connecting by using the SSID that I gave my router in the Network settings under administration but that didn't work.  I couldnt even ping my router so something must be really wrong that I am doing.  Other than that, I am completely lost about this and I can't get my wired card to reach my router so I have to rely only on the wireless.

Please help and thank u!
I would not continue with this thread...  It is unrelated, and buried.  Start a new thread with a better title for you.  Use something specific like "Linksys WMP54G - No connection" and in the thread we will need model and version.

---

