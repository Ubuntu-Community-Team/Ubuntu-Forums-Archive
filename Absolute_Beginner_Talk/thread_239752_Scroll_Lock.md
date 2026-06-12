---
title: "Scroll Lock?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Olly1234 on 2006-08-19
Hey everyone, sorry to bother you again but I noticed when I press "scroll lock" on Ubuntu it doesn't work, I was wondering if this was meant to be, beacuse it works wth my windows OS ? Thanks :)

---

### Post by Big_J on 2006-08-19
You know I never used that key before in my life... but now that you mension it yeah it doesn't work for me either.

---

### Post by dmizer on 2006-08-21
i'm looking for an answer to this one too.  in my case, hitting scroll lock twice is what triggers my kvm to switch.

---

### Post by rowanparker on 2006-08-21
What is the scroll lock meant to do?
Cause it didn't stop scrolling (on Windows) if thats what its meant to do.

---

### Post by ironfistchamp on 2006-08-21
I thought scroll lock was only used in the olden days and was obselete nowadays.

---

### Post by Jedi Josh on 2006-08-29
I have a KVM switch that requires you to use the scroll lock to toggle between PC's.  It won't work for me in Ubuntu since the scroll lock key doesn't seem to be working.  Does anyone else have this problem or is it just something that I have configured incorrectly?

---

### Post by dmizer on 2006-09-01
> **Jedi Josh said:**
> <snip> Does anyone else have this problem ... <snip>
|
|
V
> **dmizer said:**
> i'm looking for an answer to this one too.  in my case, hitting scroll lock twice is what triggers my kvm to switch.

i'm told that most kvm's can be configured to trigger by any set of key combinations you desire.  i can't configure mine because the documentation is not in a language i understand.

---

### Post by DonS on 2006-09-01
Hi,

Under Linux, the Scroll Lock can be used in the virtual terminals (the scary black temrinal you get when you hit ctrl-alt-F1.  Hit ctrl-alt-F7 to get back) as a "pause", allowing you to read messages as they go whizzing by.  This was useful in the olden days, but now all you young whippersnappers are using your fancy GNOME and KDE and whatnot.

Alas, I'm not sure of the answer to your question though :(

---

### Post by dmizer on 2006-09-01
okay ... thanks DonS. I actually remember the days before there were any such thing as windows too.  And the big new thing was norton's commander. whooo.

anyway, i tried scroll lock in the full terminal mode ctrl+alt+f1 ... then i can switch my kvm with the scroll lock key.

it won't work when i am in the gui.  why could this be?

---

### Post by talen.quickblade on 2006-10-19
Same issue here. KVM switch is activated by scroll lock key useage, but when GDM is active I cannot change the status of the scroll lock.  So the good news is that switching to a full terminal allows me to use my KVM switch normally.

In testing the availability of the key: I am not able to toggle the keyboard light for the function, however in GDM I am able to set a keyboard shortcut for the key successfully, and GDM responds with the correct action when the key is pressed.

/** update
found relevent post with more information. seems to be ubuntu specific and has been persistent over last few releases.
[http://www.ubuntuforums.org/showthread.php?p=1446586&highlight=scroll+lock#post1446586](http://www.ubuntuforums.org/showthread.php?p=1446586&highlight=scroll+lock#post1446586)

---

### Post by zenon212 on 2007-05-24
I was messing around trying to solve this KVM/Scroll Lock problem and found something interesting.  Everything in my TrendNet KVM Manual says that the Scroll Lock is the key to use, but when I hit the Num Lock key twice in either Ubuntu or Vista it switches just fine.  I only looked because the Scroll Lock wasn't lighting up the LED.  I hit the Number Lock key once to turn it on and light up the LED and then again to turn it off and I was switched back to my Windows box.

So, for me, Num Lock works in both, but Scroll Lock only works in Windows.

---

