---
title: "Stuffed Drake A L'Orange"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by John Murphy on 2006-08-29
Once again it seems that yet another Linux romance is at an end after only 3 days!

I finally had things almost the way I wanted them Opened a program and the system crashed - zero response from the keyoard. Had to Hard Shut down. On reboot the whole kernel is messed up from what I can see - cannot connect to the internet. Open menus or drag windows is like taking Muchrooms Acid and Mesculin all at the same time and looking at a Photograph.....

It's as if the window is made from rubber!!! What a mess!

Need I say it - I need help fast!!! Thanks in advance

---

### Post by Toxicity999 on 2006-08-29
Windows like rubber? Congrats you just attained a natural Compiz! haha... Bad joke... anyway... Need a little more info than that. You had to of done SOMETHING for you internet module and other modules to not respond and/or load entirely... it couldn't of been just opening a program.

---

### Post by John Murphy on 2006-08-30
Complete mess - The Drake is dead and now being served a la Peking in Lee Ho Fuk!!!

Back to WindA$$ unfortunately until my Mac gets here - with any luck it'll be this week

---

### Post by Toxicity999 on 2006-08-30
Will if your just killing time till the mac shows up play with some more distros. Even if you don't stick with them you'll learn alot. And if you have nothing else to do. That's always good.

---

### Post by Tomosaur on 2006-08-30
How about telling us what program caused the crash? It could be a nasty bug, or maybe you just did it wrong. Giving up helps nobody :/

---

### Post by John Murphy on 2006-08-30
Toxicity - good Point Bro'!!!!

I wish I knew but I always get this - Same happenes with SuSE when trying to configure my mouse.

All I remember from this particular install was

aMSN - latest version, configured no Problem
Skype - any version but the latest beta gave sound problems
Evolution installed, configured pulling down hotmail and used a debian beta for Spam-killer called PopFile which really was doing a great job before the crash. Had Maya installed but I think this is what led to the crash. Ubuntu does horrible things with hotkey shortcuts such as assign the ALT button to stupid little things like moving the window around the desktop - you can do that with the mouse alone so why tie up the alt utton into the bargain.

Everything seemed okay

I had configured y 5-button mouse and it seemed to be working okay but none of the Maya functions like 'undo' were workin.

I soon discovered why... Although I had origially configured my keyboard as ritish english it now wanted to be Spanish, On the next reboot it was German!!!!

When I tred to ende text into web forms it was nonsense - just characters and the 'e' key didn't work

Eventually I changed the keyboard to British and unticked the ALT handler for windows and launched Maya

For 3 minutes and no more I had the system as I wanted it.......

Suddenly the System just locked up - couldn't use the keyboard and had no choice but to hard shut-down.

On reboot my windows had turned to rubber - clothes blowing round on a washing line would be a better description. The keyboard language was once again - rubbish!

No internet connectivity

Maya wouldn't open because of some layer error message

I replaced the xorg.conf origonal (but stupid me forgot to back up fstab previously....) I rebooted again and well it was not a pretty picture - The Drake was Dead!!!!

That's it as best I can remember............ Had a kernel for all of 3 Days! Amazing!!!!

I'm quite sure X was messed up too - I had the same deal also with SusSE - You get a kind of Grey Screen straight after the nVidia on start up [I reconfiguredthe nvidia mod to nvidia etc]
I needed the advanced 3d settings and OpenGL which dont load with te default driver setting..

---

### Post by Toxicity999 on 2006-08-30
that's completely insane... that's a true horror story... I'm not even entirely sure how to respond to that... Ehm... Could it be your Locale setup just began a path of self mutilation and the way you have you're internet connectivity set up it relys on a correctly set Language? Could it be that you just have some odd keyboard that ubuntu can't detect correctly and it jumps all around? (someone help me out here does it attempt to detect the language of the keyboard layout everytime it sees what it thinks is a new keyboard?) Try with some different peripherals that work out of the box perhaps on that front. As for the graphics so much can go wrong there, I know for me when I tried to be the rebel and see if FGLRX would do anything for my old Radeon 7500 I got distortion like that so that in itself is entirely probably to just be a video error. Now... It's also possible that hard reboot of yours happened at just the right time to mess up something in particular, who knows there... But the fact that you say this type of thing happens accross very different distros is what really confuses me here. Leaving only one possible conclusion of some bit of hardware fighting with the kernel or something generally included on those distros you've tried.

I'm baffled and shooting in the dark.

---

### Post by jimrz on 2006-08-30
> **John Murphy said:**
> Once again it seems that yet another Linux romance is at an end after only 3 days!

I finally had things almost the way I wanted them Opened a program and the system crashed - zero response from the keyoard. Had to Hard Shut down. On reboot the whole kernel is messed up from what I can see - cannot connect to the internet. Open menus or drag windows is like taking Muchrooms Acid and Mesculin all at the same time and looking at a Photograph.....

It's as if the window is made from rubber!!! What a mess!

Need I say it - I need help fast!!! Thanks in advance


How many more of these whiney little stories do you plan to post before you FINALLy take your little troll self back to where ever you came from?

Have a lovely trip...no need to write

---

### Post by John Murphy on 2006-08-30
> **Toxicity999 said:**
> that's completely insane... that's a true horror story... I'm not even entirely sure how to respond to that... Ehm... Could it be your Locale setup just began a path of self mutilation and the way you have you're internet connectivity set up it relys on a correctly set Language? Could it be that you just have some odd keyboard that ubuntu can't detect correctly and it jumps all around? (someone help me out here does it attempt to detect the language of the keyboard layout everytime it sees what it thinks is a new keyboard?) Try with some different peripherals that work out of the box perhaps on that front. As for the graphics so much can go wrong there, I know for me when I tried to be the rebel and see if FGLRX would do anything for my old Radeon 7500 I got distortion like that so that in itself is entirely probably to just be a video error. Now... It's also possible that hard reboot of yours happened at just the right time to mess up something in particular, who knows there... But the fact that you say this type of thing happens accross very different distros is what really confuses me here. Leaving only one possible conclusion of some bit of hardware fighting with the kernel or something generally included on those distros you've tried.

I'm baffled and shooting in the dark.

Yeah Tox - it looks like it's come down to something like that - fully cannot figure it out. I've been trying to run them oth on a Dell Inspiron 8600 and my guess is there's some conflict with the kernel when tring to configure the graphics card FeForceGo 5600 with the 'nvidia' nodule as opposed to the 'nv'. I'm thinking it has to be one very specific piece of Hardware to crash it the same way on 2 differnent distros and unfortunately this being a laptop I haven't too many options!

Sadly need the 'nvidia' for 3d apps among other things...

Thanks again for your input unlike some others here

============================================================



And jimrz - if this is too adult for you 'try closing your' eyes otherwise go take a hike and stop flaming!!!

---

### Post by Toxicity999 on 2006-08-31
I found a few pages to reference specific to your system though some of them the hardware has changed since you bought yours apparently (dells notorious for doing that and pissing off the peopl who buy their units!)

[http://www.koeniglich.de/dell_8600.html](http://www.koeniglich.de/dell_8600.html)
[http://folk.uio.no/staalep/i8600/](http://folk.uio.no/staalep/i8600/) (This one has your vidoe card.)

On that second page skim down to remaining issues and read that the 'latest' (at the time of that printing) drivers do NOT work with that card. I assume without reading much more you have to use an older version pre regression to fic that, more details on the page. Like I mentioned though you have a nvidia our issues are the same, but Radeon 9000m doesn't like hte more recent drivers. some kind of regression took place.

Whenever you have a carbon copy machine or something from a large company that 's popular just google 'Linux "Inspiron 8600"' excluding the outer 'seses of course. The second page seems to equal your specs anyway. Might need to append it to Ubuntu I didn't catch which OS they used only skimmed it.

Enjoy, And good luck!

To the person who was a complete idiot above. Someone was asking for COMMUNITY support from a COMMUNITY using a COMMUNITY based Distro... Do you see the continuity there? When people have problems they Post on the SUPPORT forums for SUPPORT... again... look a pattern. Go back to windows if you have the all for me attitude. Ubuntu is about the community spirit, something you most apparently lack. There's no reason to be on a support forum unless you have answers to give or ask. I repeat, Rethink your attitude to someone who wasn't Whining as you say, but telling a story of their issue. You added nothing to the conversation but posted anyway. THAT Is somethign a 'Troll' Does.

---

