---
title: "[SOLVED] System beep at odd occasions"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-09-23
Suddenly I get system beep when OpenOffice asks me if I want to save a document or when Firefox can't find any words on a web page that matches my search...
I've disabled system beep in sound preferences, but no luck. I haven't checked if I have the option of disabling it in BIOS, but I don't really want to either, as I think there's a point in having the system beep at rare, critical occasions when it's the only way of knowing what your PC is generally up to. SO - anyone got a hint?

---

### Post by Happy_Man on 2007-09-23
I believe that that is an OpenOffice setting.... not in GTK or GNOME properties. I think the firefox one is in about:config, under the key accessibility.typeaheadfind.soundURL. Not sure, though. I like my system beeps.

---

### Post by OliverN on 2007-09-23
> **Happy_Man said:**
> I believe that that is an OpenOffice setting.... not in GTK or GNOME properties. I think the firefox one is in about:config, under the key accessibility.typeaheadfind.soundURL. Not sure, though. I like my system beeps.

I can't really find it. Anyway, isn't it strange that these turned on spontaneously and simultaneously if they are individual settings? -Just dreaming of the neat switch labeled 'solve issue' ;)

---

### Post by Happy_Man on 2007-09-23
The OpenOffice beeping is default, btw. As for Firefox, well, it's useful if I don't have my speakers on.... but the OpenOffice beeping? Gotta go.

---

### Post by OliverN on 2007-09-23
> **Happy_Man said:**
> The OpenOffice beeping is default, btw. As for Firefox, well, it's useful if I don't have my speakers on.... but the OpenOffice beeping? Gotta go.

Hm, guess I just didn't notice until now, then. Well, it's not like I lie sleepless at night because of it either. I just want to make sure it doesn't happen while I'm in a lecture or when somebody's sleeping in the same room. It's quite loud, and I often find it embarrassing not being able to control it. For me Linux is a lot about feeling in control over my PC, and this beep is just making me its bitch. Forgive the wording :)

---

### Post by Dr Small on 2007-09-23
System > Preferences > Sound > System Beep > [Uncheck] Enable System Beep

That should stop the system beeps period.

Dr Small

---

### Post by Happy_Man on 2007-09-23
He already said he did that..... and if you didn't, please go and do that now, OP, while I berate myself for not reading your post right.

---

### Post by OliverN on 2007-09-23
> **Dr Small said:**
> System > Preferences > Sound > System Beep > [Uncheck] Enable System Beep

That should stop the system beeps period.

Dr Small

I already did that. I guess I wasn't being completely explicit about that, so sorry.

> **Happy_Man said:**
> He already said he did that..... and if you didn't, please go and do that now, OP, while I berate myself for not reading your post right.

No, you are right, I already did that. And I can tell from other posts, that for some reason that just isn't universal.

[EDIT]

But I >really< don't get it, cos another one of my beeps happen when I press a certain button (on my Danish keyboard it contains the symbols ^ ¨ ~) which requires a double-pressing to actually type it's symbols. If I press this button >once< and then press backspace, the PC beeps regardless of what app I'm currently typing in! Why doesn't that classify as a >system< beep, and how do I kill it? I've been to keyboard preferences, but no luck there. And if anyone has specific guidance on how to kill beeps for firefox and openoffice,  I'd like to hear :)

---

### Post by gedanken on 2007-09-29
I'm having the same issue - I thought there may have been an option in kcontrol to solve it (I don't run kde but use some of the apps). It is driving me mad - whenever I backspace in terminal and it reaches the start, the system beeps until I let go! :hm:

---

### Post by gedanken on 2007-09-29
OK fixed - [http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

Hope you have the same luck, Oliver

---

### Post by OliverN on 2007-09-30
> **gedanken said:**
> OK fixed - [http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

Hope you have the same luck, Oliver

yea, I already read that thread, but thanks for reminding me of it. The reason I didn't go with the 'blacklist pcspkr'' - solution was that I wanted a system beep to remain on the rare, critical occasions when it is actually the *only* way of knowing what's going in with the pc. But it seems to be way too much work shutting all these beeps down separately so for now it's blacklisted! Thanks again. I'm gonna mark as solved.

---

### Post by gedanken on 2007-09-30
Yeah I ended up blacklisting it too. It's just too much hassle. :shrug:

---

