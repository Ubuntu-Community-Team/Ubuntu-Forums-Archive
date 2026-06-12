---
title: "huge bios problem need fast help"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by lolzlolz on 2008-01-26
ok so, this is randomly popping up,
when i restart sometimes grub won't load, not as in error won't load
it won't even show the message grub 1.5 loading
so this randomly started while i hadn't done anything new, if grub doesnt load i can't boot into either os, but it seems this is with the bios as it won't even show grub loading, 
the fix is terrible:
if i turn off my comp and unplug it (turning off won't do it) i must wait 30min to 1hr and plug back in turn back on and it will usually work, sometimes it won't but this is the only way to fix it, what should i do, i am currently afraid to turn off my comp or restart because i won't be able to get back in,
there is no error when it doesn't show grub loading
it seems the reason this works is I'm reseting the cmos or something, or could it be my cpu overheating? which wouldn't make any sense because i had overclocked with no problems, then decided to lower it again so i lowered it and didn't have problems until a week later, any ideas, thanks :)

---

### Post by doorknob60 on 2008-01-26
Maybe it's somehow related to the honking lol :P Seriously though...

---

### Post by wolfen69 on 2008-01-26
it could be a combination of things, obviously. reset/update the bios. check memory/operating temps. it's easier to diagnose a problem when you're there.

---

### Post by spiderbatdad on 2008-01-26
```
sudo dmidecode -s bios-version
``` will show you the current bios. You can compare it with the vendors recommended version. If you have to flash the bios, it will probably be muchly much much more easier in windows with a .exe from the vendor. If it is done improperly, your motherboard will make a nice wall hanging. Don't think you're resetting the cmos by powering down for a short while. You would probably have to remove the internal cmos battery.

---

### Post by lolzlolz on 2008-01-26
6.00 PG
 is my bios version, so i will check their site
[http://www.evga.com/support/drivers/default.asp?switch=2]("http://www.evga.com/support/drivers/default.asp?switch=2")
that is there page is that wat u mean, i can switch to windows although the bios may have problems again -.-
reset the bios from the bios such as reverting to default?

---

### Post by doorknob60 on 2008-01-26
If you know the exact motherboard model you could try that. And useing Google can be helpful too :D

---

### Post by lolzlolz on 2008-01-26
wat u mean???
the name on the manual lol is:
122-CK-NF68

---

### Post by spiderbatdad on 2008-01-26
you may know this, but...the bios is not stored on your harddisk. It is burned into the chipset on your motherboard. Generally done by creating a floppy disk and inserting it, then booting from it. Some bios allow a cd to act as a floppy by creating a fake drive simulation. Read as much documentation from your vendor's site as you can, and follow the instructions carefully.

---

### Post by lolzlolz on 2008-01-26
it doesnt look like it has anything on this and how to reset it, should i just change to default?

---

### Post by spiderbatdad on 2008-01-26
[http://www.evga.com/support/knowledgebase/](http://www.evga.com/support/knowledgebase/)

---

### Post by spiderbatdad on 2008-01-26
setting to default might work, but if the version is outdated compared to driver updates...IDK. that link didnt work, but search the database for flash bios.

---

### Post by spiderbatdad on 2008-01-26
They claim their bios is very stable and should not need updating. There are some links to heat problems in that knowledge base.

---

### Post by doorknob60 on 2008-01-26
Make sure your CPU fan is wokring properly...someone said that might be the cause of your computer's honking and it could be your solution.

---

### Post by lolzlolz on 2008-01-26
ok, maybe i should open the side of the case or get a bigger fan, i will try to boot up once i have let the computer cool, thank you :)

---

### Post by doorknob60 on 2008-01-26
Or simply make sure the fan you have now is working correctly, or go in to the BIOS and monitor the CPU temperature and see if it ever gets too high.

---

### Post by bwtranch on 2008-01-26
Okay, everybody is trying to over-impress everybody else with their so-called understanding of CMOS chips. Get to the real problem which is a software problem in my humble opinion. Post some output.

---

### Post by lolzlolz on 2008-01-26
ok i left the case open overnight with the powersupply off came back and booted up and it worked fine, this appears to indicate heat, thus i have to cool my system, but which component is too hot, is there anyway to find out which component is running too hot and why, 
I've never had this problem before and it started about 3 days ago, i had undid my overclock about 2 weeks ago, and haven't done anything new lately, if the component is running hot wiith no reason you guys can think of I'll have to get a new fan, currently I'm using the stock cooler on my cpu, but i could get a much better cooler, so what should i do?

---

### Post by lolzlolz on 2008-01-26
just saw that post, i dont think it is software but it might be i have no idea cuz ive never had problems, so it would seem after my last test it is my cpu or something and could very well be related to the honking :( meaning new fan but i could be a hd or something else

---

### Post by lolzlolz on 2008-01-26
bump

---

### Post by Paulmd on 2008-01-26
> **lolzlolz said:**
> ok so, this is randomly popping up,
when i restart sometimes grub won't load, not as in error won't load
it won't even show the message grub 1.5 loading
so this randomly started while i hadn't done anything new, if grub doesnt load i can't boot into either os, but it seems this is with the bios as it won't even show grub loading, 
the fix is terrible:
if i turn off my comp and unplug it (turning off won't do it) i must wait 30min to 1hr and plug back in turn back on and it will usually work, sometimes it won't but this is the only way to fix it, what should i do, i am currently afraid to turn off my comp or restart because i won't be able to get back in,
there is no error when it doesn't show grub loading
it seems the reason this works is I'm reseting the cmos or something, or could it be my cpu overheating? which wouldn't make any sense because i had overclocked with no problems, then decided to lower it again so i lowered it and didn't have problems until a week later, any ideas, thanks :)

Well, you've got to open up the machine.

I think the problem's not the bios.

My 2 chief suspects are a failing motherboard, or a failing power supply. If you had a problem with your bios, it would have surfaced earlier.

Check for bad capacitors. They look like little soda cans. If any are bulging or leaking, even a little bit, they're bad.

As for the power supply, it wouldn't hurt to replace it anyway.

---

### Post by lolzlolz on 2008-01-26
lol expensive though :(
i can try but after i let it cool it boots fine, later i will check temps in bios 
thanks

---

### Post by Paulmd on 2008-01-26
> **lolzlolz said:**
> lol expensive though :(
i can try but after i let it cool it boots fine, later i will check temps in bios 
thanks

A good power supply will set you back maybe $50.

---

### Post by lolzlolz on 2008-01-26
my powersupply was like $250 and its not a higly specialized, although i think it's still under warranty at less than a year later anyways
ok haha, i went into bios set every fan to 100% can boot with case open cpu temps were normal for stock cooler 38 celcius but stuck all fans on 100% i hve found that sometimes it take 30seconds on a part where it says looking for ide drives when it takes about 30seconds grub won't load (i dont have any ide drives)
when the message dissappears after 3 or 4 seconds grub loads fine so it would appear it is related to this although  with the side of my case open right now its fine, so first time in a while ive been able to shut  down and get back in without waiting 30minutes first i opened case and adjusted some things and checked mobo so it was about 10minutes later when i turned on again so then it worked :guitar:
but it would seem this won't be consistent i am taking the cpu fan off later and checking the contact/cooling liquid, if there isn't good contact i will reapply thermal cooling liquid, i will keep u updated :)
hopefully i will be able to get it to boot consistently soon, and be able to put the side of the case back on, the side has a fan and air slits, so thanks

---

### Post by Paulmd on 2008-01-27
> **lolzlolz said:**
> my powersupply was like $250 and its not a higly specialized, although i think it's still under warranty at less than a year later anyways
ok haha, i went into bios set every fan to 100% can boot with case open cpu temps were normal for stock cooler 38 celcius but stuck all fans on 100% i hve found that sometimes it take 30seconds on a part where it says looking for ide drives when it takes about 30seconds grub won't load (i dont have any ide drives)
when the message dissappears after 3 or 4 seconds grub loads fine so it would appear it is related to this although  with the side of my case open right now its fine, so first time in a while ive been able to shut  down and get back in without waiting 30minutes first i opened case and adjusted some things and checked mobo so it was about 10minutes later when i turned on again so then it worked :guitar:
but it would seem this won't be consistent i am taking the cpu fan off later and checking the contact/cooling liquid, if there isn't good contact i will reapply thermal cooling liquid, i will keep u updated :)
hopefully i will be able to get it to boot consistently soon, and be able to put the side of the case back on, the side has a fan and air slits, so thanks

$250 is way too much.

On the bottom end, you can get a psu for $15. I'd buy one of these only to fix a p3 with, or something not worth putting dough into.

[http://www.google.com/products?hl=en&q=psu&scoring=r&show=li&price1=&price2=40.00&lnk=prsugg](http://www.google.com/products?hl=en&q=psu&scoring=r&show=li&price1=&price2=40.00&lnk=prsugg)

You can, for around $60 get a case that uncludes a psu, or a good-quality psu.


In the $100 price range, you run in to things like hot-swap power supplies for servers, and other specialty products. That and rip-offs.

[http://www.google.com/products?hl=en&q=psu&scoring=r&show=li&price1=90.00&price2=100.00&lnk=prsugg](http://www.google.com/products?hl=en&q=psu&scoring=r&show=li&price1=90.00&price2=100.00&lnk=prsugg)

At $250, it had better be a high-quality, high effiency, high wattage unit with a good warranty. For example, $250 might be justifiable for this one. (Now, do you have a system that NEEDS such a beast?)

[http://www.advivainc.com/store/index.php?main_page=product_info&products_id=483553](http://www.advivainc.com/store/index.php?main_page=product_info&products_id=483553)



What's the make and model of your current PSU?

---

### Post by lolzlolz on 2008-01-27
its a 700watt oxs xtreme gamer powesupply i will get the exact details when i find the box :lolflag:
it has a lighted blue fan on the bottom of it,
i think i fixed the problem mabe not permenantly but i set all fans to 100% in the bios, thus cooling everything, i havent had problems since, also it was suggested to me that there is a setting that can be changed with a mobo monitor in windows that makes ur cpu change the temp ur cpu wont let u boot at and kicks u out at etc, i didnt find this option in nvidia ntune when i was in windows :( any ideas?
i ofund the powersupply is under warranty, so if the problem is the powersupply i can get it replaced, but i dont want to if it isnt the powersupply so i need u to tell me a way to be sure its the ps

---

### Post by lolzlolz on 2008-02-08
any utilities for windows or ubuntu that can detect what is happening and why it sin't working because it still randomly does it but not as often

---

