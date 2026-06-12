---
title: "Bittorrent blocklists and splist.zip"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by yanewby on 2008-01-25
I wish to use Bluetack.co.uk's splist.zip blocklist to block certain IP ranges when I am downloading files (I know of the arguments for and against using these lists so there is no need to go into this again in this thread!).

I used to use it all the time when using Deluge Bittorrent Client (but recently Deluge has become too buggy on my machine - the 25 Jan 2008 update was the last straw).  I have tried several other clients (Azureus, kTorrent, utorrent under wine) but none quite fit the bill.  Deluge has everything I need but is too buggy on my machine, Transmission appears to have everything except IPBlocking (and they will *not* be adding this).  If there was another way to use the blocklists I could give Transmission a whirl.

I am looking for an easy-to-follow solution that allows me to update the blocklists and keep "safe" or a bittorrent client (not Deluge, Azureus, kTorrent) that allows the use of splist.zip.  Can someone please offer some advice?

---

### Post by mikewhatever on 2008-01-25
If you were happy with Deluge version from the repositories, why not go back and use it? Running after the latest and the greatest will usually get you unexpected bugs. You can also use any other version of Deluge from their home site.

---

### Post by Kilz on 2008-01-25
> **yanewby said:**
> I wish to use Bluetack.co.uk's splist.zip blocklist to block certain IP ranges when I am downloading files (I know of the arguments for and against using these lists so there is no need to go into this again in this thread!).

I used to use it all the time when using Deluge Bittorrent Client (but recently Deluge has become too buggy on my machine - the 25 Jan 2008 update was the last straw).  I have tried several other clients (Azureus, kTorrent, utorrent under wine) but none quite fit the bill.  Deluge has everything I need but is too buggy on my machine, Transmission appears to have everything except IPBlocking (and they will *not* be adding this).  If there was another way to use the blocklists I could give Transmission a whirl.

I am looking for an easy-to-follow solution that allows me to update the blocklists and keep "safe" or a bittorrent client (not Deluge, Azureus, kTorrent) that allows the use of splist.zip.  Can someone please offer some advice?

You could install [moblock]("http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock") then use whatever torrent application you want.

---

### Post by yanewby on 2008-01-25
> **Kilz said:**
> You could install [moblock]("http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock") then use whatever torrent application you want.

I have just tried MoBlock but it seems to block way too much stuff!  I cannot even access Google with that running...

I have followed the instructions here: [MoBlock]("https://help.ubuntu.com/community/MoBlock")

Are there any other easier solutions?

---

### Post by bumanie on 2008-01-25
I too am very disappointed with the deluge 'upgrade', yes, before it was a bit buggy at times, but now it won't install any blocklists at all. I can't agree with the deluge website where they claim they have got rid of the bugs. I think they got rid of some and created worse bugs in the process. There doesn't seem to be a bug report area on their website.

---

### Post by yanewby on 2008-01-25
> **mikewhatever said:**
> If you were happy with Deluge version from the repositories, why not go back and use it? Running after the latest and the greatest will usually get you unexpected bugs. You can also use any other version of Deluge from their home site.

The version in the repositories is buggy on my machine and the later versions even more so.

Deluge is not an option for me until the bugs are ironed out.  I just want something that fits my specifications and doesn't crash every day (as Deluge does on my machine).  I expect once Deluge becomes stable I will move back to using it - but not yet!

---

### Post by yanewby on 2008-01-25
> **bumanie said:**
> I too am very disappointed with the deluge 'upgrade', yes, before it was a bit buggy at times, but now it won't install any blocklists at all. I can't agree with the deluge website where they claim they have got rid of the bugs. I think they got rid of some and created worse bugs in the process. There doesn't seem to be a bug report area on their website.

I totally agree with you here!  For every bug they "fix" at the moment they appear to be introducing more to the point it is no longer a viable option for me.  I just want something stable at the moment and not have to worry about whether it has crashed or not.

---

### Post by mikewhatever on 2008-01-25
I think you guys are a bit harsh on Deluge. I've been running it a lot lately (about 3-4 months) and did not experience any crashing. Curious about the newest release (0.5.8.2), I downloaded and reinstalled, and the IP blocking plug-in did not work, but it took two minutes to solve it. Here you are [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=1143](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=1143).
There is no section called 'Bug Report Section', but what's wrong with the one called 'Support'?

yanewby, I think Azureus has IP blocking feature. You might also want to check clients comparison from Wikipedia [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client).

---

### Post by yanewby on 2008-01-25
> **mikewhatever said:**
> I think you guys are a bit harsh on Deluge. I've been running it a lot lately (about 3-4 months) and did not experience any crashing. Curious about the newest release (0.5.8.2), I downloaded and reinstalled, and the IP blocking plug-in did not work, but it took two minutes to solve it. Here you are [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=1143](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=1143).
There is no section called 'Bug Report Section', but what's wrong with the one called 'Support'?

yanewby, I think Azureus has IP blocking feature. You might also want to check clients comparison from Wikipedia [http://en.wikipedia.org/wiki/BitTorrent_client](http://en.wikipedia.org/wiki/BitTorrent_client).

Don't get me wrong, Deluge /used/ to be great but they keep introducing more and more bugs or it looks that way on my machine.  They have gone from a very usable client to one that crashes frequently on my PC.  I have lost count of the number of times I have lost all my settings (happened daily) and/or had to delete config files to get things working.  Surely these types of thing should be picked up in their bug testing... (especially the IP Blocking plug-in not working if you already use it since that was supposed to be one of the major improvements in the latest edition).  This isn't meant to be a Deluge-bashing post anyway!

Thanks for the suggestion of Azureus also, I have tried that one also and will probably return to them if no-one has any other solutions.

---

### Post by mikewhatever on 2008-01-25
> **yanewby said:**
> Don't get me wrong, Deluge /used/ to be great but they keep introducing more and more bugs or it looks that way on my machine.  They have gone from a very usable client to one that crashes frequently on my PC.  I have lost count of the number of times I have lost all my settings (happened daily) and/or had to delete config files to get things working.  Surely these types of thing should be picked up in their bug testing... (especially the IP Blocking plug-in not working if you already use it since that was supposed to be one of the major improvements in the latest edition).  This isn't meant to be a Deluge-bashing post anyway!

Thanks for the suggestion of Azureus also, I have tried that one also and will probably return to them if no-one has any other solutions.

I remember myself feeling the same about uTorrent about two years ago. It was then version 1.4 or similar and under heavy development, and every time something broke, it sucked. uTorrent is great now (too bad it's Windows only), and I really hope Deluge will catch up. I am actually pretty amazed at how they manage to keep it multi-platform, small and well featured. For comparison, look at aMule. The latest stable version was released like a decade ago. Anyway, if you find a good replacement, please report back here, but if you don't and have to go back, try their support forum to solve your bugs.

---

### Post by bumanie on 2008-01-26
> **bumanie said:**
> I too am very disappointed with the deluge 'upgrade', yes, before it was a bit buggy at times, but now it won't install any blocklists at all. I can't agree with the deluge website where they claim they have got rid of the bugs. I think they got rid of some and created worse bugs in the process. There doesn't seem to be a bug report area on their website.

I think I may have retract the above comment. Today I went to the deluge community site and got a fix for the blocklist problem. There was an apology on the site (Iguess from a programmer) for taking the original blocklist away. Unfortunately there was no mention on the website as to how to get the new function working, but someone on the community (ie deluge forum) fixed that up. For anyone else with this problem, in terminal type
cd /usr/share/deluge/
rm ~/.config/deluge/blocklist.conf

Then check your /usr/share/deluge/plugins/ file and check that you have blocklists there and a package called nipfilter.dat.gz If you have these, I found it took a while to work its way through  to the program (?why, I don't know), but after a time the blocklist comes up as before, you insert the blocklist url you wish to use and then can choose how often to update it. This means a blocklist is not installed upon every opening of the program. It would have been helpful if this fix was on the website, but now installed, deluge does seem more stable and the blocklist does in fact work.

---

### Post by mikewhatever on 2008-01-26
I am also quite happy with the current version and think we should all remember that this is a community. Not trying to moralize anyone, but reporting bugs where possible is really the least we can do to help, even if forced to switch to another program.

---

### Post by yanewby on 2008-01-27
> **mikewhatever said:**
> I am also quite happy with the current version and think we should all remember that this is a community. Not trying to moralize anyone, but reporting bugs where possible is really the least we can do to help, even if forced to switch to another program.

mikewhatever, I am glad you are happy with Deluge, please accept my view that I am not.  I find it buggy on my computer.  I have reported these bugs and nothing has been done about them.  Understandably, they are busy developing their product on a number of different platforms and cannot address every bug immediately.  I accept this and I am trying to find an alternative solution.

Regarding bugs, I totally agree.  I always report bugs when I come across them and even try to fix them when they are in my field of expertise.  

mikewhatever, do not judge me when you know nothing about me.  I object to your "moralizing" which was so obviously pointed at me.  I find it offensive that you believe I am bashing their project for the sake of it.  This thread is not meant to be about how good or how bad any product is but you have attempted to divert the thread to one that appears so.

I could easily go into a rant about bug reporting but that would not help and does nothing to solve my original query.  I am trying to keep the thread on topic.

So back on topic, can anyone help with the original question?

I am looking for an easy-to-follow solution that allows me to update the blocklists and keep "safe" or a bittorrent client (not Deluge, Azureus, kTorrent) that allows the use of splist.zip. Can someone please offer some advice?

Following helpful advice on this thread I have tried MoBlock but it is too aggressive as it appears to block all traffic to my PC, I only require a solution that will filter bittorrent traffic.  Maybe I am missing something here?

---

### Post by bumanie on 2008-01-27
yanewby, if you look at my post from yesterday, it should fix all your problems and at least on my machine, it is stable and the blocklist does work with the fix noted there.

---

### Post by yanewby on 2008-01-27
> **bumanie said:**
> yanewby, if you look at my post from yesterday, it should fix all your problems and at least on my machine, it is stable and the blocklist does work with the fix noted there.

I saw your post but it doesn't solve all my other problems with Deluge which is why I am trying to find an alternative method.  Deluge is still not stable on my machine (they blame it on Ubuntu in their forums!).

I would like an alternative solution that does not involve Deluge :)

---

### Post by bumanie on 2008-01-27
I don't know of any other bitorrent client on linux that gives a blocklist option. Up to you what you do, but deluge does seem more stable. Did not have one crash today - often had half a dozen in few minutes before (usually at start up). Your experience may be different, so I hope you can find a replacement.

---

### Post by mikewhatever on 2008-01-27
My apologies for posting off topic yet again but I think you are making a stand against something that does not exist.

> mikewhatever, I am glad you are happy with Deluge, please accept my view that I am not. I find it buggy on my computer. I have reported these bugs and nothing has been done about them. Understandably, they are busy developing their product on a number of different platforms and cannot address every bug immediately. I accept this and I am trying to find an alternative solution.

You point of view is well accepted and respected. There is nothing wrong in looking for alternatives. Sorry if it wasn't obvious.


> Regarding bugs, I totally agree. I always report bugs when I come across them and even try to fix them when they are in my field of expertise.

mikewhatever, do not judge me when you know nothing about me. I object to your "moralizing" which was so obviously pointed at me. I find it offensive that you believe I am bashing their project for the sake of it. This thread is not meant to be about how good or how bad any product is but you have attempted to divert the thread to one that appears so.

I have not judged nor moralized you in any way. Had I wanted to, I would have done that openly, mentioning your name, because I think it's OK to disagree and express a different opinion. Never have I said you were bashing Deluge, nor hinted at it in any possible way.
I have nothing more to add to your thread, so will not post there any more, yet, I do hope you'll find a good client to replace Deluge.

---

### Post by chewearn on 2008-01-27
Have you seen this:
[HOWTO: Graphical IP Blocker]("http://ubuntuforums.org/showthread.php?t=530183")

I find it a close replacement to the popular Windows program PeerGuardian2, though (in my opinion) not quite there yet.  But it get the job done well enough and has allowed me to switch from Windows bittorrent set-up to Ubuntu.

As for a suitable bittorrent client, I have been running uTorrent under wine.  It's almost as good as running it under Windows, except you have to put up with a bit of lag in the UI and the interface is also not as slick (but importing the ms-ttf fonts into wine took care of some of the problems).

---

