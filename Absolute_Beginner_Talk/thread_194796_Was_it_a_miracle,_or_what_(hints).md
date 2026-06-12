---
title: "Was it a miracle, or what? (hints)"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2006-06-11
First, off I would like to say that I am typing this from Dapper... in my basement! 

Ok, here is the story. For about a week I played around with different distros and liveCD's. Basicaly just getting used to how linux works. Alot of forum reading. 

**HINT**: Before trying something go read everything you can on the subject. This menas more than a search in these forums. 

Then for the next week I was downoading and buring iso's like mad. I couldn't get the cd's to verify. 

**HINT:** Burn slow. 8X was my iBook's slowest setting. it only had one error, Quite bootable, though.

Then I had to get my system to boot form the cd. I really had to fught with ide's and the bios. My bios only showed the item to boot if at that moment the cd was actualy in. OK, then I had to install.

**HINT: **A fast cd drive is more important that alot of ram for installation.

I only have 64mb of ram and so i used the alt cd. For some reason it diddn't install x. That means only command line. I tried this install twice. 

I tried to boot the desktop cd, but it took 20 minutes to get past the screen that you choose to boot. Of course i had a **4X** cd drive.

I switched it with my 54x and it only took 5 minutes! I was albe to finaly pull off the install after one and a half hours. It was worth it becasue now i could boot into ubuntu. 

Then I had to get ndiswrapper working. Turns out i didn't even have MAKE installed.. It was really a pain in the neck to figure that out.

**HINT:** Go to the IRC chat if you need help. It REALLY helps because you can talk quickly. Opera is an IRC client, btw. 

Someone told me to use synaptic to download ndiswrapper. I had no internet, but I had to put the cd in. (don't use that goofy add programs button in the apps menu for this) 

After the dl I was just about to start ndiswrapper from the command line. Then i was going to give it the exe drivers. But I typed "lspci" and it did not see the card at all. Then the power went out in the house. Arg!

**HINT:** Don't forget to restart after downloading ndiswrapper. I almost forgot to, but the lightning reminded me ;)

When I restarted, I went into "networking" and truned on the card. then I gave it the right network name and all that. Just for the hell of it i sarted Firefox. This was a leap of guess becauise it takes like 30 seconds to open firefox and at the moment i was cramped for time. To my suprise, it worked!

If you were wonedring here is my setup:

Compaq Deskpro box
Intel Mobo
Pentium II 500Mhz
64mb RAM
6 Gb HD
Ubuntu desktop Dapper
linksys WUSB54Gv4
ATI rage video card
54x CD drive

Feel free to ask any questions about how i installed my wireless (more specific than i mentioned) 

All i needed was the desktop CD and the USB card. nothing else!

**NOTE** Don't tear me apart. This is my first post like this. If you have a suggestion, I will gladly fix whatever needs fixin'

---

