---
title: "ATI Graphics card problem."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-08-14
Hi Group,
I've a duel boot system:- XP + Ubuntu.
For some time now, Ubuntu has worked flawlessly. XP however, from time to time just shuts down......screen goes black, then computer re-starts.
Thinking that I'd tracked it down to the graphics card.........the problem often occurs when there's a lot of graphic stuff going on.....I decided to install a new graphics card. Until then, I had an on the motherboard graphics card. I'd been advised from the start that this might not 'cut the mustard.'

So, I fitted an ATI Radeon X1300.
Mainly because it has a low profile and would fit inside the case.

It appears to have fixed the Windows shut down problem, but couldn't get Ubuntu to start at all.
If you check the board, there are a number of suggestions saying how to get it to work....I've tried a few....and they don't work.

So, I took out the card. Now I'm back to square one.

So should I :-
Try to get Ubuntu to use the ATI card before I put the card back in.
or
Try another make of graphics card.

I don't need cutting edge graphics ability........being able to watch a DVD without getting chopping would be nice.

All the best,
Phil

---

### Post by Inxsible on 2007-08-14
Generally, NVidia cards are much better supported in Ubuntu as compared to ATI. But that is not to say that ATI doesn't work at all. 

Many on this forum successfully use ATI as their graphics card. So if you are willing to  be patient and configure your ATI card, then you should.

Else if money is not a problem, or you can return the ATI and get a replacement NVidia then you should do that. Also note that not all NVidia cards work out of the box. You might still have to tweak a few things here and there, no matter what card you get.

I have a NVidia GE Force Go 7600 which worked out of the box. Try to find out a list of cards that have worked for most ppl and that could help you make your decision better.

---

### Post by Hospadar on 2007-08-14
Well also to, when installing a new card like that, Your xserver won't automatically detect and correct for the change, you'll need to manually edit your configuration.

If you can at least start into the command line (safe graphics mode or whatever) or do recovery start off a livecd, then you can use a tool like envy (which you can install with "sudo apt-get install envy") to do most or all of the configuration for you

---

### Post by groeswenphil on 2007-08-14
you can install with "sudo apt-get install envy") to do most or all of the configuration for you[/QUOTE]

I tried that, but my computer said that Envy couldn't be found.

Perhaps I should try looking for one of the other of the Seven Deadly Sins......perhaps I should start with Lust?

All the best,
Phil

---

### Post by Inxsible on 2007-08-14
> **groeswenphil said:**
>  Perhaps I should try looking for one of the other of the Seven Deadly Sins......perhaps I should start with Lust?

LOL. That is funny as hell !!!

---

### Post by Hospadar on 2007-08-14
Do you know if you have a working net connection?
Also you may need to enable some extra sources in your /etc/apt/sources.list file.
do a "sudo nano /etc/apt/sources.list" and add the universe and add the universe, multiverse and restricted repos.  I think you might just be able to uncomment them (remove the # at the beginning of the line)

see [here]("https://help.ubuntu.com/community/Repositories/CommandLine") for more info.

then update and try again
```

sudo apt-get update
sudo apt-get install envy
envy -t

```

---

### Post by Alterax on 2007-08-14
Your problem is not on the Ubuntu side of the fence.  It's on the Windows side of the fence.

You are using Windows XP; in it there is a setting that causes XP to do a core dump and reboot.  This was Microsoft's "fix" to the Blue Screen of Death.  Reboot so the user doesn't see it.  Nice.

What you will need to do is find out exactly what is janky with Windows XP to fix the problem.  It  may help to stop it from rebooting on failure.  You will need to be logged in to XP with an account with Administrative Privileges.

Right-Click on "My Computer", click "Properties" then the Advanced tab.  There should be a section marked "Startup and Recovery" with a settings box beside it.  Click it, then uncheck the box that is marked "Automatically Restart" then click [OK] out of everything.

That will keep it from rebooting; you will get a blue screen instead.  But this is a good thing since it gives you an error message, which you can write down, reboot into Ubuntu, and do a search for.  My suggestion is not to say anything about Ubuntu in the search, since the problem is specific to Windows; putting it in there will only narrow out anything that might help.

Just off the top of my head, I am betting that it is a device driver problem.  Put the card you are going to use for both in and get the drivers for that one.  You may have to hit F5 during windows boot and choose "Safe Mode with Networking" if you need to download the driver.

--Alterax

---

### Post by Alterax on 2007-08-14
As far as getting the X1300 to be recognized by Ubuntu (Which is what I use at home), Envy is nice and all, but I can't remember the repository and it's not a standard Ubuntu package.  Instead, if you are using Feisty or Gutsy(pre-release), you'll need to enable the restricted drivers.

In Ubuntu:
System > Administration > Software Sources
Enter your password to continue, then check the box marked "Proprietary Drivers for Devices (Restricted).

Click "Close" and it should handle it for you; reconfiguring X and everything.

--Alterax

---

### Post by groeswenphil on 2007-08-14
In Ubuntu:
System > Administration > Software Sources

I haven't got Software Sources.
I'm running Dapper.

Is there another way?
Phil

---

