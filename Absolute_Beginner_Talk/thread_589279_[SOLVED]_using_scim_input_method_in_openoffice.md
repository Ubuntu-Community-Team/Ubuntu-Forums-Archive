---
title: "[SOLVED] using scim input method in openoffice"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-10-24
i can't use scim input method in openoffice and firefox like i do in gedit. every time i need to type Chinese characters i need to open a tomboy note to get the job done.

---

### Post by Sef on 2007-10-24
What happens when you try and type in Chinese?  Does Chinese show up on the scim?

---

### Post by afeasfaerw23231233 on 2007-10-24
no, when i use gedit or tomboy to type chinese, i right click and choose 'input method --> scim input'. but when i use firefox and openoffice, i cannot find this option

---

### Post by jenhsun on 2007-10-24
> **afeasfaerw23231233 said:**
> no, when i use gedit or tomboy to type chinese, i right click and choose 'input method --> scim input'. but when i use firefox and openoffice, i cannot find this option

Of course, you can't trigger the scim input by right click, show popup menu and choose method because of the fundamental application design in different.

Go to your system/preferences and add the language support, enable the complex characters input. You might be able to type Chinese after reboot.

However, currently SCIM and the Desktop integration is buggy. You might find that you can't do the input in your desktop except within your application. My lame solution is disable it. It will back to normal.

:guitar:

---

### Post by afeasfaerw23231233 on 2007-10-24
I have follow your step to add this: 
a scim icon appear on the panel 
but how to type chinese in this situation

---

### Post by jenhsun on 2007-10-24
> **afeasfaerw23231233 said:**
> I have follow your step to add this: 
a scim icon appear on the panel 
but how to type chinese in this situation

Great, try to right click that icon and do the initial setup.
You will see there are tones of input methods you could do. However, please select the input service you like and define your hotkey. After all these setting, trigger your scim by your hotkey.

You better try to play around with this SCIM, it's fun.

---

### Post by afeasfaerw23231233 on 2007-10-24
sorry, i don't know how to do the setting!
i only use changjie3 and english.

---

### Post by Sef on 2007-10-24
When you left click, do you get a list of languages to choose from?

---

### Post by jenhsun on 2007-10-24
> **afeasfaerw23231233 said:**
> sorry, i don't know how to do the setting!
i only use changjie3 and english.

You are doing great. Follow my steps:

Pic1. In your input method step, try to clean all unwant methods except English and changjie3
Pic2. mark the "changjie3", click "edit hotkey", it will bring up a config menu, your window title might be "edit hotkey for changjie3", click the button that I circle...
Pic3. It will ask you the press any key, you can just press any key you want.
Then you will see your config menu has one more option for you, then you click "Add" to add the key for you. Mine is Ctrl+Super_L, I press these two to bring up the input.
Pic4. Here is the Global setting from mine.
The Super_L is my keyboard's Window Logo key, I think you can find it.
Pic5. Here is the result.

If you got problem on input characters in your Desktop, right click the SCIM keyboard icon, bring back the menu and click exit.
Then open a Terminal and type: scim -d     to bring back the SCIM.

---

### Post by afeasfaerw23231233 on 2007-10-24
i have followed your steps but still can't work. i press contrl+window's key but nothing happened. i've also tried the scim-d command and reboot my computer. here's my screenshot

---

### Post by jenhsun on 2007-10-24
> **afeasfaerw23231233 said:**
> i have followed your steps but still can't work. i press contrl+window's key but nothing happened. i've also tried the scim-d command and reboot my computer. here's my screenshot

Your SCIM setup is supposed fine now.
When you do scim -d in terminal, make sure you kill your panel's scim first.

If don't, uncheck the input method "enable complex characters input...."
Go to this site and do in manual
[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

It should work by add all these command. If don't, I am sorry.

Currently SCIM is buggy in Gutsy I mentioned before. It will be fixed and patched some days.

---

### Post by afeasfaerw23231233 on 2007-10-24
i'm too lazy to follow those steps in the link. then i have to wait for a few days until this bug has been fixed....................

---

### Post by cstoh on 2007-10-24
I was happily able to do chinese input when I was using Feisty Fawn. I somehow regret upgrading to Gutsy Gibbon. Suddenly my SCIM input does not work anymore.

---

### Post by jenhsun on 2007-10-25
> **afeasfaerw23231233 said:**
> i'm too lazy to follow those steps in the link. then i have to wait for a few days until this bug has been fixed....................

You know what, I think you can downgrade to Fesity 7.04.
I feel there is no much different between 7.04 and 7.10, and the performance is better.
When you add language support In Fesiy 7.04, it will automatic add the SCIM for you.
All you have to do is to setup your hotkey, that's it. And the SCIM functionality is straight to your desktop global environment.

Wait the fix for Gutsy, or downgrade to keep the function and usability is up to you.

---

### Post by jenhsun on 2007-10-28
About anything related on SCIM, Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)
or here
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)
And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

### Post by afeasfaerw23231233 on 2007-11-09
i have followed the link on your last post and it works!! but now i want to change my first choice as english keyboard, and second choice as changjie3 (because i type english more than chinese). how do to this?

---

### Post by afeasfaerw23231233 on 2007-11-09
i get my problem solved by editing a hotkey for english and changjie3. thanks

---

