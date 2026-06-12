---
title: "ati radeon 7000 problems -- i tried everything i kno!! i need to know more"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-08-09
hello all

i recently installed feisty on my bro's computer. it is an old computer. 650 mhz, p3, 256 ram. the problem seems to be with the radeon 7000 64mb card. it is an agp card and it is one i got a long time ago. its made by Sapphire (powered by ati).

the problem is that the video works but then after some short while the screen turns off displaying 'no signal'. i know the pc is still running and working fine. it responds to my commands such as ctrl + alt + Backspace and Ctrl+atl+F4 ( i have been making use of these commands constantly). everytime this happens i have to restart the xserver. i get back to the login screen and log in and then everything is working fine and then monitor goes off. and rinse and REPEAT. very annoying.

here is what i have tried. i switched to the "radeon" driver and played around with the options. and it showed the same symptoms.

i switched back to the "ati" driver and i dont really know any options for it and that didnt really help the problem either. 

finally i just picked some random driver (vesa) and then the problem went away. the monitor was fine for 2 days (as in, it was running and i was using it for 48 hours (obviously with me sleeping some, lol).

then i wanted to be able to play avis and dvds (i cant do that with the vesa drivers apparently) so i switched back to the radeon and played around with it more. it was working fine for another day. and then last night it started turning off (while i was playing yahoo games and using java (if that helps anyone understand my situation any betters). however, the dvds and avis started working. glxinfo shows things are working properly and glxgears also works. (these things dont work with the vesa drivers)

i know its not the monitor because i used another one and it had the same problem (one was an ACER and the other a COMPAQ). i set the vert/horiz properties myself and i am using refresh rates and resolutions that the monitor supports.

the problem occurs randomly. it could happen a few minutes after i login or a few hours. im hopin it doesnt happen now or i will have to type all of this again. ARGH! :confused: :confused:
 

plz guide, o wise ones.

TIA

---

### Post by Majere on 2007-08-09
Interesting bug. I could be a power managment problem. Maybe you could try turning off DPMS in the xorg.conf file and see if the problem goes away

---

### Post by Miroku on 2007-08-09
what is dpms exactly? i will turn it off. but i was just wondering what this DPMS is. i saw it in xorg and i saw it in my monitor specifications.

i will report back as soon as i can.

---

### Post by Miroku on 2007-08-10
well after turning off DPMS (by commenting the "options" under the monitor section), and having the 'radeon' drivers, the result is that when X is restarted, it just gives me a black screen. the monitor is still on, there is no picture. the computer is still working and responds to my commands. i tried the 'ati' drivers while turning off DPMS, but still no luck with the same problem.

i searched around and apparently 'vesa' automatically turns off DPMS but i dont know why that doesnt give a black screen. 

any more suggestions would be very appreciated because i am running out of ideas/patience/strength ( i have been at this for 3 days nonstop) :mad:

TIA

---

### Post by Miroku on 2007-08-10
alright i am back

so things arent working that great yet. unfortunately, now when i use 'ati' or 'radeon' in xorg, the screen goes black on start. the only drivers that work are the  "vesa" drivers. and thats all. do i need to do a fresh install to get the radeon drivers to work again? argh

i am not even sure why this is behaving this way.

help me plzzzzzzzzzzzzzz

is no1 replying because no1 knows? because if that is the reason, let me know so i can stop hopin for some1 to reply. lol.


TIA

---

