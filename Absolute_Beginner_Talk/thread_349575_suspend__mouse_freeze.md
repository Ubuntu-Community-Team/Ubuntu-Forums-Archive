---
title: "suspend / mouse freeze"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-30
Hi,

I have ibm t60 laptop. Suspend was not working for a while and I used hybernate option. Then I tried yesterday suspend again and amazingly it works so far, I tried 5 times and worked all. However at the last try, although computer woke up nicely, mouse freezed, keyboard was ok, but I could not find the shutdown key, so I had to push power button to restart the computer.

Why mouse freezed? Is there a way to recover? If freezes again, is there a way to shutdown laptop by logging of ubuntu rather than pushing power button?

thanks
findik

---

### Post by jgubes on 2007-01-30
ctrl+alt+del

---

### Post by findik1 on 2007-02-01
that did not work to shut down at all.

For the mouse: even if you move mouse around, there is no way that I can click on any application. Background applications all freezed

---

### Post by HotFoot on 2007-02-02
> **findik1 said:**
> that did not work to shut down at all.

For the mouse: even if you move mouse around, there is no way that I can click on any application. Background applications all freezed

I have had this exact problem.  It occurs once in a while when I am switching between applications or if one application is busy and I try moving the window.  I'm able to move the mouse cursor, but I can't click anything.  In the past, I could fix this problem by hitting alt+esc, but since I've installed the beryl window manager, even this doesn't work.  Is there a different combination I should be hitting to kick-start the mouse action?  ctrl+alt+del doesn't do anything for me.

---

### Post by findik1 on 2007-02-08
yes, I can move mouse around but there is no clickable icons on the desktop, everthing freezed. Panels freezed. so only thing I do is to force quit by pressing power button which I dont like at all, not good for laptop. there should be a way.

---

### Post by Claus7 on 2007-02-11
Hello all,

You are lucky that you have your mouse working. I have freezing issues where I cannot move even the mouse. As I have searched the Ubuntu forums I have found out that instead of Ctrl+Alt+Del you should use [COLOR="Red"]Ctrl+Alt+[COLOR="RoyalBlue"]Backspace[/COLOR][/COLOR]. I hope that this might help you to avoid hitting the power button. For my case I use a desktop instead of a laptop and I think that my problem has to do with hardware issues. Unfortunately the combination I described you doesn't work in my case...
If our case is indeed a hardware problem, which might be the best way to find out what is going on?

Regards!

---

### Post by Claus7 on 2007-06-09
Hallo,

This is my story of how I was able to solve my problem.

Both from windows and Linux I was facing freezing and restarting problems. Lately they were very irksome. In windows the problems where more intense (the sequence was far greater than that of Linux). I searched the net a little bit and almost every post was indicating that it was a hardware issue. Especially for the kernel panic message it was posted that it had to do with memory issues. 
So while I was trying to find a pci slot to my motheroboard I tried to remove the memory card. I wiped it with a damp cloth (on one side it had a lot of dust not to say dirt, even inside the port, the other side was very clean I have to say). Anyway I put it back and from that time I face no problems of freezing or restarting. Just in case someone has the same problem.
From windows if I remember correctly it had something to do with product 768_1.
I have to add that not always I saw the kernel panic message. This was happening when I wanted to open my computer and I couldn't log in to Ubuntu (very few times). The general symptoms were freezing and restarting. Even the alt-control-backspace combination as I have said, didn't work. Now all seem to be OK.

This issue, as I have searched, unfortunately does not have only one cause. Yet, I think that this solution is easy and it may save you a lot of valuable time.

Regards!

---

