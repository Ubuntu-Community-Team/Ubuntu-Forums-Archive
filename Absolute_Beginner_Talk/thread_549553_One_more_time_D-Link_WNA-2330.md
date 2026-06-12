---
title: "One more time: D-Link WNA-2330"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by hiloguy on 2007-09-12
After reading about all the successful installations of the D-Link WNA-2330 Adaptorin 7.04, I bought one to replace my antiquated old Belkin.  I was eager to avoid the multi-step process to use the Windows drivers.

Well, 6.1 at least recognized that the adaptor was there.  7.04 does not, and every one of the install processes I'm seeing says to first locate the wifi adaptor in the Network Setting window.  So what if it isn't there?  I've tried rebooting with the adaptor in place, and that didn't help, either.

I feel so stooooopid.

:confused:

---

### Post by hiloguy on 2007-09-12
What? A reply to my own question?  Well, it’s more like an addenda.  Or another question, namely, am I missing something really basic here?

I’ve now read a lot of postings of basically the same question:  How does one get a D-Link WNA-2330 adapter working under Feisty? In response to this question I have read numerous “ways to get it to work,” with as many repeated cries for help when those ideas didn’t fly.

So what I might be missing: is Linux Ubuntu  typically a system under which there are no step-by-step instructions that work at least most of the time?  

I’ve (to the best of my newbie ability) chased down several of these instructions and each has led me to a blind alley, like a window that did not offer the suggested option, or an install CD that simply would not respond to the Synaptic Package Manager instructions as presented  Ad nauseam!

This is getting discouraging.  I love the potential I see in Ubuntu and I really want to stick with it, but if it’s going to be this much of a challenge every step of the way, I don’t know.  I don’t expect “plug-and-play,” but it oughta work better than this.

So now there are a bunch of us out here who cannot get our WNA-2330 adaptors working, in spite of the fact that we all bought then in response to postings about how they work out-of-the-box.

Step-by-step . . . Am I dreaming?

And to you who are patiently dealing with us newbies, mahalo nui loa!

---

### Post by Brightbelt on 2007-09-12
Hi, I just sold a laptop that I had used a WNA-2330 on, and at first, I had had a Linux Guru from my neighborhood computer store configure it,

Then one day, I had to do a reinstall and I was faced with doing it myself. And it wasn't that hard, but I may have been lucky too.  But I also plugged in wired to my router to get internet access for what I needed. And you may have to do the same. Here's how I configured it:

First, make sure you have Ndiswrapper installed from The Synaptic Package Manager (System Menu/Administration/Synaptic Package Manager. Also you should have Network Manager already installed with Ubuntu by default.
1) I went to Add/Remove and downloaded 'Windows Wireless Drivers'. (it's a Graphic User Interface for Ndiswrapper)
2) Download the Windows driver from D-
link and search the folders for the INF file
3) You'll find 'Windows Wireless Drivers' in the System menu/Administration/Windows Wireless Drivers.
4) Pull up the interface, click the 'Install File' and browse to the INF file and install it. 

Restart your computer and it should work for you.....Good Luck,

Frank B.

---

### Post by hiloguy on 2007-09-13
> **Brightbelt said:**
> Hi, I just sold a laptop that I had used a WNA-2330 on, and at first, I had had a Linux Guru from my neighborhood computer store configure it,

Then one day, I had to do a reinstall and I was faced with doing it myself. And it wasn't that hard, but I may have been lucky too.  But I also plugged in wired to my router to get internet access for what I needed. And you may have to do the same. Here's how I configured it:

First, make sure you have Ndiswrapper installed from The Synaptic Package Manager (System Menu/Administration/Synaptic Package Manager. Also you should have Network Manager already installed with Ubuntu by default.
1) I went to Add/Remove and downloaded 'Windows Wireless Drivers'. (it's a Graphic User Interface for Ndiswrapper)
2) Download the Windows driver from D-
link and search the folders for the INF file
3) You'll find 'Windows Wireless Drivers' in the System menu/Administration/Windows Wireless Drivers.
4) Pull up the interface, click the 'Install File' and browse to the INF file and install it. 

Restart your computer and it should work for you.....Good Luck,

Frank B.



OK, I installed Ndiswrapper and Network Manager is in place, too.  You said you went to Add/Remove and downloaded "Windows Wireless Drivers."  So I didn't see anywhere from within Add/Remove where I could download anything, so I'm figuring I don't yet have the GUI for Ndiswrapper.  How do I get there from here?

Sheeeeesh.  I only have about 8 random hours a day to devote to this, so I'm kinda having to do it in spurts.

Also, when I was just trying another way from Terminal, I got stopped by a password request.  Then it wouldn't let me enter a password.  The cursor simply didn't work.

HELP!!

---

### Post by splintercellguy on 2007-09-13
Ah, the Unix way of entering passes. I'm surprised how many people get confused by me. When you get a nice Terminal prompt to enter a password, the cursor does not move so a screenlooker cannot count the chars. While you can get ndisgtk (the ndiswrapper GUI) by doing:

sudo apt-get install ndisgtk

I don't personally like it. Have you read the Ubuntu Wiki article on ndiswrapper? [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

---

### Post by hiloguy on 2007-09-13
> **splintercellguy said:**
> Ah, the Unix way of entering passes. I'm surprised how many people get confused by me. When you get a nice Terminal prompt to enter a password, the cursor does not move so a screenlooker cannot count the chars. While you can get ndisgtk (the ndiswrapper GUI) by doing:

sudo apt-get install ndisgtk

I don't personally like it. Have you read the Ubuntu Wiki article on ndiswrapper? [https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

Moving right along  . . . I installed sudo apt-get install ndisgtk.  Nothing happened and if I actually installed a GUI for Ndiswrapper, where is it?

Next, I went to the URL you suggested and followed their promising-looking step-by-step, until I got to "Enter the APT line for the repositories you are trying to install."  Cool.  Where do I find the APT lines for the repositories? I thought there was a way you could do this by choosing from a list . . .

Thanks for the pass heads-up.  Hey, I finally actually learned something that works! :)

---

### Post by splintercellguy on 2007-09-13
The APT repos are in /etc/apt/sources.list, the link just wants you to enable multi/universe, which is already enabled for Feisty. Carry on with the rest.

---

### Post by Brightbelt on 2007-09-13
Hi, I am here again, if I can still help. Sure, the GUI of Ndiswrapper has its limitations and at times  it can actually "break", meaning it just stops working.

But it's a great tool for newbies and it has worked for me several times when I was in a jam. To see it in Add/Remove, you have to click the drop-down menu in the upper right and select 'All Available Applications'. Then in the search box in the upper left, type in 'Windows Wireless Drivers'.  Then when it appears in the list (hopefully it's there by now), click the check box by it  and click Apply to install. 

You may already have successfully installed it by now, in which case you'll see it appear in the list with the box already checked. By the way, that's a good way to check to see if you've gotten a program installed successfully. 

Where is it? (I did mention this in my first post) It should be at the System Menu/Administration/Windows Wireless Drivers. 

And like I said, you'll need to download the Windows Driver for the D-link WNA-2330 from the D-link website. (You may have to try both the XP driver and the Windows 2000 driver to see which one works; I would start with the Windows 2000 driver) 

In those driver folders is an INF file and that is the file you need to install using Ndiswrapper.

I hope this helps,....Frank B.

---

### Post by hiloguy on 2007-09-13
> **Brightbelt said:**
> Hi, I am here again, if I can still help. Sure, the GUI of Ndiswrapper has its limitations and at times  it can actually "break", meaning it just stops working.

But it's a great tool for newbies and it has worked for me several times when I was in a jam. To see it in Add/Remove, you have to click the drop-down menu in the upper right and select 'All Available Applications'. Then in the search box in the upper left, type in 'Windows Wireless Drivers'.  Then when it appears in the list (hopefully it's there by now), click the check box by it  and click Apply to install. 

You may already have successfully installed it by now, in which case you'll see it appear in the list with the box already checked. By the way, that's a good way to check to see if you've gotten a program installed successfully. 

Where is it? (I did mention this in my first post) It should be at the System Menu/Administration/Windows Wireless Drivers. 

And like I said, you'll need to download the Windows Driver for the D-link WNA-2330 from the D-link website. (You may have to try both the XP driver and the Windows 2000 driver to see which one works; I would start with the Windows 2000 driver) 

In those driver folders is an INF file and that is the file you need to install using Ndiswrapper.

I hope this helps,....Frank B.



Well, maybe we're moving forward here albeit at a glacial pace . . .

So I got as far as the Wireless Network Drivers window, clicked Install New Driver, and then I get a little box that says Select inf file.  Like, whoopee, right?  So I click on Locationand I get another box that allows me to look only in the root directory.  There seems to be no way of looking anywhere else.   The driver is located on the CD, plus I also copied it to my Home directory in the off-chance that I would be allowed to search for it there.

I feel so utterly stupid not being able to do something that should be this easy.  I just don't get why the Ubuntu interface needs to be so cryptic.  It seems that an enormous amount of thought went into creating and updating Ubuntu -- why is it still so difficult to accomplish a simple task?  Judging from the forum posts, I'm not alone in having these issues, and I am no stranger to managing computers.

Anyway, two questions at this point:

1. How do I accces the inf file from the Secelt Inf File window.
2. You said to download the inf driver -- can't I use the one on the CD that came with the adaptor?

Thank you, thank you, thank you!

---

### Post by hiloguy on 2007-09-13
> **hiloguy said:**
> Well, maybe we're moving forward here albeit at a glacial pace . . .

So I got as far as the Wireless Network Drivers window, clicked Install New Driver, and then I get a little box that says Select inf file.  Like, whoopee, right?  So I click on Locationand I get another box that allows me to look only in the root directory.  There seems to be no way of looking anywhere else.   The driver is located on the CD, plus I also copied it to my Home directory in the off-chance that I would be allowed to search for it there.

I feel so utterly stupid not being able to do something that should be this easy.  I just don't get why the Ubuntu interface needs to be so cryptic.  It seems that an enormous amount of thought went into creating and updating Ubuntu -- why is it still so difficult to accomplish a simple task?  Judging from the forum posts, I'm not alone in having these issues, and I am no stranger to managing computers.

Anyway, two questions at this point:

1. How do I accces the inf file from the Secelt Inf File window.
2. You said to download the inf driver -- can't I use the one on the CD that came with the adaptor?

Thank you, thank you, thank you!




UPDATE!

OK, I managed to get the dirver folder into the root directory so the driver that is on the CD is now installed.  I un/re-inserted the adaptor, rebooted and now the adaptor has gone into "roaming mode," whatever that is.  I've unchecked "enable roaming mode" and it won't stay unchecked.

Also, when I tried to unzip-install the downloaded driver, it won't. 

Good thing I have lots of patience, eh?

Aloha!

---

### Post by Maestro23 on 2007-09-13
> **hiloguy said:**
> UPDATE!

OK, I managed to get the dirver folder into the root directory so the driver that is on the CD is now installed.  I un/re-inserted the adaptor, rebooted and now the adaptor has gone into "roaming mode," whatever that is.  I've unchecked "enable roaming mode" and it won't stay unchecked.

Also, when I tried to unzip-install the downloaded driver, it won't. 

Good thing I have lots of patience, eh?

Aloha!

Can you provide a link to where you downloaded the driver?

---

### Post by Paul133 on 2007-09-13
```
 sudo apt-get install zip unzip
``` should install programs necessary for you to zip and unzip files. As far as the wireless drivers, they're a part of life. It's not always that easy. But after this, Ubuntu really is easy to use, even for Linux newbies. What are you doing now?

---

### Post by Brightbelt on 2007-09-13
I don't think you want to uncheck the roaming mode, though I could be wrong. Try just Rrebooting and I think you have a chance of your adaptor working - you did say you got the INF file installed. 

And yes the INF file within the driver folders off your CD should work fine.

Frank B.

---

### Post by hiloguy on 2007-09-13
And yet another update.  I downloaded the driver zip to a W-XP machine and unzipped it.  The driver is the same as the one on the CD and the W2000 and W-XP drivers are the same, too.  So I think I have the correct driver.

When I ran iwconfig I got back an output that compared well to the one in one of my books that said the card is being recognized, yet in other tests, there "is no card."

Hey, another day in trying to get wireless.  I'm glad I don't have anything better to do . . . like work!:)

---

### Post by hiloguy on 2007-09-13
**IT'S WORKING!!!**

So now I understand why it's so difficult to give anyone step-by-step instructions. My D-Link WNA-2330 is working now but I don't have a clue as to why or what I did that finally made it work.

I did reboot the machine about 6 times and I pulled and replaced the adapter a few times. Funny thing, there are two slots on this laptop.  The top slot, whcih is where my old card was when this was a fully-functioningW- XP machine, doesn't work with this card. Matter of fact, if I hot install it, it locks up the computer.  The bottom slot is where it works.  (And I did have it in the bottom slot through most of the above attempts.)

So anyway, thank you all for your assistance.  Probably every one of the things I did that didn't work were essential components in getting it to finally work.  Or not.  Whatever, it works.

Now let's see about opening another can of worms here . . .

Aloha Nui Loa!

Hiloguy

---

### Post by Brightbelt on 2007-09-13
I'm glad you got it going!! Once you get the INF file installed with Ndiswrapper, that should do the trick. 

One thing to note and learn is where Network Manager comes up on your taskbar. (you'll see the double-monitor icons there).  There may be times you have to click that and choose your preferred network or sign in with a password etc.

Congratulations!! Once the wireless gets solved with Ubuntu, it's much smoother sailing after that.

Frank B.

---

### Post by pumpkinpapa on 2007-12-30
I have this card as well though I am running 7.10. I think the restricted drivers are powering the card but this is my first entry into wireless so I'm left to wonder if Gutsy suppoerts WPA so well then why can't I connect?

I likely am missing something in my configurations that is going to surprise me :)

BTW I do have a wired connection that is fine through the WBR-1310 router.

---

