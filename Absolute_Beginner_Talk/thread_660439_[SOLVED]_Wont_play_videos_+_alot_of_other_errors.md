---
title: "[SOLVED] Wont play videos + alot of other errors"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Aaronought on 2008-01-06
ok, i have a .WMV on my desktop and i double click on it TOTEM wont even open it

so i installed VLC player and it plays for like 30 seconds.

then the player will go black and white and when i try to quit i have to press force quit.

while it is black and white the video still plays.

oh and no video i play has sound. thats another problem i have.

anybody know whats happening? and a fix?

onto another thing that isnt right now i have flash working but firefox just stops responding whenever i go anywhere with flash on it.

im not having much luck with this at all lol but i am liking liinux its great lol.

i dont know what i need to tell you cos im such a newb ill give it you just tell me what you need

---

### Post by eapache on 2008-01-06
Installing Ubuntu-Restricted-Extras from Applications>Add/Remove should fix your problems. If you've already done this (or the problems persist), please list your video card. Also try disabling Desktop Effects under System>Preferences>Appearance.

---

### Post by Aaronought on 2008-01-06
its a radeon 9600

disabling desktop effects now.

edit: restricted extras is installed

---

### Post by Aaronought on 2008-01-06
sorry just noticed my profile was saying that i was running kubuntu but im not, im running ubuntu

---

### Post by 1337455 10534 on 2008-01-06
If that video is corrupted, then this is to be expected. If its incomplete (eg it was torrented halfway) then this normally happens. If VLC cant handle it, I cant think of *anything* that can...

On an unrelated note, I was random-article searching in Wikipedia and I found a video format called CorePNG. Is there any such thing as a a video format converter for Linux?? CorePNG sounds like something I want to try very much!!

About your sound issue, its possible that your sound card is not supported or that the sound is being played from the wrong devices.. Check if you have headphones plugged into your computer.
Also, go to sytem- preferences - sound and run those tests.
If it doesn't tell you what your sound card is from there, you have a problem.

---

### Post by Aaronought on 2008-01-06
well i can say that it works in windows in WMP

i mean if you want i can upload it for you to try... 

it isnt illegal or anything just a video of a guy juggeling hamers  but they hammer a nail into the roof...

if that made sense =/

---

### Post by 1337455 10534 on 2008-01-06
Then I have no idea why its messing up. Sorry :(/

---

### Post by Aaronought on 2008-01-06
oh well, Thanks anyway pal

Heres the video

[http://rapidshare.com/files/81861368/turbo_juggling.wmv](http://rapidshare.com/files/81861368/turbo_juggling.wmv)

---

### Post by mdpalow on 2008-01-06
LOL. :)

That was a pretty good video! 

Works for me fine. I know you said you installed the restricted files, but I find a lot of people who say that, but didn't install them all or the right ones.

Check out my signature links below. They should get you going in no time.

Good luck...

---

### Post by Aaronought on 2008-01-07
lol yea i thought it was great but he has soo much wastd time lol.

anyway back to my problem lol.

your program works to a certain extent. it now plays in TOTEM but gets to like 43 seconds and stops
and goes grey.

VLC does the same as before.

and dthere still no sound lol

---

### Post by eapache on 2008-01-07
Very peculiar. Try running totem from the command line and see what output it gives```
totem
```

---

### Post by mdpalow on 2008-01-07
This might be a tough one to try and figure out over messages. There are just so many variables:

Did you do a fresh install of Ubuntu 7.10
Did your sound work before or does it work on everything else
Do you have other movies that do work
What did you install that might have caused this problem
Does your video card show up in the forums as being problematic
How much RAM do you have and did you create a swap drive when installing Ubuntu
Are you using a separate sound card or is it built into the motherboard
Are you using 32-bit or 64-bit Ubuntu

as you can see - several variables we're dealing with...

Here's my recommendation for whatever it's worth:

Since it only takes about 15 minutes to install Ubuntu 7.10 and isn't too bad with the updates, why not do a fresh install. Then get your OS looking like you want before adding any additional applications. Then download QuickStart from my signature below and install FLASH stuff, DVD / Codecs files, and whatever else you want. Then use QuickStart to back-up your system. All of that won't take more than another 10 minutes. Save your back-up files somewhere else.

Then test your ability to play the movie and have sound. If all is good - then you can move on with installing other stuff. However, after each app. install, test the movie again to see if you can identify which, if any, app. is causing the problems. At this point, if anything goes wrong, you can recover your whole system in about 20 minutes total; that includes having all your updates and configurations you made.

If it doesn't work after a fresh install and adding the flash/dvd/codecs stuff then it might be easier to narrow it down to your video card and/or sound card/chipset.

Hope this helps....

P.S. right now theres definitely something going on because when I or everyone else, that I know of, has used QuickStart to install the Flash and DVD/Codecs; it works fine. Assuming you don't have a hardware issue, it should work for you too.

Let us know what you decide to do...

---

### Post by Aaronought on 2008-01-07
> **mdpalow said:**
> This might be a tough one to try and figure out over messages. There are just so many variables:

Did you do a fresh install of Ubuntu 7.10
Did your sound work before or does it work on everything else
Do you have other movies that do work
What did you install that might have caused this problem
Does your video card show up in the forums as being problematic
How much RAM do you have and did you create a swap drive when installing Ubuntu
Are you using a separate sound card or is it built into the motherboard
Are you using 32-bit or 64-bit Ubuntu

as you can see - several variables we're dealing with...

Here's my recommendation for whatever it's worth:

Since it only takes about 15 minutes to install Ubuntu 7.10 and isn't too bad with the updates, why not do a fresh install. Then get your OS looking like you want before adding any additional applications. Then download QuickStart from my signature below and install FLASH stuff, DVD / Codecs files, and whatever else you want. Then use QuickStart to back-up your system. All of that won't take more than another 10 minutes. Save your back-up files somewhere else.

Then test your ability to play the movie and have sound. If all is good - then you can move on with installing other stuff. However, after each app. install, test the movie again to see if you can identify which, if any, app. is causing the problems. At this point, if anything goes wrong, you can recover your whole system in about 20 minutes total; that includes having all your updates and configurations you made.

If it doesn't work after a fresh install and adding the flash/dvd/codecs stuff then it might be easier to narrow it down to your video card and/or sound card/chipset.

Hope this helps....

P.S. right now theres definitely something going on because when I or everyone else, that I know of, has used QuickStart to install the Flash and DVD/Codecs; it works fine. Assuming you don't have a hardware issue, it should work for you too.

Let us know what you decide to do...

Well i thought id answer your questions and do a clean istall like you suggested so here goes


Did you do a fresh install of Ubuntu 7.10
[COLOR="RoyalBlue"]Yes, I created a 100gb Partition on my 400gb SATA HDD[/COLOR]

Did your sound work before or does it work on everything else
[COLOR="RoyalBlue"]I hear the login sound when i log in and XMMS plays a .wav i have on my desktop[/COLOR]

Do you have other movies that do work
[COLOR="RoyalBlue"]No.[/COLOR]

What did you install that might have caused this problem
[COLOR="RoyalBlue"]Compiz? the only things ive installed is Compiz and a couple of addons (cube atlantis, 3d windows) VLC player, flash, DVD codecs, XMMC and thats it i think      [/COLOR]

Does your video card show up in the forums as being problematic
[COLOR="RoyalBlue"]Not Sure i dont think so ill search after i post.[/COLOR]

How much RAM do you have and did you create a swap drive when installing Ubuntu
[COLOR="RoyalBlue"]I have 1gb (1024mb) DDR memory and i created a 100mb swap partition. i wasnt sure how big it needed to be.[/COLOR]

Are you using a separate sound card or is it built into the motherboard
[COLOR="RoyalBlue"]Its an onboard sound card.[/COLOR]

Are you using 32-bit or 64-bit Ubuntu
[COLOR="RoyalBlue"]32-bit Ubuntu[/COLOR]


Now then ill give it half an hour or so before i fresh install just incase the solution springs up lol.

Oh and i seriously appreciate you help pal


@eapache

When i execute it TOTEM gui apears the goes grey (not responding)

---

### Post by Aaronought on 2008-01-08
This is fixed now and all errors are gone.

It was probably my fault for only giving linux 100mb swap file lol.

a clean install with 2gb of swap file has made it much better.

QuickStart has sorted my video and flash out and they work perfectly.

Thanks!

Aaron.

---

