---
title: "Xp loads exedingly slowly, is ubuntu the prob?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by bobandirus on 2007-09-03
Formated laptop (Tosh Equium M50-164, with 1.5Gig of ram instead)
Loaded windows, then installed various progs, and then downloaded Wubi, to install ubuntu, gave ubuntu 10Gig, which left me with 40Gig approx free space on windows, but then, windows began loadin impossibly slowly, with like 5 minute loading times.
When it has finished loading, however, it runs as normall. This is not helpful as this laptop is used in schools, so fast loading times are a must.

What could have caused this? It cant be that Xp is running out of room, because it still has 40 Gig left..

More importantly, can I fix this without zapping ubuntu? I love both and want to keep both...

---

### Post by Jerubaal on 2007-09-03
5 mins loading time for XP sounds about normal to me :twisted:  Honestly, mine is well slow, even with a reasonably fast PC.

---

### Post by jingo811 on 2007-09-03
Could it be that when you wiped out your entire hard drive and re-installed Windows XP from scratch followed by Ubuntu.  Your Windows XP now needs time to catchup to all the security patches that's now running in secret?

Why use Wubi?  What is that?  Why can't you install Ubuntu with the regular install CD?

PS.
I had a somewhat similar situation with a heavy XP game that crashed on me when I cleaned my puter and re-installed everything.  The problem was that my CPU fan had accumulated 3 mm layers of dust.  So I just vacuumed it and now it runs smooth.  Maybe you should give your Laptop to Toshiba or something and let them clean the fans for you.  My friend had dust problems on his Laptop after 2-3 years of use.

---

### Post by bobandirus on 2007-09-03
Wubi allows you to install Ubuntu on Xp with out evan bothering to use a disk [http://wubi-installer.org/](http://wubi-installer.org/) (its stupidly easy)

Thanks for reashuring me its not ubuntu, will go and get vacume cleaner to get what I can....

---

### Post by jingo811 on 2007-09-03
Try and Uninstall Ubuntu from your Wubi manager or whatnot and see if Windows still lags.
From what I read from the Wubi site you aren't really installing Ubuntu like you do normally with additional operating systems.  That's sounds like a troublemaker to me.
You're basically running an Operating system on top of another that means 2x the load.  With Dual boot you only choose which OS to startup and thus 1x the load.

[COLOR="Red"]Be careful with the vacuum cleaner on you Laptop, I've never done it personally only on my stationary PC.  Best would be to ask Toshiba how to proceed since Laptops have rules for what you can open up .[/COLOR]

---

### Post by Mud.Knee.Havoc on 2007-09-03
From the Wubi FAQ:
> 
Wubi Internals

How does Wubi work?

Wubi adds an entry to the Windows boot menu which allows you to run Linux. Ubuntu is installed within a file in the windows file system (c:\wubi\disks\system.virtual.disk), this file is seen by Linux as a real hard disk.

Is this running Ubuntu within a virtual environment or something similar?

No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble to create a free partition for Ubuntu. And we spare you the trouble to have to burn a CD-Rom.

So it seems that you've just created a huge (or maybe a number of huge) files on your Windows partition.

Maybe you need to defragment your hard drive?

I'd be a bit uneasy about using Wubi.  Basically, it installs Ubuntu to a file in your Windows directory instead of in its own partition.  Call me crazy, but it's easy enough to install Ubuntu the normal way (which has been tested by thousands upon thousands of people), why not just do that?

---

### Post by bobandirus on 2007-09-03
Uninstalled Wubi, windows still lags dramaticly, so this is now a windows prob.

Not gona mark this as solved, on the off chance that anyone has any idea.

Admin change this to solved if this goes agains what you would like.

Thanks for the support :biggrin: this is the most helpful forum in the world :biggrin:

---

### Post by jingo811 on 2007-09-03
> Thanks for the support this is the most helpful forum in the world 
I don't want to brag but we're indeed the best in the world, no corporation can come close to our greatness 8-[

---

### Post by JBAlaska on 2007-09-03
You might want to follow Mud.Knee.Havoc's advice and defrag (With a good progran like O&O defrag or diskeeper) your HD, Use a full defrag scheme like "name" or "access", also try doing a registry clean/compact and see if that speeds up your load time.

---

### Post by jingo811 on 2007-09-03
If you use Ubuntu for everyday work, surfing, media files.  You won't have to defrag a single time within your lifetime.  That's why it's my primary OS today.  Back when Win XP was my primary OS I had to defrag every 3 weeks even though I didn't do much on it except for playing games on a separated partitions setup for Windows.

---

### Post by bobandirus on 2007-09-03
Do you ever have to de-frag ubuntu, or does it keep it nice and orderd for you?

---

### Post by MenZa on 2007-09-03
> **bobandirus said:**
> Do you ever have to de-frag ubuntu, or does it keep it nice and orderd for you?

You won't need to defrag it---ext3 is good at keeing files unfragmented.

However, if it breaks, fsck is only a terminal away.

---

### Post by bobandirus on 2007-09-03
Yay! its nice and simple :D *is in love with ubuntu, and is now downloading the .iso instead of wubi* :biggrin:

---

### Post by jingo811 on 2007-09-03
Yay 1 guy Assimilated some 6 billion ppl left to go.
[IMG]http://i8.tinypic.com/4tsz4oi.jpg[/IMG]

---

### Post by bobandirus on 2007-09-03
hehehehe

you know what they say - oaks come from acorns, and now that dell offers ubuntu instead of xp on some of there laptops, maby this is that start of something huge?

---

