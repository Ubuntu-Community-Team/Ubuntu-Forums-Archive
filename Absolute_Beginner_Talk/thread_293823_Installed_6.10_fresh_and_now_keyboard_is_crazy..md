---
title: "Installed 6.10 fresh and now keyboard is crazy."
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Flaystus on 2006-11-05
Its a pretty basic MS keyboard on a KVM switch. I had it dual booting with XP and the previous Ubuntu and today blew away the ubuntu partitions and installed fresh.

When I type its like the keys stuck so that I'll get "suddddddddddddo" when I try to type sudo. Happens with any key at random. 

Still works fine in Windows. Any ideas?

---

### Post by bmathis on 2006-11-05
i have almost the same issue, but its on my Acer laptop. Its not the keys sticking but it seems like there is a lag time between key strokes which causes it for me... no idea why though.

---

### Post by Flaystus on 2006-11-05
> **bmathis said:**
> i have almost the same issue, but its on my Acer laptop. Its not the keys sticking but it seems like there is a lag time between key strokes which causes it for me... no idea why though.

EXACTLY what I'm having.

Also it did this on the Live CD also.

---

### Post by wyohermit on 2006-11-05
You might try system -> preferences -> keyboard

Ken

---

### Post by Flaystus on 2006-11-05
> **wyohermit said:**
> You might try system -> preferences -> keyboard

Ken

and what exactly? I can change the settings but that does not fix this problem.

---

### Post by Flaystus on 2006-11-05
So I went into Ubuntu again and this time neither the keyboard or the mouse worked. Both are USB and neither had any lights on. Upon reboot the mouse works and the keyboard had the same problem as before.

Once again, everything is fine inside Windows.

---

### Post by Flaystus on 2006-11-05
Fixed.


I had to UN overclock my PC. When its over clocked (Pent 805D)it acts all crazy. Which is odd because every other OS including the previous Ubuntu was just fine.

---

### Post by bmathis on 2006-11-05
> **Flaystus said:**
> Fixed.


I had to UN overclock my PC. When its over clocked (Pent 805D)it acts all crazy. Which is odd because every other OS including the previous Ubuntu was just fine.

Hmm... i guess my situation is different because I dont overclock my laptop, my problem is random but it doesnt bother me that much thats why I never posted until I seen yours... well congrats on the fix! =D>

---

### Post by Flaystus on 2006-11-05
> **bmathis said:**
> Hmm... i guess my situation is different because I dont overclock my laptop, my problem is random but it doesnt bother me that much thats why I never posted until I seen yours... well congrats on the fix! =D>

Actually. Turns out I spoke to soon. Upon the next reboot the same old problem was back.

So its random, sometimes no keyboard or mouse, some times mouse with messed up keyboard, some times neither, and every million boots it all randomly works perfectly.

I even removed my KVM and that had no effect either. Maybe I should give in and go back to PS/2 sheesh.

---

### Post by ljpm on 2006-11-17
Same problem here guys.

What is really strange is this is the second time I installed Edgy anddddddddd it didn't happen the first time (although I didn't run it for long on the first install).


Note: the above repeated letter was spontaneous.

---

### Post by talbain on 2006-12-05
I ammmmmmmm alssssso haaaaaavinggggg thhhisssssss probleeeeeeem, someeeeeeeeeeone pleasssssssssse heeeeeeeeelpppppppppp.
I cant even log into my other computer, there must be a fix for this, it's sooooooooooooo annoying!

thanks in advance.

---

### Post by talbain on 2006-12-08
Okay, how i solved my problem:

The computer i installed edgy on was so old that i even forgot it has no acpi support in its chipset.

(Im using a USB mouse and a PS/2 keyboard)

So what i did was:

Let the machine boot and show the login screen, since i couldnt login, i pressed "Ctrl+Alt+F1" to show the console and log in.

Then:
```
sudo nano /boot/grub/menu.lst
```

and added the text in red to this line:

```
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda1 ro quiet splash [COLOR="Red"]acpi=off noacpi[/COLOR]
```

things were still kinda crazy so i went into the BIOS and changed an option (that you might or might not have) that says "USB Legacy Mode" from "Enabled" to "Disabled" and everything went smooth as silk...

But just to be ultra super sure i decided to reinstall edgy, let the cd boot (i used the alternative disk, not the live one) and press "F6" then add "acpi=off noacpi" to the end of the line so this option gets preinstalled.

I noticed that if my BIOS has "USB Legacy Mode" set to "Enable" the comp would instantly restart after pressing "Enter", so i had to disble that first and then again the installation went smoothly.

Kudos to [bsherman]("http://www.ubuntuforums.org/member.php?u=1327") for [this]("http://www.ubuntuforums.org/showpost.php?p=9953&postcount=3") post on diabling ACPI, thread [here]("http://www.ubuntuforums.org/showthread.php?t=2620&highlight=acpi").

Later on i also added the apm module as indicated in his post.

Hope this helps anyone.
Good luck.

---

