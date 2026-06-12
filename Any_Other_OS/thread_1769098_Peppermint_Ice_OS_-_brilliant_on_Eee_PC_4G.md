---
title: "Peppermint Ice OS - brilliant on Eee PC 4G"
date: 2011-05-27
forum: Any Other OS
---

### Post by BigSilly on 2011-05-27
Just wanted to post up here, because I know a lot of users are having trouble finding that one true OS that works well on the venerable old Asus Eee PC. Ours is a 701 4G Surf model, and it's been terrific. Up until recently it was running Ubuntu UNR 10.04 which was great, but it was a little slow and I felt it needed a change. For some reason I couldn't successfully complete a Puppy Linux install, which was my first choice for a lightweight OS. GRUB never installed properly and I couldn’t fix it so it would boot. I tried a few others such as Lubuntu, but there were issues installing there too.

Then I discovered [this little known distro]("http://peppermintos.com/2010/07/introducing-peppermint-ice/"). Blimey this thing is really something on the wee machine! Flash is still a little slow (but then it's slow everywhere isn't it?), but that's about the single only issue I have with this brilliantly fast and easy Linux. It comes based on Ubuntu (which suits me perfectly), and takes some things from Mint too, but features the OpenBox window manager, and is stripped of other applications, leaving it a dedicated internet OS. Though I will add you can still install anything you like from the Ubuntu repos.

It's just fantastic on the Eee and I wanted to bring it to your attention if you're an Eee fan still searching for something great. I don't think you'll be disappointed with this at all.

Give it a go! :)

---

### Post by tomerof on 2012-02-09
Thank you!
i have been looking for lightweight OS to my old eee PC ^_^

---

### Post by drawkcab on 2012-02-10
I don't see how it would be that much different than Lubuntu.

---

### Post by Plumtreed on 2012-02-10
> **tomerof said:**
> Thank you!
i have been looking for lightweight OS to my old eee PC ^_^

The initial post predates the intro of Peppermint Two which is somethig to  consider.....still lightweight, fast etc.

...also consider installing Jupiter to improve battery time and operation of your eeePC701...........google 'Webupd8 Jupiter' for a 'Howto' and for the extra step for 701 users.

---

### Post by BigSilly on 2012-02-11
> **drawkcab said:**
> I don't see how it would be that much different than Lubuntu.

In my defence I posted this last year, and have since discovered Lubuntu. ;)

Peppermint is excellent though. :)

---

### Post by brus brother on 2012-03-08
Can someone help me with the Peppermint-Two install. Is this the same as Peppermint Ice??? I tried unsuccessfully with Peppermint-Two. It says it finished and showed me the intro screens but never offered the option to continue live or reboot.
Is there anything I need to set in the bios before changing the OS? Advanced/Operating system? Fast boot disable or enable??
I like how sleak Peppermint-Two is but have tried installation twice and had to go factory reset twice to get the li'l fellow up and running again.

---

### Post by drawkcab on 2012-03-09
I think you have to turn fast boot off in the BIOS.

---

### Post by brus brother on 2012-03-09
> **drawkcab said:**
> I think you have to turn fast boot off in the BIOS.
In the Bios Setup Utility:
Under Boot,  there are three options. Quiet Boost and Quick Boost under Boot Settings Configuration and there is also Boot Booster under Boot Settings. 
Also, do I need to change OS Installation under Advanced Settings?
What settings should I be using?

---

### Post by Plumtreed on 2012-03-09
PeppermintTwo is the most recent version and fits and works nicely on my eeePC 701SDX.

I don't remember any particular problem in installing it.....I don't recall any special steps. 

Perhaps you should take us thru your install procedure...are u installing from a CD or USB?

---

### Post by drawkcab on 2012-03-09
> **brus brother said:**
> In the Bios Setup Utility:
Under Boot,  there are three options. Quiet Boost and Quick Boost under Boot Settings Configuration and there is also Boot Booster under Boot Settings. 
Also, do I need to change OS Installation under Advanced Settings?
What settings should I be using?

I think you just need to deselect quick boot--quiet boot is fine.

The only other thing to think about is whether or not the installation exceeds 4GB.  If Xubuntu requires 4+GB to intall I bet the installation will hang.

---

### Post by brus brother on 2012-03-09
Deslected quick boot and am trying again.
Using USB stick md5checksum of download ok.
Boot from USB dongle.
Wait very long time to run live.
Used the following directions: from [http://peat.me.uk/2011/12/24/breathing-life-into-eee-pc-g-surf/](http://peat.me.uk/2011/12/24/breathing-life-into-eee-pc-g-surf/)
"it won&#8217;t install straight off the USB drive. To get it to install you have to boot into Peppermint from the USB drive, use alt-F2 to run a command, and type the following:
gksu gedit /usr/lib/ubiquity/plugins/ubi-prepare.py
Then on line 310, change &#8220;min_disk_size = size * 2&#8221; to &#8220;min_disk_size = size * 1.4&#8221;
Author above was right as I couldn't get it to install past the language selection page without that change.
Used the full 4G disk for the install.
Once again it "completed" but am left with the spinning wheel!:confused:
Well I gave up on waiting for the spinning wheel, rebooted from hard disc and waddayaknow, it's Peppermint.

---

### Post by brus brother on 2012-03-09
I'd like the quickest startup for this machine.
In User Settings, Password asked on login is greyed out. I'm only admin and can't change this. Any suggestions?
Can I automatically by pass the grub menu screen with options of os, recovery, memtest etc?

---

### Post by Plumtreed on 2012-03-10
Great news, it is good to hear that you have got Peppermit working. To keep you in the picture there is a 'new' version promised soon and I would suggest you visit the Peppermint Forum to keep up to date and check out all the tutorials.

Don't forget to get Jupiter installed to improve battery time.......google 'Webupd8 Jupiter'.......there is an extra step to take to get extra features specific to the eeePC.

---

### Post by drawkcab on 2012-03-10
There used to be a gui tool called start up manager that would let you edit your grub configuration.  Also you should be able to set your OS to log you in automatically.

---

### Post by brus brother on 2012-03-13
> **drawkcab said:**
> There used to be a gui tool called start up manager that would let you edit your grub configuration.  Also you should be able to set your OS to log you in automatically.
Peppermint comes with Startup Manager installed but that doesn't seem to make much of a difference.
What I have run into is a situation where sometimes the system starts as I want, straight to OS, but sometimes the grub menu comes up on startup. On some occasions if I hit enter for the OS, it will proceed and other times it goes back to the grub menu until I do a hard restart. I have tried changing the timeout time in the Startup Manager but that doesn't seem to make any difference. Tried with battery and on outlet, quick and quiet boot on or off but still get a grub menu with no apparent rhyme or reason. Even did a fresh install, allowing it to go to the screen "Continue live/Restart".
For the sake of spreading info, I found the following tutorial for enabling autologin:
1. Hit Alt+F2 to bring up a run dialog and type "gksu pcmanfm" to open the file manager as root and enter your password. Note: I got a false error about the password but just click OK and continue.
2. Navigate to /etc/xdg/peppermint/lxdm and open the configuration file there.
3. Uncomment (delete the # sign and preceding space) in front of the lines for "autologin" and "session", then change the username dgod (who was the guy who wrote LXDM) to whatever your username is. 
I will continue to check on updates to P'mint but would appreciate any thoughts on the demonic possession related to grub menu occurrences.
Thanks

---

### Post by brus brother on 2012-03-16
> **brus brother said:**
> 
What I have run into is a situation where sometimes the system starts as I want, straight to OS, but sometimes the grub menu comes up on startup. On some occasions if I hit enter for the OS, it will proceed and other times it goes back to the grub menu until I do a hard restart. 
PROBLEM SOLVED: Bad stick of RAM was the apparent cause. Switched out and all has been well.
Now to install Jupiter.
Thanks for all the suggestions.

---

