---
title: "Total Windows Support"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2007-08-24
I know that there are many different programs out there that emulate a windows environment in Linux. I love the idea of Linux and the fact that it is Open Source. However there are some programs that I have to have and can't run on Linux. I have tried WINE but I need something that will run more programs. Does anybody have any alternatives? I am shooting for a list of all of the Windows environment emulators, so if you know of one, please post it even if it has less compatibility than WINE. This way mabye it would be possible to run several different emulators, each covering a different incompatibility, and ultimately be able to run all windows programs on Linux. 

I thank you for your help and for reading the post of someone who has limited Linux and hardware knowladge.

**IN SHORT, this is what I am asking:**
[LIST]
[*]List all of the Windows emulators you know of, indicating clearly if one post contians more than one.
[*]Please do not make repeat suggestions, though you can comment on previous suggestions as you please.
[*]Please post a link
[/LIST]


-Ian

---

### Post by Dr Small on 2007-08-24
What programs do you need to run on windows?
Then we might be able to list some alternatives for you.

Dr Small

---

### Post by Vadi on 2007-08-24
I know of CrossOver (aimed towards business applications) and Cegeda (aimed towards gaming).

But I suspect you'd be much better off posting the list of programs that you need to get working here :)

---

### Post by oilchangeguy on 2007-08-24
here's a non-free app:
[www.codeweavers.com](www.codeweavers.com)

---

### Post by insane_alien on 2007-08-24
first off, WINE Is Not an Emulator. (see where the recursive acrnym comes from) it's a comatability layer.

2nd. the best you can do is install a vitrual machine, and install windows on that so you'll be running windows on linux. i would recommend vmware-server as it is in the canonical commercial repositories.follow this guide

[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

and you'll be able to run the apps on your desktop. though at the cost of a third taskbar.

---

### Post by Ian505 on 2007-08-24
Well... for one thing I need Paint Shop Pro Photo XI. I cant use alternatives. I know this sounds like bologna, but I am morally obligated to use it for private reasons. I also need to be able to run Battlefront II, Guild Wars: Nightfall, as well as Cyberlink PowerDirector as well as Cyberlink PowerDirector Express. The last two are of the upmost importance- enough that I may not be able to move from Windows if I cant get them to run with full, un-hindered functionality. I think it might be a problem because they use a PCI card from Turtle Beach. These all cam in a bundle in Turtle Beach's [ADX package]("http://www.turtlebeach.com/products/vaadx/home.aspx").

I have a feeling that this will be hard to work around... but I am willing to try.

-Ian

---

### Post by Vadi on 2007-08-24
Think you can set up dual-boot so you can keep windows for those games, and ubuntu for... everything else?

By the way, try looking at Cedega then. It's specially designed to make windows games run on linux.

Another virtualization (virtualization = you'll have your windows running inside your ubuntu) option is VirtualBox, which is free, and I found very easy to install. Also has better speed ratings than vmware.

---

### Post by Ian505 on 2007-08-24
> **insane_alien said:**
> first off, WINE Is Not an Emulator. (see where the recursive acrnym comes from) it's a comatability layer.

2nd. the best you can do is install a vitrual machine, and install windows on that so you'll be running windows on linux. i would recommend vmware-server as it is in the canonical commercial repositories.follow this guide

[http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/](http://www.venturecake.com/10-minutes-to-run-every-windows-app-seamlessly-on-your-ubuntu-desktop/)

and you'll be able to run the apps on your desktop. though at the cost of a third taskbar.

1- I apologize, see my signature.
2-I have considered this- however it is out of my price range unfortunately. (I currently run ubuntu under innotek VirtualBox.)

---

### Post by Ian505 on 2007-08-24
> **Vadi said:**
> Think you can set up dual-boot so you can keep windows for those games, and ubuntu for... everything else?

By the way, try looking at Cedega then. It's specially designed to make windows games run on linux.

Another virtualization (virtualization = you'll have your windows running inside your ubuntu) option is VirtualBox, which is free, and I found very easy to install. Also has better speed ratings than vmware.

I thought of doing that, but I was hoping I wouldn't have to resort to dual-booting. (I am a speed demon.) I also hate Windows for its near monopoly. (Minor details.)

---

### Post by dca on 2007-08-24
I think going the virtualization route (VMWare, Virtual Box, etc) would be the easiest route...

---

### Post by Vadi on 2007-08-24
I hate Windows for it's ugliness :|.

Look up Cedega.

---

### Post by Ian505 on 2007-08-24
Just a question, I know that Cedega is aimed towards gaming, but will it applications too? I know that this is probably a omg how could you be so stupid kind of question (I have answered my share of those myself.) but I would really appreciate it if someone answered.

-Ian

---

### Post by Ian505 on 2007-08-24
I am going to have to rule out Cedega, as am more against subscriptions than I am one time licenses (like Windows) Sorry.
-Ian

---

### Post by oilchangeguy on 2007-08-24
"I apologize for my ignorance. I have been ignorant of linux my whole life untill the bast year or so"

you may want to edit your sig. until,  only has 1 L. and i'm guessing you mean last, and not bast.

also, did you read post #4?

---

### Post by Ian505 on 2007-08-24
> **oilchangeguy said:**
> "I apologize for my ignorance. I have been ignorant of linux my whole life untill the bast year or so"

you may want to edit your sig. until,  only has 1 L. and i'm guessing you mean last, and not bast.

also, did you read post #4?

Oops... :redface: Thanks...

I did checkout CrossOver, and though it does seem pricey, I am going to go with the trial and see if its worth it because its certainly cheaper than Cedega and it focuses on more than just games.

Thanks
-Ian

---

### Post by insane_alien on 2007-08-24
> **Ian505 said:**
> 1- I apologize, see my signature.
2-I have considered this- however it is out of my price range unfortunately. (I currently run ubuntu under innotek VirtualBox.)


1/ as long a syou learn and keep learning thats fine.

2/ £0 is out of your pricerange? you bankrupt or something. vmware-server is gratis but closed source, often faster than virtual box(for me at least) you do need to register to get a  key but it is perfectly free. you can download the program from canonical's commercial repositories

---

### Post by Ian505 on 2007-08-24
> **insane_alien said:**
> 1/ as long a syou learn and keep learning thats fine.

2/ £0 is out of your pricerange? you bankrupt or something. vmware-server is gratis but closed source, often faster than virtual box(for me at least) you do need to register to get a  key but it is perfectly free. you can download the program from canonical's commercial repositories

I am sorry but I was refering to Cedega which is a subscription-based program.  I will use Virtual Box for now, but I am wondering if vmware allows access to a PCI card? (Like a video capture card.) Just wondering. 

(Sorry for long reply: chickens were making a fuss....[stupid cat])

---

