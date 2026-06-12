---
title: "How to configure Talker for KSayIt/Festival ?"
date: 2008-01-17
forum: Assistive Technology &amp; Accessibility
---

### Post by Bob Unitt on 2008-01-17
I'm trying to get text-to-speech working on my 7.10 Gutsy. So far I've installed KSayIt and Festival, but I can't select a Talker as none are offered in the appropriate dialog. When I run KSayIt it asks me to configure it, which I start. The next screen 'KTTSMgr' then offers me a tab for 'Talkers' and an 'Add' button. I press the 'Add' button and get an 'Add Talker' dialog offering various languages in one drop-down box, or 'Festival Interactive' or 'Festival Lite' in the other. Regardless of what I select here, when I press 'OK'  I'm presented with a 'Talker Configuration' dialog. This contains a disabled empty drop-down list 'Select Voice' and a 'Rescan' button. I assume 'Rescan' is used to find  some kind of voice files, but when I press it nothing is found and the drop-down list remains disabled. I've downloaded a tar of Male English voices which contains 'rablpc16k.scm' and 'rablpc16k.group', but I don't know if they're the missing voices or, if so, where they should reside on the system.

Any assistance would be gratefully appreciated...

---

### Post by Bob Unitt on 2008-01-28
Bump... ?!

---

### Post by raylitalo on 2008-01-31
Bob,

I'm having similar problems.   I can't get a voice selected, and the controls are always enabled.  If anyone has any clues, I have been really struggling with this and am desperately seeking help--there are very few posts of this out in google-land, maybe this is a new bug?  I'll look into the bug-reporting system and give that a try.

Ross

---

### Post by raylitalo on 2008-01-31
Bob,

I'm guessing its not a bug, mine is working now after my son helped me out.  (He is a real, actual Linux Guru, they are handy to have around.)

This is what he'd done::

sudo apt-get install festival

(I thought I had festival already installed via the "add/remove programs", but the command-line did something.  I also thought that since I had the kttsd daemon installed, that meant I had installed festival, but now I'm not so sure. )

Then run 
apt-cache -n search festival

This should give you a list of voice packages you can install:

Then run

sudo apt-get install <package-name>

for each voice you want to use.

For example, to install the

festvox-kdlpc8k - Americal English male speaker for festival, 8hz sample rate

run

sudo apt-get install festvox-kdlpc8k

If you are having the same problem I was having, this could help.

--I've reconstructed this by looking at my history, hoping I haven't missed anything.


Good luck,

Ross

---

### Post by Bob Unitt on 2008-02-01
Ross - that did the trick !
Thank you very much.

---

### Post by soumen08 on 2008-02-03
Awesome help Mr.Ross! I being a total newbie was able to get ksayit working in minutes!Thank u!

---

### Post by whitefort on 2008-03-18
Just wanted to add my thanks too!  I was going nuts trying to get this to work, and now it's fine!

Thanks!

---

### Post by TheDro on 2008-05-09
I've got a random question about the choice of voices. Is there one like the "woman"'s voice in portal? That would be awesome. I'll be installing festival and all that tonight using this guide.

---

### Post by notsoworried on 2008-05-13
+1 thanks worked for me too

---

### Post by krlhc8 on 2008-09-13
Thank you Raylitato!!!

---

