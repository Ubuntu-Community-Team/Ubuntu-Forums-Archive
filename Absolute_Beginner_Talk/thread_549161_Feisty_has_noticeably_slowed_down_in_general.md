---
title: "Feisty has noticeably slowed down in general"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-09-12
I ran Edgy for 3 or 4 months, no problems with speed.  I upgraded to Fesity 2 months ago and again,zippy with no problems.  Now, out of the blue the entire system has slowed down.  Boot up / shutdown, app launch times, internet speeds, and hard disk access times (it takes 3 or 4 seconds to display a folder when I first open an folder window).

I don't have much info to go on.  I haven't installed or modified the system recently.  I do the suggested upgrades regularly but couldn't tell you what I upgraded when the system slows.

Could it be a virus / spyware? (I have no security installed besides iptables / firestarter)?  Is this something other people have noticed?

---

### Post by atria on 2007-09-12
There might be a process that is hogging all the available CPU power.

While in the console enter 'top' (without the quotes) and look out for any process that might be utilizing an inordinate amount of cpu power.

There might be other causes too but its usually caused by such processes.

---

### Post by nvteighen on 2007-09-12
That's strange. Have you looked which processes are running? Go to Terminal and type:

```

top

```

That may tell you what's eating up memory.

---

### Post by civilmonkey on 2007-09-12
I will check that.  I had checked with the GUI and The largest (i think) was firefox at 65 megs, but I will check closer and report.

Thanks,

---

### Post by nvteighen on 2007-09-12
Just a note: close any application before looking.

---

### Post by rsambuca on 2007-09-12
You are not the first person to have mentioned this recently.  Do you have an ATI card by chance?

---

### Post by Harpoon on 2007-09-12
I have a laptop with intel graphics, and mine is slowing noticably, too.   Kind of reminds me of .....

---

### Post by nvteighen on 2007-09-12
I may have a lot of good luck: I've noticed Feisty to run faster after I've removed Ubuntu's boot splash (the progress bar at startup). Don't know how it can be related, but it's so.

---

### Post by Beggar on 2007-09-12
I noticed this the other day. Turns out theres a nasty firefox bug right now, certain web pages are messing with things, in my case it was an ad on digg.com which opens up offscreen and (based on what I read about the problem) has a width=100% tag. This caused my lag dramatically, but the fix was just to adblock the ad, not really that big of a deal.

My point is its not really fair to say feisty has slowed down. Whats far more likely is there is a problem with one of the packages on your system. Just wanted to add my 2 cents.

P.S. top is your friend.

---

### Post by civilmonkey on 2007-09-12
[quote=rsambuca]You are not the first person to have mentioned this recently. Do you have an ATI card by chance? [/quote]

My video card is Nvidia 7600GT, I have the 'restricted drivers' driver installed in the Feisy admin menu.

[quote=Beggar]My point is its not really fair to say feisty has slowed down[/quote]

I'm not really blaming Feisty and guessed it was likely a new package or something.  I was just checking if other users have noticed this as well.  As an aside, I find that the automatic updates pops up so often I end up accepting it without seeing what it's updating.  

I will run ```
top
``` and check the system processes.  Truth be told, I was pretty avid about controlling my WinXP system processes out of necessity but Ubuntu was running so smooth I haven't worried about it yet.

---

### Post by rsambuca on 2007-09-12
> **civilmonkey said:**
> As an aside, I find that the automatic updates pops up so often I end up accepting it without seeing what it's updating.  

How often is 'so often"?  I usually only get maybe one or two sets per week.  Maybe you have some strange repositories enabled?

---

### Post by Nussbaum on 2007-09-12
Not sure if this will be of use but I noticed twice that when a piece of hardware stopped working(one time wrong printer another time my internet providers network was down) that Feisty slowed down considerably. The linux splash screen after login stayed ages on my desktop, everything started slow etc. Plenty of free resources and rebooting didn't help. Once the printer/network was in order again everything worked fine(after reboot)

---

### Post by dwhitney67 on 2007-09-12
> **rsambuca said:**
> How often is 'so often"?  I usually only get maybe one or two sets per week.  Maybe you have some strange repositories enabled?

Once or twice a week is *often*.

How does one turn off the auto-update notifier?  I would like to perhaps update my system once a month.

---

### Post by hessiess on 2007-09-12
run a ram test just to rule that out

---

### Post by rsambuca on 2007-09-12
> **dwhitney67 said:**
> Once or twice a week is OFTEN.

How does one turn off the auto-update notifier?  I would like to perhaps update my system once a month.

Hey, sorry!  No need to shout at me.  I guess we have different definitions of often. :(

In any event, you can change the update notifier behaviour if you go to "System -> Administration - Software Sources".  Select "Updates".  The most you can change it to is every two weeks.

An alternative is to stop the update notifier completely from your Sessions settings.

EDIT:  Hey, I just noticed I wasn't even talking to you in the first place, dwhitney.  No need to hijack a thread and start shouting at people trying to help.

---

### Post by civilmonkey on 2007-09-12
> **hessiess said:**
> run a ram test just to rule that out

Will do tonight.  How do I do that?

EDIT:  I'll try this method
[http://ubuntuforums.org/showpost.php?p=3334249&postcount=8]("http://ubuntuforums.org/showpost.php?p=3334249&postcount=8")

[quote=Nussbaum]Not sure if this will be of use but I noticed twice that when a piece of hardware stopped working(one time wrong printer another time my internet providers network was down) that Feisty slowed down considerably[/quote]

I think you may have something there, it sounds familar to me as well.  I noticed Ubuntu is much happier when I internet is working well, and it has been flakly lately.  I wasn't sure if it was the net or Ubuntu.  I'll try re-starting my router tonight as well.

I will have lots to report tonight :)

---

### Post by civilmonkey on 2007-09-13
> **Nussbaum said:**
> Not sure if this will be of use but I noticed twice that when a piece of hardware stopped working(one time wrong printer another time my internet providers network was down) that Feisty slowed down considerably. The linux splash screen after login stayed ages on my desktop, everything started slow etc. Plenty of free resources and rebooting didn't help. Once the printer/network was in order again everything worked fine(after reboot)

This is exactly what happened to me.  Running top shows nothing out of the ordinary, and once my internet was stable again Feisty speed right up.  My DSL tends to do that and I need to re-start my router every few weeks or so, I had just never connected the two.

Thanks for everyone's input, id'ed tha prob and learned about 'top'.  Wierd that non internet apps. in Feisty slow down when my net is wonky.

---

### Post by dwhitney67 on 2007-09-13
How does your system run if you do not have an internet connection at all?

Have you run the command "free".  This command displays how much memory is available, and how much swap space has been used.  It is possible that you are running an application that has a memory leak, yet does not take up that much CPU time.  I recall a few years ago that the MP3 player "xmms" suffered those symptoms (on my Mandrake system).

---

### Post by civilmonkey on 2007-09-13
> **dwhitney67 said:**
> How does your system run if you do not have an internet connection at all?

Have you run the command "free".  This command displays how much memory is available, and how much swap space has been used.  It is possible that you are running an application that has a memory leak, yet does not take up that much CPU time.  I recall a few years ago that the MP3 player "xmms" suffered those symptoms (on my Mandrake system).

Here is my output of free fresh after a reboot.  sorry for the formatting, Can I use HTML tables in here or anything?

```
      total            used           free     shared    buffers     cached
Mem:       1035776     360664     675112          0      10800     234080
-/+ buffers/cache:     115784     919992
Swap:      1574328                0      1574328

```

I'll try to see if I can link slow performance with an application.  When I unplugged my ethernet cable system performance was okay, but it isn't really a conclusive test.

If I notice anything else, I'll post here.

---

### Post by dwhitney67 on 2007-09-13
Just use your system as you normally would.  The point is to see after a (long?) while whether your system's memory is exhausted and the swap space has come into play.

It is more efficient for every application you have running on the system to run from RAM.  However the more and more applications you run, the less likely that you will have sufficient RAM to run everything.  At that point, the OS will need to swap memory from RAM into the swap space so that it can clear space for an application that is being launched.  Naturally, the time is takes the OS to write to swap will slow things down a bit.

I've been running my system since mid-day today.  I am building a ton of software packages and running several xterms, and of course, browsing the web with Firefox.  Here's my output from running free:

```
             total       used       free     shared    buffers     cached
Mem:        514840     485380      29460          0       5876     163188
-/+ buffers/cache:     316316     198524
Swap:      1510068      34308    1475760
```

Notice how that I have very little "free" RAM available and that my swap space is being used.  Just launching the xterm to get this information took a moment or two for the xterm to appear.

Anyhow, I hope this post enlightens you.  It is normal when running many apps that a system's performance will degrade.

P.S.  Firefox is a memory hog.

---

### Post by likemindead on 2007-09-13
Yeah, I ditched FireFox for Epiphany and found it to be a much smoother experience.

---

