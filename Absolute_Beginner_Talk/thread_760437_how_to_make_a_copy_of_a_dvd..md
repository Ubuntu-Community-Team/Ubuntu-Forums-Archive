---
title: "how to make a copy of a dvd."
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-20
I have a trip comming up this weekend.  I am going to be chaperoning a bus trip for the local HS Band.  I live in Central PA.  We are going to Virginia Beach.  Gonna be a long time in the bus.  They have dvd players in them.  I want to make a copy of a few of my movies to play on the way down and back to pacify the rowdy beasties:).  I do have a pair of dvd burners installed in the machine.  I guess it's time to see if they work.

Just want to know how to copy the dvd's and what programs to use.  I do have the Gnome and KDE desktops installed if it matters to you guys.  I'm trying to learn how to use both.  Any help would be appreciated.

Mark Shuman

---

### Post by forrestcupp on 2008-04-20
A program called k3b is excellent at burning and copying CD's & DVD's.  I'm not sure about getting around commercial DVD copy protections schemes, though.

---

### Post by freduardo on 2008-04-20
I'd recommend k9copy for that.

```
sudo apt-get install k9copy
```

It's pretty easy to use and very intuitive

---

### Post by mikeyphi on 2008-04-20
Several DVD rippers available through Add/Remove

---

### Post by sailor2001 on 2008-04-20
google  dvd43

---

### Post by Vuddha on 2008-04-20
Definitely k9copy. I haven't met a DVD I couldn't copy yet (even the new ones).

I like to burn with Brasero.

---

### Post by phread59 on 2008-04-20
Is the copy protection gonna be a problem?  I figured it would be.  If so how do you work around it?  Does K9copy take care of it, and can it burn the new DVD or do I need a seperate burner?  I'm a ereal Neophyte at this game.  I talked to a coupla guys at work.  They run Widughs.  They probably could get me there with Windows but I really would love to reformat the hard drive with it on and put something else on it!!!  I may need my hand held here.  I'm gonna do some research on K9copy and see where it leads and come back here later on this afternoon.  Thank you for the help.

Mark Shuman

---

### Post by freduardo on 2008-04-20
Just use k9copy for ripping (and shrinking so it would fit on a normal dvd-r) and k3b or brasero for burning.

K9copy should take care of the copy protection. 
Just like Vuddha, I haven't had any problems with it either.

---

### Post by indytim on 2008-04-20
Mark,

Unfortunately, you live in the U.S.A (based on your signature).  The long and short of it is, by the letter of the law, what you want to do is illegal.  Our genius's in Washington have set copying dvd's as illegal, even if you own the original.

IndyTim

---

### Post by freduardo on 2008-04-20
> **indytim said:**
> Mark,

Unfortunately, you live in the U.S.A (based on your signature).  The long and short of it is, by the letter of the law, what you want to do is illegal.  Our genius's in Washington have set copying dvd's as illegal, even if you own the original.

IndyTim
Aha,
I didn't know that.

Sorry for luring you to 'the dark side' Mark ;)

---

### Post by Hallvor on 2008-04-20
> **phread59 said:**
> Is the copy protection gonna be a problem?  I figured it would be.  If so how do you work around it?  Does K9copy take care of it, and can it burn the new DVD or do I need a seperate burner?  I'm a ereal Neophyte at this game.  I talked to a coupla guys at work.  They run Widughs.  They probably could get me there with Windows but I really would love to reformat the hard drive with it on and put something else on it!!!  I may need my hand held here.  I'm gonna do some research on K9copy and see where it leads and come back here later on this afternoon.  Thank you for the help.

Mark Shuman

For copy protected DVDs, just transcode the movie with VLC media player. It is the only native player able to backup *anything* that plays on it. :)
k9copy will not copy some copy protected DVDs.
For Gnome/XFCE I`d run an application called dvd95 (sudo apt-get install dvd95), or k9copy for KDE (sudo apt-get install k9copy)
Bottom line: Use VLC for anything that fails on dvd95 or k9copy.

---

### Post by phread59 on 2008-04-20
Thanks guys, I tried to burn a copy of Pirates of the Caribbean 2 tonight using K9 and failed miserably.  It spent 2 hours ripping the dvd and failed when it tried to burn.  All kinds of error codes.  I believe I used the wrong settings somewhere.  I downloaded some tutorials tonight.  I'm going to bed and will give it another go tomorrow after work.  

I do understand the law here.  I am fully cognizant that what I want to do is really a  gray area.  It is the wife's dvd.  So I really don't want to take an original with me.  Having kids getting access to her dvd and ruining it would make home life real bad.  It was purchased by me and the copy is for me and not to be given away or sold.  I do feel justified in doing this.  I don't want to steal DVD's.  I just want a disposable copy of a coupla movies for a school trip.

Mark Shuman

---

### Post by crjackson on 2008-04-20
> **Vuddha said:**
> Definitely k9copy. I haven't met a DVD I couldn't copy yet (even the new ones).

I like to burn with Brasero.

It won't work on all.  It couldn't handle "Gone Baby Gone" for me today...  In fact, it won't even play.

I keep a dual boot system just because of video editing and DVD video backup aren't up to snuff for Linux yet...

For what it's worth, DVD95 is GREAT when the DVD can be decrypted...  It's less complicated so you may want to give that a go.

---

### Post by Afkpuz on 2008-04-20
Solution: 
1.) buy a cheap cd carrying case.
2.) Remove the movies you think the kiddies will like from your collection and place in the carrying case
3.) Take carrying case onto the bus
4.) Play DVDs on bus using actual discs (This however is also illegal cause more than 5 people are watching and it's considered a public viewing.  Crap!)


In all seriousness, I'll throw it out there that I have backed up some of my movies by simply right clicking on the DVD drive and selecting "Copy Disc".  Then, chose "File Image" instead of a dvd burner for the destination.  This will create an exact ISO copy of the disc.  you can watch these in VLC.  It copies the whole thing with encryption included ( I think).  These files are big.  Like 7+ Gigs, so you need the big sized DVDs.  I've never tried burning those ISOs to a DVD, but I know that it's very easy to get a straight up ISO.  Take that for what it's worth

---

### Post by crjackson on 2008-04-20
> **Hallvor said:**
> 
Bottom line: Use VLC for anything that fails on dvd95 or k9copy.

Doesn't work with some new protections.  It can't play or rip "Gone Baby Gone".

---

### Post by Hallvor on 2008-04-21
> **crjackson said:**
> Doesn't work with some new protections.  It can't play or rip "Gone Baby Gone".

It will rip anything it can play, but it it can`t play there is a problem. Perhaps I`ve just been lucky, but I have backed up a lot of copy protected DVDs and never had a problem with VLC.

---

### Post by billgoldberg on 2008-04-21
> **indytim said:**
> Mark,

Unfortunately, you live in the U.S.A (based on your signature).  The long and short of it is, by the letter of the law, what you want to do is illegal.  Our genius's in Washington have set copying dvd's as illegal, even if you own the original.

IndyTim

That's just stupid.

I'm glad the "lobbies" don't have that power here.

---

