---
title: "Language Configuration Now Dependent on OpenOffice?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by clubsoda on 2007-11-20
Under "Language Support" I have a hyphen against "English".  If I try and tick this, the system wants to install OpenOffice and starts downloading some huge files.  Is (X)ubuntu now fully dependent on OpenOffice???  That would be disturbing, given that OpenOffice is not even included on the Live CD.  Wouldn't that mean that language configuration will always be broken unless you install from the "alternative" CD or have a broadband internet connection to download the OO monster?

---

### Post by p_quarles on 2007-11-21
My guess is that the package you're clicking on is actually a meta-package that installs language support for various common Ubuntu apps. Since Ubuntu comes with OpenOffice.org, it probably wants to download the English language spellchecking dictionary for that suite.

I believe you'll be able to get the basic English language pack by using apt-get:
```
sudo apt-get install language-pack-en-base
```
That should allow you to install the language translations without installing the OOo spellchecker.

---

### Post by clubsoda on 2007-11-22
Thanks, that helps, but it also leaves a hanging question mark, i.e. what other adjustments are necessary?  I like the idea of installing specific packages via Synaptic but what about changing LANG settings and any other tweaks which are performed by the Language Support app?  Ideally, that app should notice that I don't have OpenOffice installed and scale back its actions appropriately.  Maybe I should e-mail this suggestion to someone.

---

