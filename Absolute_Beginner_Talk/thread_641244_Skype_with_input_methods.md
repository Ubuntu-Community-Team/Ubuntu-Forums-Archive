---
title: "Skype with input methods"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by riutaro on 2007-12-15
Hello all,

I updated to Gutsy Gibbon in hope that an input method problem has been resolved there but it hasn't; input methods don't work on Skype.

I have a GB-English login and hoping to use at least Japanese, Thai, IPA and Chinese (&#26234;&#33021;&#25340;&#38899;) input methods in different programs.  I have activated relevant language supports at System > Administration > Language Support.

I have followed different howTo's that suggested installing UIM as opposed to Ubuntu default SCIM and using Qt bridge but they weren't really helpful.  Currently, I think I am using SCIM but not sure.  (Have no idea how to clean the mess up  :confused:).  All the input methods above work fine now; except for when I type in something in Skype fields.  Input methods (whichever I happen to be using) gets turned off.  When I focus the cursor in another program, the input method is brought back to activity.

I will appreciate IMMENSELY if you guys could help me out!

---

### Post by misha1983 on 2007-12-18
I have the same problem.

SCIM works fine for all apps except for QT (e.g Skype).

I've tried the approach detailed at [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM), it hasn't helped.

While I'm focused on the Skype window, I can't use the keyboard shortcuts to cycle through my input methods.  I can click on the SCIM icon in the toolbar to change them, but it doesn't influence anything I type into Skype.

I hope someone can point us in the direction of a fix.

For reference, here is my env:

```
misha@poseidon:~$ env | grep IM
QT_IM_MODULE=scim-bridge
XMODIFIERS=@im=SCIM
GTK_IM_MODULE=scim-bridge
misha@poseidon:~$ env | grep XMOD
XMODIFIERS=@im=SCIM
```

Cheers,
Michael

---

### Post by misha1983 on 2007-12-22
Alright, I haven't been able to get Skype going with SCIM. Unfortunately, I haven't got a whole lot of time I can spend on this, so I've decided to try some alternative methods.

This is what worked pretty much straight away: [http://iamacat.wordpress.com/2007/05/31/setup-multilingual-environment-for-non-gtk-apps-in-gnome/](http://iamacat.wordpress.com/2007/05/31/setup-multilingual-environment-for-non-gtk-apps-in-gnome/)

I'm hoping that whatever it is that's preventing me from using SCIM with QT apps at the moment goes away in the future.

Cheers,
Misha

---

### Post by somekool on 2007-12-29
I had SCIM working with Skype and other Qt/KDE apps before. you might want to try removing all uim/scim related packages and then installing skim

BUT : SCIM conflicts with deadkeys and I absolutely need to write in French (w/ deadkeys), Japanese and US English. there for SCIM is not an option for me. I have had SCIM for years with a broken French keyboard and I recently learned of this conflict. If anyone have a solution for this, that would be greatly appreciated.

NOW : I switched to uim-anthy which allow me to use French+English+Japanese perfectly.
except for Qt applications which include Skype and All KDE ... 

anyone for uim-anthy to work with Skype/Qt/KDE ??? 

or did anyone solve the deadkeys conflict w/ SCIM ?

THANKS

---

### Post by ryukent on 2008-02-11
Sounds like you probably need the QT package for UIM installed. I got UIM working in GTK, QT and XIM mode. See:

[http://ubuntuforums.org/showthread.php?t=684469]("http://ubuntuforums.org/showthread.php?t=684469")

---

