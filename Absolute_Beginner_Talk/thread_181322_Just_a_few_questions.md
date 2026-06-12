---
title: "Just a few questions"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by superwurm on 2006-05-24
Hi everybody, I've installed Kubuntu yesterday and I'm very happy now. I'm finaly redeemed from the M$ terror :)
I've allready installed a few programs, but I'm looking for a few easy to install tools and I have also a configuration problem:

1. An easy-to-install spam filter for Kubuntu.

2. An easy to install program for my hauppauge TV card. In windows I used Dscaler, but I couldn't find a linux version.
I tried Mythtv, but I couldn't figure out how to install that. You need a year to read all those docs:-| 

3. I have 2 soundcards. One is an onboard-card (AC'97) and the other is a creative Live card for my 5.1 suround speakerset.
The system uses the onboard-card, but how do I configure the system to use the 5.1 surround-card?
Yesterday I clicked an hour on the mixxer but without any result:( 

If somebody has a solution I would be very happy

Greetings from the Netherlands

---

### Post by Titus A Duxass on 2006-05-24
1. Spam filter - can't help you there, I don't use one.
2. Mythtv - follow hyam's How-To and it should take you about 2 hours. But myth is a media centre type thing and not just for watching tv.
3. Disable the on-board sound in BIOS that should automatically bring up your other sound card.

---

### Post by adamkane on 2006-05-24
I wasn't satisfied with mythtv. I was able to set everything up, but the configurations weren't always persistent. This was due to poor mysql integration in my opinion, and I am someone who knows how to use mysql.

I'm going to try freevo next, when I have a chance.

---

### Post by Bukunut on 2006-05-24
Superwurm

> 1. An easy-to-install spam filter for Kubuntu. 

Well bogofilter does the job just right for me, sits in KMail like a charm and easy to set up, Kmail auto detects it's installed! The same can be said for the impressive SpamAssassin too, both are worth a look. 

Bukunut

---

### Post by richbarna on 2006-05-24
[QUOTE=superwurm]
2. An easy to install program for my hauppauge TV card. In windows I used Dscaler, but I couldn't find a linux version.
I tried Mythtv, but I couldn't figure out how to install that. You need a year to read all those docs:-| 
[/QUOTE]
Hi superwurm,
I use kdetv for my hauppauge WinTV card and it works fine.
You can get it from the repositories.
Good Luck ! :cool:

---

### Post by superwurm on 2006-05-24
Hi I tried both, and followed the instructions, but the "make" command (and also the alternative 'gmake' commands don't work

I get "bash: make: command not found"

---

### Post by superwurm on 2006-05-24
with KDETV the same thing
when I follow the instructions I get only bash & command not found messages

---

### Post by superwurm on 2006-05-24
hey, anyway, Bogofilter is installed allthough I got these command not found messages
hopefully this has also happened with Kdetv

---

### Post by richbarna on 2006-05-24
For make problems you need to get build-essential.
From the Terminal/Console do :-
> sudo apt-get update
Then :-
> sudo apt-get install build-essential
This will give you all the packages necessary to compile, build and install software.

---

