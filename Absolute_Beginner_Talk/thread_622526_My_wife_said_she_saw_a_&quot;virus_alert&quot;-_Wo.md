---
title: "My wife said she saw a &quot;virus alert&quot;- Wont boot now"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by jankind on 2007-11-24
Ok so my wife just came downstairs and said she was surfing the internet and she saw a "virus alert" and that it quickly "started some sort of scanning process" so she shut down Ubuntu in the normal way to come down and tell me about it. I told her there should be no problem as the security thing was one of my selling points to switch our home PC over to Ubuntu. 

Anyway, I came upstairs and what do you know? I'm not booting up at all here. Nothing... No start screen, no usual beep tones... Nothing.
(I'm on my Mac right now) 

SO where do I start? What could have possible happened here? Unfortunately, the above is ALL I have to go from.

SO yeah, my wife is not sold on Ubuntu yet.

---

### Post by G. Cotgreave on 2007-11-24
are you shure your wife didn't click on a pop up window that said ''stop this virus'' or something?

---

### Post by Taboo Mirage on 2007-11-24
Define "not booting."  You say your computer does not "beep" at all.  This beep is known as the POST: Power On Self Test.  If you are getting no feedback when you turn on your computer, i.e no video output and no beeps whatsoever, then what you're describing sounds like a very critical hardware problem.  Are the fans spinning at least to indicate that power is running through the board in some capacity?

---

### Post by jankind on 2007-11-24
Unfortunately, I have no clue what she saw, or what she did. SHe said it was doing some sort of "virus alert" and "scan" so she shut down (normally) and now I can't boot ...

What were you referring to, what would that do?

---

### Post by geirha on 2007-11-24
Not much to go on indeed, my first guess would be that the processor has overheated ... Or does it get to the bios and grub and then goes black?

---

### Post by jankind on 2007-11-24
> **Taboo Mirage said:**
> Define "not booting."  You say your computer does not "beep" at all.  This beep is known as the POST: Power On Self Test.  If you are getting no feedback when you turn on your computer, i.e no video output and no beeps whatsoever, then what you're describing sounds like a very critical hardware problem.  Are the fans spinning at least to indicate that power is running through the board in some capacity?

Right, exactly. It isn't passing the post even.  No beep codes, But the power is firing up, fans are spinning etc...

---

### Post by mouseboyx on 2007-11-24
So is there just a blank screen with nothing when you turn on the computer?

---

### Post by jankind on 2007-11-24
> **geirha said:**
> Not much to go on indeed, my first guess would be that the processor has overheated ... Or does it get to the bios and grub and then goes black?

No, not reaching the bios or the start up screen.

---

### Post by Taboo Mirage on 2007-11-24
Okay, this is very ambiguous and you're not being given a lot to go by here.  You could try some of these things:

1. Check connectors within the computer, namely power including 4-pin "P4" connector if your CPU requires it.
2. Reseat the CPU, RAM, Graphics Card.
3. Disconnect all components except CPU, 1x RAM chip and video card.  Try booting.
4. Reset CMOS by removing the battery or using the jumpers.
5. Ensure nothing is shorting the board and that is mounted on the motherboard pins correctly and not making contact with the case.

Those would be the initial steps off the top of my head.  Unfortunately there are more grave things that could have happened which may be causing this.  Things such as power surges damaging the motherboard itself can also provide the symptoms you're describing which would essentially signify the end of the machine's life.

Anyway, this is definitely symbolic of an issue purely relating to hardware.  I really doubt anything your wife did in Ubuntu caused this.

---

### Post by geirha on 2007-11-24
Pop the hood and turn it on, see if all the fans are spinning and relativly dust free.

---

### Post by mouseboyx on 2007-11-24
do you have an integrated graphics card?

---

### Post by MozartlovesUbun2 on 2007-11-24
can u get to the bios ?

whats your boot set to, check usb drives are unplugged and remove any cd / dvd from drive

i cant imagine your pc got overheated as gutsy has HAL or something, anyway it should run cool, i know my lappy does.

i think the ubuntu live cd has a rescue system or something similar, well put it in and try booting.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-24
sounds like a hardware problem to me you wife always tells you the hole truth right?
or if it just died and she thought she broke it but dosent want you to know would she fib and say it said something about a virus

kuss thats what my sister would do and my mom and my brother "i dont know got a virus or something"

loi

---

### Post by NET WT on 2007-11-24
Did you have anti-virus installed on this computer?

---

### Post by jankind on 2007-11-24
> **Taboo Mirage said:**
> Okay, this is very ambiguous and you're not being given a lot to go by here.  You could try some of these things:

1. Check connectors within the computer, namely power including 4-pin "P4" connector if your CPU requires it.
2. Reseat the CPU, RAM, Graphics Card.
3. Disconnect all components except CPU, 1x RAM chip and video card.  Try booting.
4. Reset CMOS by removing the battery or using the jumpers.

Those would be the initial steps off the top of my head.  Unfortunately there are more grave things that could have happened which may be causing this.  Things such as power surges damaging the motherboard itself can also provide the symptoms you're describing which would essentially signify the end of the machine's life.

I actually did do all of the above a few months ago when I was having a similar problem. Maybe it's coming back to haunt me. It just seems so odd, what she is describing to me, and all of a sudden it won't boot.  

What makes it even worse is trying to sell her on the switch from windows when little issues come up that I can't explain to her, being a noob myself.  !!!  NOW she is definitely not buying the security benefits of using Linux. Argh.

---

### Post by MozartlovesUbun2 on 2007-11-24
> **geirha said:**
> Pop the hood and turn it on, see if all the fans are spinning and relativly dust free.

keep the vacuum cleaner in hands reach.

---

### Post by MozartlovesUbun2 on 2007-11-24
> **jankind said:**
> I actually did do all of the above a few months ago when I was having a similar problem. Maybe it's coming back to haunt me. It just seems so odd, what she is describing to me, and all of a sudden it won't boot.  

What makes it even worse is trying to sell her on the switch from windows when little issues come up that I can't explain to her, being a noob myself.  !!!  NOW she is definitely not buying the security benefits of using Linux. Argh.

remember its not linux is more secure, its the **USER's ignorance** which breaks a OS.

*I've run windohzs for years without a problem*

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-24
> **MozartlovesUbun2 said:**
> keep the vacuum cleaner in hands reach.

no don't use vacuum cleaner some thing about staic and crap use air in a can

---

### Post by Taboo Mirage on 2007-11-24
> **jankind said:**
> What makes it even worse is trying to sell her on the switch from windows when little issues come up that I can't explain to her, being a noob myself.  !!!  NOW she is definitely not buying the security benefits of using Linux. Argh.

Frankly, what she said doesn't really make a whole lot of sense.  It certainly didn't cause this hardware failure, that I can say with a degree of certainty. I'd wager she just saw one of those annoying banner ads which say these things and simulate a "scan", which is nothing more than an animated GIF of a progress bar.  Did you even have any anti-virus Linux packages installed?

> **<<joe>> said:**
> no don't use vacuum cleaner some thing about staic and crap use air in a can

There are vacuum cleaners with anti-static heads, you know. =P  They can reduce the risk of ESD.

---

### Post by MozartlovesUbun2 on 2007-11-24
> **<<joe>> said:**
> no don't use vacuum cleaner some thing about staic and crap use air in a can

true, thats a good idea

(i've always vacuumed though, hmm i guess its ok if you dont touch the parts)

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-24
> **Taboo Mirage said:**
> Frankly, what she said doesn't really make a whole lot of sense.  It certainly didn't cause this hardware failure, that I can say with a degree of certainty. I'd wager she just saw one of those annoying banner ads which say these things and simulate a "scan", which is nothing more than an animated GIF of a progress bar.  Did you even have any anti-virus Linux packages installed?



There are vacuum cleaners with anti-static heads, you know. =P  They can reduce the risk of ESD.

yes then from now on we must spesify anti-static head vacuum cleaners

---

### Post by Shazaam on 2007-11-24
Try this for a quick diagnostic on a desktop::
1. Unplug the powercord from your ups/powerstrip/wall outlet.
2. With the pc unplugged, push in and hold the power button on the pc for a count of ten.
3. Plug the powercord back in and see if it will boot.

---

### Post by MozartlovesUbun2 on 2007-11-24
have you moved your pc around a lot? (like bumpy car rides)

apparently one should remove the graphic card, and carry it separately.

same for any other agp, pci, etc cards

---

### Post by jankind on 2007-11-24
> **Taboo Mirage said:**
> Frankly, what she said doesn't really make a whole lot of sense.  It certainly didn't cause this hardware failure, that I can say with a degree of certainty. I'd wager she just saw one of those annoying banner ads which say these things and simulate a "scan", which is nothing more than an animated GIF of a progress bar.  Did you even have any anti-virus Linux packages installed?


.

Exactly. That's what I was thinking as soon as she came down and told me about it. I'm sure it's nothing, just a stupid banner that is obvious to most people that it's just a stupid banner. No worries. But then I came up here and now this. I'm thinking from  the responses here, we might have overheated the processor? Oh... and no to your last question...

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-24
> **MozartlovesUbun2 said:**
> have you moved your pc around a lot? (like bumpy car rides)

apparently one should remove the graphic card, and carry it separately.

same for any other agp, pci, etc cards

I didnt even think to do that but thats good idea 
i would sujest to reseat every card in the comuter (pull out and put back in)

---

### Post by Taboo Mirage on 2007-11-24
> **jankind said:**
> I'm thinking from  the responses here, we might have overheated the processor?

As I said it could be a multitude of things.  You should try some of the stuff I've said as well as take a look at some others.  The guy suggesting disconnecting and holding the power button for 10 seconds is also viable; it will discharge the internal capacitors and its worth a try.

Personally I'd steer away from a graphics/RAM/CPU issue as if any of these things were problematic it would emit a specific beep code indicating the nature of the problem.  There are cases when they may not, however.  Resetting the CMOS would be high on my priority list after a brief visual inspection of everything to ensure its connected.  Reseating components also wouldn't hurt here.

As mentioned though if there's been something like a power surge which has caused damage to the motherboard, which I have seen to cause these symptoms in the past as well, then you may be looking at a dead computer.

---

### Post by jankind on 2007-11-24
> **Taboo Mirage said:**
> As I said it could be a multitude of things.  You should try some of the stuff I've said as well as take a look at some others.  The guy suggesting disconnecting and holding the power button for 10 seconds is also viable; it will discharge the internal capacitors and its worth a try.

Personally I'd steer away from a graphics/RAM/CPU issue as if any of these things were problematic it would emit a specific beep code indicating the nature of the problem.  There are cases when they may not, however.  Resetting the CMOS would be high on my priority list after a brief visual inspection of everything to ensure its connected.  Reseating components also wouldn't hurt here.

As mentioned though if there's been something like a power surge which has caused damage to the motherboard, which I have seen to cause these symptoms in the past as well, then you may be looking at a dead computer.

I'll try those things. Definitely resetting the CMOS at least. I actually replaced the battery recently...
I'll try the power supply thing too. 

Thanks for all the responses everyone, hopefully I'll get up and running here and also convince my wife that this switch was, in fact, a good thing.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-11-24
> **jankind said:**
> I'll try those things. Definitely resetting the CMOS at least. I actually replaced the battery recently...
I'll try the power supply thing too. 

Thanks for all the responses everyone, hopefully I'll get up and running here and also convince my wife that this switch was, in fact, a good thing.

even if you cant convince her it was a good thing you could convince her that it is not ubuntu's falut that it died errr is haveing a problem

---

### Post by jankind on 2007-11-24
> **<<joe>> said:**
> even if you cant convince her it was a good thing you could convince her that it is not ubuntu's falut that it died errr is haveing a problem

I sure hope so. It's not even that she was a huge fan of all things windows either. She just wants to sit down and have things work. Then she blames me AND Ubuntu when they don't. 
LOL

---

### Post by gali98 on 2007-11-24
As far as the virus thing goes...
First I've never seen a virus as such (the flashing ad) targeted at linux. There's almost really no point. An usually the only reason why someone would have anti virus on linux is because it is connected to windows somehow. I think this must be some strange coincidence. I don't see how a virus especially a linux virus could get through and attack the hardware.
Kory

---

### Post by jankind on 2007-11-24
> **gali98 said:**
> As far as the virus thing goes...
First I've never seen a virus as such (the flashing ad) targeted at linux. There's almost really no point. An usually the only reason why someone would have anti virus on linux is because it is connected to windows somehow. I think this must be some strange coincidence. I don't see how a virus especially a linux virus could get through and attack the hardware.
Kory

Yeah, I'm thinking it's a strange coincidence and  I'm simply having hardware problems directly after her seeing some stupid banner ad somewhere.

---

### Post by MrKlean on 2007-11-24
I don't think I saw anyone mention to go into bios...check it and "save and exit" .  That's happened to me before...from shutting down wrong..Although I ALWAYS shut down the right way !!  LOL!!

---

### Post by MozartlovesUbun2 on 2007-11-25
> **MrKlean said:**
> I don't think I saw anyone mention to go into bios...check it and "save and exit" .  That's happened to me before...from shutting down wrong..Although I ALWAYS shut down the right way !!  LOL!!

:) I did!

---

### Post by gn2 on 2007-11-25
Get the hard drive out and connect it to another PC either externally in a USB enclosure or internally and scan it.

I would stake my life's savings that there's no virus on it.

---

### Post by Sawta on 2007-11-25
Make sure that if you start messing around inside the computer that you ground yourself first! :)

I don't have much to contribute that hasn't been said already, but you mentioned that you had recently replaced the CMOS, I was wondering, how old is this computer? Does it tend to have a lot of hardware issues?

At the very least, I would try to convince your wife that it is infact a HARDWARE problem and not a SOFTWARE one.  The way I'd go about approaching this would be saying something like this:

A mechanical pencil snapping because the plastic is worn out vs using a new form of graphite in that same pencil; just because you were writing with this new graphite at the time doesn't necessarily mean that THAT'S what broke your pencil ;)  (Keep in mind that, if you use my analogy, you are infact, trusting people on the internet, possibly an unwise choice:lolflag:)

Good luck either way and I hope you get your problem solved soon.

---

### Post by tdrusk on 2007-11-25
Since your wife is a liar who broke your computer...
```
sudo aptitude remove wife
```
aptitude handles dependencies better :P

Then, see if there's anything else out there for you:

First see what's out there:
```
sudo aptitude update
```

Then be more specific:
```
sudo aptitude search wife
```

or try something new
```
sudo aptitude search partner
```


Okay that was all a joke. Don't take offense.

I am having a similar problem with my computer. I will try to mess with the motherboard (move it) and reseat everything.

Good luck!

---

### Post by MozartlovesUbun2 on 2007-11-25
> **Sawta said:**
> Make sure that if you start messing around inside the computer that you ground yourself first! :)

I don't have much to contribute that hasn't been said already, but you mentioned that you had recently replaced the CMOS, I was wondering, how old is this computer? Does it tend to have a lot of hardware issues?

At the very least, I would try to convince your wife that it is infact a HARDWARE problem and not a SOFTWARE one.  The way I'd go about approaching this would be saying something like this:

A mechanical pencil snapping because the plastic is worn out vs using a new form of graphite in that same pencil; just because you were writing with this new graphite at the time doesn't necessarily mean that THAT'S what broke your pencil ;)  (Keep in mind that, if you use my analogy, you are infact, trusting people on the internet, possibly an unwise choice:lolflag:)

Good luck either way and I hope you get your problem solved soon.

take her out for a nice dinner or maybe get her a new pc (XMas is here soon)

---

### Post by travm on 2007-11-25
My wife doesnt lie to me anymore when she breaks my computers.  She knows i'm just going to take it apart and find out what happened the hard way and then be double angry because she broke my computer and lied to me.  Usually though she has no idea what she did.  
I think its funny that I can run, even windows for a year or more without it getting junked up.  but she cant go 1 month without her system grinding to a halt with errors everwhere.  

Even linux isnt bullet proof.  i had one of my non tech friends over the other day, and he was trying to transfer music to his phone, which he did, but in the process I had 4 blank launchers on my desktop, my filesystem launcher was gone from the desktop and I no longer had a splash screen during boot.  
How could one person do this in 10 minutes, while still actually doing something useful?
I just laughed to myself on this one, but it happens.  Thankfully most of us can just fix it and be done with it.

Sorry if i'm no help, but you clearly have a hardware problem.  My wife once spilled a whole bottle of coke on my laptop keypad, then tried to wash it off with water.  Ever seen a laptop blow a breaker?  its cool.  (thanks dell warranty)

---

### Post by jhenager on 2007-11-25
> **jankind said:**
> Yeah, I'm thinking it's a strange coincidence and  I'm simply having hardware problems directly after her seeing some stupid banner ad somewhere.

That'd be my conclusion, too.
1. Very few viruses are targeted at Linux.
2. There are tons of web based ads and malware designed to fool the newbie user that they are infected, and to click on a popup to get a cleaner.

Since you mention a similar issue months ago, I'd look at the hardware first, by removing all devices and all the memory you can. Leave the video card and enough RAM to boot.
If you have a diagnostics disk, use it. 
The suggestion to try a Ubuntu Live CD was a good one, because you know there is no virus on it. However, you first need to get it to POST.

---

### Post by Riffer on 2007-11-25
Been through this to many times to count.  Your wife did nothing wrong, it was just a coincidence is all.  

With no post beep means its your graphics.  If you have a card then just swap it out for a new one (check for compatibility for Ubuntu).  If you have integrated video (graphics come from your motherboad) means you MB is toast and needs to be replaced.  If money is an issue you can try putting a graphics card in and see if that works.

I have replace many a graphics card because they suddenly die.  You can try doing all the reseating etc, but I have found that reseating never works.  Graphic cards are pretty rugged and will take alot but when they give up its because they're now crap.

After you swap out your card you will need to change drivers, with windows you would just use the install cd that comes with your graphics card.  With Ubuntu its a bit different.  You will boot into a text screen which will tell you that your xwindows doesn't match your card.  You will need to reset xwindows.  It isn't hard but you will need to know your vender (who makes the card) and model of the card.  Also it helps if you know the vendor and model of your moniter.

Hope that helps

---

### Post by philinux on 2007-11-25
I had a bad shutdown with feisty, after which the bios screen went very slow. When I went in to the bios using the cursor keys it would take ages to move.

I reflashed the bios and it fixed it. Managed to find an update.

---

### Post by sailor2001 on 2007-11-25
ctrl/alt/ f1  sign in and then sudo dpkg-reconfigure xserver-xorg

---

