---
title: "Steam-CounterStrike Source"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-12
Hi guys. 
Before I switch to the 32bit Ubuntu version from the 64bit, I installed Steam with the game CounterStrike Source. It was successful, but once CS:S finished downloading, when I went to run the game, the screen turn black but nothing happened...
When I restarted the computer, it gave me a message saying something about my graphics, and the screen was blue all over...
Can anyone please point me to a link, or maybe show me in here, how to successfully install Steam on Ubuntu 32bit, and so that I can play the game with no problems?
Thank you soooooooo much in advance... :)

---

### Post by lamalex on 2007-04-12
are you using wine? i seem to remember wine having issues with steam. I use Crossover office with no problems, the only problem (lol) is that CXO is not free, it's $40.

---

### Post by makinasvp on 2007-04-12
> **Iamalex said:**
> are you using wine? i seem to remember wine having issues with steam. I use Crossover office with no problems, the only problem (lol) is that CXO is not free, it's $40.

So wait, with Crossover office, you are running Steam with NO PROBLEMS whatsoever?? Because if that's the case, I don't mind paying for the $40. It will be well worth it since I am in love with the game lol.
Now also, once you answer my question, can you please show me where and how I can install Crossover as well as Steam with it?
Hopefully you can help me and we can celebrate by playing on the same server some times... :)

EDIT**** When I installed Steam on the 64bit version, I was using wine.... So I guess wine WAS having problems with Steam.
Hope to hear from  you soon!!!

---

### Post by lamalex on 2007-04-12
my only problem is being pwnd by noobs in CS:S :) because only noobs play CS:S, 1.6 is for people who are truly 1337. [www.codeweavers.com](www.codeweavers.com) and they have very good instructions, they ahve a 30 day trial you can test steam with. it's SO easy to install. Much easier than WINE.

---

### Post by makinasvp on 2007-04-12
> **Iamalex said:**
> my only problem is being pwnd by noobs in CS:S :) because only noobs play CS:S, 1.6 is for people who are truly 1337. [www.codeweavers.com](www.codeweavers.com) and they have very good instructions, they ahve a 30 day trial you can test steam with. it's SO easy to install. Much easier than WINE.

Thank you SO MUCH!!! I will try that!

---

### Post by bluewagon on 2007-04-12
after looking at the site, heres my question, if they(codeweavers) support wine, by the looks of it they support it a lot, wouldn't wine be just the same as crossover?

---

### Post by lamalex on 2007-04-12
same concept, different code. CXO has worked better for me, idk why. but it has.

---

### Post by makinasvp on 2007-04-13
> **Iamalex said:**
> same concept, different code. CXO has worked better for me, idk why. but it has.

Hey when I tried installing Crossover, look what I get:

[IMG]http://i34.photobucket.com/albums/d123/siasalami/Screenshot1.png[/IMG]

Can you help me? What am I doing wrong?

---

### Post by makinasvp on 2007-04-13
any ideas why Im getting that error?

---

### Post by makinasvp on 2007-04-13
ttt

---

### Post by makinasvp on 2007-04-13
bump... help please

---

### Post by Technophobia on 2007-04-13
I think you have to run it from the Terminal

something like:


$ sh install-crossover-standard-demo-6.0.1beta1.sh


it says it in the instructions

[http://www.codeweavers.com/support/docs/crossover-standard-demo/install](http://www.codeweavers.com/support/docs/crossover-standard-demo/install)

2.1.1. User mode

When installed as a single user, the CrossOver environment will be set up for one account only. Only that user will be able to install and use Windows applications.

If you are installing CrossOver on a personal computer for private use, you should use this installation mode. It is the easiest, simplest, and safest installation method.

File locations. The CrossOver application will be installed in ~/cxoffice. Windows applications and configuration files will be placed in ~/.cxoffice.

How to install. Log in as the user who will be using CrossOver and run the install script.

$ sh install-crossover-standard-demo-6.0.1beta1.sh

---

### Post by makinasvp on 2007-04-13
So all I have to do is type "$ sh install-crossover-standard-demo-6.0.1beta1.sh" into the terminal? Man I am such a noob!!! Gah...

---

### Post by darkrose on 2007-04-13
Isn't steam in the repositories? or at the very least there is definetly a linux binary for it, would save alot of faffing about with wine.

wget [http://www.cstrike-planet.com/dls/steam](http://www.cstrike-planet.com/dls/steam)

---

### Post by makinasvp on 2007-04-13
> **darkrose said:**
> Isn't steam in the repositories? or at the very least there is definetly a linux binary for it, would save alot of faffing about with wine.

wget [http://www.cstrike-planet.com/dls/steam](http://www.cstrike-planet.com/dls/steam)

Ok I ran that on my terminal. Now what do I do from there?
My last line on the terminal says:

```
100%[====================================>] 7,822,833    927.91K/s    ETA 00:00

07:50:37 (897.66 KB/s) - `steam' saved [7822833/7822833]
```

please help!!

---

### Post by lamalex on 2007-04-13
the steam in repos is for servers only. you need cross over. all you have to do is
```

chmod a+x install-crossover-standard-demo-6.0.1beta1.sh
./install-crossover-standard-demo-6.0.1beta1.sh

```
and follow the directions. CXO's website has a very straight forward install page.

---

### Post by makinasvp on 2007-04-13
> **Iamalex said:**
> the steam in repos is for servers only. you need cross over. all you have to do is
```

chmod a+x install-crossover-standard-demo-6.0.1beta1.sh
./install-crossover-standard-demo-6.0.1beta1.sh

```
and follow the directions. CXO's website has a very straight forward install page.

Oh crap, so what I did in the terminal was wrong?? How do I take it back? Is it going to affect me at all?

---

### Post by lamalex on 2007-04-13
you didn't do anything except download a file, just delete it. it's probably in your home directory look for a 7822833 byte file named steam

---

### Post by igknighted on 2007-04-13
I'd really have to recommend Cedega over CXO for games.  Cedega is designed to support as many of the latest games as possible, while CXO focuses on other products.  Plus Cedega is only $15USD (sign up for the three month min of updates... if you want longer its $5/mo.).  Cedega is about to release (maybe already has, i haven't checked in a few days) a brand new version of their engine so it will be top of the line.

---

### Post by makinasvp on 2007-04-13
This is what I get when I tried to install....

[IMG]http://i34.photobucket.com/albums/d123/siasalami/crossover.png[/IMG]


What am I doing wrong?

---

### Post by lamalex on 2007-04-13
You're not in the right directory. ```
cd Desktop/
```

---

### Post by frodon on 2007-04-13
@makinasvp, this is a more than common bug, give me the wine version you are using and the intructions you followed.
I have this bug if i enable GLSL shader from wine 0.31 but without GLSL shader `enabled no problem at all, i run CS:S smoothly with wine 0.34.

Don't forget cedega if you are looking for a commercial apps, it's made for the games.

---

### Post by lamalex on 2007-04-13
My experience with cedega and steam has been awful. 20 fps maximum, choppy, locked up.

---

### Post by makinasvp on 2007-04-13
great! Now I have no clue which one to go for lol
All I want to do is play CS:S!! lol

---

### Post by lamalex on 2007-04-13
you already started with CXO, if you don't like it, get rid of it and try another. Cedega doesn't give trials though.

---

### Post by frodon on 2007-04-13
it depends, i had 20 FPS with wine 0.22 (edgy version) but i have an average FPS of 76 with the performance test now withe wine 0.34 and all pixel bugs are gone.

@makinasvp: give details, without details i can't help you with wine.

CS:S runs perfectly with wine but you may need some tweaks to get it working that's why i need the exact instruction you followed to be able to help you.
The reference instructions are there :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by bisbebri on 2007-09-16
I would download Automatix, it will install it for you...

---

