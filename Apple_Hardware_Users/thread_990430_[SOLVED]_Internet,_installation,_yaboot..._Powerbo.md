---
title: "[SOLVED] Internet, installation, yaboot... Powerbook G4 troubles"
date: 2008-11-22
forum: Apple Hardware Users
---

### Post by Danny Shumway on 2008-11-22
Ok, I know that I've messed this up pretty well, but if someone can help me out, I'd really really appreciate it.
After a long struggle, I finally installed Ubuntu Hardy Heron on my Powerbook G4 (I'm not sure which version or how to find out.)
After a few more problems (black screen at start up, solution, in yaboot enter Linux video=ofonly nosplash)
Ubuntu was amazing, but unfortunately, unusable for me in most ways because I didn't have internet.  I got a Linksys Wireless-G Notebook Adapter with Speedbooster (it has 2.4GHz written on it too, so I'll include that.  It's a pretty old wireless card)and plugged it in.  I'm pretty sure the drivers worked, because I got a few more options on my network menu that I didn't have before.  It couldn't find my wireless internet though even on roaming mode and I got rather frustrated.  I eventually got it to show bars for my network, but said there was no service.  I typed in the passphrase and keyphrase a bunch of times in a number of different combination and it didn't work.  It was asking some questions I didn't know the answers to and weren't written down anywhere I could find on my windows or on the paper that came with the internet, or anything. Frontier is my internet provider if that makes any difference.
I tried automating the process above so Ubuntu would boot up without me helping it, following directions from another post that people said had worked.  I did something wrong though, instead of adding the command to a line I deleted the text already there and added just the command.  So, now Ubuntu wouldn't boot up.
Solution?  During installation, it asked something about networks that I skipped because I thought it would be easy to set up later.  So I thought, why not kill 2 birds with 1 stone and fix both the problems you caused to yaboot, and the internet, by simply reinstalling it over the old linux.  That's where I am now.  The installation started to go fine, for a second I thought it would work.  But now the CD I used last time with no errors isn't working.  And I can't eject it with F12.

I know I've probably messed this up pretty badly myself, but if anyone can help me out here, I'd really appreciate it.  I like to think of myself as good with computers, but up against Ubuntu I seem to have failed every time.

1. How do I eject the CD now?

2. Why isn't the CD working anymore?

3. Can some one guide me through setting up internet?

4. Can some one guide me through making yaboot use the command 
Linux video=ofonly nosplash every time it boots up so I don't have to enter it?

For the brief period I had it, I was really impressed with Ubuntu.  My battery was stronger, my computer didn't get as hot, the screensavers, etc..  Please help me get this working right so I can use it.

Thanks in advance.

Oh, almost forgot, I downloaded my version of Ubuntu from
[http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-alternate-powerpc.iso)
if that helps anyone.

I don't know how to tell what specific version my powerpc is other than its a powerbook G4, but if someone gives me instructions I'll find out.

My internet provider is frontier, I have an IP adress, a keyphrase, a passphrase, a username, etc...
I don't have a domain name, gateway, submask and probably one or two other things I can't remember from trying to get it to work

I haven't tried calling my internet provider for tech support, assuming that they wouldn't know much about Ubuntu.  I can try it, but first I have to get Ubuntu installed again.

Thanks.

---

### Post by stream303 on 2008-11-22
> **Danny Shumway said:**
> Ok, I know that I've messed this up pretty well, but if someone can help me out, I'd really really appreciate it.

First of all, you're not a failure.  PPC is no walk in the park, and if I had a dime for every time I bricked my machine...  You've reached out to the community, done some homework, got it to work, but later got into some trouble - even if you never get Ubuntu back on that machine, you can never say you failed because it appears you gave it your best shot.

Before we tackle anything I think the goal here is to just get a basic install working, and wireless can be tackled later.  To help later though, what is your environment?

1) Is this your only machine?
2) Do you have OSX installed on it, or is it dedicated solely to Ubuntu?
3) Does your broadband modem / router have an ethernet port from which you might be able to use a cable, temporarily?

Are you holding down the "C" key when rebooting to force the system to boot from the CD?  Alternately, have you tried holding down the "alt / option" key during reboot long enough to get to the boot icons from which to choose the CD as the boot device?

If you can get it to boot you may want to make a decision:  do I try to revive the original yaboot.conf, find my mistake and fix it in rescue mode with the vi editor, or should I just reinstall the whole mess again?

So the first thing to do is somehow get the cd to boot...

You can stop your need to enter video=ofonly nosplash by editing /etc/yaboot.conf as root by placing those options in both of the "append=" lines, and then doing sudo ybin -v

But first the cd boot issue.  Perhaps leave the wireless card out this time.  If you have a way to attach an ethernet cable jumper to your mac, so much the better.

---

### Post by Danny Shumway on 2008-11-24
Thanks for replying so quickly, and sorry for replying so late.  I wrote up a nice long reply two days ago and then hit the refresh button and lost it.
The answers to your questions-
1. Depends on how you look at it.  This is MY only machine, but we have a family Windows that I use more often.  I can't do anything to it, because it's not mine, but I can check or download things from it.
2. It's dedicated soley to Ubuntu, or at least I'd like it to be.  Right now, I don't think there's one operating system fully on at all.  I have the Mac OSX install CD, and I was thinking about overwriting Ubuntu to get the computer back to it's previous state, and then overwriting Mac to get it back to how I had it when Ubuntu was on.  If I have to put Ubuntu on as a secondary operating system that's OK, but I'd prefer to make it purely linux if at all possible.
3. I think so.  It'll hook up by phone-line to go online if that's what you mean.  I tried that when I had Ubuntu without any success.  If I can get it to work, though, I'm fine leaving that as permanent.  The laptop had some screen problems(hinge fell off) a long time ago so as long as I can remember it's been hooked up to a wooden frame.  I won't be moving it around much so wireless internet isn't a necessity, I had just hoped it would be easier to get working.

I can boot from the CD fine with C, I can't eject the CD with F12, though.  I didn't try alt/option, but I don't know if that will work.  I would be surprised if there was a workable version of Ubuntu on there, right now I think it's a mash between 2 of the same Ubuntus.

The "append=" lines is how I messed up in the first part.  Rather than add video=ofonly nosplash, I cleared everything but the "append=" for that line and then added it.
The line looked like
"append="video=ofonly nosplash
rather than, I think it was-
"append=""splash"video=ofonlynosplash
or something similar to that.  I can't remember the exact word.

You're right though, first off I'll try and get Ubuntu totally installed on there.  The CD worked perfectly before, it's confusing why it wouldn't work afterwords.  I'll fiddle around with it and try and get it working again.
Thanks again for getting back so quickly.

---

### Post by stream303 on 2008-11-24
> **Danny Shumway said:**
> Thanks for replying so quickly, and sorry for replying so late.  I wrote up a nice long reply two days ago and then hit the refresh button and lost it.

No problem - no time-schedule here.  Considering some of my rants, I kind of wish this would happen to me more often. :)

> This is MY only machine, but we have a family Windows that I use more often.  I can't do anything to it, because it's not mine, but I can check or download things from it.

Ok - best to check with the family "sysadmin" before doing anything drastic to it. :)  At least with a temporary ethernet jumper, it is likely you'll be able to get a better install experience- however it is possible the sysadmin has set it all up for static addresses and not dhcp, or perhaps the system is not set up to share multiple internet connections and the presence of a new machine borks the connection or broadband authorization etc.  Tread lightly. :)

> It's dedicated soley to Ubuntu, or at least I'd like it to be.

That makes the job even easier.  When it comes time for Ubuntu guided partitioning, just "use the whole disk", and everything will be wiped out and will start with a clean ubuntu-dedicated machine.

> It'll hook up by phone-line to go online if that's what you mean.  I tried that when I had Ubuntu without any success.

Unfortunately the software-driven modems are not ppc friendly, although there are some packages out there that might work at reduced speeds unless you pay for them.  I'd ignore the modem for now.

> I won't be moving it around much so wireless internet isn't a necessity, I had just hoped it would be easier to get working.

Maybe do one step at a time.  Get comfortable just getting it all installed, and customized with some manual configuration edits, and then tackle the wireless.

> I can boot from the CD fine with C, I can't eject the CD with F12, though.

One way of doing it temporarily is when booting up, hold down the CMD-OPTION-O-F keys, and when the openfirmware prompt shows up, type "eject cd" without quotes.  I also vaguely remember being able to hold down the "E" key when booting up to get it to spit it out.  Memory fails me on that one.

> The "append=" lines is how I messed up in the first part.

Well since you say you have a mishmash of stuff, maybe it is best to start over.  So this time, when you have to use those parameters at the second-stage yaboot boot: prompt (Linux video=ofonly nosplash) and you are back into a working machine, make a copy of the original.  This way, you'll be able to get into rescue mode to bring back the original if you mess up again.

```
sudo cp /etc/yaboot.conf  /etc/yaboot.conf.original
```

Now you can add those kernel parameters to the "append=" lines of /etc/yaboot.conf, followed by a *sudo ybin -v* to make it take affect for the next reboot.  The original file has been safely renamed in case you need to restore it.

Editing /etc/yaboot.conf means that you'll have to have root permissions, so use nano to do it with sudo:

```
sudo nano /etc/yaboot.conf
```
ctrl-o to write, ctrl-x to exit nano.

If for some reason you made some grave errors, and the system is borked again, you can boot with the install disk, but this time at the second-stage yaboot: boot prompt, type  (hitting TAB at this point will stop the countdown and you'll see your options, although Linux single works too)

```
rescue
or
Linux single nosplash
```

The system will appear to be installing again, but will stop short asking you where you'd like to be dropped into a root shell.  If you've chosen to "use the whole disk" when you originally partitioned the machine earlier on, you probably want to tell it to drop you into /dev/hda3 (or /dev/sda3).

Now, replace the pristine original yaboot.conf over the borked one:

```
cp /etc/yaboot.conf.original  /etc/yaboot.conf
```

Note that since we are in rescue mode, aka Linux single mode, we are already root, so there's no need for *sudo* to precede these commands.

and of course now do a
```
ybin -v
```
to make it notice the restoration of the original yaboot.conf. Now type exit to get out of the rescue mode.

Bingo - back to square one without having to reinstall.

Hope this helps!

---

### Post by Danny Shumway on 2008-11-24
I wish I had gone on here and checked this earlier tonight!
I might have linux installed now.  I'm not sure though, it was an interesting experience.
In any case it's good to know how to eject the CD.
Installation worked fine up to a certain point.  I'd selected the option to use the whole disk and everything worked fine up to 6% of "select and install software" then it told me the step failed.  I retried the step a few times with the same result, then chose an option to verify the CD.  It got half way through and told me there was an error and the CD might be corrupt.  I selected the option to eject the CD, and got an error message for that.  Still in the same installation, I retried the "Select and Install Software" step, then went downstairs.  I came up and found an error message on select and install software again, but at a different place.  Out of curiosity, I retried the step yet again and left it for a while.  When I went back up, "Select and Install Software had gone through with no errors, but there was a yaboot error.  I'm still not sure how, but the installation continued despite this, and a brief box popped up telling me that Ubuntu was installed fine, but yaboot wasn't, and I'd need to do some special command to get Ubuntu open.  Then it ejected the CD and gave me the option to restart.  That's where I am now, not sure whether to try it or not.
Will the instructions you gave me still work at this point to get back the old Ubuntu?
How can I boot with an install disk?  Will the PowerPC work as a live CD?
Do I put that code in when booting up the installer, or Ubuntu itself?

> Unfortunately the software-driven modems are not ppc friendly, although there are some packages out there that might work at reduced speeds unless you pay for them. I'd ignore the modem for now.

Yeah, my main concern right now is just trying to get the operating system working again.  Out of curiosity, is it possible to use the modem from the mac, or will that not be compatible?

This will be a huge help with yaboot, if it ever starts working.  I feel a lot more comfortable knowing there is a way to boot back up if I accidentally do something wrong again .  20/20 Hindsight, if I had posted about this 3 days ago, I could have used the process you wrote about to get in and never would have been in the fix I am now.  I kind of jumped into this without thinking.

---

### Post by stream303 on 2008-11-24
> **Danny Shumway said:**
> In any case it's good to know how to eject the CD.

I remember now .. hold down the mouse button (or left button on a non-apple mouse) while booting up.  Eject!

> I'd selected the option to use the whole disk and everything worked fine up to 6% of "select and install software" then it told me the step failed.

I normally get those long pauses every once in awhile while installing, but in your case I'll bet it is because you are not connected to the net, and things are just having to time out, like getting the right software repositories set up, etc.

Your CD might have been burned at just too fast a speed as well.  So the CD can be verified eventually, but the cdrom is doing a LOT of error-correction.  If you can, burn that image at a slow speed if you need to do it again.

> but there was a yaboot error.  I'm still not sure how, but the installation continued despite this, and a brief box popped up telling me that Ubuntu was installed fine, but yaboot wasn't, and I'd need to do some special command to get Ubuntu open.

I have only seen the yaboot error on install when trying to install to an external drive that it can't quite figure out.. hmmm

> Then it ejected the CD and gave me the option to restart.  That's where I am now, not sure whether to try it or not.
Will the instructions you gave me still work at this point to get back the old Ubuntu?
How can I boot with an install disk?  Will the PowerPC work as a live CD?

yes, yes, yes. :)

My gut feeling is like you said, this was kind of rushed.  Is there any way you can re-burn the Ubuntu iso, but at a very slow speed, say 2X or 4X?  Then try the install again by "using the whole disk".  Just a hunch, because you really shouldn't have troubles with yaboot finding an internal drive.

I'm just wondering if the data was laid down without too many errors to begin with.

However, you've got nothing to lose at this point.  You could try to boot from the existing install cd, and at the yaboot boot: prompt, type *Linux single* and just see what happens to get some familiarity with the process.

---

### Post by FredSambo on 2008-11-25
Another way to eject a cd is to use the emergency button.  If you have a slot loading drive, you can straighten out a paper clip and stick it into the far right hand side of the slot, there is a button in there that will force the disk to eject.

[IMG]http://km.support.apple.com/library/APPLE/APPLECARE_ALLGEOS/HT3064/88068_1.gif[/IMG]

On my tibook there isn't a specific hole, as pictured above.  Just stick the paper clip all the way to the right in the slot and you'll feel it slip into the button hole.

---

### Post by Danny Shumway on 2008-11-27
Sorry for not posting sooner, but with Thanksgiving I haven't had much time to play around with Ubuntu.  
Thank you both!  I can eject CD's now!
I tried using the computer in the state it was and typing Linux single as well as anything else I could think of.  I kept telling me a file was corrupt.  
I'm still confused about why the CD's acting like this.  I burned it as slow as 1X when I made it, and it worked flawlessly before.  I checked it and there's not a smudge or scratch to be found.  This is just confusing.
I reinstalled Mac OSX and am going to try one of two things.
Either-
1. Try and reinstall with this CD.  I don't know about this, it's becoming very clear to me that the CD is corrupt.  I don't know how it got that way, but I'm pretty sure it is.
2. Make a new CD and try and reinstall with that.  Like you said above, I think this is the best choice.  If I do this, I'm leaning toward just upfront using Intrepid Ibex instead of 8.04.  Maybe an updated version might solve a few problems.

The other thing I was wondering is, there is a point during the mac OSX installation where the drive is completely wiped but Mac isn't installing.  If I restart the computer then, it'll be completely empty.  Do you think that would help?

---

### Post by Danny Shumway on 2008-11-30
I reinstalled Mac without any trouble, then I tried the alternate powerpc installer for Intrepid Ibex, then I retried the installer for Hardy Heron.  Both told me now that no CD drive was detected.  I'm confused about this.  If it couldn't find the CD drive, why did it boot up the installer?  Maybe the problem isn't with my installation disks, it's that my CD drive is starting to go bad.  What do you think?

---

### Post by pxwpxw on 2008-12-01
It could be this one -

The ubuntu-8.10-alternate-powerpc Installer-CD failes to detect the CD-ROM Drive.
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by Danny Shumway on 2008-12-02
That's the EXACT message I got.  Thank you so much, I'll try it tonight.

---

### Post by Danny Shumway on 2008-12-03
Thanks, I'll look at this right away.  It's exactly the same message!

---

### Post by Danny Shumway on 2008-12-03
That worked perfectly!  Thank you so much!  I have Ubuntu 8.1 fully installed, now to deal with the rest of it.

Can some one give me a walk through for setting up either wireless or wired internet?

Can some one help me automate a task with yaboot?
I'm pretty sure I know how, but would like to confirm it first.  I'll


Is there a way to get sound set up?


On a side note, help won't load in 8.1 for some reason.  Does anyone know what's going on with that by any chance?

Thanks again.  It's great to have Ubuntu back.  And I even got the ability to activate the wobbly windows too!

---

### Post by pxwpxw on 2008-12-03
Can you call this thread SOLVED and start a new thread for the next thing you want to do, there is too much there for me.

You should look at the Sticky for PowerPC (top of this forum), it has links to setting up info.

Also the people at the ppclinux.info link in my signature below may be able to help you.

---

### Post by Danny Shumway on 2008-12-04
Will do.  Thank you all for your help so far.

---

