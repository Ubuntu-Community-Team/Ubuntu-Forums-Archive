---
title: "[SOLVED] Need Full Screen Help"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by condar_1 on 2008-04-07
I guess I don't have enough beans to be posting the main support catagories. LOL  At least I haven't gotten any response from there. 

I was hoping someone would help out with a full screen problem I an having. 

When I open a video in totem it plays fine.  When I double click the video to go full screen, my monitor shuts off and says "out of range". I'm sure that the player is changing the resolution automatically as it toggles into full screen mode.

I would like to know how to change this or maybe an alternate media player that will not give me this problem. 

Thanks for your help.

---

### Post by Hobo Joe on 2008-04-07
Use VLC.
```

sudo aptitdue install vlc

```

---

### Post by Inxsible on 2008-04-07
Could you please try the same video in VLC?

if you havent installed vlc, you can search for it in Synaptic and install it.

EDIT: Got beat, by Hobo Joe !!

---

### Post by condar_1 on 2008-04-07
Ok...

Remember I a newbie here.   3 weeks Ubuntu only.  What is VLC?  I'm assuming it's a media player of some sort....

Can you post a link of where I can download it from?

Sorry if I'm sounding to Bill Gates here.  I'm really trying to love linux and give Ubuntu a honest chance.  You have to remember I'm still in a DOS mindset here when it comes to droping command lines. 

Thanks

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> Ok...

Remember I a newbie here.   3 weeks Ubuntu only.  What is VLC?  I'm assuming it's a media player of some sort....

Can you post a link of where I can download it from?

Sorry if I'm sounding to Bill Gates here.  I'm really trying to love linux and give Ubuntu a honest chance.  You have to remember I'm still in a DOS mindset here when it comes to droping command lines. 

ThanksSorry about that. VLC is another media player. AFAIK, it can play almost anything you can throw at it.

Here's the link from Videolan (the makers of VLC) -- straight from the horse's mouth - so to speak.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by condar_1 on 2008-04-07
Great!  By the way, thanks for the fast posts.

Now, FYI; I'm running Ubuntu off the CD because one of my 2 hard drive took a dump.  That is actually why I went to Ubuntu.  My window xp install crapped out (hard drive failure) and it takes and act of God to recover windows. Anyway....

Will I have any trouble installing VLC being that I'm running Ubuntu from a CD?  

If so...  I have heard that there is a way to save your settings and programs even though you are booting from CD.  I don't know how but I have read it IS possible.

My new hard drive should be here in a few days.  Until then, I am just trying to watch a few movies and make do.

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> Great!  By the way, thanks for the fast posts.

Now, FYI; I'm running Ubuntu off the CD because one of my 2 hard drive took a dump.  That is actually why I went to Ubuntu.  My window xp install crapped out (hard drive failure) and it takes and act of God to recover windows. Anyway....

Will I have any trouble installing VLC being that I'm running Ubuntu from a CD?  

If so...  I have heard that there is a way to save your settings and programs even though you are booting from CD.  I don't know how but I have read it IS possible.

My new hard drive should be here in a few days.  Until then, I am just trying to watch a few movies and make do.
If you are using the Live CD, then you will have to install VLC everytime that you reboot. I don't think the Live CD's can write to the disks, so your VLC install won't be permanent.

Once you install however, you should be good to go. Infact, now that you said you are using the Live CD, Totem not playing in full screen is probably because you are not using the restricted drivers for your graphics card.

---

### Post by condar_1 on 2008-04-07
Inxsible... thank you Soooo much from your help with that.  I'm ok with VLC not being a permanant install.  I'm just trying to get by until my new hard drive gets here.  

I will try to install VLC in a few minutes and see what happens.

So....  what is a "restriced driver"?  I have never heard of that before in my days of windows.  As far as I was concerned, there were just "drivers".  They either worked or didn't.  Not that it really matters. I just curious. :confused:

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> Inxsible... thank you Soooo much from your help with that.  I'm ok with VLC not being a permanant install.  I'm just trying to get by until my new hard drive gets here.  

I will try to install VLC in a few minutes and see what happens.

So....  what is a "restriced driver"?  I have never heard of that before in my days of windows.  As far as I was concerned, there were just "drivers".  They either worked or didn't.  Not that it really matters. I just curious. :confused:As a philosophy of Open Source, Ubuntu does NOT come shipped with proprietary software. Restricted drivers simply mean drivers which have been created by a company who does not release the source code.

eg. NVidia is a company which creates graphics cards and writes the drivers for those cards. They also do not release the source code. Those drivers are called restricted in Ubuntu world.

Having said that, its not too difficult to enable the "restricted" drivers to get things working.

---

### Post by condar_1 on 2008-04-07
OK... I understand.  I see, Linux is very understandable.  Just takes some time.  I didn't learn Windows 3.11 - Vista overnight either. :) 

Interesting...

I know this a little off topic BUT...  

I didn notice that totem didn't have a graphic EQ or anything to tweek the sound of my audio files.  In return the sound was weak and thin.  Much much worst in overall sound quality vs. mediamonkey or window media player.  

Does VLC have those type of plugins or do you recommend an audio player that I can get some extra features for playing my mp3 collection?

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> OK... I understand.  I see, Linux is very understandable.  Just takes some time.  I didn't learn Windows 3.11 - Vista overnight either. :) 

Interesting...

I know this a little off topic BUT...  

I didn notice that totem didn't have a graphic EQ or anything to tweek the sound of my audio files.  In return the sound was weak and thin.  Much much worst in overall sound quality vs. mediamonkey or window media player.  

Does VLC have those type of plugins or do you recommend an audio player that I can get some extra features for playing my mp3 collection?

Using a separate audio player is a good idea, especially with specialized audio players which can maintain and manage your music collection. Mind you, VLC and totem are both capable of playing mp3 files (after you install the proper codec, that is)
But audio players like Amarok and Rhythmbox - clones of iTunes are great.
Audacious is similar to Winamp in Windows. I have never used Banshee, so I am not sure how that is. There are probably hundreds of other audio players out there, but the ones I mentioned are widely used.

---

### Post by condar_1 on 2008-04-07
Awsome!  A "Thanks" goes your way for all your help.

If I have any problems I may bump the thread in the next day or so.  

The people like you (inxsible) make me more and more comfortable switching to Ubuntu.

Thank you again for your help. I think it's great that you take your time to help out all of us (newbies).  I can only hope that I can pass along the help to someone in the future.  You rock man!! :guitar:

---

### Post by Inxsible on 2008-04-07
> **condar_1 said:**
> Awsome!  A "Thanks" goes your way for all your help.

If I have any problems I may bump the thread in the next day or so.  

The people like you (inxsible) make me more and more comfortable switching to Ubuntu.

Thank you again for your help. I think it's great that you take your time to help out all of us (newbies).  I can only hope that I can pass along the help to someone in the future.  You rock man!! :guitar:awww Shucks !!

We all do what we can !

Welcome to the world of Ubuntu. I hope you love it here as much as I do :)

---

### Post by condar_1 on 2008-04-07
> **Inxsible said:**
> awww Shucks !!

We all do what we can !

Welcome to the world of Ubuntu. I hope you love it here as much as I do :)

Ok... don't get sweet on me.  :)

---

