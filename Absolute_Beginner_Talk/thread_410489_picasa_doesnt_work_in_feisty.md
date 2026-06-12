---
title: "picasa doesnt work in feisty"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by searayman on 2007-04-15
i just up-graded to fesity and i downloaded and installed picasa and when i try an open it, it doesnt come up. But when i look in system monitor it says it is running?

---

### Post by qamelian on 2007-04-15
It's working fine here in feisty. DId you have any trouble / error messages when you installed it?

---

### Post by searayman on 2007-04-15
> **qamelian said:**
> It's working fine here in feisty. DId you have any trouble / error messages when you installed it?

nope none at all, this is really bugging me!

---

### Post by qamelian on 2007-04-15
> **searayman said:**
> nope none at all, this is really bugging me!

Bizarre. I don't use it myself. I just installed it to see if I could help with your problem. I find it to be a real resource pig on my laptop. 

Have you tried starting it from a terminal window to see if you get any feedback that might help identify the issue?

---

### Post by searayman on 2007-04-15
> **qamelian said:**
> Bizarre. I don't use it myself. I just installed it to see if I could help with your problem. I find it to be a real resource pig on my laptop. 

Have you tried starting it from a terminal window to see if you get any feedback that might help identify the issue?

nothing happens

---

### Post by qamelian on 2007-04-15
> **searayman said:**
> nothing happens

Out of curiosity, how did you install it? Did you double-click on the deb file and let GDebi install it or did you install it from the command line with dpkg?

---

### Post by searayman on 2007-04-15
> **qamelian said:**
> Out of curiosity, how did you install it? Did you double-click on the deb file and let GDebi install it or did you install it from the command line with dpkg?

i first installed it by double clicking on the .deb and had the same problem, then i looked aorudn on google and found a repo then i installed it from there, and i still have the same problem...

---

### Post by qamelian on 2007-04-15
> **searayman said:**
> i first installed it by double clicking on the .deb and had the same problem, then i looked aorudn on google and found a repo then i installed it from there, and i still have the same problem...

Okay. I also installed it by double-clicking on the deb. I'm at a loss, but I'll keep thinking about it. Sorry I haven't been more help.

---

### Post by Emerzen on 2007-04-15
Did you search Synaptic to see if it's in the repo's?  I know there's also a Picasa2 now.

---

### Post by true_friend on 2007-04-15
Try installing it through Automatix may a change help...
now out put in terminal is strange there should be some errors at least when u type "picassa"(or what name of application) in a terminal.

---

### Post by searayman on 2007-04-16
> **true_friend said:**
> Try installing it through Automatix may a change help...
now out put in terminal is strange there should be some errors at least when u type "picassa"(or what name of application) in a terminal.

ok just tried automatix to install picasa and that too gives me the same results....

any more ideas why this is happening?

---

### Post by searayman on 2007-04-16
ok i also just tried the bin version too and i get the same thing..... WHat could the problem be? coudl somethign be wrong with my x maybe? cause i was having trouble gettign nvidia drivers to work so i cant use my nvidia card....

---

### Post by diatribe on 2007-04-16
n/m misread

---

### Post by Maestro23 on 2007-04-16
Running Feisty w/ATI X1600.  Just went to the picasa site and d/l the .bin

Installed with no problems and it is scanning my computer for all my pics as I type this.  

You said you have trouble with installing Nvidia drivers.  What graphics card are you running now?

---

### Post by searayman on 2007-04-16
> **Maestro23 said:**
> Running Feisty w/ATI X1600.  Just went to the picasa site and d/l the .bin

Installed with no problems and it is scanning my computer for all my pics as I type this.  

You said you have trouble with installing Nvidia drivers.  What graphics card are you running now?

you can check out my nvidia problems here: [https://bugs.launchpad.net/ubuntu/+bug/106906]("https://bugs.launchpad.net/ubuntu/+bug/106906")

but in the xorg i changed nvidia to vesa and now i can at least get into the gui

---

### Post by searayman on 2007-04-18
any more ideas? this is killing me?

---

### Post by mgmiller on 2007-04-22
I have an nvidia 7800 GT running the nvidia drivers from ubuntu repositories and just upgraded from edgy to feisty.  I had been using picasa a lot and have over 1000 pics in it.  It had been getting very sluggish towards the end and I read that as the database of pics increases, it tends to bog down.  I started using f-spot as an alternative which works well, but does not have the same ability to search and other features I came to like in picasa.  After the feisty upgrade, picasa flies!  It runs as fast as f-spot and I couldn't be happier.  I added the google repository to my sources.list and use synaptic to install and keep it upgraded.

```
# Google Picasa for Linux repository
deb http://dl.google.com/linux/deb/ stable non-free
```

---

### Post by rifazmohamme on 2007-05-06
i installed picasa but can't run
it says  

/dev/nvidia0 or /dev/nvidiactl are not accessable. Picasa will crash if these file are not accessible.
 it says to run chmod 666 /devnvidia0 /dev/nvidiactl

i did that but still the same prob

---

### Post by staib on 2007-05-06
I have Picasa running fine in 7.04 (with Envy nVidia drivers), but there several issues:

The slide show only seems to run in a small size (800 x 600 or less?), although manually you can go to full size and page through the show - but you do then lose the smooth transition. 

I know there is an option to tick if you want full size slide shows, but it seems not to work.

Uploading to Blogger (at least the new blogger) does not work at all (which is a real pain).

Does anyone know if there are workarounds for any of these things yet, or are we all waiting for the next version of Picasa for Linux to address this?

Cheers,

Nick

---

### Post by thebrade on 2007-05-07
I'm having a problem as well. Picasa installs properly and starts scanning my photos, but always freezes after about a minute (on a different picture each time). I have to force quit and restart. It may be related to other problems I've had on feisty with freezing. An app will fade to gray and not respond. Sometimes it wakes back up after too long of a time, sometimes not. It's kinda pissing me off since I didn't have these problems w/ edgy...

---

### Post by TheDoulos on 2007-05-20
I've got both Ubuntu *and* Kubuntu Feisty installed in separate partitions...Installed Picasa from Google's Debian / Ubuntu .deb file on both installations...Picasa runs fine under Ubuntu, but does **not** run under Kubuntu.

Clicking on the Picasa icon causes some activity while it runs the /opt/picasa/bin/picasa script, but I can't tell where it's failing.

---

### Post by phetre on 2007-05-21
Rifazmohamme, I had this problem with the secondary account on my machine (Ubuntu 7.04 Feisty), and all I had to do was:
1. From the main Ubuntu menu, choose System / Administration / Users and Groups.
2. In the "Users settings" window, click "Manage Groups."
3. Click "Add Group."
4. In "Group Name" enter "video" (without quotation marks).
5. In the list underneath, select each user that wants to use Picasa.
This grants those users access to the files, and at least for me, solves the problem. Thanks to whoever it was who first figured this out -- I can't find the post anymore! :(

---

### Post by martinquested on 2007-06-15
Phetre, sounds good, but it doesn't help me.

I too am using Kubuntu, and I have just upgraded from Edgy to Feisty.  It worked under Edgy, but now nothing happens.  Exactly as described above, the process is running, according to "ps" but nothing is visible at all.

Help!

---

### Post by martinquested on 2007-06-15
OK, I've pretty much got it working now.  I had to reboot because I couldn't kill all the processes, it appeared.  Two things I've changed before the reboot - one of them was the key.  One was to change the group stuff as described above.  The other was to sort out my ntfs-3g problem.  I had to simplify my /etc/fstab file, so that I simply used the "defaults" option for my windows (ntfs) partition, with no groups or anything else, as per the ntfs-3g.org website.  Now, after a reboot, picasa works.

Except it's just crashed.  But I'm sure that is a different problem...

---

### Post by phetre on 2007-06-15
Martinquested, glad to hear you've (mostly) got it working now. Good luck with the rest!

As a side note, I've recently switched to Kubuntu and am now trying Digikam. It's nowhere near as glitzy as Picasa, but it seems really powerful, so if you continue to have trouble with Picasa, you might want to give it a try.

---

### Post by Brutus2006 on 2007-06-15
I had the same problem I rebooted and it was there.

---

### Post by FerhatBingol on 2007-07-05
try Latest Picasa2 for Windows with Wine. You do not need to install over Wine.

Just copy the Picasa2 directory (24.6mb) to your Linux box from a friend and run with wine.

It has also WebAlbum upload option.   ;)

---

### Post by mik9dt on 2007-07-13
Now here is a funny thing,
I cannot get picasa to run and have tried everything in this thread to no avail.:confused:

Some history : I had picasa working on Edgy. When Feisty came along I did not do a clean install, I updated from Edgy to Feisty using update manager.

I cannot get picasa to work.

Last week I made a new login for my daughter, guess what... on her login picasa works just fine.

Now, I have tried to remember just how I installed picasa ... I'm sure I have installed from the google site, although when I had difficulties I have tried to un-install and then reinstall with automatix. I can't remember with sufficient detail to be forensic about this.

Something about picasa in my home directory must clearly be wrong, but that something is not corrected by removing and reinstalling picasa. Investigations continue...

---

### Post by RomeReactor on 2007-07-13
Hi everyone. Just a suggestion: I don't know if any of you have tried this, but according to [Picasa'a FAQ page]("http://picasa.google.com/linux/faq.html#10b"), if you have a home network (sharing files, printers, etc.) it is recommended that on the first run, you tell it to scan **only your desktop**. I would suggest deleting the **.picasa** folder on your home directory (just open Nautilus, press CTRL+H, look for the **.picasa** folder, delete it, press CTRL+H again, and close Nautilus), then run Picasa again and do just that. Hope this helps.

---

### Post by Ltselan on 2007-08-14
Thanks RomeReactor.  Deleting the .picasa folder solved my problem.  I had Picasa previously working, and after a Linux update it stopped working.  Once again I appreciate the good suggestion.

---

### Post by mik9dt on 2007-08-15
Thanks are due to RomeReactor.
Deleting the .picasa folder solved my picasa issues at last.
:)

---

