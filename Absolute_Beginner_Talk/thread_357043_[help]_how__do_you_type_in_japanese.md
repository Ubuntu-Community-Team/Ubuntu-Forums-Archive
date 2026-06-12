---
title: "[help] how  do you type in japanese?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-09
I somewhat have it set up but not quite. I can type the characters, but its not the same as in ms office. for example. when i type "g", it prints the kana symbol of "ki". How do i get it to print out the characters that i type in english? i want to type "ga" and it to print out the symbol for "ga", rather than a symbol for "g" and a symbol for "a". Does anyone know how to do this?

---

### Post by rai4shu2 on 2007-02-09
I'm using scim/anthy as this page shows you how to install:

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

&#12393;&#12358;&#12356;&#12383;&#12375;&#12414;&#12375;&#12390;&#12290;

---

### Post by The55Gon on 2007-02-09
thanks for responding. i think i have scim, it shows up under system > preferences > scim input method setup. but i cant activate it! i tried opening firefox/openoffice and pressing shift+space or control+space but nothing happens. pressing the two alt buttons allows me to somewhat type in japanese but again i get the wrong characters as explained above. how would i know if scim is installed properly?? and what am i doing wrong!"?!!?! 

thanks

---

### Post by rai4shu2 on 2007-02-09
You should get a keyboard icon in your notification area (in the Gnome panel). You should also have a SCIM application in your System menu. That will let you change settings.

In nearly any application, you should be able to get a menu when you click on the keyboard icon. That should let you select Japanese > Anthy (which will activate the input method and its toolbar, etc.).

---

### Post by The55Gon on 2007-02-10
okay i have the icon thing now, but i can only switch to japanese by pressing the two alt buttons. also, i still have the character problem. when i type "ga" the japanese "ga" doesnt appear, just two characters for "g" and "a". i dont know how to set it to anthy either..

---

### Post by onlysolution on 2007-02-10
You should just be able to click the keyboard icon and the text next to it in the SCIM bar to switch to Anthy.  That will bring up a couple of new input mode buttons for switching between hiragana/katakana, etc.  Anthy defaults to romanji entry liked you wanted originally.  I strongly recommend setting up hotkeys with scim setup (right click the SCIM icon in its toolbar).

---

### Post by gregconquest on 2007-03-27
From this thread, an update:
[http://ubuntuforums.org/showthread.php?p=2360491#post2360491](http://ubuntuforums.org/showthread.php?p=2360491#post2360491)

I am estatic :)  I upgraded ubuntu to 7.04 beta per the instructions here:
[https://help.ubuntu.com/community/FeistyUpgrades]("https://help.ubuntu.com/community/FeistyUpgrades")

I didn't expect any great improvements in the Japanese text entry, and at reboot I didn't notice anything different. However, on the "Language Support" box, there is a new checkbox. It says, "Enable support to enter complex characters". A google search for that string at present turns up one hit -- a bug report on the French version -- nothing helpful for me. And there is no help button there. Nonetheless I checked it, and clicked "Apply" and then rebooted.

BOOM! At reboot I had the IME keyboard on my panel next to the speaker icon and the clock. Oh, could it possibly be . . . ? ? ? I hit my hankaku/zenkaku key (&#21322;&#35282;&#12539;&#20840;&#35282;), and the icon changed! I clicked it, set it to Japanese Anthy, AND IT WORKS! FINALLY! &#26085;&#26412;&#35486;&#12434;&#26360;&#12365;&#12414;&#12377;&#12290;

I don't know if this is an officially supported feature, but if it is, the Asian Language Support box at [http://distrowatch.com/table.php?distribution=ubuntu]("http://distrowatch.com/table.php?distribution=ubuntu") should be checked as it is for openSUSE [http://distrowatch.com/table.php?distribution=suse]("http://distrowatch.com/table.php?distribution=suse")

Greg Conquest
&#12358;&#12428;&#12375;&#12356;&#12391;&#12377;&#12290;

PS I wonder if this will work for kubuntu and xubuntu . . . I'm using xubuntu on my notebook, and I'd love to have Japanese text entry ability there too. I haven't yet found the command lines to upgrade it. The commands I take it are different than ubuntu, but I see nothing official on upgrading xubuntu -- just a few users suggestions that didn't work . . . I can always do it from a new CD I guess . . .

keywords: cjk

---

