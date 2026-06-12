---
title: "Everyone, i have about 1 day , help"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Hmarroqu on 2007-10-05
I have one day to introduce someone to ubuntu and possibly replace vista on their brand new laptop..  What should i do other than plop the live cd  and make sure it is compatible with the hardware...

He is native spanish speaker so i would maybe install in spanish

Very computer illiterate,

will mainly use computer for internet, modem dialing and wireless.

If he uses aol to sign in and dial up, will that be an issue in ubuntu?

What would be a good way to set up his desktop so that it doesnt scare him ?

---

### Post by tdrusk on 2007-10-05
> **Hmarroqu said:**
> I have one day to introduce someone to ubuntu and possibly replace vista on their brand new laptop..  What should i do other than plop the live cd  and make sure it is compatible with the hardware...

He is native spanish speaker so i would maybe install in spanish

Very computer illiterate,

will mainly use computer for internet, modem dialing and wireless.

If he uses aol to sign in and dial up, will that be an issue in ubuntu?

What would be a good way to set up his desktop so that it doesnt scare him ?

Search for his model on the forum. Try to find him an install guide. Do it all for him, but bookmark the link.

---

### Post by Hmarroqu on 2007-10-05
> **fuzzyhair said:**
> Search for his model on the forum. Try to find him an install guide. Do it all for him, but bookmark the link.

This gets the award for biggest coincidence for my day....he has the same one you do.....

---

### Post by overdrank on 2007-10-05
> **Hmarroqu said:**
> This gets the award for biggest coincidence for my day....he has the same one you do.....

Hi and i have the same laptop and the wireless was the only hurdle ( have not tried the modem). Just one thing I have notice about the acer is that they all do not have the same hardware. Like the Acer 3680 will have 4 more number and this defines the hardware installed on that system. Good luck! :KS

---

### Post by tdrusk on 2007-10-05
> **Hmarroqu said:**
> This gets the award for biggest coincidence for my day....he has the same one you do.....

I knew it! Vista blows on this computer.

Upgrade him to Gutsy Beta. I have no problems with it and it works better with the hardware.

run lspci 
make sure his network card isn't recognized. If it isn't, follow this guide
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Install 915 resolution for proper resolution (just install it and ctrl+alt+backspace and it will work)

for sound he has to toggle the surround in the mixer. Kind of a pain, but at least it works.

That's about it. Good luck.

---

### Post by Presto123 on 2007-10-05
What does he like to see? The eye candy? Or the higher performance (512+mb usage in Vista vs. 140+/- in Ubuntu)?  IMO: I would attack the situation with the performance difference since he only has 512mb RAM, then introduce him to Beryl or Compiz/Fusion Cube.  :)

Currently, my laptop on Vista is using 488-600+ RAM just with the normal sidebar running. On my desktop with Ubuntu with Beryl running, I'm sitting right at 199.6 MB. That alone made me happy with this system.

I wouldn't get rid of Vista Entirely, though. Let it handle the Windows-only software and Linux can attack the programs with WINE. This is all my opinion, take it for a grain of salt because I know not one thing works for everyone. ;)

Also, I am not an expert with RAM usage in any sense, so correct me if I am missing something. ;)

---

### Post by Hmarroqu on 2007-10-05
run lspci?

---

### Post by adamorjames on 2007-10-05
> **Hmarroqu said:**
> run lspci?
Type "lspci" in the terminal.

---

### Post by Hmarroqu on 2007-10-06
ha yea i figured but that does what?. before i go do something i have no idea what im doing, doesnt look good while trying to introduce someone to the" wtf is that" of linux.

---

### Post by Hmarroqu on 2007-10-06
> **fuzzyhair said:**
> 


Install 915 resolution for proper resolution (just install it and ctrl+alt+backspace and it will work)

for sound he has to toggle the surround in the mixer. Kind of a pain, but at least it works.



How to?

---

### Post by adamorjames on 2007-10-06
> **Hmarroqu said:**
> ha yea i figured but that does what?. before i go do something i have no idea what im doing, doesnt look good while trying to introduce someone to the" wtf is that" of linux.

"make sure his network card isn't recognized" It either shows or doesn't show the network card.

---

### Post by tdrusk on 2007-10-06
> **Hmarroqu said:**
> How to?

run 
```
lspci
```

If part of the output says:
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
then you should follow the ndiswrapper guide that I linked to.

Now, for sound, double click on the volume controller to open the mixer.
Go to 
Edit>preferences
check surround.
Surround is what you control your volume levels with. Pretty simple, kind of stupid, but an easy steparound.

---

### Post by Hmarroqu on 2007-10-06
Fantastic, im about to begin doing this, i have all of tonite to get it right and hopefully i wont have any questions cause you all most likely be on here for very long.  Thanks very much and if i can get this right, ill have convinced yet another person in my house to start using ubuntu

---

### Post by mivo on 2007-10-06
> **fuzzyhair said:**
> Upgrade him to Gutsy Beta. I have no problems with it and it works better with the hardware.

I just went back to Feisty, because Gutsy randomly froze 3-5 times a day. The updates also still tend to break things -- yesterday there was an issue with CUPS, for example. Easy to fix for someone with a little experience, but he said his friend is "very illiterate" when it comes to computers. When Gutsy is ready, I agree that it will be the better choice, but I'd not go for it right now.

Hmarroqu, Ubuntu works best if the computer is in a network or connected to a router. You said your friend uses a modem and AOL, so you might need to fiddle around a bit to make it work. Look at Gnome PPP for this, see [here]("http://www.gnomefiles.org/app.php?soft_id=41"). You might want to download this and put the .deb on an USB stick or a disk since you might not be able to download it on his machine without a connection. See also [here]("http://www.ubuntux.org/how-to-install-dialup-ppp-client-gnome-ppp"). Depending on the modem type, this may not work at all. Internal modems, especially in notebooks, can be tricky.

---

### Post by Hmarroqu on 2007-10-06
Great so Ubuntu's first retard moments of the day....followed the guide to getting the wireless to work...went well, at the restart the stupid thing said the hdd had been mounted 24545+ times , i dont recall exactly but it was a large ******* # and it forced a check, then as i attempted to login to the network via wireless, the stupid thing froze, let it be known that this is THE very first time that ubuntu freezes on me. It pulled a windows on my ***.
Im very worried because this person is here for 2 days and lives in georgia, im in florida so if **** goes wrong i cant drive over and say sorry ubuntu is retarded sometimes, explain its advantages, look at the forums for a fix and drive home...

^asterisks... lol ^

---

### Post by Hmarroqu on 2007-10-06
As you might infer, im pissed now.  Everytime i try to login to network it freezes.  Why , i dont knw, anyone know, well by the time you answer it might be to late...his computer is rendered useless now....

---

### Post by n3tfury on 2007-10-06
> **Hmarroqu said:**
> As you might infer, im pissed now.  Everytime i try to login to network it freezes.  Why , i dont knw, anyone know, well by the time you answer it might be to late...his computer is rendered useless now....

lol, i hope you have recovery disks for his vista install.

---

### Post by Hmarroqu on 2007-10-06
Well, I regret even considering installing this pos.  Ubuntu is fine with me but it is the stupidest thing on this acer , if this laptop werent mine, id throw it out the ******* window right now.  Wireless sucks, it freezes all the time when I want to connect to any damn network.  I think its stupid and this computer should kill itself.  Im done trying to introduce idiots to this crap , the first shot i get and i happen to have the worst computer in the world
I always happen to have the worst luck with ubuntu and instaling them, so far every computer gives me so much trouble its getting ridiculous.
No one on the forums so far knows why it freezes and the people that i read figured it out were kind enough to not leave a word as to how they did so. 
so im screwed now, have been up all night and this laptop was better off with vista.  All this guy needed was internet access and i was under the impression that it would have been easy to install on this computer.  Guess im stuck now.

---

### Post by Hmarroqu on 2007-10-06
> **n3tfury said:**
> lol, i hope you have recovery disks for his vista install.
and that just put me in an even better mood

---

### Post by om1 on 2007-10-06
upgrade to gutsy beta... it works alot better for wireless... you can do it with this command
```
update-manager -d
```

---

### Post by n3tfury on 2007-10-06
> **Hmarroqu said:**
> Well, I regret even considering installing this pos.

so now ubuntu is a pos because you're having wireless issues on a certain model of acer laptop?  

ok.

> **Hmarroqu said:**
>  Wireless sucks, it freezes all the time when I want to connect to any damn network.  I think its stupid and this computer should kill itself.

yes, it's the hardware's fault. :rolleyes:

> **Hmarroqu said:**
> Im done trying to introduce idiots to this crap

oh, so everyone's an idiot except you?  lol.

> **Hmarroqu said:**
> have been up all night and this laptop was better off with vista.  All this guy needed was internet access and i was under the impression that it would have been easy to install on this computer.  Guess im stuck now.

yep, you're worse than stuck now.  you're about to give back a laptop to a person without the OS they paid for and worse than that without an OS *period*.  

why you didn't run the LiveCD and try and get wireless working under it to make sure things worked straight away is beyond me.  

look at it this way - you learned a good lesson these past few hours :)  good luck!

---

### Post by Capricori on 2007-10-06
Calm down, there's always a way to fix stuff :)
I just spent two days introducing a couple of my friends to Ubuntu, but they're now back on Vista..
They complain about Vista, and yet, as soon as you show them something else, they complain because it's NOT Vista... ("why can't I use my wireless out of the box, like in Vista?" "Why can't I play Age of Empires, like in Vista" "Why can't I install programs the Vista way, with .exes, rather than with that convenient package-manager/repository combination?")

They also laughed when I told them you have to 'mount' a hard drive... bloody juveniles :)

---

### Post by Hmarroqu on 2007-10-06
> **om1 said:**
> upgrade to gutsy beta... it works alot better for wireless... you can do it with this command
```
update-manager -d
```
 
I did lots and lots of reading, some where some one said gutsy is stupid for this computer , it freezes it frequently

---

### Post by eentonig on 2007-10-06
Why on earth did you want to convert this guy?
- You only had one day.
- He lives miles away from you
- He cant help himself
- You don't seem to be that much of an expert

The whole situation was screaming "Problems ahead!!"

---

### Post by Hmarroqu on 2007-10-06
> **n3tfury said:**
> so now ubuntu is a pos because you're having wireless issues on a certain model of acer laptop?  

ok.



yes, it's the hardware's fault. :rolleyes:



oh, so everyone's an idiot except you?  lol.



yep, you're worse than stuck now.  you're about to give back a laptop to a person without the OS they paid for and worse than that without an OS *period*.  

why you didn't run the LiveCD and try and get wireless working under it to make sure things worked straight away is beyond me.  

look at it this way - you learned a good lesson these past few hours :)  good luck!

ubuntu has always been a pos to me regarding all my installations but i still prefer it to windows, given that i dont have to use itunes for the ipod or other crap along those lines...

The main issue with all linux distros from what the opinions of others have also stated is the damn hardware compatibility and prior to installing i was inclined to believe that the wireless was an easy fix.....

"everyone is an idiot except you?" 

...

stupid question

Vista ran worse than ubuntu does on this computer so he is better off although he wont be connecting wireless often, the computer itself cost $400 and was bought at walmart,

It has an OS, a retarded one...same as vista.

and i did run the live cd on it....as i said prior, i was aware of the issues and from several threads and post, was convinced it was an easy fix...for some reason this one decides to be the black sheep of the bunch..

The lesson I learned is to not install/introduce ubuntu to anything or anyone anymore cause ill just keep it all to myself and be stupid with it.

---

### Post by Hmarroqu on 2007-10-06
> **eentonig said:**
> Why on earth did you want to convert this guy?
- You only had one day.
- He lives miles away from you
- He cant help himself
- You don't seem to be that much of an expert

The whole situation was screaming "Problems ahead!!"


so much for being easy to install huh.

---

### Post by n3tfury on 2007-10-06
> **Hmarroqu said:**
> I did lots and lots of reading, some where some one said gutsy is stupid for this computer , it freezes it frequently

i've been using gutsy for over a month as my main OS and have had zero freezes.

> **Hmarroqu said:**
> so much for being easy to install huh.

the biggest gripe has always been wireless.  but then again, it's not ubuntu or linux's fault for that matter.  point the finger elsewhere.

eentonig is right:  this spelled disaster from the get-go.  you're trying too hard to convert people it seems.

---

### Post by tdrusk on 2007-10-06
> **Hmarroqu said:**
> As you might infer, im pissed now.  Everytime i try to login to network it freezes.  Why , i dont knw, anyone know, well by the time you answer it might be to late...his computer is rendered useless now....

Is it freezing on bootup, on the splash screen? If so, flip the wireless switch to turn it off (it's on the front), then go to system>administration>restricted drivers manager and disable the atheros driver.

Isn't there a program for Ubuntu so you can be in one place and use someone elses? If so, you have more than one day?

btw, post the output of your lspci.

---

### Post by Hmarroqu on 2007-10-06
03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

or did you want to see the whole thing?

It freezes when i try to connect to a WAP2 network , the unsecured ones work fine...Just WAP2 .

The volume thing is fixed thanks to the links you gave me, i also got the resolution going too...

Right now my main concern is making sure that when he tries to connect to a WAP2 up in georgia it wont freeze on him, other than that its as good as its gona get....better than vista for sure

BTW fuzzy, how is the dvd playback for yours?
I installed the restricted "whatever they are called" using automatix but when i try to load a dvd , it does not recognize it and spits it out...literally.

---

### Post by tdrusk on 2007-10-06
> **Hmarroqu said:**
> 03:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

or did you want to see the whole thing?

It freezes when i try to connect to a WAP2 network , the nsecured ones work fine...Just WAP2 .

The volume thing is fixed thanks to the links you gave me, i also got the resolution going too...

Right now my main concern is making sure that when he tries to connect to a WAP2 up in georgia it wont freeze on him, other than that its as good as its gona get....better than vista for sure

BTW fuzzy, how is the dvd playback for yours?
I installed the restricted "whatever they are called" using automatix but when i try to load a dvd , it does not recognize it and spits it out...literally.

My dvd playback is perfect. I'm glad you got wireless working to an extent. I was having freezing problems. I fixed it by reinstalling, but I actually think it has to do with the restricted drivers manager making conflicts. Please do what I said above, because eventually the computer won't boot if wireless is on.

There are more choices than just secured wap2. Try hexidecimal, it's what I used to connect.

---

### Post by Cannaregio on 2007-10-06
> **Hmarroqu said:**
> I have one day to introduce someone to ubuntu and possibly replace vista on their brand new laptop..  What should i do other than plop the live cd  and make sure it is compatible with the hardware...

He is native spanish speaker so i would maybe install in spanish

Very computer illiterate,

will mainly use computer for internet, modem dialing and wireless.

If he uses aol to sign in and dial up, will that be an issue in ubuntu?

What would be a good way to set up his desktop so that it doesnt scare him ?

Given the problems you had installing ubuntu on that box, I think you should try things the other way round.
"Clean" first of all his windoze: let him arrive to GNU/Linux by himself, using his own brain.

1°
away goes MSIE, in comes opera  for windows (that is waay quicker and at the end of the day even better than Firefox coz it comes with everything you need out of the box)
Show your friend how you can eliminate -once for all- any advertisment pop up from the sites he likes visiting just rightclicking and choosing "block content", he will never go back to MSIE again :-)
He'll gasp in awe at the speed and power

2°
away goes (if he had it) MSoffice, in comes Openoffice. Ditto for gimp.
Show your friend how he can have even in windows (almost) everything for free 
He'll gasp in awe at the concept

3°
and so on and so on (in windows)
firewall and antivirii: norton crap away, "free" alternatives (à la AVF) come in
He'll gasp in awe at the speed gains once norton has been kicked off

4°
Tell your friend about DRM, sniffing programs, rootkits and so on.
He'll gasp in awe at the dangers and at his inexistent anonymity.
Explain him that there's no real anonymity on the web, but that this is no reason  everyone and his dog should (and will) know in redmond what the hell he's searching on his own harddisk :-)

5°
Tell him that his new, (somehow) cleaned and "free" windows box is but a pale mirror of a _real_ free GNU/linux box, and that he has to try Linux, and maybe Ubuntu, by himself.
If he's interested, he'll join by himself
if not, good riddance

---

### Post by tdrusk on 2007-10-06
I think you should set up nomachine nx so you can control his computer from yours.
[http://www.nomachine.com](http://www.nomachine.com)

---

### Post by Hmarroqu on 2007-10-06
sigh*, random freezes again, i turned off the restricted driver too....i dont knw what else to do. this is like the 5th installation
trying to get the codecs and little things set up but im constantly hindered by the freezing , this network issue is the only thing holding me back from having a good solid and reliable installation.

---

### Post by Hmarroqu on 2007-10-06
> **fuzzyhair said:**
> I think you should set up nomachine nx so you can control his computer from yours.
[http://www.nomachine.com](http://www.nomachine.com)


What about the "remote desktop" option that comes with ubuntu?

---

### Post by Hmarroqu on 2007-10-06
screw it, everytime i have the ethernet cable and it gets disconnected it freezes the system, im just gona put xp on this computer, maybe i wont have as much trouble with the drivers and im pretty sure it wont freeze like ubuntu on this laptop

---

### Post by n3tfury on 2007-10-06
> **Hmarroqu said:**
> screw it, everytime i have the ethernet cable and it gets disconnected it freezes the system, im just gona put xp on this computer, maybe i wont have as much trouble with the drivers and im pretty sure it wont freeze like ubuntu on this laptop

so you did wipe out his vista eh?  how did you explain that one?

---

### Post by Paul820 on 2007-10-06
Why on earth did you mess with someones computer like that? Did you not even back-up his vista partition or make another partition for ubuntu so he could fall back to vista? Man, i would be fuming, i hope your friend is understanding. :(

---

### Post by tdrusk on 2007-10-06
> **Hmarroqu said:**
> What about the "remote desktop" option that comes with ubuntu?

I think that only works with a network.

Sorry you couldn't get Ubuntu running. It's running great on mine.

---

### Post by Hmarroqu on 2007-10-06
> **Paul820 said:**
> Why on earth did you mess with someones computer like that? Did you not even back-up his vista partition or make another partition for ubuntu so he could fall back to vista? Man, i would be fuming, i hope your friend is understanding. :(

1. because he told me two,
2 there was nothing to back up its a brand new computer , if you read the first posts
3. fall back on vista....no

---

### Post by Hmarroqu on 2007-10-06
> **fuzzyhair said:**
> I think that only works with a network.

Sorry you couldn't get Ubuntu running. It's running great on mine.

Thanks for you help, i appreciate it, this goes for all the other people who contributed as well.

---

### Post by HermanAB on 2007-10-06
You can try a different distribution.  There are many other ones out there, for example Mandriva, Fedora and Suse.  Ubuntu is popular but it isn't the Alpha and Omega - it is middle of the road - a good standard.

The thing to remember is that while each distro vendor has hundreds of machines in their labs, nobody has everything and they cannot test with every piece of hardware ever manufactured on the planet.  Shopping around a little, will likely find you a distribution that will Just Work.

My top recommendation is Mandriva.  This is a large distribution that has everything including the kitchen sink, so it tends to be a bit daunting to a beginner, but the 2007 version is very likely to work on this machine and 2008 will be out in a week or so.

Other than that, I guess you learned a lesson - don't mess with other people's stuff unless you *really* know what you are doing.  Next time, just give the person a live CD or memory stick with some sort of Linux on it.

Cheers,

Herman

---

### Post by Paul820 on 2007-10-06
> **Hmarroqu said:**
> 1. because he told me two,
2 there was nothing to back up its a brand new computer , if you read the first posts
3. fall back on vista....no

What about rescue disk, you can make rescue disks from a new computer. I could have made them with mine. Yes, i did read your posts. Why not fall back to vista, it's a pile of crap but at least he would have had an operating system.

---

### Post by UI-Freak on 2007-10-06
Hehe as soon as he gets into trouble, you start bad mouthing him.

Linux is for computer enthusiasts, and its one hell of a problem to install on a lot of computers. Wireless and modem is especially painfull.

You may laugh and LOL in your protected areas, these enthusiast communities, but outside this place people struggle with Linux when they even consider using it. Not many does. Not because they are ignorants, but because they don't need Linux. They need programs. Linux has a few good programs and tons of amateur stuff in v0.4.

You blame everything but Linux, laugh at people that are unlike yourself and call people with no interest in Linux for ignorant people that doesn't want to learn anything new. You are fanboys.

Even Dell and M Shuttleworht admits that Linux is not ready for general desktop use, and there is no pro software out there for the people.

sudo apt-get better product

Being a fanboy and posting here doesn't help your precious Linux. Improve the product instead.

---

### Post by Hmarroqu on 2007-10-06
"sudo apt-get better product"  

word

I got it to work as best as possible, through tedious installations.
WEP2 will still freeze it so i told him to not to try and connect to them and let it do it for him when there is an available network.  

when he had the comp he didnt even knw that he had a build in wireless card, he just used the ethernet .

I made everything for him automatic regarding media, taught him to use it in 5 minutes and now his computer runs like  a $1000 one,  this one only costing him $400.  

So thank you very much to those who gave me so much input i appreciate people like you,  and no thanks to those who made everything for me that much counter productive.

Besides, i was just going by what the writing on the Cd ubuntu sent me encourages...

---

### Post by adamorjames on 2007-10-07
All's well that ends well. :)

---

### Post by mivo on 2007-10-07
> **UI-Freak said:**
> Even Dell and M Shuttleworht admits that Linux is not ready for general desktop use, and there is no pro software out there for the people.

So, all the government agencies, even entire towns, that switched to Linux don't use "pro software"? I use Linux exclusively for my job, and I work in the IT/entertainment sector. There is plenty of professional software available. Sure, there are some specialist applications that only exist on different platforms, but that does not apply to the average professional user, and certainly not to the average desktop user. The latter may use Photoshop because they pirated it (see my signature), but they don't "need" it. GIMP still offers far more than they would need.

Linux's current weaknesses are hardware drivers (this has massively improved in the past few years), and high-end gaming. Considering that console gaming is where the money is now and that revenue from PC games has been decreasing consistently (more and more studios and developers stopped making games for PCs), the gaming issue will sooner or later disappear, even if you ignore the fact that there are native Linux games (Neverwinter Nights, X3, next month Unreal Tournament 2008, etc.). 

I see little difference between a fanboy and a hater.

---

