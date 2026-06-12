---
title: "[SOLVED] Typing Special Letters Problem"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Killer Cop on 2006-08-31
Hi,

I have just downloaded and burned Ubuntu to disk and boot'ed my computer. I have not installed Ubuntu yet. It all goes fine but when I try type type - ? * ' letters, for an example, its comes up with different letters. Like if if pressed ' it came up with ? I think it was.

Why does Ubuntu do that, and how do I fix it?

---

### Post by macdo on 2006-08-31
At a guess, your keyboard is not a 'regular' qwerty. 
Fear not! in the installer, you get an option to choose your keyboard - and a chance to test it. 

There should also be an option to change the keyboard layout in Gnome, but I can't tell you where, as I'm under KDE...

---

### Post by Killer Cop on 2006-08-31
The installer?

---

### Post by macdo on 2006-08-31
That's the application on the Desktop of the Live CD that allows you to install Ubuntu to your HD. I *think* the keyboard is step 2.

---

### Post by Jenda on 2006-08-31
Looks like you're used to a different keyboard layout than Ubuntu uses by default, or it detected your keyboard wrong.

What I'd do is create a xmodmap file which gets loaded every time you boot up (unless you need to be able to switch keyboards).
It involves creating a file that contains all the keycode (a number the PC knows your keys by) - keysym (a name for a symbol, eg. letters are simply a,b,c,etc., but the keysym for * would be 'asterisk') combinations you want on your keyboard. Check out /usr/share/xmodmap/xmodmap.<something> (replace <something> with your appropriate locale).

---

### Post by Killer Cop on 2006-08-31
> **Jenda said:**
> Looks like you're used to a different keyboard layout than Ubuntu uses by default, or it detected your keyboard wrong.

What I'd do is create a xmodmap file which gets loaded every time you boot up (unless you need to be able to switch keyboards).
It involves creating a file that contains all the keycode (a number the PC knows your keys by) - keysym (a name for a symbol, eg. letters are simply a,b,c,etc., but the keysym for * would be 'asterisk') combinations you want on your keyboard. Check out /usr/share/xmodmap/xmodmap.<something> (replace <something> with your appropriate locale).

English please.. I'm new to Linux... And I have tried getting Linux for about a half year, and finally now I have succeded. You know why? Because it's so freaking complicated! I understand why Linux hasn't become popular like Windows.

---

### Post by Jenda on 2006-08-31
Well, first try the easier advice above. What type of keyboard do you have?

---

### Post by Killer Cop on 2006-08-31
Logitech MX3000.. And I have also tried with my standard keyboard.. Its the same..

But I'm not ready to install Ubuntu yet.. I have to get this Linux clear first..

---

### Post by macdo on 2006-08-31
What country do you live in, and what language do you speak?

---

### Post by Killer Cop on 2006-08-31
Denmark, Danish.

---

### Post by macdo on 2006-08-31
Okay. I haven't got a Ubuntu PC anywhere (I use Kubuntu), but if you have a look in the System menu, then there should be an option called keyboard (maybe keyboard layout), where you can set your keyboard to Danish. Have a search - you're using a Live CD, so you'll need to set it each time you reboot.
Have a look here: [http://en.wikipedia.org/wiki/Keyboard_layout]("http://en.wikipedia.org/wiki/Keyboard_layout") to see the differences between your keyboard and the US-International one that is the default in Ubuntu.

---

### Post by Killer Cop on 2006-09-01
That fixes the problem.. Thanks.

---

