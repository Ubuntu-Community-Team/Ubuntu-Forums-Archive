---
title: "Input signal out of range at splash screen"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-10-21
I have just done a clean install of gutsy and when the splash screen appears I get the ubuntu logo but where the loading bar should be I get a message telling me "Input signal out of range". I have tried some of the suggestions from previous threads but have come up empty. I never had this problem with Fiesty and am wondering if this is a new problem unique to gutsy.

---

### Post by Perfect Storm on 2007-10-21
I don't know what you have tried, buthave you tried editing /etc/usplash.conf

---

### Post by Sain on 2007-10-21
I don't have splash screen at all! :)

This occurred even at booting a live CD.... Screen just goes black (it actually turns off monitor). Eventually, when it loads, everything gets back to narmal.

This happens only with gutsy :-/

---

### Post by rahimveron on 2007-10-21
@sain you have to edit  /etc/usplash.conf with the desired resolution.
Mine was set to a higher reso than 1024*768.
Advise backup your current  /etc/usplash.conf and then edit it.

---

### Post by cwrann on 2007-10-21
when I go to filesystem/ etc/ I do not have a usplash folder.

do I go to etc somewhere else?

---

### Post by Perfect Storm on 2007-10-21
Don't it display anything when you do?
```
cat /etc/usplash.conf
```

---

### Post by ronmarley1 on 2007-10-21
We had this same error message on our RedHat box at work.  It was some time ago, but if I remember correctly, it had something to do with Xorg getting corrupted.  I'll check at work tomorrow and see if I can shed more light on the problem.

EDIT: does the same thing happen when booting the live CD?

---

### Post by cwrann on 2007-10-21
I edited usplash.conf to show the proper resolution. The weird thing is that I now have the load bar when I am shutting down but have the same problems at boot up.

---

### Post by cwrann on 2007-10-24
SOOOO.. nobody else thinks it's weird that the problem was solved in the logoff bar but not the boot up bar. Isn't it the same thing?

---

### Post by aidanr on 2007-10-24
there's 3 'fixes' [here,]("https://bugs.launchpad.net/bugs/150930") [last one]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930/comments/56") worked for me

---

### Post by icheyne on 2008-02-19
Thanks aidanr. I had exactly this problem and it worked for me too.

---

### Post by dcstar on 2008-02-19
> **cwrann said:**
> SOOOO.. nobody else thinks it's weird that the problem was solved in the logoff bar but not the boot up bar. Isn't it the same thing?

No, the "boot up" splash settings are actually compiled into the initramfs image - because the X video drivers are not yet loaded at that stage (they are when you shut down - so the settings in that file can be used).

You will find that if you get a kernel upgrade then the boot splash settings on startup will "magically" now be the same as the shut down ones, this is because the upgrade also does an initramfs recompile.

After you change usplash.conf, you can manually do an update with this command (substitute your current kernel for the last bit):
```
sudo update-initramfs -u -k 2.6.22-14-generic
```

---

### Post by erginemr on 2008-02-20
I have written a howto on this. You may also refer to:
[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)

---

### Post by philinux on 2008-02-20
I installed startupmanager from synaptic. Easy gui no command line or editing files. Way to go.

---

### Post by erginemr on 2008-02-20
> **philinux said:**
> I installed startupmanager from synaptic. Easy gui no command line or editing files. Way to go.

I have also tried startup manager. But it has managed to mess up my system once in the past.

The problem with this promising tool is that, there are many advanced options therein for a beginner with no clue on what they do, it assumes some values rather than reading and showing the ones existing in our system (a least for my system) and what's more, there is no cancel button!! So, you open to take a peek, and when closed, it starts out to writing to your system. There should have been a Cancel button.

So long story short, I find startupmanager kind of dangerous and still suggest the old-school way where one has the full control on what s/he does.

---

### Post by philinux on 2008-02-20
It's worked fine for me. I would hardly describe the options as advanced or difficult.

Also under the advanced tab is a button to restore original settings.

---

### Post by erginemr on 2008-02-20
> **philinux said:**
> It's worked fine for me. I would hardly describe the options as advanced or difficult.

Also under the advanced tab is a button to restore original settings.

I still feel that there should have been a Cancel button for crying out loud. I have just tried it to see if there is any improvement. On the surface, everything is amazing, you have all options at your finger tips. 

But still, I had a look at the available usplash resolutions from the dropdown menu, changed it to 1024x768 from 800x600, and reverted back to 800x800. So on the paper, there is no change. But when I close the tool, it started to write down the same settings to initramfs although there was no need to do that. 

Worse still, if the process is somehow interrupted, then the computer won't boot any more with a corrupted initramfs file. 

Bottom line: Startupmanager needs a polish and some on-the-fly undo mechanism to be recommended to a newbie.

---

