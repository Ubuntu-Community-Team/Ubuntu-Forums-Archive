---
title: "Sound Schemes"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Orwell on 2006-11-12
Searched for this, surprisingly could'nt find the answer.

I'm wanting to use some personal sound files for various alerts, specifically, Evolution Mail. I've gone into "Preferences", "New Mail Notification" and have told it where to find the sound I wish to be played upon new mail being received. The file i'm wanting to use is in .wav format.
Anyone know why this isn't working for me? Should I be using a different sound format?

Cheers :confused:

---

### Post by xyz on 2006-11-13
Well I don't use Evolution but I went 
Applications > System Tools > Configuration Editor then click on apps > evolution.
I noticed there's some configuring to be done there. so maybe..

---

### Post by Orwell on 2006-11-13
hmmm, when I go Applications/System Tools I get to something called "Automatix", not sure what it is....

---

### Post by xyz on 2006-11-13
I didn't try this but I opened System > Preferences > Sound.
A windows opens and it says "no sound" which is normal since I use no sound.

But when I click on the small arrow, a menu scrolls down and it says "Select sound file...". Check it out!
Automatix does a lot of things but it won't allow for selection of various sounds as you'll see here:
[Automatix]("http://www.getautomatix.com/wiki/index.php?title=Main_Page")
Let us know...

---

### Post by Abiezer on 2006-11-13
On my Dapper install, the path would be System > Preferences > Sound, where it looks like you can use your own sound file for a number of events and warnings.

[Edit] or what xyz said

---

### Post by linux4me on 2006-12-17
Orwell, did you ever find a solution to your Evolution sound problem?

I have been researching this since I have the same problem and discovered that it was the wav file I was trying to use.

This is what you do in Dapper to confirm that the problem is not with your sound setup:
[LIST=1]
[*]Click System, point to Preferences, and click Sound
[*]Make sure 'play system sounds' is enabled.
[*]Click the arrow button to the right of a system sound that has been assigned, like 'log in', for example, to test it. If none are assigned, assign one of the default sounds and test. If you hear the sound, you know the system sounds are okay.
[*]Next, use one of the unassigned system sounds to select the wav file you are trying to use for Evolution, then click the arrow button to preview it. If you are having the same problem I am, you won't hear a thing. 
[/LIST]

Next, make sure Evolution's mail notification is working:
[LIST=1]
[*]In Evolution, click 'Edit' then select Preferences and Mail Preferences.
[*]In the 'New Mail Notification' Section, use the Browse button by 'select filename' to browse to the /usr/share/sounds folder on your machine and select one of the default sounds that you know works.
[*]Click Close to save your changes.
[*]Send yourself a test email to see if Evolution plays the sound.
[/LIST]

What I discovered in this is that the wav file I was trying to use in Evolution wouldn't work. It played fine in Totem, so I can't explain it. I'm going to try to find some other wav file to work, and failing that, I'll just use a system sound.

---

