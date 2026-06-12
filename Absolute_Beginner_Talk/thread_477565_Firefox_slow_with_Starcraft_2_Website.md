---
title: "Firefox slow with Starcraft 2 Website"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by Hasen_A on 2007-06-18
Has anyone else had problems with the firefox browser when viewing Blizzard's new website of [Starcraft2]("http://www.starcraft2.com")?

My browser is pretty slow when viewing the site. Symptoms:
[LIST]
[*]Slow scrolling
[*]Browser crashes
[*]The site is also displayed wrong at certain points
[/LIST]
The worse is when I scroll down near the image at the bottom, where amoveable picture of space is visible behind the background.

Any hinters on how to fix this? I haven't found anything under google. I'm guessing maybe an option of my firefox may be causing the problem.

Thanks in advance

---

### Post by starcraft.man on 2007-06-18
> **Hasen_A said:**
> Has anyone else had problems with the firefox browser when viewing Blizzard's new website of [Starcraft2]("http://www.starcraft2.com")?

My browser is pretty slow when viewing the site. Symptoms:
[LIST]
[*]Slow scrolling
[*]Browser crashes
[*]The site is also displayed wrong at certain points
[/LIST]
The worse is when I scroll down near the image at the bottom, where amoveable picture of space is visible behind the background.

Any hinters on how to fix this? I haven't found anything under google. I'm guessing maybe an option of my firefox may be causing the problem.

Thanks in advance

Uh, well the reason it performs less well is that the entire thing (with exception of like a few links) is flashed based (right click on things to see). I can easily tell cuz no scripts blocks the flash unless I allow it. I see what you mean by a bit of trouble scrolling, its not that noticeable on my comp though, what are your specs please, its probably just too much flash/movie at the same time for your computer to handle all at once (it is the entire page after all).

Honestly, I despise sites like these (sorry Blizzard, you got me upset again) they have no respect for those with less bandwidth/less power and for the most part are a waste of time. When I go to a site, I don't think I should ever have to wait for anything to load like flash trailer/intro, the information should just be there easy to get in 2 clicks or less no wait/slowdown. That said, its designed for gamers I suppose, flashy like and expecting them to spend time oogling at the trailers...

---

### Post by tgm4883 on 2007-06-18
Either im seeing a different website or something else.  Mine is fast, and not flashed based.

There is a link to the flash based site though.

---

### Post by starcraft.man on 2007-06-18
> **tgm4883 said:**
> Either im seeing a different website or something else.  Mine is fast, and not flashed based.

There is a link to the flash based site though.

Hmmm, interesting. Mine defaulted to flash based and yours to non... I dunno. I did just notice however the "toggle flash" button, hadn't noticed that before. Push that Hasen and you should see a better performance, its right under the 3 smaller tailer images, it will toggle all the flash off. I guess Blizzard not so bad, I'd prefer if I had been asked for flash or not though before loading the page...

---

### Post by Hasen_A on 2007-06-19
> **starcraft.man said:**
> what are your specs please, its probably just too much flash/movie at the same time for your computer to handle all at once (it is the entire page after all).

My computer specs should be fine: Athlon 3,5+Ghz; ATI X800; 1024MB RAM.
Perhaps the problems lies with the ati drivers. I am using **fglrx** on my desktop and also have an X800 in my laptop using the **ati driver**. On both machines, the site rendering causes problems such as lag, slow scrolling.

I don't blame Blizzard at all for making a flash site. They have also got a non flash site for low bandwidth connection, I just can't find the link to it anymore :(. And anyhow, I wan't all that flash to work right!

---

### Post by Golyadkin on 2007-06-19
When you get that login prompt for the root password when you try to install something, does the screen flicker when it goes to grey? If so, I have the same on my slower PC (with a Radeon 9200) but not on my other pc with an  X1650XT Ultra. The difference is that the 9200 works with the default drivers, and the X1650XT uses restricted drivers which give me much more performance. The flash is a bit choppy on the 9200 and on the X1650XT it is supersmooth.

---

### Post by Hasen_A on 2007-06-19
> **Golyadkin said:**
> When you get that login prompt for the root password when you try to install something, does the screen flicker when it goes to grey? If so, I have the same on my slower PC (with a Radeon 9200) but not on my other pc with an  X1650XT Ultra. The difference is that the 9200 works with the default drivers, and the X1650XT uses restricted drivers which give me much more performance. The flash is a bit choppy on the 9200 and on the X1650XT it is supersmooth.

Yes it does flicker a bit when opening the SPM, but not as much on my desktop in comparison to my laptop. I mean cmon, with an X800 it has to be a driver issue.

So you are saying I should download and install the fglrx restricted drivers from ATI directly and not through SPM using the current package?

---

### Post by Golyadkin on 2007-06-19
What I did was follow the steps [in this sticky]("http://ubuntuforums.org/showthread.php?t=414194") and it solved all my problems.

---

### Post by Hasen_A on 2007-06-19
> **Golyadkin said:**
> What I did was follow the steps [in this sticky]("http://ubuntuforums.org/showthread.php?t=414194") and it solved all my problems.

Well these drivers are loaded and the sticky didn't change anything for me :(.

---

### Post by Golyadkin on 2007-06-19
What is your cpu usage like when the flash page is open? You can see with top in the console, or with the System Monitor.

---

### Post by Hasen_A on 2007-06-21
> **Golyadkin said:**
> What is your cpu usage like when the flash page is open? You can see with top in the console, or with the System Monitor.

When I open the site, CPU is at 60-80%, once its loaded and leave the browser in front 50%. When I scroll down to the space pic on the bottom the CPU goes up to a 100%.

You can't tell me a 3,5+ GHz is too slow. It has to be a problem relating driver and java compatibility :(.

---

