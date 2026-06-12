---
title: "my clock runs and mp3 are speedy!"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by werto on 2005-10-02
Yo all :)
i'm new in this comunity and i'm glad to make a first post about my problems..

so, i'm a new ubuntu breezy user, and now i'm using it on a Hp Pavilion laptop with a amd athlon 64bit 3500+ and a Ati Radeon XPress 200M 128 mb video card...

I've some problems using ubuntu onto this computer..

first of all the Cpu clock runs under ubuntu! °_° so much! the time is in the future, if i set it, very soon the today clock time is time of tomorrow °_°

second problem is that when i try to play a mp3 (i installed w32codecs from marillat repository) it runs so much! Playng mp3 is so speedy! 

third problem is my video card...
if i set xorg.conf with vesa it starts (but with 1024x768 max resolution and no 3d acceleration) and if i set it with Ati, it bloks charging gnome when i try login in from gdm...

i'm in trouble :)

what should i do?

thanks for reading that message composed of very uncorrect english ^_^''

see ya'
peace and love
werto

---

### Post by tseliot on 2005-10-02
Open System monitor and check the CPU usage. If it is near 50% (when no other apps are running) then you might use my guide to solve the DOUBLE CLOCK SPEED BUG.

[http://ubuntuforums.org/showthread.php?t=53094]("http://ubuntuforums.org/showthread.php?t=53094")

EDIT: about mp3 playing: the problem is caused by the DOUBLE CLOCK SPEED BUG. Do you use an AMD64 processor, do you?

About ATI I can recommend you this guide (to install ati proprietary drivers):

[http://ubuntuforums.org/showthread.php?t=65276]("http://ubuntuforums.org/showthread.php?t=65276")

---

### Post by a8o on 2005-10-02
thanks solved my problem....now the thread starter on hte other hand...

---

### Post by tseliot on 2005-10-02
[QUOTE=a8o]thanks solved my problem....now the thread starter on hte other hand...[/QUOTE]
I'm happy for you :)

---

### Post by metalLord on 2005-10-02
[QUOTE=tseliot]Open System monitor and check the CPU usage. If it is near 50% (when no other apps are running) then you might use my guide to solve the DOUBLE CLOCK SPEED BUG.
[http://ubuntuforums.org/showthread.php?t=53094]("http://ubuntuforums.org/showthread.php?t=53094")
EDIT: about mp3 playing: the problem is caused by the DOUBLE CLOCK SPEED BUG. Do you use an AMD64 processor, do you?
About ATI I can recommend you this guide (to install ati proprietary drivers):
[http://ubuntuforums.org/showthread.php?t=65276]("http://ubuntuforums.org/showthread.php?t=65276")[/QUOTE]

i've the same problem and cpu usage is 2/3%...
mp3 are speedy with totem and vlc but not with mplayer...

---

### Post by tseliot on 2005-10-02
[QUOTE=metalLord]i've the same problem and cpu usage is 2/3%...
mp3 are speedy with totem and vlc but not with mplayer...[/QUOTE]
Try the "Ubuntu 32bit" solution in my guide (noapic) and tell me if it works for you even if you haven't this exact problem.

---

### Post by werto on 2005-10-02
[QUOTE=tseliot]Try the "Ubuntu 32bit" solution in my guide (noapic) and tell me if it works for you even if you haven't this exact problem.[/QUOTE]
like **metallord** my cpu had a small usage percentage..
so your guide it's a miracle :D
everythink works! mp3 too! 
i'm going reading ati guide
i'm happy! Thanks! ^0^
see ya'
peace and love
werto

---

### Post by metalLord on 2005-10-02
[QUOTE=werto]like **metallord** my cpu had a small usage percentage..
so your guide it's a miracle :D
everythink works! mp3 too! 
i'm going reading ati guide
i'm happy! Thanks! ^0^
see ya'
peace and love
werto[/QUOTE]

well...then I'll do...

grazie tseliot.

---

### Post by tseliot on 2005-10-02
Happy to help :)

---

### Post by werto on 2005-10-02
[QUOTE=tseliot]
About ATI I can recommend you this guide (to install ati proprietary drivers):
[http://ubuntuforums.org/showthread.php?t=65276]("http://ubuntuforums.org/showthread.php?t=65276")[/QUOTE]

unfortunately it doesn't work with my ati 200M...

i'm going to control ati site...

:)

see ya'
peace and love
werto

---

### Post by metalLord on 2005-10-02
sorry but...

after booting with noapic and nolapic my lan seems like dead.
if I ping my server (my lan= 2 PCs wired each other) result is Host Unreachable... I can't work this way...

---

### Post by tseliot on 2005-10-02
[QUOTE=metalLord]sorry but...
after booting with noapic and nolapic my lan seems like dead.
if I ping my server (my lan= 2 PCs wired each other) result is Host Unreachable... I can't work this way...[/QUOTE]
It can be a side effect so you have to set your file back to defaults (delete the 2 words you added). The method for Ubuntu 64bit is safer but it works ONLY on 64bit systems. I don't know how to help you in this case. You could upgrade the bios of your motherboard (could you tell me the name of the model?).

---

### Post by metalLord on 2005-10-02
[QUOTE=tseliot]It can be a side effect so you have to set your file back to defaults (delete the 2 words you added). The method for Ubuntu 64bit is safer but it works ONLY on 64bit systems. I don't know how to help you in this case. You could upgrade the bios of your motherboard (could you tell me the name of the model?).[/QUOTE]

i've the same laptop of werto, hp pavilion zv6181ea...i think it has an hp motherboard...i don't have a clue...

---

### Post by tseliot on 2005-10-02
Unless you want to install Ubuntu 64bit I can't help you.

---

### Post by metalLord on 2005-10-02
[QUOTE=tseliot]Unless you want to install Ubuntu 64bit I can't help you.[/QUOTE]

ok thanx a lot...!

---

### Post by werto on 2005-10-02
[QUOTE=tseliot]Unless you want to install Ubuntu 64bit I can't help you.[/QUOTE]

my lan was dead too...

ati driver doesn't start...

there's nobody who can help?

thanks so much for your help tseliot... so our amd64 system should be in trouble for time...

using ubuntu breezy amd64 i had lot of package dependencies problems...

i'm glad to continue using that sh°°ty win xp...

someone can help?

see ya'
peace and love
werto

---

### Post by werto on 2005-10-02
news:

i'm now in ubuntu breezy amd64,,,

but the times runs too!!!!!!!!!!!!!!!!!!! °___°

it's impossible!!!

---

### Post by poofyhairguy on 2005-10-02
Well....with Ubuntu being the development version, some things just don't work. Heck, even after release the 64 bit version is so new that it still might not work.

You might not like it, but the best advice is to either file a bug and hope it gets fixed or put Hoary in there.

No one that thinks their post belongs in this forum needs to mess with Breezy.

---

### Post by werto on 2005-10-03
[QUOTE=poofyhairguy]Well....with Ubuntu being the development version, some things just don't work. Heck, even after release the 64 bit version is so new that it still might not work.
You might not like it, but the best advice is to either file a bug and hope it gets fixed or put Hoary in there.
No one that thinks their post belongs in this forum needs to mess with Breezy.[/QUOTE]

i think i will not leave breezy amd64, i wish to help community doing beta tester. I'll try to found solution.... 

^_^ i wish :rolleyes: 

see ya'
peace and love
werto

---

### Post by tseliot on 2005-10-03
[QUOTE=werto]news:
i'm now in ubuntu breezy amd64,,,
but the times runs too!!!!!!!!!!!!!!!!!!! &#176;___&#176;
it's impossible!!![/QUOTE]
Have you tried my method for Ubuntu 64bit (the 1st one in my guide) (no_timer_check)?

---

### Post by werto on 2005-10-03
[QUOTE=tseliot]Have you tried my method for Ubuntu 64bit (the 1st one in my guide) (no_timer_check)?[/QUOTE]

I tried it when i had ubuntu breezy 32 bit, and unforntunately like metallord my lan was dead... so i had to leave noapic nolapic...

so now i'm in ubuntu breezy 64 bit.. so i think i should have the same problem with noapic nolapic trick..

or not? ?_?

---

### Post by tseliot on 2005-10-03
[QUOTE=werto]I tried it when i had ubuntu breezy 32 bit, and unforntunately like metallord my lan was dead... so i had to leave noapic nolapic...
so now i'm in ubuntu breezy 64 bit.. so i think i should have the same problem with noapic nolapic trick..
or not? ?_?[/QUOTE]
Please have a look at my guide again: I refer to the "no_timer_check" trick and not to the noapic one.

---

### Post by metalLord on 2005-10-03
i've installed ubuntu breezy for amd64 and i've used your guide...

now all is going well!!
thanx...you're great!!

two questions:

1) why you added the no_timer_check option on the commented line and not below?

2) you're italian...so why don't you "translate" your guides and add them to the italian site? we need you! (too much work here?) and why don't you add me on your msn/jabber/googletalk friend-list? (just kidding dah! :razz: )

---

### Post by tseliot on 2005-10-03
> **metalLord]i've installed ubuntu breezy for amd64 and i've used your guide...
now all is going well!!
thanx...you're great!!
two questions:
1) why you added the no_timer_check option on the commented line and not below?[/QUOTE]
I'm not sure to understand your question but I can answer you that's the way I do it  said:**
> 2) you're italian...so why don't you "translate" your guides and add them to the italian site? we need you! (too much work here?) I'm not a registered user in the Italian forum (BTW what's the address?). I hang around here because I study foreign languages at the university and the more I practise the better.

[QUOTE=metalLord]and why don't you add me on your msn/jabber/googletalk friend-list? (just kidding dah! :razz: )[/QUOTE]
Believe me or not I've never used jabber (I don't know what it is) (Werto had asked me this in a private message)

---

### Post by metalLord on 2005-10-03
> **tseliot]I'm not sure to understand your question but I can answer you that's the way I do it  said:**
> 

yeah...i'm not so good in english...you know...molto maccheronico.

[QUOTE=tseliot]I'm not a registered user in the Italian forum (BTW what's the address?). I hang around here because I study foreign languages at the university and the more I practise the better.

[http://www.ubuntuitalia.org]("http://www.ubuntuitalia.org")

[QUOTE=tseliot]
Believe me or not I've never used jabber (I don't know what it is) (Werto had asked me this in a private message)[/QUOTE]

ahahahah werrrrtooo...damned leech!!

however...thanks again...you're very [disponibile] ! :D

---

### Post by tseliot on 2005-10-03
You're welcome. I'll do my best to help here. I'll be kind of busy the next days (and months) as I've got to get my 1st level degree (in december) and I have to attend 2nd level degree lessons (starting from tomorrow). 

I don't know when I can register to the Italian forum, we'll see.

---

### Post by metalLord on 2005-10-03
[QUOTE=tseliot]You're welcome. I'll do my best to help here. I'll be kind of busy the next days (and months) as I've got to get my 1st level degree (in december) and I have to attend 2nd level degree lessons (starting from tomorrow). 
I don't know when I can register to the Italian forum, we'll see.[/QUOTE]

for the italian forum you don't need any registration, ubuntu international forums are "linked" each other...your nick is valid in every ubuntu forum. 
in bocca al lupo for your studies. ;) you deserve those degrees

---

### Post by tseliot on 2005-10-03
[QUOTE=metalLord]for the italian forum you don't need any registration, ubuntu international forums are "linked" each other...your nick is valid in every ubuntu forum. 
in bocca al lupo for your studies. ;) you deserve those degrees[/QUOTE]
Crepi il lupo! ;)  and thanks for appreciating my work.

---

### Post by werto on 2005-10-03
**No More Problems** about double speed clock in ubuntu breezy amd64 !!!

apt-get update
upgrade
dist-upgrade

and voila'! no more problems ^_~

to master tseliot:
(useful ot ^_^'')
bross, jabber is an open IM :) i think you can be interested in it ^_^ 
[www.jabber.org](www.jabber.org), there are sooooo muuuch clients, so i think one of the best is psi (psi.affinix.com).

thanks so much for your helps ^_^

crepi il lupo e in bocca al lupo anche a te ! anzi, all'universita' si dice "in culo alla balena!" e come risposta si dice "nuotero' nella merda!" 

^___^

see ya'
peace and love
werto

....
but... still the ati problem--- ;__; sigh

---

### Post by tseliot on 2005-10-04
[QUOTE=werto]to master tseliot:
(useful ot ^_^'')
bross, jabber is an open IM :) i think you can be interested in it ^_^ 
[www.jabber.org](www.jabber.org), there are sooooo muuuch clients, so i think one of the best is psi (psi.affinix.com).[/QUOTE]
I have installed gnome-jabber which is up and running now.

[QUOTE=werto]thanks so much for your helps ^_^
crepi il lupo e in bocca al lupo anche a te ! anzi, all'universita' si dice "in culo alla balena!" e come risposta si dice "nuotero' nella merda!"[/QUOTE]
I didn't know it. But you know most of students of Foreing languages are girls and if I said something like that thay would kick my ass (usiamo solo in bocca al lupo quindi)

[QUOTE=werto]but... still the ati problem--- ;__; sigh[/QUOTE]

I can't help you with that, mine is a Nvidia card.

---

