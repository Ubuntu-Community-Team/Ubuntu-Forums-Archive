---
title: "Fresh Install, having some problems."
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by se1zure on 2007-03-01
So I decided to put on Ubuntu 64 bit version on my computer, which has these specs:

core 2 duo e6600, asus p5w dh delux mobo, and an ati radeon x1950 pro.

Here are my issues:

Video Card: Can anyoen help me find the drivers for my x1950 pro? I can only find them for Windows... and it is a fairly popular card. I assume I need it for beryl too.

Resolution: THe maximum resolution I can set is 1280 x 1204. which looks horrible on my 22in monitor. HOw do I set it to 1680 x 1050?

Windows: THe windows are REALLY laggy, as in, they leave trails behind them when I drag them. I am using all new, fairly top of the line hardware, so this shouldn't be happening. What can I do to fix this?

---

### Post by Kateikyoushi on 2007-03-01
Check this thread about installing the Video card. [LINK]("http://ubuntuforums.org/showthread.php?t=361240")
Then you can set the resolution as well and the windows won't leave a trail either.

---

### Post by overdrank on 2007-03-01
> **se1zure said:**
> So I decided to put on Ubuntu 64 bit version on my computer, which has these specs:

core 2 duo e6600, asus p5w dh delux mobo, and an ati radeon x1950 pro.

Here are my issues:

Video Card: Can anyoen help me find the drivers for my x1950 pro? I can only find them for Windows... and it is a fairly popular card. I assume I need it for beryl too.

Resolution: THe maximum resolution I can set is 1280 x 1204. which looks horrible on my 22in monitor. HOw do I set it to 1680 x 1050?

Windows: THe windows are REALLY laggy, as in, they leave trails behind them when I drag them. I am using all new, fairly top of the line hardware, so this shouldn't be happening. What can I do to fix this?


Hi this thread may help also. Good luck!
[http://ubuntuforums.org/showthread.php?t=367820&highlight=x1950+pro](http://ubuntuforums.org/showthread.php?t=367820&highlight=x1950+pro)

---

### Post by se1zure on 2007-03-01
Err... Neither of those links had any solution to installing the x1950...

which from what i understand is causign all of the problems.

I even tried downloading the x1900 drivers, but when I double click the file that I downloaded from ATI, it says:

"Could not open the file /home/cory/Desktop/ati-d&#8230;ler-8.34.8-x86.x86_64.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

Which doesn't make any sense at all.... Good god, Ubuntu is giving me nothing but problems....

---

### Post by Kateikyoushi on 2007-03-01
Gedit is a word processor so it can't run the driver.

Follow this guide to install the driver. [LINK]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by se1zure on 2007-03-01
i don't know unix or terminal commands. How do I install it without the terminal?

Also, it says "To do this in GNOME, go to your System Menu > Administration > Software Sources. Place a check next to "Proprietary drivers for devices (restricted)," click Close, click Reload, and let the application update the package list."

There is no "Software Sources" option.

Is everything in linux this hard.......

ANd I went to install flash player, and It forces me to use terminal also... HOw do I do ti without commands? It says in readme to "Navigate to the unpacked tar.gz file" which doens't make sense. How do I navigate with text?

---

### Post by Kateikyoushi on 2007-03-01
Which version of ubuntu did you install ?

Do you have synaptic in administration ?
You could do the same there as well, in settings > repositories.

I do not think it is hard, just different and blame ati for it's drivers.

---

### Post by se1zure on 2007-03-01
I'm not blaming ati, it's not their fault.

If you make a product, you make ti to fit with the things people are accustomed to, you don't expect the whole world to stop and change everything to work with you, you have to work with it.

So hwo do, i per se' install or go about getting x1950 drivers?

I still can't figure out how to install without the terminal... and I don't know any unix commands. What format is linux'es .exe or .dmg?

also, wher can I find drivers for my logitechboard. RIght now, none of the speacial hotkeys work... :(

---

### Post by se1zure on 2007-03-01
no-one? 

where is Ubuntu's fantastic community that I hear so much about?

---

### Post by Maestro23 on 2007-03-01
> **se1zure said:**
> no-one? 

where is Ubuntu's fantastic community that I hear so much about?

Since you don't yet know you way around a terminal, commands, or file structure, give the Envy script a try.

1. Get the correct drivers for you card.

2. Run the Envy script:[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Script supports both ATI and Nvidia

Good luck.

---

### Post by se1zure on 2007-03-01
okay. I downloaded the Envy thingy. I ran it, and it didn't report any errors. It said at hte end to reboot. I did, but it didn't change a thing. The windows still suck, and the resolution is still crappy.

what am I doing wrong!?!

---

### Post by se1zure on 2007-03-02
bump

---

### Post by Synister on 2007-07-10
Basically, the drivers you downloaded will not do a heck of a lot, they are for the wrong card after all.

At this time you will have to wait until ATI releases the drivers for your card, so, if you want something to blame the finger is pointed at ATI for this for not fully supporting their hardware.

As a side note, I also have a 1950 in my Ubuntu system (Feisty), the base Linux drivers get you up and running, but the graphics acceleration will be nil until the driver release.  You should be able to run basic Linux games and blender, Gimp, and just about everything else works fine on my box, just can't run beryl, wow (too choppy).  but that is about it.

Cheers.

---

### Post by mr.v. on 2007-07-10
Sorry about your troubles.

I had an ATI card too (9800 pro) but ended up ditching it because of hardware freezes and other things in linux only (kept working fine in Windows) in favor of a slower NVidia card because Nvidia has infinitely better driver support for linux than ATI does.

ATI is under no obligation to support Linux. They choose to pay lip service to it, but their linux drivers are unacceptable for actual use. Anyway, vote with your wallet. Sell your ATI and buy a Nvidia card and write a letter to ATI saying exactly why you switched.

That's what I did. (of course their drivers still seem to suck now so I guess it didn't have much influence =)

---

### Post by Synister on 2007-07-10
I know what you are talking about Mr.V, unfortunately I am the only one to blame for the X1950 fiasco, I bought the card because of the stock heat sinks back flow air in and out take and I am also far too stubborn to admit defeat at the hands of a large corporation... Even though nVidia does make a better product...

I still feel that the best possible solution to get some quality drivers out of the mega corps is to make Linux a common name in the household and eventually sink m$oft. *I can dream* :)

But as long as I can still use Blender and Gimp I will be willing to wait for a proper driver release.

---

