---
title: "back to dapper from edgy"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by montonec on 2006-11-29
is it possible or i'd better install dapper again from scratch?

---

### Post by PartisanEntity on 2006-11-29
Actually I was thinking the very same thing myself last night, whether it is possible to 'sudo apt-get downgrade'. (I am using Dapper and am very happy with it, so for me it is just a theoretical question).

---

### Post by xyz on 2006-11-29
Sorry but the answer is no!
But check **jgcamp99's links**
[HERE]("http://www.ubuntuforums.org/showthread.php?t=286785&highlight=sudo+apt-get+downgrade")
or fresh install Dapper - SAVE your data...good luck!

---

### Post by Oki on 2006-11-29
I installed Edgy but was not happy, there was to many bugs. So I installed Dapper Drake again - and been happy since. 

Do you know if there ever will be another LTS version after Dapper Drake? And will also next Ubuntu relise bee "edgy" and not stable?

---

### Post by Steve S. on 2006-12-02
> **Oki said:**
> I installed Edgy but was not happy, there was to many bugs. So I installed Dapper Drake again - and been happy since. 

Do you know if there ever will be another LTS version after Dapper Drake? And will also next Ubuntu relise bee "edgy" and not stable?

Would you tell us why you didn't like Edgy?  An anyone else for that matter that didn't like Edgy.

I'm VERY happy with Dapper, and I have it highly customized, but am thinking about upgrading.  I'm wanting to know what everyone thinks and whether or not an upgrade is worth it.

---

### Post by jingo811 on 2006-12-02
I think Ubuntu Corporations has failed on this subject.  They shouldn't have their latest release so easily accessible for newcomers who has never Linux:ed before.
I didn't grasp the concept of universe etc. until I had gone through 5+ OS re-installs.  New Windows/Linux users still think in a Bill Gates kind of way.

The newer the more fixed and patched it is.  But that's not how Linux works instead the motto here is:
The newer the more unstable!

What worked previously might not work with an upgrade.

---

### Post by Steve S. on 2006-12-02
> **jingo811 said:**
> I think Ubuntu Corporations has failed on this subject.  They shouldn't have their latest release so easily accessible for newcomers who has never Linux:ed before.
I didn't grasp the concept of universe etc. until I had gone through 5+ OS re-installs.  New Windows/Linux users still think in a Bill Gates kind of way.

The newer the more fixed and patched it is.  But that's not how Linux works instead the motto here is:
The newer the more unstable!

What worked previously might not work with an upgrade.

Um, not sure about all your comments.  I've been through a couple of upgrades myself...I started with Hoary.

I don't view it from a Winbloze perspective, just want to know if it is worth switching, if there is anything in Edgy that just says, man, you should switch!  When I went from Hoary to Dapper it was worth the switch...

But, as I understand it, your overall view is that it may not be worth it if I like Dapper, yeah?  Is Edgy really worth it is my question.

I know it is an opinion question, but I just want to know what the general consensus is.

---

### Post by agonoruci on 2006-12-02
I believe Edgy is a solid upgrade, some stuff did not work for me in the beggining so I began fishing for some more programs/codecs and I've got everything I want now, If you have a problem with something just ask on the Forum thats what I did, because Edgy is perfects it's just that I had to take the time to get some stuff that will hopefully come by default in the next upgrade of Edgy.

---

### Post by Papa-san on 2006-12-02
THERE IS A REASON THIS IS POSTED!!!!

[http://www.ubuntuforums.org/showthread.php?t=286209](http://www.ubuntuforums.org/showthread.php?t=286209)

There is also a reason it is titled IMPORTANT!

Read on:

I made the Ubuntu jump the wrong way about a year ago:
I got frustrated for the last time with the whole windows crashing thing, and the need for spending more money to fix it.. AGAIN...

So, I burned 'breezy 5.10 install' to a disc... I didn't even bother with the live CD... I was DONE with windows...

It was a HARD adjustment, but I survived it. Eventually I upgraded to Dapper, and was OK with it except that my video card isn't properly supported. (Even still...)

I was excited about edgy due to the problems I had with Dapper, so I installed it as soon as I could...

I soon discovered that this was a mistake. There was no way to get the wireless working, my video card issue had me locking up within minutes of booting. Answers in the forums weren't coming because it was too new for many people to have become familiar enough with it. (I guess... I just know I posted three or four topics that still haven't had a response...)

I went back to breezy. This made it easy enough to set it all back up, as I had done it before. Then I went through the apt-get upgrade to get the LTS version loaded, but this time I knew what answers to give when it asked if I wanted to keep custom settings, or install the new stuff!

I know the admins have tried, and have posted sticky's that warn people. The problem is that so many people don't read them...

There are specific warnings that Edgy shouldn't be a 'First Step' into the linux world... 

If you do not have experience with a previous distro, DON'T INSTALL IT AS YOUR PRIMARY OS...

Start with Dapper, as it has the long term support. Yes, some people will have it work for them on the first shot, but a significant majority will have hardware issues, or knowledge issues, etc... Please give them time to iron out some of the wrinkles!

---

### Post by Oki on 2006-12-02
Papa-san: 

If you go to the download site for Ubuntu ([http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)), there are no information that Edgy is "Edgy", it is presented as the latest version. And it dos not stand that you should read a thread on a forum before chooisng your distro. And you know most people are telling that Edgy is as stable as Dapper D. now. 

Nothing wrong to ask how to downgrade in "Absolute Beginner Talk" imho.

---

### Post by HokeyFry on 2006-12-02
cant you change all the words "edgy" to "dapper" in /etc/apt/sources.list   and then run

```
sudo apt-get update
sudo apt-get upgrade
```

i thought this would successfully downgrade your system

---

### Post by Papa-san on 2006-12-02
I wasn't saying there was anything wrong with asking your question... It's a good question.

Neither was I trying to bag on the OP or anyone else that has run into this. I am simply stating that it would be nice if the 'Powers that Be' could have some consistent warnings and fuller explanations, especially on the download pages. 

Open Source is awesome because of what is trying to be done. One of the problems is, however, that so many people are working on it, that things just don't flow so smoothly, like a disclaimer on the downloads page that leads to a relavent page that offers an explanation of these things.

I don't know how to make this all work, but this is one thing that keeps closed source stuff going... One page or site that can convey the relavent information clearly to Everyone who shows up.

(Whether or not they read the information is up to them, and the problems created by their ignoring it should be addressed as they seek help so that they might do their homework FIRST next time instead of afterwards...

No offense was intended!

---

### Post by Caraibes on 2006-12-02
I wiped Edgy from my laptop and came back to Dapper, because of the issue with Skype : whenever I turned Skype on, the laptop would freeze !

There was nothing in Edgy that was so much better that Dapper, so I just re-installed from the cd...

This was Xubuntu Dapper, alternate install, and Automatix...

I am very happy to be back to Dapper, it makes me feel like sticking to LTS releases...

---

### Post by Steve S. on 2006-12-02
Wow, didn't know anything about that warning thread...thanks for the info.

I'll stick with Dapper, as I love it and no one has said, "Oh, man, have you tried the [insert newest cool thing here] in Edgy!  Amazing!"

When someone posts that in a thread, then I'll upgrade.  Thanks.

---

### Post by flyingsolo on 2006-12-02
I wonder if the warning sticky regarding Edgy is perhaps less relevant with the passage of time and Edgy gets its updates/corrections/improvements.  It has worked well on my laptop though broadcom wireless isn't yet working (but Dapper wasn't successful  either!) I'm VERY happy with Dapper on a six year old Dell desktop but trialling Edgy on new laptop.  No problems with Skype, Democracy player, Amarok, Kino (some of my fav's!)on either Edgy or Dapper.
Just my 2 cents.

---

### Post by Steve S. on 2006-12-02
> **flyingsolo said:**
> I wonder if the warning sticky regarding Edgy is perhaps less relevant with the passage of time and Edgy gets its updates/corrections/improvements.  It has worked well on my laptop though broadcom wireless isn't yet working (but Dapper wasn't successful  either!) I'm VERY happy with Dapper on a six year old Dell desktop but trialling Edgy on new laptop.  No problems with Skype, Democracy player, Amarok, Kino (some of my fav's!)on either Edgy or Dapper.
Just my 2 cents.

Just the mention of wireless not working makes me leary.  I've got dapper set up to run a linksys to a cantenna settup to pick up the router in the other room and it has worked great since Hoary...actually wireless ease was the reason I picked Ubuntu over other distro's in the first place.

Hopefully your right and edgy will get better reviews as time marches on...

---

### Post by cytutchi on 2006-12-02
yeap...
i was also downgraded from edgy to dapper again...
i was new also in dapper n then edgy came out...
off course wanted to try out the latest technology and the latest software support but as already said it was so difficult n so much time just to get smthing workin...or it was just me that it was taking me so much time to make it work....
but many bugs...simple but all added up 4 me to go back to dapper and be happy! :)

the DapPer world is nice....more simple n more stable...at least for newbies!

njoy people whatever you have n dont forget to expiriment n contribute back since what you got was also free ok?...giving n receiving!

c ya!

---

