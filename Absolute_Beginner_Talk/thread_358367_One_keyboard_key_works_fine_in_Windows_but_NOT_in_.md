---
title: "One keyboard key works fine in Windows but NOT in Ubuntu"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-10
I use a UK-English 105-key keyboard on a dual boot system (Edgy and WinXP).
Recently my Left-Arrow key stopped functioning although all others keys were fine.
What is strange is that this is only a problem in Ubuntu.
When I switch to Windows, this key works perfectly.

Even more strangely, I discovered by chance today that this key, which I had thought was essentially dead (in Ubuntu) will actually cause my music to switch from Play to Pause.
So the key seems to have been mapped to another function.

Can anybody help me recover the functionality of this key?

---

### Post by teaker1s on 2007-02-10
you may find a more suitable keymap and keyboard model in keyboard options,

---

### Post by nickoli_02 on 2007-02-10
Try System -> Preferences -> Keyboard. You should be able to find your keyboard layout in there

---

### Post by PaulFXH on 2007-02-11
Thanks for the replies.
OK, so I went Systems>Preferences>Keyboard>Layout>Reset to Defaults and I've now got my Left Arrow key back.
Sounds so incredibly easy and obvious but I was really on the verge of splurging out on a new keyboard (which actually wouldn't have solved the problem).
However, I still haven't figured out how this aberration happened. 
Best wishes
Paul

---

### Post by nickoli_02 on 2007-02-11
When you install Ubuntu it tries to detect what keyboard layout you're using. It does ask you if the layout is correct during installation, so it's possible you overlooked it. Glad it was an easy fix ;)

---

### Post by PaulFXH on 2007-02-11
Yes, the fix was easy but twice already today I have had to click on the Keyboard Layouts "Reset to Defaults" button as the Left-Arrow key had once again transmogrified itself into a Music Player Pause button.

This and the fact that the default keyboard layout during Ubuntu installation is US English (which has exactly the same functionality for the Left Arrow key as on my keyboard) suggest that this is not at all due to wrong keyboard layout choice on install.

I'm keeping an eye now on what exactly is promoting this mysterious change and I may start another thread if I ever discover what is the cause.

Cheers
Paul

---

### Post by teaker1s on 2007-02-12
for my two thoughts on this:-
1) unless you have session save setting on gnome will reset every time to last saved session
2)To stop this you could set it with xserver
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]

---

### Post by PaulFXH on 2007-02-13
Thanks for the advice, teaker1s

However, I really don't believe this is a problem with my keyboard layout moving from one language/setting to another when I'm not looking.:) 
It really is just ONE key that changes its function (the left-arrow key). I cannot believe there is a language out there that has exactly the same keyboard layout as UK English but with the left-arrow key substituted by a music player Pause button (especially when the other three arrow keys are as they should be).

It seems to me that the problem may be related to Beryl. I can use Right arrow + Ctrl + Alt to turn the Beryl cube anti-clockwise with no problems. However, when I use Left arrow +Ctrl + Alt it moves the cube just once in the opposite direction and then stops.
Nevertheless, if I use Ctrl + Alt+ PgDn to unfold the cube, I can then use either the Left arrow and  Right arrow keys to scroll through the cube faces in either direction.
Weird!!

As I can use the Left arrow key on the numeric keypad this really is not a major headache.
Too, any inconvenience caused by loss of the (main) left-arrow key functionality can be readily relieved by Resetting to Defaults in the Keyboard Layout box.

Cheers
Paul

---

### Post by teaker1s on 2007-02-13
report as a bug

---

