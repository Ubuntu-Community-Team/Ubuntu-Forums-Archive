---
title: "Arabic text!!!"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by ubugoda on 2006-03-02
i'm using Ubuntu 5.10, Breezy Badger!,And i can't read or write any Arabic text!!
anyone can help??thnx!!

---

### Post by newuser111 on 2006-03-02
sudo apt-get install language-support-ar

sudo apt-get install language-pack-ar

sudo apt-get install language-pack-gnome-ar

---

### Post by ubugoda on 2006-03-04
the packages are downloaded and installed well but still not working,,i've tried restarting and doing the same as root,,,
thnx anyway

---

### Post by rameez on 2006-05-12
I have the same problem, I can view arabic but when vowels are used it unjoins the words, anyone has a solution for this?

---

### Post by matthew on 2006-05-13
You may not have installed a keyboard layout for an arabic keyboard yet.

If you are using Gnome try this:
Right click on the bottom panel
Select from the menu: Add to panel->Utility->Keyboard Layout Preferences
A new button should appear on the panel. Right click it and choose Preferences
From there you can add an Arabic keyboard layout of your choice as well as other languages
Then you can switch language input by clicking on the keyboard button

EDIT: I attached 3 screenshots; one of me using OpenOffice2.0 and typing in both English and Arabic, one of the button I refer to showing the USA keyboard layout enabled and another with Arabic enabled.

---

### Post by Jagot on 2006-05-13
Not sure if this is relevant, but do you have the arabic fonts package added?  If not,:

```
sudo aptitude install xfonts-intl-arabic
```

Then rebuild the font information cache files:

```
sudo fc-cache -f -v
```

---

### Post by matthew on 2006-05-13
I just thought I'd add this for those who figure out how to add the keyboard layout but don't know where each letter is located.

[IMG]http://www.datacal.com/s_images/arabic-101-layout.gif[/IMG]

---

### Post by Mahmoud on 2006-05-17
Any keyboard shortcuts to change Language?

---

### Post by mostwanted on 2006-05-17
[QUOTE=matthew]I just thought I'd add this for those who figure out how to add the keyboard layout but don't know where each letter is located.

[IMG]http://www.datacal.com/s_images/arabic-101-layout.gif[/IMG][/QUOTE]

How do you write in Roman letters? Do you need to change keyboard layout to do that?

---

### Post by Maria_Firewire on 2006-05-17
I have done this for German...I think it is probably the same for Arabic.

If you are using Gnome go to System > Preferences > Keyboard > Layouts (Tab)

Add whatever language you want in addition to your default. Then under the 'Layout Options' tab you can select your preferred shortcut to switch between language groups. I have mine set as ALT-SHIFT because its comfortable.

hope this helps! :) 

Maria

---

### Post by rameez on 2006-05-18
my problem was atually the shor vowels, when you have short vowels in arabic the letters are seperated.

---

### Post by matthew on 2006-05-18
[quote=rameez]my problem was atually the shor vowels, when you have short vowels in arabic the letters are seperated.[/quote]I'm sorry, I haven't been able to reproduce the problem so I can't figure out how to solve it. Anyone else??

---

### Post by rameez on 2006-05-20
this is how it seperates the letters with vowels

---

### Post by Googler on 2006-05-20
[QUOTE=Mahmoud]Any keyboard shortcuts to change Language?[/QUOTE]

use this command to change the language by using alt+shift
```
setxkbmap -layout "us,ar" -option "grp:alt_shift_toggle"
```
you can make it as script and put a shortcut in the desktop

---

### Post by Mahmoud on 2006-05-20
> 
I have done this for German...I think it is probably the same for Arabic.

If you are using Gnome go to System > Preferences > Keyboard > Layouts (Tab)

Add whatever language you want in addition to your default. Then under the 'Layout Options' tab you can select your preferred shortcut to switch between language groups. I have mine set as ALT-SHIFT because its comfortable.

hope this helps!

Maria

Thanks.. It works :)

> 
```

setxkbmap -layout "us,ar" -option "grp:alt_shift_toggle"

```
you can make it as script and put a shortcut in the desktop

Googler

Thanks for the command. Using Keyboard shortcuts in Preferences are easier

---

### Post by rameez on 2006-05-21
did anyone else ever get this problem with short vowels?

---

### Post by menkent on 2007-02-11
it seems that many of the arabic fonts just don't support voweling. try importing the traditional and/or simplified arabic fonts from windows.

---

