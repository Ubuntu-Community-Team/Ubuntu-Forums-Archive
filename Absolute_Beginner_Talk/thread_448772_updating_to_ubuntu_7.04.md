---
title: "updating to ubuntu 7.04"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-05-19
guys.. iused to edgy for a month then i switched back to xp but i didnt like it so now im back to edgy... but i need a little help.. i cant upgrade to ubuntu 7.04.. it says authentication failed.. what should i do ? thanks

---

### Post by GrueTamer on 2007-05-19
How exactly are you going about upgrading?

---

### Post by HunkieChan on 2007-05-19
> **GrueTamer said:**
> How exactly are you going about upgrading?

um.. ok i got the update snippets.. and it asked me whether i wana upgrade to feisty fawn or not.. i click upgrade and it loaded after it was done it said authentication failed

---

### Post by AlexenderReez on 2007-05-19
easiest way is...type in terminal...line by line.....


> sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
sudo apt-get upgrade 

---

### Post by HunkieChan on 2007-05-19
> **reez0105 said:**
> easiest way is...type in terminal...line by line.....

thanks bro

---

### Post by Kobalt on 2007-05-19
You might want to check out this as well : [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Cozza on 2007-07-16
Hi

I've got Ubuntu 5. something (I forget the version number) from my lecturer at University. I installed it last night but I was told Ubuntu 7.04 was more up-to-date. I plan to update it then sort out my wireless network on it, is there a way to go about it? I'm on my parent's PC that runs Windows XP Home with Internet so I'm thinking of getting the Ubuntu CD icon thing and installing it on my laptop. How could I do this? I tried the Terminal coding but its asking for internet connections. 

Any help would be appriciated thanks.

Cara xx

---

### Post by Cozza on 2007-07-16
Hi

Where can I get the Ubuntu from?

Cara xx

---

### Post by meborc on 2007-07-16
> **Cozza said:**
> Hi

Where can I get the Ubuntu from?

Cara xx

[www.ubuntu.com](www.ubuntu.com) - the lick to download is the big green one ;)

---

### Post by Cozza on 2007-07-16
Hi

Thanks for that, how do I put it on the cd?

If I put it in to the laptop can I install it how I did with my previous version of Ubuntu?

Thanks

Cara xx

---

### Post by overdrank on 2007-07-16
> **Cozza said:**
> Hi

Thanks for that, how do I put it on the cd?

If I put it in to the laptop can I install it how I did with my previous version of Ubuntu?

Thanks

Cara xx

Hi this link has some really helpful information.
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)
Good luck!:popcorn:

---

### Post by meborc on 2007-07-16
> **Cozza said:**
> Hi

Thanks for that, how do I put it on the cd?

If I put it in to the laptop can I install it how I did with my previous version of Ubuntu?

Thanks

Cara xx


ok.. lets go through this:
1) download the ISO file
2) read this [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and burn the ISO
3) change the BIOS settings to boot from CD and reboot

if you already have ubuntu installed:
1) open /etc/apt/sources.list and change all breezy (hoary) to feisty
2) sudo apt-get update
3) sudo apt-get dist-upgrade

---

### Post by AlexenderReez on 2007-07-16
> **meborc said:**
> ok.. lets go through this:
1) download the ISO file
2) read this [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and burn the ISO
3) change the BIOS settings to boot from CD and reboot

if you already have ubuntu installed:
1) open /etc/apt/sources.list and change all **breezy (hoary) to feisty**
2) sudo apt-get update
3) sudo apt-get dist-upgrade

hm...dude...if you refer to upgrade notes,only edgy is allowed to upgrade to feisty.....so if anybody is having breezy,he/she need to upgrade to dapper then edgy then feisty...maybe for people who having few softwares it won't make any difference..but most of average system will get crash .....

---

### Post by meborc on 2007-07-16
> **reez0105 said:**
> hm...dude...if you refer to upgrade notes,only edgy is allowed to upgrade to feisty.....so if anybody is having breezy,he/she need to upgrade to dapper then edgy then feisty...maybe for people who having few softwares it won't make any difference..but most of average system will get crash .....

hmm... i upgraded my breezy lappy to feisty with no problems... and it wasn't a clean breezy install :)

of course you are right... there have even been (minor) problems in upgrading from edgy to feisty not to speak of from breezy... you will never be sure...

that is why i listed the cd option... if something fails, download-burn-boot 

i expect that all data has been backed up :D

---

### Post by Jerubaal on 2007-07-16
Last year I installed 6.06 LTS in the hope of migrating from XP. However, I have hardly done anything since, due to baby arriving.  Now that I get the odd evening to myself, I would like to start over again with Ubuntu.
Q1: As I am near enough a newbie, should I stick with the Long Term Support version until I am confident enough with it, or just replace the whole installation with a fresh copy of 7.04?
Q2: It's been so long, I have forgotten my password.  Is there anything I can do about this, or is this a prime opportunity to reformat & put on 7.04?

---

### Post by HunkieChan on 2007-07-16
i think you should open a new thread for your question, thanks

---

