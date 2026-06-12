---
title: "Creative Soundcards?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Fillibuster on 2007-04-02
I just installed Ubuntu today on a new partition on my Dell XPS 400.  I have some variation of the Creative X-Fi sound cards, and I've heard from friends on another forum that there is no Linux support for Creative cards.  Is this true? Or is there any kind of workaround for my soundcard? Any responses are appreciated, I'm enjoying Ubuntu so far even though I've had issues, its a great learning process! Thanks!

---

### Post by teaker1s on 2007-04-02
found this
[http://opensource.creative.com/]("http://opensource.creative.com/") sounds like support later in the year

---

### Post by 23meg on 2007-04-02
Don't count on Creative's word on drivers; they're notorious for not keeping their promises.

---

### Post by Fillibuster on 2007-04-02
Well that is unfortunate isn't it.  I will keep my eyes peeled for the support, but in the meantime I wasn't planning on getting rid of Windows so it isn't a big deal at all, since I'm just tinkering and learning how to use Linux as of now.  Thanks for the replies...

---

### Post by teaker1s on 2007-04-02
your welcome, welcome to the forums:popcorn:

---

### Post by freebird54 on 2007-04-02
Just a question - what actually doesn't work yet?  Maybe Creative accidentally released something compatible with one of their earlier cards?  :)

Also - it might work so far as it is Blaster compatible...

---

### Post by Fillibuster on 2007-04-02
Well the volume control icon in the top right says that it doesn't detect any devices to control...I'm not sure if it's Blaster compatible, how would I tell?

---

### Post by freebird54 on 2007-04-02
It should mention it as a feature on any spec sheets or bumpf from the company.  Do you hear the drums at login, or the boot up 'tune'?

---

### Post by Fillibuster on 2007-04-02
No I don't hear anything...I'll get on Windows and see if I can find out which card it is, and see if I can find specs about it.  I'll post back what I find out...

---

### Post by Fillibuster on 2007-04-02
I can't find anything specific.  All I know is its a Sound Blaster X-Fi.  I'm guessing its the Extreme Audio one but I'm not positive.

---

### Post by freebird54 on 2007-04-02
Sorry for the delay (dinner and a nap :) ).  I don't find anything specific yet - but here is one place to look:
[http://alsa.opensrc.org/Sound_cards](http://alsa.opensrc.org/Sound_cards)
If you can figure out which chip set you are running, (for instance mine turned out to be an emu10k)  you will probably find someone that knows how to make it go.  Have you Googled those terms yet?  It's awful to have to, but sometimes its the best way...

I'll see if I locate something too - increases the odds!

---

### Post by Fillibuster on 2007-04-02
Awesome, thanks for all the help! I'll get on it...

---

### Post by j002 on 2007-04-02
You need to install your soundcard.

Look in "excerpt from Ubuntu book" in Help about 2/3rds the way down in the "problems" chapter.

---

### Post by Fillibuster on 2007-04-03
So according to ALSA I have one of only two Creative cards that aren't supported.  Anyway to work around this or am I stuck waiting for the support from Creative?

---

### Post by freebird54 on 2007-04-03
I'm sorry - it doesn't look good, unless Creative actually comes through "2nd quarter 2007".  I guess that means 30 June, 07?

Hard to believe it has no fall-back modes at all - but that appears to be the case.

Might be nice when it does, though!

---

### Post by henry8596 on 2007-04-04
i have the same soundcard too
creative sound blaster X-fi
i bought it in 06 summer
i don't know if it is really now
but since i am a new ubuntu user, learning all the stuff, how to install...
it is sad to find out that X-fi doesn't have any driver suitable for ubuntu
especially i am a new user, really happy on learning how to use it
but anyway, right now we can just wait

---

### Post by vatechtigger on 2007-04-04
If creatives open source driver web page is any indication of the time and effort they plan to put into linux drivers, you might be SOL

---

### Post by freebird54 on 2007-04-05
Perhaps if everyone wrote a little note to Creative, expressing their disappointment that something they bought 'for their computer' requires and expensive add-on like Windows that isn't clearly specified as required.  (so what does the average person know about drivers - until too late?)

If there are enough of them coming in, it MIGHT get them to think.  After all  - many of the people who would like to USE all the features of their system are the same people who use Linux because of all the tweaking and features available there too!

AT least they might release enough information for a 'basic sound experience' driver (little proprietary information about their advanced featureset) to be written for them by the open source community :)

---

### Post by Garyu on 2007-04-05
X-Fi is an entirely new technology as I understand. I am no sound expert, but they say that this is about as big a leap as from 32 to 64 bits in a processor. 

Creative don't want to release linux drivers because they are afraid that people will hack them and understand how their sound processors work and copy the technology. As if you couldn't do that anyway...

Don't expect any drivers until July. Personally, I am going to buy a card exactly when the linux drivers are released. If enough people do what I do - that will send a much stronger signal than anything else... "Hey, we are making a lot more money when we release the linux drivers. Let's do that more often!" :)

---

### Post by kyphi on 2007-04-06
I use a Ceative Soundblaster card and it works perfectly in Ubuntu 6.06 where it is identified as a Dell Soundblaster Live.

If you do not hear any sounds at all when in Ubuntu, have you checked to see if sound has been enabled ?

System -> Preferences -> Sound.  Put a tick next to Enable software sound mixing (ESD).  At the bottom select your default sound card.

---

### Post by Garyu on 2007-04-06
> **kyphi said:**
> I use a Ceative Soundblaster card and it works perfectly in Ubuntu 6.06 where it is identified as a Dell Soundblaster Live.

You should read the contents of the thread before you post kyphi. The OP here has a Soundblaster X-Fi which is the newest card from Creative and lightyears ahead in technology. Your card (Live) is the best supported soundcard ever for Linux, partly because it is quite old. X-Fi will not be supported until (maybe) June/July.

---

### Post by kyphi on 2007-04-06
The question being asked initially was -

"... and I've heard from friends on another forum that there is no Linux support for Creative cards. Is this true?"

The answer is that it is not true.  Most of them are supported.

Since there is no support at present for this particular card, why not swap it for one that works in the interim - such as the SoundBlaster Live.  That way you can enjoy Ubuntu now.

Re old technology:
Although I have a SB Live in a spare computer, build date January, 1999, the one I currently use has a build date of March, 2006.  Not very old really and, yes, the card has changed and incorporated technological advances.

That the X-fi may sound better than the SB Live is quite likely.  It is aimed at the HomeTheatre and Gamers market.

My previous response was intended to be of help, as is this one.  So, keep it civil.

Cheers,
Kyphi

---

### Post by Lucifiel on 2007-04-07
There might be no official company support for Creative cards, however, you could always look for a solution yourself.

I use a Creative Audigy 2 Live Value card and it has no problems working at all.

---

