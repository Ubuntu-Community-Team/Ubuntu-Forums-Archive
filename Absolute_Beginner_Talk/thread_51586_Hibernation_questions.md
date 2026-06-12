---
title: "Hibernation questions"
date: 2005-07-24
forum: Absolute Beginner Talk
---

### Post by Nanaki on 2005-07-24
Alright, I'm still not working with Ubuntu, but I'm taking it one step at a time. :) One of the best features of Windows XP is the hibernation (not that it works properly, it hangs half of the times used).

It saves all contents of the RAM to the HDD and then **shuts down** the computer. When I then select my "Windows" entry from GRUB, Windows XP is resumed in less than 3 seconds.

Ubuntu does it differently, it doesn't really hibernate at all. It just does "something" (like launch a screensaver, and then ask for username/password to go back - eh?). Is there a way to make it behave like Windows? Actually shutting down the computer?

Also, is there a way to configure my power-button? I would like to push it once to hibernate (in the above described way) and hold it to shutdown. Last, when I close my laptop, I don't want any action to be taken (next to my screen going off that is).

Sorry for the long post, hope anyone can help me.

tnx,

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Nanaki]Alright, I'm still not working with Ubuntu, but I'm taking it one step at a time. :) One of the best features of Windows XP is the hibernation (not that it works properly, it hangs half of the times used).

It saves all contents of the RAM to the HDD and then **shuts down** the computer. When I then select my "Windows" entry from GRUB, Windows XP is resumed in less than 3 seconds.

Ubuntu does it differently, it doesn't really hibernate at all. It just does "something" (like launch a screensaver, and then ask for username/password to go back - eh?). Is there a way to make it behave like Windows? Actually shutting down the computer?

Also, is there a way to configure my power-button? I would like to push it once to hibernate (in the above described way) and hold it to shutdown. Last, when I close my laptop, I don't want any action to be taken (next to my screen going off that is).

Sorry for the long post, hope anyone can help me.

tnx,[/QUOTE]

there are three things that are really hit and miss in Ubuntu: webcams, wireless cards and suspend functions.

Do this:

[https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29](https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29)

If it doesn't work...Ubuntu doesn't support suspend on your system. Sorry if thats the case. Of my two laptops (both Toshibas) one works even better than Windows and one doesn't work at all.

---

### Post by Nanaki on 2005-07-25
[QUOTE=poofyhairguy]there are three things that are really hit and miss in Ubuntu: webcams, wireless cards and suspend functions.

Do this:

[https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29](https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29)

If it doesn't work...Ubuntu doesn't support suspend on your system. Sorry if thats the case. Of my two laptops (both Toshibas) one works even better than Windows and one doesn't work at all.[/QUOTE]
 Thanks for the help,

Don't forget sound, I got it, but it sounds like crap. :) I'll fix that another time tho. ^^

I've followed the wiki-page-instructions, but they didn't work. :( I still keep getting some log-in screen after I use the hibernate-script. So is there any explanation of how to get Suspend2 to work? It seems promising.

---

### Post by poofyhairguy on 2005-07-25
[QUOTE=Nanaki]Thanks for the help,

Don't forget sound, I got it, but it sounds like crap. :) I'll fix that another time tho. ^^

I've followed the wiki-page-instructions, but they didn't work. :( I still keep getting some log-in screen after I use the hibernate-script. So is there any explanation of how to get Suspend2 to work? It seems promising.[/QUOTE]

Breezy (the October release) is really focusing on suspend support. I know patience is a virtue, and I hope you have some to spare.

---

### Post by Nanaki on 2005-07-25
[QUOTE=poofyhairguy]Breezy (the October release) is really focusing on suspend support. I know patience is a virtue, and I hope you have some to spare.[/QUOTE]
 Good to hear, I didn't know if there would be Suspend-improvements in Breezy. It's good to hear that's yet another feature I'm currently missing that will be improved/added. Breezy will rock. :)

---

