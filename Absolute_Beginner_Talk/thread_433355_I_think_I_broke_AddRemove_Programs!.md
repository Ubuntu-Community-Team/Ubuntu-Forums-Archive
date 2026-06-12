---
title: "I think I broke Add/Remove Programs!"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by tcabeen on 2007-05-04
I hate creating new posts, knowing the same question has INVARIABLY been asked before, but I just can't find anything.

I was playing with Ubuntu at work today (shhh) where the wireless connection is REALLY weak.  I tried installing a couple of things, but the downloads failed, so I cancelled it.  Bummer.  I'll try it again when I'm at home, with a strong connection.

Now I have a beautiful 88% connection to my router, and am having no trouble.  Oh, except that Add/Remove Programs is nothing but errors.

I will try to be detailed, but I'm sure you'll have a few questions I missed.  Forgive how long I'm sure this will be...  I'm on a Toshiba laptop (model is irrelevant, right?) with a core duo processor and a gig of ram.  I've plenty of HD space left.  I had no trouble with wireless (I'm on it now to post this) or video or anything.  The SD reader didn't work, but I found the fix here and that's good now.  Everything else went perfectly.

Ubuntu is 7.04 Feisty etc and it's been running gorgeously.  Suspend bug affected me, so I shut down all the time now and have had absolutely no problems since.

Moving along, things were a bit iffy with my error today, but I thought not much of it.  Rock solid OS and all that.  FileZilla would be a bad example, because:
"FileZilla cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."
I can't imagine why, but ok.  Let's find something that should work....

Actually, I'm going to change my tune on that.  I'm getting the same error for Thunderbird.  I have Firefox installed by default (as does everyone, I guess), so why wouldn't Thunderbird be supported?  Now I think I'm getting that error in, well, error.

Ok, here we go, there's no error for Microsoft Core Fonts.
1) Check it.
- Install unupported and restricted software?

2) Install
- Cannot install "msttcorefonts'
- This application conflicts with something else ... switch to 'synaptic' to resolve.

Well, I went to Synaptic, and have no idea what the problem is.
So I can't even ask my original question, because I exited the error message in an attempt to recreate it, but now get a new error, as the software is allegedly not supported on my system.  What the... ?

Alright.  I give up.  Everything is either unsupported on i386 or conflicts with something I already have.  I haven't installed ANYTHING except the bubble-alert.  At this point, any advice would be immensely helpful.

---

### Post by Acglaphotis on 2007-05-04
I think i know what is happening. I got the same error with add/remove.

The fix is 

```
sudo gedit /etc/apt/sources.list
```

Comment eveything in there.

```
sudo aptitude update
```

Then, run:

```
sudo gedit /etc/apt/sources.list 
```

And uncomment eveything you commented, the run again: 

```
sudo aptitude update
```

And your good to go.

Hope i helped.

-Acgla

---

### Post by tcabeen on 2007-05-04
> **Acglaphotis said:**
> Comment eveything in there.

Forgive the ignorance, but I'm still new here.  Comment is #, or ##?
Is there a long comment I can do on the whole file, like slashstar, starslash?

---

### Post by Acglaphotis on 2007-05-04
# worked for me. But remember when you uncomment just uncomment the things you commented.

-Acgla

---

### Post by Sef on 2007-05-04
> Forgive the ignorance, but I'm still new here. Comment is #, or ##?

A comment (#) tells the machine to ignore that line.

---

### Post by tcabeen on 2007-05-04
It's saying "Password:" !!
What do I do ???

Ok, kidding!

Ok, I ran through the steps you said, and then came back to respond, and there were new updates in the .. update bubble alert thing.  Two of them.  "update-manager" and "update-manager-core"

Ok, so I start all my sentences with Ok, and tell it to go ahead.  Do it.
No, it totally can't.  It cries out, "Could not download all repository indexes!"
It goes on to elaborate:
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)"

It says it twice, to make sure I get the point.

The funny part is that when I first clicked that, it immediately goes to something like "Downloading file 42 of 44"
For two updates, I just know that's flat wrong.

In the time that it took me to type out the errors (with frequent interruptions by Monsoon Wedding, my favorite film), it prepared itself to work.  I tried it again, and the two auto updates worked.  "Your system is up to date."
Isn't that just special.

Filezilla still wont work with my dastardly i386, but Thunderbird no longer throws up an error.  Too bad I have no use for it (strictly gmail for me, folks).

There's still a ton of things I can't install because of the i386 thing, and mscorefonts can't be installed because of the conflict.  At least that 42/44 thing is resolved.  And the auto updates worked ok.

If there are any more suggestions for the remaining ... annoyances... I welcome them.  Thanks so much for helping me through this much!

---

### Post by eabhi on 2007-05-16
Even I was facing the same problem with Add remove program. Most of the programs and even the plugins that were searched use to display that they can't be installed.

I followed the above approach and now everything is back to normal and I don't get the message.

Though at the end of the process mentioned above I did get the foillowing message

[FONT="Times New Roman"]W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
[/FONT]

Is that any major problem...???

---

### Post by netwerx on 2007-05-16
have you tried running...

sudo apt-get update

?

---

### Post by Grungydan on 2007-05-16
Go to Synaptic and filter by Broken Packages.  I was having trouble with Add/Remove yesterday, and I found some broken packages that were causing issues.  After removing them (completely), everything went back to normal. 

Might not be related, but I thought I'd post it just in case.

---

### Post by tcabeen on 2007-05-24
Ok, synaptic has no broken things.  I didn't even know you could check that.  Thanks.

I ran sudo apt-get update, and got a couple screens of results.
Most of the lines start with Get, Ign, or Hit.  Those are ok, right?
The next page is where it gets interesting(ly bad?)

I'll just paste it here.  Anyone know how I can fix these things?

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [14 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [15 Packages gzip 0]             
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 63.5kB in 3s (19.9kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



I ran it again (as it suggested) and got the same result.



Now I'm going bonkers, because I have a scad of NEF files (nikon raw) that I need to convert.  I'm loving on what I've read about Raw Therapee but it's not a "package" (??) so I have NO idea how to install it.  At all.

I can't even express how frustrating it is, having been on computers for so long, making a friggin living on the things, and so on and so forth, but not being able to install a simple, friggin program.

Additionally, I had Firefox stop responding on me this weekend while I was playing with flickr's geotagging.  And then f-spot went bonkers , stopped responding twice, and just exited once.

What frustrating unfun!
But I will not be swayed from my ultimate goal!

So any and all help is seriously appreciated.  Thanks for everything so far!

---

### Post by tcabeen on 2007-05-24
Raw Therapee is now installed.  I wrote the program's author who explained to me that it simply needs to be unpacked and run.  Huzzah!

Furthermore, I found this concise guide for installation, which has been immensely helpful.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

