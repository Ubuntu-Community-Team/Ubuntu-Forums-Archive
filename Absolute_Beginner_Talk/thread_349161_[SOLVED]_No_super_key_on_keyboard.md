---
title: "[SOLVED] No super key on keyboard"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by xtrm_redbull on 2007-01-29
Hi,

I manage to install beryl, but my thinkpad r50e has no windows key. Im wondering how can I have a super key? Can I assign other key as  substitute for this? How? 

Im new to linux and xubuntu and a step by step guide will be useful. I really want to use the zoom in function of beryl.

Thanks.

---

### Post by moshuptrail on 2007-01-29
There are two entries under System > Preferences that might help:
Keyboard
Keyboard Shortcuts

But you might post under the Desktop Environments category and see about how to customize Beryl itself.

---

### Post by xtrm_redbull on 2007-01-29
I found the keyboard settings in the xfce settings menu, but i can't figure out how to assign a super key. My laptop doesn't have a windows key on it.

Can anybody point me to step by step guide. 

Thanks for the suggestion moshuptrail.

---

### Post by Waappu on 2007-01-30
Hi

I don't know can you replace super key with fn key?

You can change keybord shotcuts from Beryl setting manager->General options->Shortcuts. Please be careful that you don't create conflict with other shortcuts

---

### Post by xtrm_redbull on 2007-02-01
Thanks waappu for your directions, I manage to change some of the commands that require super key (the zoom function) , using shift key as an alternative. Although I didn't assign it all to shift key, because of conflict with other beryl shortcuts. Thanks again :D

---

### Post by mrphd on 2007-02-25
Go to System->Preferences->Keyboard and under keyboard model in layouts, try Generic 105-Key (Intl). See if this works now.

See [http://ubuntuforums.org/showthread.php?t=312704](http://ubuntuforums.org/showthread.php?t=312704) for more information.

---

### Post by xtrm_redbull on 2007-03-03
Thanks mrphd for your reply and link, my keyboard is already set to Generic 105-Key (Intl), I did some experiment on the settings of system>preference>keyboard>layout options tab>alt/win key behavior and set "Left alt is swapped with left win key" after that I tried that setting with beryl and  I and it actually works I have a super key by pressing the left alt key. The only problem with this method is that it has keyboard shortcut conflicts in beryl and I cant rotate my cube. :confused:

---

### Post by xtrm_redbull on 2007-06-29
Hi,

I installed the compiz fusion today, and starting to play with it. Can anyone suggest to me an alternative key to windows key. Since beryl I used the shift key as super key, but now I want to try out the new plugin's   in compiz fusion like the ring switcher but some of the key commands uses a combination of Shift+Alt+Super+Tab.

I hope someone with similar problem can enlighten me on this one. I'd like to know what do you guys use as an alternative to the windows key, that has less or no command conflicts with other shortcuts.

As always thank you very much. :D

---

### Post by rimoth on 2007-07-03
Hi,

Same goes for me. Is there anyway of using the AltGr key? I also saw a post about remapping the capslock key - anyone done this?...Thanks

---

### Post by xtrm_redbull on 2007-07-04
Yes 3 days ago I got reply from kronepils about this from another thread, How to: Compiz Fusion on ubuntu 7.04. 

>  Originally Posted by kronepils

I use my caps key for super. I have this in my .xmodmaprc:
! No Caps Lock
clear lock
! Caps Lock as Win key
add mod4 = Caps_Lock

Then I have this command in my session:
xmodmap ~/.xmodmaprc

It works wonders for me!

And me :D

---

### Post by Vadi on 2007-07-27
Nevermind.

---

### Post by //randi on 2007-08-02
Preferences>keyboard>alt/win>super is mapped to the win keys

that worked for me.  

-//randi

---

### Post by altonbr on 2007-12-11
> **Vadi said:**
> Nevermind.

So with that, the 'super' key is now... what key?

---

