---
title: "ATI Drivers in Kubnto(rage &amp; mach?)"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-18
Well,been using Ubunto for a while now and it all works great.All just worked out the box.Most of the stuff is onboard so that might be why.Even the glxgears flys round and "direct rendering" says "YES" so i assume even the graphics is working properly??.Network,multimedia..the lot,all works!

Our kubunto that the kids use mostly though has two separate graphics cards i think but im a wee bit confused with things on this(2 inside & 2 game ports.Bit compact to tell though with this compaq presario 5130) 

When i do "lspci" i get the below info from it 
dad@Kubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:14.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:14.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:14.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:14.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro AGP-133 (rev dc)
dad@Kubuntu:~$

So assuming that the fella at the bottom is one of these cards i go looking in the display &  graphic section and i find the stuff showing in the screenshot below
[ATTACH]15928[/ATTACH]

Now i have seen 2 cards inside this(compaq presario 5130) and there is two lots of jotstick ports on these two separate cards.It`s pretty compact IN there and i aint entirely sure whats what(im trying though):biggrin: 

SO if the "rage" thing and the "utah" thing ARE indeed these 2 separate graphics cards then could someone tell me exactly what i might need to get to have them work properly as the "glxgears" dont really budge on this one.I know it`s "ATI" drivers but i cant find any of those names in adept and dont want to mess THIS pc up too or the kids will have me up all night re-doing for them:lol: 
I have loaded about 20 of the available games on this one for the kids that all seem to work SO i never really paid much more attention to it other than stick the internet back in now and again to check for updates.Done a wee bit of writing on it but thats it.
IF i see the desktop and the games play then i just assumed THIS pc ALL worked as my Ubunto seems to do.I dont know my way around this as much as i do mabey do the Ubunto ...............mmmmmmmmmmm:-\" 
Sorry for the long post but just want to put things in prespective in case somebody wants to tell me i should have had this done by NOW.
I can select and apply either "ati or rage LT Pro OR the mach one but upon "test" none of them seem to work according to the "test"Hence i realise it must be the drivers for them that are missing.:-\" 

As some of you know aleady im still a PC noob(relatively)..SO it`s all still a bit confusing at times....NO "windows POWER ranger" background for me unfortunately.......Sorry"power user".(not that it would help eh)
I had planned to get stuck into this too until the recent death of my XP\Ubu...which sort of sidetracked me a bit

Thanks in advance for any wee shove in the right direction

---

### Post by bulldog on 2006-09-18
I can't imagine why you should have two video cards.

Normally you have an onboard graphics controller or you have an AGP slot with a graphics card.

You can't use them both together if that's what you want to do.

---

### Post by xpod on 2006-09-18
I KNOW i cant use them together:biggrin: 
But i just want to figure out how to work at least one of them.
It was an old pc a pal messed up and gave to me,Theres a separate modem in one slot and these 2 things in the others.I thought myself one had to be for sound but they both have game controller ports on them mate and im only guessing...DONT KNOW:-\" 

Plus theres the stuff i see when i look at the screenshot i took.It`s telling me it detects that "mach" one but then "lspci" points to the "rage" one..

SO....You see how my confusion has arisen mate.....OR is it all really straight forward and im just "not seeing the woods for the trees"...AGAIN:-\" 

Excuse my ignorance mate

---

### Post by nickpaton on 2006-09-18
Xpod, you need to go into the bios and disable the onboard video. Not sure which heading it will be under, but try 'advanced' or similar.

Reboot with the Rage card in and Kubuntu should see only that.

---

### Post by xpod on 2006-09-18
AHHH as simple as THAT eh.....Well there in lies another bloody problem my man...
Getting INTO the bios on thiat thing.
When i first salvaged it i tried every combination of possibilities and still could`nt find out what key it was.

Of course "being moi" it was only THEN that i discovered it already booted from cd first....

So ive not needed to be IN that one since then.

I`ll go hammer on all those keys till i find which one it is then and see what happens from there.
So WHATS the other "mach" thing it say`s it`s detected?.
I understand the basics mate but the "display" section i posted the screenshot of sort of threw me.
Cheers for the shove mate

---

### Post by bulldog on 2006-09-18
I think the 'Mach' thingy is some onboard video chip,which should be disabled automaticly when you put in another graphics adapter.

You should look at the backside of this computer to determine if your monitor is atached to one or the other.

But rage lets me think at ATI and mach doesn't mean anything to me.
So I presume your monitor is atached to this card,but having a look to be sure is nothing to you.

---

### Post by xpod on 2006-09-18
THe moitors on a whole different connection mate.

Down at the bottom of the back theres the "ethernet" port and then these two different Other slots with a joystick port on each and both have the 3 little   jack plug holes as well....I also have the 3 jacks further up too.(the little holes for mic`s or speakers etc)#

Inside the pc i can see the 2 different cards but it is a bit squashed so i cant see right in...

Anyway......still trying bios keys..F19 brought up a "select password" screen but still no bios#-o ....Will keep trying

EDIT: right on closer inspection one has "game port" wrote on it and one has a tiny musical "note" on it so that must be sound after all..Unless thats just indicating the audio jack on it.WHY would a sound card have a game cotroller port on it though??

---

### Post by bulldog on 2006-09-18
EDIT: right on closer inspection one has "game port" wrote on it and one has a tiny musical "note" on it so that must be sound after all..Unless thats just indicating the audio jack on it.WHY would a sound card have a game cotroller port on it though??

I have a soundblaster soundcard WITH a gameport on it,it's not so strange though.

I'm interrested where you're monitor hangs on.
On one of the two cards or on the motherboard?

If so you are using the onboard chip and not the extra graphics adapter,if it's one.

I should put the thing on the kitchen table and tear it apart to see what it's all meaning.

See what the two cards are and get them out for inspection.
Take a good look at what kind of slots they where in.
PCI or AGP it makes a whole lot of difference.

So don't go to sleep tonight but do your duty as a dad and tear it apart!!

I will hear tomorrow,after a good night sleep :biggrin: ,where the results of your nightly exploring lead to.

---

### Post by nickpaton on 2006-09-18
To add to Bulldog's message, the plug - in graphics card will be in the first slot nearest to the main circuit board connectors.

I would suggest simply removing it and making sure tht your monitor is plugged into the 15 pin D shaped connector on the motherboard back connector.

---

### Post by xpod on 2006-09-18
NOOOOO CHANCE.....Well,mabey just a wee while:biggrin: 
Excuse the ignorance about game controller ports on sound cards.
Just opened it up again and the thing is`nt in one of the shorter cream coloured slots but a longer black slot
Then the other one is in one of the short cream clooured slots.:confused: 

Sorry my desriptions aint as technically specific as you might like but
that asides NONE of them have anything on them i can go on.I cant see any of the names i seen in "display setup"

I actually have a "maxi gamer phoenix" card in a box i was thinking of trying but it seems it must require a different type of slot to whats available on the present mobo.#-o 

Anyway.STILL cant get into bios.Im wondering if "bios passwords" can be set as the only thing ive had come up so far is a light blue "SETUP PASSWORD"
box and try as i might i just cant find any other key thats letting me in there...

It`s NO big deal really as the rest works for what me or the young un`s use it for....BUT:biggrin: ...It`s bugging me now,and i cant have THAT!!!!

EDIT:sorry.....the monitor is definetly NOT attatched to those things...IT`s at the top and those are away down the bottom.
The monitor could`nt attatch to one of these things...different plugs

---

### Post by nickpaton on 2006-09-18
i'm slightly lost as to which slots you are talking about.

Can you have a look at the following diagram which gives a description of a typical mobo, and tell us which boards are plugged into which slots

[http://www.bestbuy.com/site/olspage.jsp?guideID=1043363094917&categoryRep=cat01000&type=page&cmp=&id=cat12077#3]("http://www.bestbuy.com/site/olspage.jsp?guideID=1043363094917&categoryRep=cat01000&type=page&cmp=&id=cat12077#3")

Getting into a locked BIOS - mmm it may be possible to unlock, but involves removing the CMOS battery, and maybe not such a good idea coz it's not as simple as that due to having to observe antistatic etc.

I'll have a search around to see if there's some propriety software to identify or unlock the bios.

---

### Post by bulldog on 2006-09-18
I think he has a very old motherboard with no AGP.

I'm thinking how the old larger slots where called..................I should know but....... it will come to me.............I'm not as young as I use to be.:lol: 

Well then you have only the onboard chip to go with and two unknown cards.

Most likely one soundcard and something unknown.

Can't say more of it withouth your nightly explore session.

Off for know,wish you all a goodnight.

---

### Post by xpod on 2006-09-18
Sorry pal...right i "think" that one is in No2 and the other is in a No3
It`s really hard to get into that bit so i took the power unit out and could see a little better.
 It`s nothing like my Ubu pc as i can at least GET into that.THIS thing is really tightly packed and without doing as bulldog suggested i just cant get right in.
 It dont have as many slots as your link mate but i think those are the right ones i showed you.
 If the worst comes to the worst i`ll take the battery out ...Ive done THAT before too on the other pc for some reason or another...Little round thing.

As i said nick this was just another bit of junk i aquired and put to good use...
Being as kubunto has been on it from day one i`ve never had the reasons like i had with m.e & xp to NEED to fix things or figure out what the bit`s all were:biggrin:  

Yellow bits and cream bits with blue bits plugged into red bits and a few bits left over just in case:biggrin:

EDIT:found this ....
[http://www.linuxforums.org/forum/linux-laptops/6746-ati-rage-mobility-m1-3d-drivers-opengl-settings.html](http://www.linuxforums.org/forum/linux-laptops/6746-ati-rage-mobility-m1-3d-drivers-opengl-settings.html)
SO i know i dont want THAT eh

EDIT2...GOODNIGHT BULLDOG...I`ll stay up ALL night:---)

---

### Post by xpod on 2006-09-19
Well bulldog.I had to go to bed last night as i was up at 6 so did`nt have time for all night Kubunto but when i got up this morning mate i come across the darndest thing...
[ATTACH]15977[/ATTACH]

Fancy THAT eh!:biggrin: 
Well she had it all out and one card was a"creative labs" sound card and one was an "ethernet" card and the last one could only have been the "RAGE LT PRO" graphics card but again there was no real info on the thing.The monitor is attatched to the board itself.
So only ! card but it looks a bit worse for the wear so it does.

She also removed the motherboard battery(thanks nick) and decided to stick a slave hd in beside the quantaum bigfoot already there. ...mabey for "home" or something."Seeing as it was open" she said:---) 
Dont know if it was the battery or hd as upon rebooting it was being a bit tempremental but after another couple of "BOOTS" it decided to relent and at least come back on.:twisted: 

In the bios now the only thing resembling anything to do with "video\graphics" was an "onboard monochrome video adapter" which was disabled only for the re-boot to stick at"loading hardware drivers"....
So the bios was reverted back to how it was and the all was well again.

Gparted live cd was used to format the second drive to "ext3" but again upon reboot it all stopped.....A little further than before but being as she was`nt sure about a simple recovery option she decided to take the easy way out and stuck the alternate cd back in and run it again..as you can see
[ATTACH]15978[/ATTACH]........cheat eh!!

Again, ALL is well but we`re still none the wiser about the graphics card.
It`s still the same deal as i showed in the earlier screenshots and the cards are all IN properly now as the one in question seemed to be hanging out.All i had done to this previously was stick another memory stick in,tried to install Ubunto then settled for Kubunto..Stuck a load of the games on it and OFF they all went...no problems.
It`s only cause i got curious whilst looking at bit closer that i even asked about it.
I had intended on getting stuck  it a while back but the death of my main UBU\xp took precedent over that:-\" 

Well you did say you were looking forward to hearing the exploits so there you go mate....just for you!!(and any other really bored people out there)
Im sure theres many people out there with much more pressing needs as they sit there pulling their hair out...where as I find it all quite funny....
OUR OWN pc calamitys that is and not other peoples stress..:-\" 

Cheers for the advice as ever......least we got all the dust bunnies out it
even if none the wiser about the cards...AND a new "home"...

BYEEEEE
[ATTACH]15979[/ATTACH]

---

### Post by bulldog on 2006-09-19
It's a pity your atachments have a wrong format so it seems.
Can't see anyone of them.:sad: 

Well a nice story and and it's up and running again.

If the unknown card is a grapics card,you could try to put your monitor on it.
Maybe you even get a signal on your monitor.

Otherwise I haven't the slicest idea what kind of card it could be.
{the older slots at your motherboard are ISA-slots if I remember correct}

But now we know what the others are.

You did a good job!:D

---

### Post by xpod on 2006-09-19
Sorrry about that mate:-\" 
Cant even get THAT right first time:p 
The monitor would`nt go on that thing as it`s a different connector completely.
I should have just took a bloody photo of the cards themselves eh(ok kassi should have:---) )

It`s no biggie as i said and i was merely trying to understand AND hopefully make it work...a bit better

It`s all okay anyway.The card in question "looks" like its had a calamity of it`s own at some point as theres a dirty odd looking bit on it so it probably dont work at all.IF i chose all the relevant choices in the hardware section then i still get a message saying "this configuration video card driver and monitor dosent seem to work" so as the monitor seems to work fine i can only assume that it`s the card itself.


You know what they say about "assumption" though eh!!
Good stuff mate...cheers

PS...THAT aint really the actuall inners of it..just messing:rolleyes:

---

### Post by nickpaton on 2006-09-19
If the graphics card has the wrong connector and has a 'calamity' then get shot of it!

Love the photos of yourself LOL!!! NOW we know what you look like:D :D 

Yeah removing and replacing the Bios battery can cause the mobo to temporarily get it's knickers (not kassies BTW!!) in a twist as it resets everything again.

Good on yer mate and Oh Aye The Noo

---

### Post by bulldog on 2006-09-19
Well well,you have an exellent technician in tha house!!

She can make it if you broke things down.

Get rid of that broken card it's for no use anymore.

If the computer is up and running without problems,you're a lucky man.

And if not............you know who can fix it:razz:

---

### Post by xpod on 2006-09-19
> the removing and replacing the Bios battery can cause the mobo to temporarily get it's knickers (not kassies BTW!!) in a twist as it resets everything again.
 
 Good on yer mate and Oh Aye The Noo[

I`ll get her to take that card out as soon as ive changed THIS.She`s still on nappies so not quite at the hormonal hissy fit stage the rest of them are but still getting the pampers a bit knotted noo and again.

BTW..it`s"och aye"...for all you highland wannabe`s:-$ :D 

oaf for ma haggis n neeps:tongue:

---

