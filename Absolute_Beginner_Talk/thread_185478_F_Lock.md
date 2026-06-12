---
title: "F Lock"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Baasha on 2006-05-31
I recently found a short utility that turns on the Num Lock automatically at boot up.  I was wondering if anyone out there knows if there is a similar utility to turn on the F Lock?

---

### Post by user1397 on 2006-05-31
[quote=Baasha]I recently found a short utility that turns on the Num Lock automatically at boot up.  I was wondering if anyone out there knows if there is a similar utility to turn on the F Lock?[/quote] I thought I was the only one with an F-lock! well i guess i'm not alone!

i've always wanted to know this, but i've never asked for some reason...:-k

---

### Post by user1397 on 2006-06-11
i'm still interseted in a solution btw!!!!!!!!!!!!

any omniscient ubuntu masters out there know an answer for us humble people? :p

---

### Post by hanexar on 2006-06-11
I'd be glad to have this answer too!

---

### Post by editrix on 2006-06-13
[QUOTE=Baasha]I recently found a short utility that turns on the Num Lock automatically at boot up.  I was wondering if anyone out there knows if there is a similar utility to turn on the F Lock?[/QUOTE]

Having no idea what an F Lock is, I Googled it using Google Linux search and found this on Linuxquestions.org:

> Apparently Logitech, in their infinite wisdom, hardcoded the F lock key as part of the internal keyboard logic, not as a key event, and to be off by default with no way to modify this short of an electronics engineer tearing it apart. As a workaround you can program the media keys on the function keys to just send the appropriate F code instead, and even reverse the setup by having the F keys send media events and the media keys send the F events.

---

### Post by u.b.u.n.t.u on 2006-06-13
I had a M$ wireless keyboard with F-lock from hell a few years ago. There is a patch for Windows. If you want me to find it for you just ask.

I use an apple keyboard now :D

---

### Post by lazyd2 on 2006-06-13
If there is a solution I would like to know as well...(microsoft keyboard)

---

### Post by u.b.u.n.t.u on 2006-06-13
This is to turn off the F-lock right?

I don't have the batch file anymore. I will try to find it or similar and post here.

Edit: update.

Update (use at your own risks):

[http://jtsang.mvps.org/flock-e.html](http://jtsang.mvps.org/flock-e.html)

[http://www.udolpho.com/weblog/?id=00582&title=Killing-F-Lock-ie-restoring-the-function-keys-on-Microsoft-keyboards](http://www.udolpho.com/weblog/?id=00582&title=Killing-F-Lock-ie-restoring-the-function-keys-on-Microsoft-keyboards)

I had a small program that did this. I will try to find it still.

Edit: another update

[http://jtsang.mvps.org/flock-e.html](http://jtsang.mvps.org/flock-e.html)

That looks familar.

"http://jtsang.mvps.org/2gflockelim.zip"

Not much good for Linux maybe but it's a start. A coder here could probably make a ubuntu version perhaps?

Does this help?

---

### Post by Stormboy on 2006-06-13
[http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

not sure if I am on the right track :)

---

### Post by u.b.u.n.t.u on 2006-06-13
One more update.

[http://en.wikipedia.org/wiki/F-Lock](http://en.wikipedia.org/wiki/F-Lock)

and from the above a Linux fix?

[http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

I hope this works for you.

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=Stormboy][http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

not sure if I am on the right track :)[/QUOTE]

I didn't see your post as I was searching. I think you have the answer for Linux.

---

### Post by Stormboy on 2006-06-13
[QUOTE=u.b.u.n.t.u]One more update.

[http://en.wikipedia.org/wiki/F-Lock](http://en.wikipedia.org/wiki/F-Lock)

and from the above a Linux fix?

[http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

I hope this works for you.[/QUOTE]
Yep it's Linux
Think it's a scrip that need to be setup ... waay over my head, newbie here :)

---

### Post by Stormboy on 2006-06-13
[QUOTE=u.b.u.n.t.u]I didn't see your post as I was searching. I think you have the answer for Linux.[/QUOTE]

That's cool!

---

### Post by u.b.u.n.t.u on 2006-06-13
[QUOTE=Stormboy]Yep it's Linux
Think it's a scrip that need to be setup ... waay over my head, newbie here :)[/QUOTE]

I think someone will be able to create that file and hopefully share it here, using a default ubuntu installation as the criteria for the path etc.

---

### Post by Baasha on 2006-08-06
For those who are still looking for a solution to this problem, the link below is the one that worked for me:

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

This is a program that not only allows you to fix the F-Lock problem but also allows you to assign any of the extra function keys that are available on some keyboards to whatever action your little heart desires.

I tried the script that was suggested at Linux Questions but that did not work on my system.  The keytouch program works like a dream.

---

### Post by BoyOfDestiny on 2006-08-27
> **u.b.u.n.t.u said:**
> I think someone will be able to create that file and hopefully share it here, using a default ubuntu installation as the criteria for the path etc.

Yep, :)

Pieced together from [http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix](http://www.linuxquestions.org/linux/answers/Hardware/Microsoft_Keyboard_Function_Key_Fix)

Download the script I uploaded here, extract it in your home directory (for simplicity)

#Open a terminal, 

sudo chmod 777 screw_f-lock
sudo cp screw_f-lock /etc/init.d/
sudo update-rc.d screw_f-lock defaults 99

Reboot.

This solved it for me, all F-keys work as they should. No problem with key combos (I use dosbox, so I need those F-keys). Best of all, I no longer have to toggle the F-lock key to use print screen (i.e. when f-lock was on, print screen became insert???).

Enjoy, should work on MS and logitech keyboards (although only tested MS).

Feedback appreciated.

---

### Post by ariel on 2007-11-21
> **Baasha said:**
> For those who are still looking for a solution to this problem, the link below is the one that worked for me:

[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

This is a program that not only allows you to fix the F-Lock problem but also allows you to assign any of the extra function keys that are available on some keyboards to whatever action your little heart desires.

I tried the script that was suggested at Linux Questions but that did not work on my system.  The keytouch program works like a dream.


Awesome!! that was it. The setkeycodes didn't cut it for me either (perhaps you have to run before X loads, in any case...)... keytouch did the trick!

---

