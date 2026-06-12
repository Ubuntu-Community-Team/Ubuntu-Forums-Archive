---
title: "Update on SVN on Jan 22nd breaks Beryl again"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by medley on 2007-01-22
Can you imagine? I've been enjoying Beryl for the last 3 days after wrestling with getting it working for 2 weeks. I used the version on SVN that was there until today; it was the only one I could get working. I think what finally fixed it was editing the first line in home/.beryl to specify python2.5. Today adept notifier tells me there is yet another update. I ask myself (based on hellish experience with updates breaking things) "should I? should I?". I click on install, and sure enough, Beryl no longer works. And this time there are no errors in konsole or anywhere. And the .beryl config file no longer exists, so I can't even check that. 

This is painfully frustrating. And it seems to happen over and over again. Finally people get things working and the next update breaks it. I know, I know, "don't use SVN unless you plan on doing debug triage, etc...". I just want Beryl to work. It's beautiful when it does. But it's like the highschool flirt. She'll tease you for a day or two, then dump you like a load of bricks.

Can someone who actually is involved in the work being done on Beryl please give me some indication where I should investigate this time? I am getting nothing. In sysguard, beryl-manager is running, but the theme-manager does nothing, not even an error. 

Don't hint at drivers, etc. They are fine. Beryl worked spectacularly for 3 days until I did this stupid upgrade. I should have known better.

Please help.

---

### Post by dbbolton on 2007-01-22
>  Can someone who actually is involved in the work being done on Beryl...

if you want that, then check the beryl forums or the #beryl irc channel

---

### Post by autocrosser on 2007-01-22
Well, Take a look at the Beryl forums. You can go back to a version that works (involves Synaptic & some work). I generally wait & watch the Beryl forums before I update. I still got caught the other day with the Python2.5 beryl-setting-manager problem:wink:.

I know that you know about beta software, but just wait, it will work again soon:grin:. That is both the good & bad about Linux, it is always moving forward. You just need to wait, the developers do it because they LIKE to do it-----not because they are paid to do it.

---

### Post by medley on 2007-01-22
> **autocrosser said:**
> Well, Take a look at the Beryl forums. You can go back to a version that works (involves Synaptic & some work). I generally wait & watch the Beryl forums before I update. I still got caught the other day with the Python2.5 beryl-setting-manager problem:wink:.

I know that you know about beta software, but just wait, it will work again soon:grin:. That is both the good & bad about Linux, it is always moving forward. You just need to wait, the developers do it because they LIKE to do it-----not because they are paid to do it.

Dan, thanks for the thoughtful response. First thing I did was check the Beryl forums, but didn't find them as active as here. Also, I restored .beryl from the trash (don't know if this did anything or not) but it turns out that beryl-manager is now launching. However, beryl-settings no longer works. When I launch it from konsole I get a Traceback saying that line 2 of beryl-settings is trying to "import berylsettings". Then it says "ImportError: No module named berylsettings" So this is where the problem lies I presume, but I don't know why it worked before I did the update this evening.

---

### Post by Shatrat on 2007-01-22
This beryl-settings error is discussed in the last few pages of Trevinos thread on the beryl forums about his SVN repository, although I thought the problem with berylsettings was resolved in the SVN version. There is a fix posted there that might help you, it worked for me when I got the error a few upgrades ago.  You can edit line 2 of /usr/bin/beryl-settings to say python2.5 where it currently just says python.  This may or may not work for you, but it worked for me and others.

Either way, Beryl is still very much bleeding edge software.  If you want it to be really stable and reliable try going to sleep for a few years like rip van winkle and then checking back with the Beryl Project. :)

---

### Post by medley on 2007-01-22
> **Shatrat said:**
> This beryl-settings error is discussed in the last few pages of Trevinos thread on the beryl forums about his SVN repository, although I thought the problem with berylsettings was resolved in the SVN version. There is a fix posted there that might help you, it worked for me when I got the error a few upgrades ago.  You can edit line 2 of /usr/bin/beryl-settings to say python2.5 where it currently just says python.  This may or may not work for you, but it worked for me and others.

Either way, Beryl is still very much bleeding edge software.  If you want it to be really stable and reliable try going to sleep for a few years like rip van winkle and then checking back with the Beryl Project. :)

Thanks. After my last post, I checked beryl-settings, and sure enough I had to once again specify python2.5 in the first line. Took care of it.

---

