---
title: "open office word"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2008-03-16
open office word has stopped pointing misspellings out. It auto corrects a few words, but doesn't res-underline the misspelled once any more. Any suggestions?? Thanks a lot.

---

### Post by kerry_s on 2008-03-16
did you check your settings?

---

### Post by Joseph5000 on 2008-03-16
Yap,

---

### Post by gobbles414 on 2008-03-16
> **Joseph5000 said:**
> open office word has stopped pointing misspellings out. It auto corrects a few words, but doesn't res-underline the misspelled once any more. Any suggestions?? Thanks a lot.

There are two visible spell checking buttons in the default toolbar configuration of OpenOffice. One of them allows you to manually check the spelling. The other button toggles automatic spell checking on and off. Make sure that the automatic spell checking button is on.

---

### Post by Joseph5000 on 2008-03-16
> **gobbles414 said:**
> There are two visible spell checking buttons in the default toolbar configuration of OpenOffice. One of them allows you to manually check the spelling. The other button toggles automatic spell checking on and off. Make sure that the automatic spell checking button is on.

The manual spell check doesn't detect anything. even if I type only "iughiugiu"
I am looking for the red underlining of e detected wrong word that when I click on it gives me a spelling suggestion, where would I find that? I looked in the default bar. In general does it seem that my computer made some independent adjusters in other programs too, like azureus where a button is missing with out that I would have done anything. But when I write this message the red underline and suggestions are there. Lost.

---

### Post by Oldsoldier2003 on 2008-03-16
> **Joseph5000 said:**
> The manual spell check doesn't detect anything. even if I type only "iughiugiu"
I am looking for the red underlining of e detected wrong word that when I click on it gives me a spelling suggestion, where would I find that? I looked in the default bar. In general does it seem that my computer made some independent adjusters in other programs too, like azureus where a button is missing with out that I would have done anything. But when I write this message the red underline and suggestions are there. Lost.

tools > options then expand language settings. Select writing aids and be sure check spelling as you type in checked in the options window (the bottom one)

---

### Post by Joseph5000 on 2008-03-16
> **Oldsoldier2003 said:**
> tools > options then expand language settings. Select writing aids and be sure check spelling as you type in checked in the options window (the bottom one)

I did all that and it looks ok in the settings, but nothing changes

---

### Post by gobbles414 on 2008-03-16
> **Oldsoldier2003 said:**
> tools > options then expand language settings. Select writing aids and be sure check spelling as you type in checked in the options window (the bottom one)

Oldsoldier2003 is correct. You'll also want to make sure that your dictionaries are enabled -- also in the language settings menu. It might also be a good idea to select *Check in all languages*. If Oldsoldier2003's idea doesn't work for you, please tell us which version of Ubuntu you are using.

---

### Post by Joseph5000 on 2008-03-16
Check in all Languages was set already, and it's Gutsy Gibbon 7.10. As I mentioned earlier. There where other settings in my computer that changed without me doing anything.

---

### Post by forestpixie on 2008-03-16
Open Format > Character and ensure that the language there matches the language in Tools > Languages

Have a look at [this]("http://www.oooforum.org/forum/viewtopic.phtml?t=50862") page, it's a spell check tutorial at oo forum

---

### Post by Joseph5000 on 2008-03-16
Yes it matches, Still no changes

---

### Post by gobbles414 on 2008-03-16
> **Joseph5000 said:**
> Check in all Languages was set already, and it's Gutsy Gibbon 7.10. As I mentioned earlier. There where other settings in my computer that changed without me doing anything.

Oops... I totally missed that you included your OS version in your profile. Perhaps the strange behaviors on your PC are the result of an Edubuntu-only bug... When was the most recent time that you ran a software update on your PC?

---

### Post by Joseph5000 on 2008-03-16
I believe I had an up date today, I believe that was for VLC player. I haven't seen any updates lately for open office

---

### Post by gobbles414 on 2008-03-16
> **Joseph5000 said:**
> I believe I had an up date today, I believe that was for VLC player. I haven't seen any updates lately for open office

In the Synaptic Package Manager, go *File => History*. Look to see if there any updates were installed around the time when you first noticed these malfunctions. You may also want to try some maintenance routines in the command line (terminal). They are:

sudo apt-get --purge autoclean
sudo apt-get --purge autoremove
sudo run-parts -v /etc/cron.daily
sudo run-parts -v /etc/cron.weekly
sudo run-parts -v /etc/cron.monthly

---

### Post by Joseph5000 on 2008-03-16
What do you say! Does that makes sense? Could have something snugged in with this??

Commit Log for Sat Mar 15 11:06:38 2008

Upgraded the following packages:
language-pack-en (1:7.10+20080205) to 1:7.10+20080229
language-pack-gnome-en (1:7.10+20080205) to 1:7.10+20080229
ubuntu-docs (7.10.4) to 7.10.5

---

### Post by Joseph5000 on 2008-03-16
can't I just re-install open office?? and would I loose any information?

---

### Post by gobbles414 on 2008-03-16
> **Joseph5000 said:**
> What do you say! Does that makes sense? Could have something snugged in with this??

Commit Log for Sat Mar 15 11:06:38 2008

Upgraded the following packages:
language-pack-en (1:7.10+20080205) to 1:7.10+20080229
language-pack-gnome-en (1:7.10+20080205) to 1:7.10+20080229
ubuntu-docs (7.10.4) to 7.10.5

The *language-pack-en* and *language-pack-gnome-en* updates are system-wide. Many of the programs on you PC will access these packages in some manner. So, it's possible that one of them is the source of your troubles. First, try those maintenance commands that I posted earlier. Restart you computer. If that doesn't solve your problems. you can try the *reinstall* option on each of these packages in the Synaptic Package Manager. Then restart again.

Did I understand you correctly that other programs besides OpenOffice are malfunctioning. If other programs are malfunctioning, then reinstalling all of OpenOffice could be a waste of your time. However, if OpenOffice is the only malfunctioning program, reinstalling OpenOffice might be a good option.

In any event, it's late where I live and I need to get some sleep. But I'll check the thread sometime tomorrow. Meanwhile, maybe someone else here in the forums can provide a fresh perspective on your problem.

---

### Post by Joseph5000 on 2008-03-16
Thanks I do the same. good night

---

### Post by gobbles414 on 2008-03-16
> **Joseph5000 said:**
> Thanks I do the same. good night

Good morning! How is your situation progressing?

---

### Post by Joseph5000 on 2008-03-16
How do I re-install open office word. Thanks

---

### Post by Lvcoyote on 2008-03-16
Package manager should do it for you....

---

### Post by shad0w_walker on 2008-03-16
You should be able to install it using Add/Remove from the Applications menu. Out of curiosity, how you did you remove it?

---

### Post by Oldsoldier2003 on 2008-03-16
> **Joseph5000 said:**
> How do I re-install open office word. Thanks

in synaptic mark openoffice.org-writer for reinstallation
or in a terminal:
```
sudo apt-get install --reinstall openoffice.org-writer
```

---

### Post by Joseph5000 on 2008-03-16
Yap, there are just a lot of open office files, would I have to re-install all of them??
My spell check doesn't work, and some people tried already last night helping me and we went through all the hoops. Now all I want is to get the spelling reinstalled or the whole word processor.

---

### Post by Joseph5000 on 2008-03-16
Thanks OldSoldier, That didn't bring the desired results. I still don't get the red underlining of misspelled words. Now I am really lost, because we tried that yesterday already for a while. Any more ideas?

---

### Post by gobbles414 on 2008-03-17
> **Joseph5000 said:**
> Thanks OldSoldier, That didn't bring the desired results. I still don't get the red underlining of misspelled words. Now I am really lost, because we tried that yesterday already for a while. Any more ideas?

You might want to try installing a new language in Ubuntu. That might force OpenOffice to reset your spelling. In Ubuntu, go *System => Administration => Language Support*. Does that help?

---

### Post by gobbles414 on 2008-03-17
> **Joseph5000 said:**
> How do I re-install open office word. Thanks

I've read your [Frustration about Ubuntu]("http://ubuntuforums.org/showthread.php?t=727205") thread and I'm sorry to read that you are so frustrated. But I would encourage you not to give up on Linux so quickly. You've been experimenting with Edubuntu. Despite the many similarities and cooperation between the two distributions, Edubuntu is NOT the same as real Ubuntu. I've been using OpenOffice in Ubuntu for almost two years, and have only encountered one bug of any consequence during that time -- the bug was patched months ago.

While I believe that you'd do better to install the real Ubuntu over your current Edubuntu installation, **there is a procedure for reinstalling OpenOffice using the Synaptic Package Manager.** All that you'll have to do is go *System => Administration => Synaptic Package Manager* and do a search for OpenOffice. Next, sort by installed applications by clicking on the appropriate column -- just like you were sorting emails or something. This should make it easier to see which OpenOffice packages are installed on your PC. Select all of the installed packages. Then right-click on one of them and choose the *reinstall* option. Then click on the Apply button. Once the reinstall is finished, restart your computer.

Did that help?

---

### Post by Jorgo on 2008-03-17
I had a similar situation.  When I first installed OpenOffice, the spell checking didn't work.  I discovered that I had to install the dictionaries.  This was done in Open Office Word by going File->Wizards->Install New Dictionaries...

Once I did that and restarted OpenOffice, the spell checking started working.  I hope this helps.

---

### Post by Steve Angelidis on 2008-03-17
I had same problem too. Solved it the same way as Jorgo.

Installed dictionary and thesaurus via File>Wizards>Install Dictionaries and then selected them via the Tools>Options>Language Settings> Writing Aids menus. 

Then restart Oo and Bob should be your uncle. 

Sorry to read about your difficulties with Ubuntu. I've been at it for about 3 weeks now and (knock on wood) no negative issues so far. I've also gotten great advice on these forums.

All the best.

---

### Post by gobbles414 on 2008-03-18
> **Steve Angelidis said:**
> I had same problem too. Solved it the same way as Jorgo.

Installed dictionary and thesaurus via File>Wizards>Install Dictionaries and then selected them via the Tools>Options>Language Settings> Writing Aids menus. 

Then restart Oo and Bob should be your uncle. 

Sorry to read about your difficulties with Ubuntu. I've been at it for about 3 weeks now and (knock on wood) no negative issues so far. I've also gotten great advice on these forums.

All the best.

Did you and Jorgo install Ubuntu with a LiveCD or with an alternate CD? I've always installed with LiveCDs, and have never encountered this OpenOffice issue.

---

### Post by Jorgo on 2008-03-18
I've always installed Ubuntu with a LiveCD.  I think the reason I had to install the extra dictionaries was because I needed the English (Australian) one which I assume was not installed by default.

---

