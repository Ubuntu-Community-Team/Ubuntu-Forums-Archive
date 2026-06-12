---
title: "My experience so far....and some questions"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-13
Hello All!  :)  (I'm a bit wordy here...apologies)

I happened to have a bunch of old parts lying around so I thought I'd build a PC with the idea that I'd sell it on eBay and make a little cashola.

This PC is a P4 2.4Ghz machine.  It's got 1 gig of RAM and a PNY Verto GeForce FX 5700 (LE) video card with 128 megs of RAM.  I bought a nice, new 550 Watt power supply and a DVD burner and a DVD ROM, plus a floppy drive (because I can't find the 3½ in cover).  An inexpensive keyboard and mouse and I'm all set.

When you consider that you can get a decent, brand-new, PC with a Core Duo and all kinds of bells and whistles for about $400.00, I decided the effort of putting my old PC together (and selling it on eBay) would not yield enough money to be worth it, so I thought, "HEY!  I'll try a Linux distro!"

Since I've been screwing around with PC's since the old DOS days, but I've never played with anything other than Windows (and DOS and a very brief bout with Warp...I hated it).  I figured I'd get a book to help me through some of the beginning hurdles, so I bought this from Amazon.com.

_Ubuntu Linux for Non-Geeks:  A pain-free, project based, get-things-done guidebook_ by Rickford Grant

Mine came with a Dapper CD, but I believe there's a 2nd edition out that deals with Fiesty.  It's a great book and I highly recommend it to any beginners out there that want to learn based on doing simple projects that build on one another.

Well, after several projects I decided to mess around on my own and I screwed something up.  I killed all the repositories and I couldn't figure out how to get them back, so I downloaded Gutsy and installed that.  Impatient.  **Lesson #1:  Be patient.  Read.  Learn.**

**Note**  I highly recommend grabbing a program called DBAN (Derik's Boot and Nuke) to scrape your hard drive before you install Linux, or any other OS (unless you've got a new hard drive...then you don't need it.)  I also recommend you use this program before you get rid of any old hard drives or PC's.  You can get it here:  [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

I'm hoping that Gutsy isn't TOO different from Dapper and that I can still use my book.  When I first loaded Gutsy, I noticed that there were something like 186 updates available.  I tried to grab them, but I kept getting error messages regarding broken packages and some other annoying problems.  I started over again.

I figured I might have a corrupted iso and/or my CD didn't burn properly, so I followed one of the stickies in the beginners forum to be sure the checksum is good and the burn was done successfully.  Everything checks out fine so far and it installed without a hitch.  

Should I go ahead and use Update Manager to see what I get?  I'm worried I'll end up with a broken package again, but perhaps since I confirmed the iso and the iso burn were good, maybe that's not such a concern anymore?

Some other questions:
I love how customizable the GNOME interface is, but it can take some time getting everything set up the way you want.  Since Ubuntu has a 6 month version cycle, and since I've read that a clean install is better than an upgrade, why would I want to upgrade to another version and go though all the work again?  Is there a way to retain your settings?

It seems very easy to completly hose up your system with Ubuntu, even if you just use the built in tools to do simple tasks (such as Update Manager).  Since I'm new to this, and since I'm used to Windows, I rely on built in things like the Update Manager to take care of things for me.  If I get an error message, I'm not sure what to do (except come here and list the problem).  (This is why I'm so glad the beginner forum was started!  Thank you!)  This can be VERY frustrating for a new user, because you're only doing what the the system is prompting you to do (i.e.  There are updates available...grab 'em with this tool)  

Please understand that I am not slamming Ubuntu here.  I really like it and I'm excited to learn something new.  I'm getting WAY too wordy, so I'll post results of the Update Manager in a separate post.

Thanks, All!

---

### Post by Trebaruna on 2008-02-13
Well, I've never had a problem with the Update Manager (except for that one time quite a while back when there was a kernel dependency problem). Are you sure everything is working on your setup?

Also, it might be easy to hose, but it is generally possible to fix, too. If I'm getting BSODs in Windows it can be a lot harder or even impossible to fix.

---

### Post by Therion on 2008-02-13
You might want/need to enable some additional repositories.  See [this link]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-a86dddc6826cec4a3847d8441b24051d07b8dc64") for how to do that.  Follow the steps listed, and re-run the Update Manager.  I too sometimes get the "broken packages" error but usually re-running the update manager - after downloading/installing what I can - fixes things.  Or I'll download/install what I can, reboot and *then* rerun the Update Manager.  What I mean to say is it's something that usually sorts itself out in my experience.

As for the ease of "hosing" yourself with Ubuntu... I had to laugh when I read that, because I can't TELL you how many times I've hosed my system partially or fully.  But you know what, that's when I've learned the most.  Either the easy way (posting and pleading for help) or the hard-way (digging through some books, trying this or that on my own, Googling etc.) but whichever, it's always proved to be a learning experience.  And you know... Worst case scenario -- reformat and reinstall.  Harsh, I know, but when it only takes an hour, I can deal with that.  The upside to it is Having the Power.  I like weilding the power of having absolute and total control over my system, what it does, how it does it, when it does it.  And if that means there's a little pain involved in the process of learning how to wield that power effectively, I'll put up with that.  Far better in my opinion than letting my OS decide for me who's in the driver's seat.

---

### Post by emarkd on 2008-02-13
I've also never had a lasting issue with updates and I've never reinstalled any of my Ubuntu boxes, and some of them have had every release since 6.06 on them.  Upgrades work fine for me and the occasional small hitches are usually easy to work through with a little research (or help from this forum).  I think many people are too quick to reinstall Ubuntu, just like they're too quick to go pulling the plug when it's acting strangely.  It's hard at first to not treat your Ubuntu installation like you used to have to treat your Windows.

So saying that, definitely get your updates.  They're important.  If you still have problems, make sure your extra repositories are enabled like Therion suggested, then try again.  If there are still problems, try again tomorrow.

---

### Post by Scut_Farkus on 2008-02-13
Wonderful!

Thanks for the responses!  I have added the repositories (or tried to) and I got the following error message:

[SIZE="4"]Could not download all repository indexes[/SIZE]

The repository might no longer be available or could not be contacted due to network problems.  If available, an older version of the index will be used.  Otherwise, the repository will be ignored.  Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.bz2:) Subprocess bzip2 returned an error code (2)

Not sure why it did this, but perhaps someone will enlighten me.  This might not even be a real problem...don't know enough yet.

Thanks!

---

### Post by Therion on 2008-02-13
Off the top of my head, sounds like a little hitch in the giddyup with the apt-get server.  Translation: No big deal; let it go for now.  Just download and install what updates you can and try again tomorrow... Or the next day even.  This could be something as simple as the server being too busy.  If the error persists over the next few days, then I would have to say it's a deeper issue; but I'd be willing to bet this is one of those things that will take care of itself.

---

