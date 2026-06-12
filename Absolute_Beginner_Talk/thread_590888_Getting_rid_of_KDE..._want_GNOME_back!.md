---
title: "Getting rid of KDE... want GNOME back!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by moerl on 2007-10-25
I'm using Ubuntu 7.10 and installed KDE to check it out and compare. Although KDE seemed very responsive and fast in general, I feel that GNOME is less cluttered and "simpler" to look at. Also, when in a KDE session, I could use none of the Compiz Fusion effects I can use when in a Ubuntu session. That may be a matter of a simple setting not being enabled.. but whatever.

In short, I prefer GNOME for the time being. Frankly, I find the whole GNOME vs. KDE debate rather confusing.. I'd like to see a list of pros and cons for each, because trying both out seemed to barely give me an accurate enough picture/comparison.

Yes, KDE is more Windows like, but there's a reason I'm checking out Ubuntu--to get away from Windows. Besides.. I can't say I'm in much need of a "friendly" transition. I feel perfectly at home in Ubuntu with GNOME. I don't need Ubuntu to try to mimic Windows... another reason why I could use a list such as the one mentioned. Pros and cons. What does KDE give me that GNOME does not? The other way around?

Anyway.. for now, I've decided that GNOME is for me, while remaining curious about all of the above. How do I get rid of the KDE desktop environment entirely, including everything that came with it, like the apps and everything?

Thanks

---

### Post by moerl on 2007-10-25
Ok, even though I had searched the forum before making my post.. a Google search AFTER posting this led me to this thread, which perfectly covers what I was trying to get answered with this thread: [http://ubuntuforums.org/showthread.php?t=126210](http://ubuntuforums.org/showthread.php?t=126210)

It also led me to this: [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php)

Damn Interwebs. Sorry about the unnecessary "overhead".

---

### Post by moerl on 2007-10-25
Ok maybe I spoke too soon.. I ran the command found at this page, [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome), (excellent page by the way.. amazing collection of tutorials, very friendly, well written, etc., bookmarked immediately), and although things seem to have worked, I'm stuck with a Kubuntu boot screen and Kubuntu login screen. Once I log in, it's all GNOME, but booting and the login screen are still KDE style, it seems. Any way to fix this once and for all?

Thanks

BTW
When I used that command.. at one point the system asked me if I wanted to kill the current window manager or something.. and I figured, well, yes. So it kicked me to a pure text based black screen with a bunch of commands which all seemed to have completed [OK]. I rebooted and then noticed the remnants of KDE.. don't think that should matter, but I figured I'd mention it for the hell of it.

---

### Post by RomeReactor on 2007-10-25
Hi. moerl, in your case go to "System->Administration->Login Window", and on the "Local" tab, select the gnome Human theme.

---

### Post by moerl on 2007-10-25
"Only one software management tool is allowed to run at the same time.
Please close the other application e.g. "Update Manager", "aptitude" or "Synaptic" first."

I'm getting this when trying to install Automatix2. I think it may be related with the removal of KDE. 

I get that after simply downloading the Automatix package and double-clicking it.. then trying to start the installation graphically. So I figured I'll try the terminal way, using the instructions here: [http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.10_AMD64.2C_i386_.28Gutsy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.10_AMD64.2C_i386_.28Gutsy.29)

I followed each step carefully.. and ended up with this:

illjazz@illjazz-ubuntu:~$  sudo apt-get install automatix2
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
illjazz@illjazz-ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
illjazz@illjazz-ubuntu:~$ 

I am definitely NOT running Synaptic, Update Manager OR aptitude anywhere. Unless I'm missing something..

---

### Post by alienexplorers on 2007-10-25
run from terminal
> sudo dpkg - -configure -a

Do not run Automatix. It is known to mess up your system.

---

### Post by RomeReactor on 2007-10-25
Maybe Update Manager is running in the background; you can check if it is in the system monitor. If it is running, it's probably checking the repositories for updates; just wait until it finishes. Also, when you run the dpkg command, use sudo:
```
sudo dpkg --configure -a
```

---

### Post by moerl on 2007-10-25
> **alienexplorers said:**
> run from terminal


Do not run Automatix. It is known to mess up your system.
Is it really that dangerous? I suppose I should steer clear of it then :/

---

### Post by alienexplorers on 2007-10-25
On my system I tried it and it messed up the sources.lst....

---

### Post by moerl on 2007-10-25
Hmmmmmmmmm.. seems like all the KDE apps remained. I still have Kopete, Konversation, KPPP, etc. in my apps list.. strange thing is that they run perfectly fine, even though I'm in GNOME now. Guess that command didn't exactly do its thing all the way :/

---

### Post by moerl on 2007-10-25
Ok nevermind.. ran that command again, and selected NO this time when that blueish looking screen showed up prompting me to kill the KDE daemon or something. I said NO this time and it continued removing things.. it also told me that if I select no, it will simply do the rest of the job once I restart the display daemon the next time or something along those lines. That should do the job.

---

### Post by moerl on 2007-10-25
Yup.. that command certainly did the trick this time. All KDE related stuff is gone, boot screen is back to Ubuntu, as is the default logon screen. Yay! It even killed my Opera, which I had originally installed in Ubuntu.. lol, oh well!

Is a good way of checking what I actually have installed on the system by using add/remove and looking for the installed apps? I guess that makes sense. Guess I'll just add Opera back now. Thanks for your help!

---

### Post by moerl on 2007-10-25
This is curious.. I just added Opera back, and when I ran it, it opened the tabs I last had open! (This is the default behavior in Opera, but obviously suggests that Opera wasn't technically removed from the system.. its files seem to have remained in place. It somehow just got removed from the list of installed apps somewhere..)

Whatever. It's back now.

---

### Post by forestpixie on 2007-10-25
there are config files hidden in /home - I think they only go if you do a purge

---

### Post by jrharvey on 2007-10-25
you should be able to get rid of KDE through synaptic package manager. Be warned though that if you are keeping any KDE programs they will act a little funny. With fiesty I wanted to try out KDE but when I got rid of it it made K3B act really funny. K3B was the only KDE app that I used but I still used it alot. There wasnt any problem with the performance of the program, the graphics would just flash and stuff of that nature. Also I had to delete it and then reinstall it.

---

### Post by jrharvey on 2007-10-25
> **moerl said:**
> Yup.. that command certainly did the trick this time. All KDE related stuff is gone, boot screen is back to Ubuntu, as is the default logon screen. Yay! It even killed my Opera, which I had originally installed in Ubuntu.. lol, oh well!

Is a good way of checking what I actually have installed on the system by using add/remove and looking for the installed apps? I guess that makes sense. Guess I'll just add Opera back now. Thanks for your help!

If you reinstalled KDE then I bet all your settings would be what you set them to. Say if you had a panel on the right side, it would probably still be there if you reinstalled. You can hardly ever truly remove every trace of a program or in this case a desktop environment. Im sure there are ways but I always wipe the system clean at least once a year anyway to get rid of all that junk just lying around.

---

