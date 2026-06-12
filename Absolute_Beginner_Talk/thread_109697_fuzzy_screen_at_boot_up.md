---
title: "fuzzy screen at boot up"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by ormus on 2005-12-29
anyone know why my boot up screen sometimes goes all fuzzy until the logon screen appears?
funny thing is that it dont happen all the time.

amd 1.4ghz
iwill mobo
1 gig ram
ati radeon 7000 pci card.

---

### Post by rjwood on 2005-12-29
I don't have an answer for you but you may want to try searching. It works.

---

### Post by ormus on 2005-12-29
yes thx. ive been searching for a month now.

---

### Post by rjwood on 2005-12-29
I suspect it may have something to do with your video/graphics. 

I would ask tselliot or poofyhairguy--they are real good with that stuff.:)

---

### Post by ormus on 2005-12-29
yes agreed, i rather think its my graphics card too. 
or possibly the kt133a chipset?

---

### Post by tedrogers on 2006-10-28
I'm using Edgy with a Radeon X850PE and my Ubuntu logo is fuzzy as well.

I think this is a Radeon thing, because on my eMac at work the boot logo is fuzzy too and that has a Radeon in it.

When I boot from the Live CD the logo is fine - looks great - but when I boot from an install it looks all fuzzy and horrible...like the faded edges have gone all 8-bit graphics!

Now, I have fglrx installed and working (I had to disable Composite in my xorg.conf file), but I would really like to be able to sort this fuzzy  logo screen out. I know it doesn't affect the functionality of the OS, but it's just gets on my nerves so much!

So can anyone out there suggest a solution?

---

### Post by nuzzy on 2006-10-28
I've had that for months...I have to do a CTRL-ALT-+ and then a CTRL-ALT-"-" to get it back

---

### Post by tedrogers on 2006-10-28
> **nuzzy said:**
> I've had that for months...I have to do a CTRL-ALT-+ and then a CTRL-ALT-"-" to get it back

Glad someone else has experienced this annoying niggle.

What do you mean exactly by the above? Where would I perform the CTRL-ALT-+ and then a CTRL-ALT-"-" in order to get rid of this?

Thanks.

---

### Post by nuzzy on 2006-10-28
On your keypad.  You'd hit those key combos.  It's just making it big and then bringing it back to size again, hence the minus and plus combo.

---

### Post by tedrogers on 2006-10-28
When I do this key combination nothing happens? Is this an Edgy thing?

However, if I do CTRL + ALT + F1, then my screen corrupts and the system hangs...I wonder what the X problem is? I have fglrx installed and working fine. I have tried different resolutions and refresh rates, but the same thing every time.

In Dapper, CTRL + ALT + F1 used to take me to the command line outside of X.

I don't understand this...although I expect that if I go back to using Mesa drivers then the problem would go away. Not sure though.

-----------------------------------------------------------------

Just a moment ago I found this:

[http://ubuntuforums.org/showthread.php?t=93715&highlight=CTRL+ALT+F1+crashes](http://ubuntuforums.org/showthread.php?t=93715&highlight=CTRL+ALT+F1+crashes)

I'm hoping that this will work when I try this later (after my dinner)!

Fingers crossed.

------------------------------------------------------------------

Sucess!! If you follow the above link and do what is suggested it works a treat for me. I now have a lovely non-fuzzy ubuntu logo, my CTRL+ALT+F1 works properly. Yay....I'm so pleased.

Now....I also had a lot of problems getting back to this forum today...remember everyone....its [www.ubuntuforums.org](www.ubuntuforums.org) and not [www.ubuntuforum.org](www.ubuntuforum.org).

Sometimes it won't always redirect from [www.ubuntuforum.org](www.ubuntuforum.org) to [www.ubuntuforums.org](www.ubuntuforums.org) (like today it seems to not be working), so if you get it wrong you can't log-in! Tsskkk....took me ages to figure that one out as well.

Anwyay...joy at last.

---

