---
title: "[SOLVED] Keyboard - Double Tap Issue"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Rabidmonkey1 on 2007-06-06
Hi everyone.  This might be a basic question, but I just installed Ubuntu today and noticed that when I want to type a quote, I need to double tap the key for it to appear.  My keyboard is fine and works perfectly in my dual booted windows so I tend to think there is a program controlling this somewhere.  Any ideas on how to get rid of the double tap?  Keyboard layout is US: Intl.  Thanks in advance!

---

### Post by Ek0nomik on 2007-06-06
What a weird problem.  ;)

I think changing your keyboard layout will fix it, but what to change it to, I do not know.

Here are two threads related to your problem:

[http://www.linuxquestions.org/questions/showthread.php?t=340333](http://www.linuxquestions.org/questions/showthread.php?t=340333)
[http://www.hostingforum.ca/254741-incorrect-keyboard-mapping-2.html](http://www.hostingforum.ca/254741-incorrect-keyboard-mapping-2.html)

---

### Post by Inxsible on 2007-06-06
Just a wild guess but....

maybe the quote key is an assigned shortcut to something which gets fired before typing the key in text. Maybe you inadvertently changed the keyboard shortcut of something to the quote key.

---

### Post by BostonBrother on 2007-06-06
I have the exact same problem.  I just re-installed feisty about a week ago and the problem came up.  I was wondering if I had set the wrong keyboard during the install.  I think it was us -intl 

Anyway, would love to hear if anyone has a solution to the problem.

[edit]
I guess I should read the links before I post.  Thanks Ekonomics those links were helpful and explain exactly what was going on.

---

### Post by Rabidmonkey1 on 2007-06-06
Alright, thanks everyone, your replies were very helpful.  

If anyone else is having a similar problem, the solution (that worked for me at least ;)), was that for whatever reason, my keyboard was recognized as Us:Intl (With Dead Keys).  

To fix it, go to Preferences>Keyboard and select Add under the Layout Tab.   Scroll down to the bottom of the list and just select U.S. English - don't bother going into the submenu-  Select that and delete your old layout when you're back in the Layout tab and you should be all set.

---

### Post by AAM on 2007-06-06
You have solved the problem! The keyboard was set to something like British instead of US English. The " key doesn't work properly, not does the @ key in that configuration. And there is another keyboard configuration where the " and @ keys are reversed.

How to check? On install when asked to pick a keyboard, use the " and @ key strokes until you find the right keyboard type.

---

