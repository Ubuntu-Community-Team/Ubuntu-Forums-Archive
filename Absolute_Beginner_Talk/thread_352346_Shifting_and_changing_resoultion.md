---
title: "Shifting and changing resoultion"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-02-03
Hi there,

When ever I open up an application that need the resolution to change - either a game in Wine or when I use VMware and go full screen, Ubuntu streches the screen in such a manner that the game or VMware does get the full screen. The only problem with this is that upon closing the app, the Ubuntu screen size stays the same stretched manner. I can only display 75% of the screen at 1 time - when I do move my mouse from side to side or bottom to top the screen shifts to follow it.

Has anybody had this? DO you understand what I'm trying to say?

Anyway - I'm looking for a solution other than restarting my computer becuase restarting X doesn't help.


Thanks for any help in advance!


Cheers,

Rudolf

---

### Post by tocleora on 2007-02-03
I've had a similar issue, it's not every time but occasionally only about 30% of the screen will show from a resolution change.  I don't load gdm when I boot up so I'm able to exit out of x all together and restart it to resolve the problem.  If you use gdm  I get the impression you're still kinda in x when that runs because things that leaving x should fix just going to the login screen doesn't fix.  Doubt this helps you any  but wanted to comment in case no one else has any advice.

---

### Post by RudolfMDLT on 2007-02-03
thanks - yeah - no one else has any comments!

---

### Post by ed-j on 2007-02-03
> **RudolfMDLT said:**
> thanks - yeah - no one else has any comments!

Novice Alert!

Try right clicking on the mouse perhaps?

---

### Post by RudolfMDLT on 2007-02-04
> **ed-j said:**
> Novice Alert!

Try right clicking on the mouse perhaps?:)

and then? I really tried most things?

---

### Post by ed-j on 2007-02-04
> **RudolfMDLT said:**
> :)

and then? I really tried most things?

Morning!

What kind of monitor do you have?

---

### Post by tocleora on 2007-02-04
> **RudolfMDLT said:**
> :)

and then? I really tried most things?

I think he's saying just change the resolution back by right-mouse clicking.  Only I don't have an option to change the resolution by right-mouse clicking.  You could click System > Preferences > Screen Resolution, only if your resolution is as small as mine you wouldn't be able to see all of it.  Maybe there's a shortcut for it or way to navigate your screen when it's that size.  And I'm assuming it's not truly a resolution (like that) issue because the screen is still it's normal 1280 x 800 I just only see the 30% of it, like I'm assuming is happening with you and your 75%.  

Here's a solution from a similar thread you might try:

```

ctrl+alt+F1
sudo /etc/init.d/gdm restart

```

---

### Post by ed-j on 2007-02-04
> **tocleora said:**
> I think he's saying just change the resolution back by right-mouse clicking.  Only I don't have an option to change the resolution by right-mouse clicking.  You could click System > Preferences > Screen Resolution, only if your resolution is as small as mine you wouldn't be able to see all of it.  Maybe there's a shortcut for it or way to navigate your screen when it's that size.  And I'm assuming it's not truly a resolution (like that) issue because the screen is still it's normal 1280 x 800 I just only see the 30% of it, like I'm assuming is happening with you and your 75%.  

Here's a solution from a similar thread you might try:

```

ctrl+alt+F1
sudo /etc/init.d/gdm restart

```

tocleora

My apologies, I did not think that right-clicking on the desktop would change Rudolf's predicament. My patience was caught off guard by his offensive "oh yeah, no more comments" and ".....Do you understand etc". His public statement about pitbulls is also a sick joke. I tried to inform a moderator about this today but as yet I have no reply. I apologize to you both for setting off a confused thread. Sorry, Novice Alert!

---

### Post by tocleora on 2007-02-04
> **ed-j said:**
> My apologies, I did not think that right-clicking on the desktop would change Rudolf's predicament. My patience was caught off guard by his offensive "oh yeah, no more comments"

I don't think he meant that in the tone you are thinking, it can be frustrating on this site to have a problem and get no response, but this is a GREAT forum for getting help and I too have found myself just not responding if I don't know the answer to the question.  I don't know what would be more frustrating, 0 responses or 10 responses saying "I don't know".  Or worse the 10th response is the answer to your question and you had to go through 9 "i don't know" responses to get to it.  So I've learned through experience with the site that no comment doesn't mean people are ignoring you, it just means that they don't know... but I was in his position not too long ago, just something that has to be learned. :)

Regarding the pitbull... I'm staying out of that one...

---

### Post by ed-j on 2007-02-04
> **tocleora said:**
> I don't think he meant that in the tone you are thinking, it can be frustrating on this site to have a problem and get no response, but this is a GREAT forum for getting help and I too have found myself just not responding if I don't know the answer to the question.  I don't know what would be more frustrating, 0 responses or 10 responses saying "I don't know".  Or worse the 10th response is the answer to your question and you had to go through 9 "i don't know" responses to get to it.  So I've learned through experience with the site that no comment doesn't mean people are ignoring you, it just means that they don't know... but I was in his position not too long ago, just something that has to be learned. :)

Regarding the pitbull... I'm staying out of that one...

Thanks for the reply and the advice! I truly am a novice, and yes,  I can learn to appreciate such things more fully. However, from my point of view, courtesy costs nothing whether you are paying for something or receiving it for free. Don't worry about the "pitbull", sense will prevail. Thanks again.

---

### Post by tocleora on 2007-02-05
So back on topic... Did that solution I respond with help? ;)

---

### Post by ed-j on 2007-02-05
> **tocleora said:**
> So back on topic... Did that solution I respond with help? ;)

I have no further post from RudolfMDLT but I am still keeping a Subscribed Thread.

---

