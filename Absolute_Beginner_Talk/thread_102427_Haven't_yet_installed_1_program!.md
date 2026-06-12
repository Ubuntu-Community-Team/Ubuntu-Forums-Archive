---
title: "Haven't yet installed 1 program!"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by kane_666 on 2005-12-12
hey this is my first post, i've been reading heaps of posts here in the beggeniner forum trying to build my knoweldge before posting but i haven't yet been able to install evan 1 program. I've tried heaps... java.deb, dguitar.zip (which is why i needed java) gnome-bluetooth.tar etc... and i have had no luck with installing them. every time i try i got errors. Any ideas?

---

### Post by matthewv on 2005-12-12
Use synaptic, or add applications to install most programs. You'll need to give further details for help on specific programs, not in the repositories. Enable the extra repositories, too. See here: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by aysiu on 2005-12-12
gnome-bluetooth is easy.
Follow the instructions in the first link of my sig.
Then open up a terminal and type ```
sudo apt-get update
sudo apt-get install gnome-bluetooth
```

---

### Post by kane_666 on 2005-12-12
but to update repositories, you need to be connected to the internet right? i cant coz the computer with ubuntu hasn't got a connection...

---

### Post by matthewv on 2005-12-12
OH...

Most software in linux comes straight off the internet. that's not to say it can't be physically distributed, its just that physical media is expensive and for most people its easier to just use the net. You can always go to packages.ubuntu.com and download software packages, and then install using ```
sudo dpkg -i <filename.deb>
``` but that way you need to resolve dependancies and such. Notwithstanding my tales of woe, try it and see how well it works. It might work fine, it might not.

---

### Post by kane_666 on 2005-12-12
i tried installing audacity.deb that way and it didn't work. i guess it was because of dependancie issues? well if thats the case, what sort if files would i be able to install without an internet connection? is it only .bin & .tar ? becuase im having trouble installing them aswell. i thought it might of been becuase i didn't have some needed files, so i went to the programs website downloaded the needed files but when i tried to install them i got errors also. it seems learning to install files on linux is going to be a hard thing to learn...

---

### Post by 23meg on 2005-12-12
[QUOTE=kane_666]it seems learning to install files on linux is going to be a hard thing to learn...[/QUOTE]
Not at all. Pretty much all you need to know is [here]("http://www.psychocats.net/linux/installingsoftware.php").

---

### Post by kane_666 on 2005-12-12
yeh i've read that but im still having trouble installing files. can annyone recomend a small program that i could try and install? maybe something that doesn't require any other files?

---

### Post by aysiu on 2005-12-12
[QUOTE=kane_666]i cant coz the computer with ubuntu hasn't got a connection...[/QUOTE] Hasn't got one...? Or you haven't gotten it to work yet?

---

### Post by kane_666 on 2005-12-12
it hasn't got a connection.. there is no phone line plugged in. which brings up another topic :) IF i get the bluetooth working lol can i use my t630 as a modem to connect to the internet? if i do this how does it work, do i still need a phone line or does my computer connect to my mobiles modem and then the mobile dials? becuase the only reason the computer doesn't have an internet connection is because i cant get a phone line in my room and i haven't got around to setting up a network (routers to expensive)

---

### Post by kane_666 on 2005-12-12
i was just looking at writing programs for my psp and i didn't know whether or not ubuntu comes with a c compiler? if not can someone give me a link to download one. hopefully one that will be really easy for me to install :)

---

### Post by hesee on 2005-12-12
[QUOTE=kane_666]i was just looking at writing programs for my psp and i didn't know whether or not ubuntu comes with a c compiler? if not can someone give me a link to download one. hopefully one that will be really easy for me to install :)[/QUOTE]


For a c compiler, you should install build-essentials package, command is ```
sudo apt-get install build-essential
```
But cause you don't have access to the net, need to download from elsewhere and install offline, like matthewv said before.

---

### Post by kane_666 on 2005-12-12
i downloaded the audacity.tar and went to install it but i got an error when running ./configure ...the error was: i needed some xvwindows file (does that sound right?) after google'ing i cant find the file. does annyone know where i can find it? also if annyone here uses DGuitar i need help running that, which it has me stumped becuase you need java 1.4.x to run it and i have java 1.4.2 :S so help with that would be great. i have a lot more programs i need to install so once i got those 2 done i should be able to get the hang on ubuntu. Thanks :D

---

### Post by hesee on 2005-12-12
[QUOTE=kane_666]i downloaded the audacity.tar and went to install it but i got an error when running ./configure ...the error was: i needed some xvwindows file (does that sound right?) after google'ing i cant find the file. does annyone know where i can find it? also if annyone here uses DGuitar i need help running that, which it has me stumped becuase you need java 1.4.x to run it and i have java 1.4.2 :S so help with that would be great. i have a lot more programs i need to install so once i got those 2 done i should be able to get the hang on ubuntu. Thanks :D[/QUOTE]

If some prog needs java 1.4.x, 1.4.2 should be  ok, as well as 1.4.1, 1.4.3, 1.4.4 and everything starting with 1.4. 

For audacity install, why don't you do like adviced here:
[http://makuchaku.info/amnesty/#audacity](http://makuchaku.info/amnesty/#audacity)

In general, if program is in repositories, it's easiest to install it from there. Just like adviced in that guide(or via Synaptic)...

[edit] Ah, I forgot your no-network situation.

---

### Post by kane_666 on 2005-12-13
about the java, i know it should work... thats why im confused. when i try to run the program (dguitar) that uses java i get errors refering to java. so thats what i dont get :S and the audacity, i cant add extra repositories because its not connected to the internet. i've downloaded audacity.tar but i think i need to download some 'needed files' because it says its missing xvwindows? does that sound right...?

EDIT: i was just looking at packages.ubuntu.com and ive downloaded the wxwindows library, about to install it, ill see how it go's. but i was going to download quake [http://packages.ubuntu.com/breezy/games/quake2](http://packages.ubuntu.com/breezy/games/quake2) but i wanted to know if i should download all those files or does ubuntu come pre-installed with some/most of them? thanks

---

### Post by sonny on 2005-12-13
Well... I have a co-worker that had the same problem, an Ubuntu (in his house) box with no internet, he told me he wasn't able to do much, so I told him to download the software from the ubuntu's ftp, copy them to a cd and then installing it in the ubuntu box, the next day he told me about his depencie problems, I told him it was because some lib or programs are not installed and he needed them, so he had to download it. He was smarter than I, cuz I would have only downloaded the files needed, he left the office pc on for a couple of days, it turn out he downloaded the WHOLE repos and burn them into several dvd's that way he solve the depencie problems... hehehehehehehe... perhaps you don't have to be that drastic, but you can track all the dependecies of a file and then download all the necessary packages, burn them and install them from the cd or dvd.

---

### Post by kane_666 on 2005-12-14
i was going to do that but when i got a list of needed files (packages.ubuntu.com) those needed files, has needed files, and so on. lol its a never ending cycle. would your office friend know how to put all those lib files in a .zip or .tar with an install file so i can just run it and it saves me doing it :)

---

### Post by dgrafix on 2005-12-14
Why dont you share your connection from your pc. Im sure ive done this with a modem before, and use a crossover between PCs ethernet ports. Windows has a reasonable help on this.

Or better yet, bin the modem, get broadband/dsl with a cheap 4 port router.
Bband is only about 20 quid a month(in sweden anyway i think its even less now in uk)
I just bought a cheap dlink 4 port ethernet router with firewall built in for 600 Sek (about £45)
Now all my machines are internet happy and nice and fast.

---

### Post by kane_666 on 2005-12-14
at the moment, i will just take my box to my phone line and connect, but i dont know how... i've made another topic for more info. [http://www.ubuntuforums.org/showthread.php?t=103386](http://www.ubuntuforums.org/showthread.php?t=103386)

---

