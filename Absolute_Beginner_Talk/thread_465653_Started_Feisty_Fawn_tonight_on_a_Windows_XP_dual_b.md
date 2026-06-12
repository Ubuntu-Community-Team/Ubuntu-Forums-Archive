---
title: "Started Feisty Fawn tonight on a Windows XP dual boot system"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Kaffekane on 2007-06-05
So far, I've had some mixed experiences using Ubuntu.

One of the good experiences is that I LOVE using this operating system.  Another is that I enjoy browsing the software repository,

The bad experiences that I had involved not being able to use internet access through wi-fi right off the bat (I know from previous posts that I've seen just how much of a problem it actually is), but I had to switch to a wired network about a month later anyway when I was using Windows because my network kept on dropping its connection over and over, and my hard drive started failing anyway.

So I try installing Ubuntu a second time a few weeks after getting a wired connection and a new hard drive.  Dual boot setup and everything, and while I'm configuring Ubuntu, I'm not even aware of the factor that Windows would no longer boot.  Had to reformat everything and re-install Windows.  That was the second bad experience that I've had so far.

Third time's a charm, eh?  Not in this case.  I just installed Feisty Fawn tonight, and now UBUNTU WON'T BOOT, even though Windows still will.  

I'm using Ubuntu through the Live CD at the moment, and I'm wondering exactly what kind of problem that I'm running into.  It's not GRUB, or I'd be getting Error 15.  I don't think it's my graphics card...least I don't think it is yet.
But whenever I go to boot Ubuntu, it'll go through the loading screen, and then stops with a couple lines of text on it.

EDIT:  Here's what it says:
* Checking battery state....                        [ OK ]
* Running local boot scripts (/etc/rc.local)    [ OK ]

It won't do anything past that.  Can anyone point me in the right direction to fix this problem?

---

### Post by tdrusk on 2007-06-05
Try reinstalling Ubuntu on the partition your broken Ubuntu is on. Something obviously went wrong.

If you install Ubuntu after Windows you need to defrag Windows about 20 times so the files aren't scattered and deleted.

---

### Post by Kaffekane on 2007-06-05
Thanks.  That thought had crossed my mind for a moment.

---

### Post by RelativelyQuantum on 2007-06-05
It's good to hear that you like the OS, but, as mentioned previously, something is obviously wrong. I'm not sure what it could be from its discription. I haven't experienced any of these problems personally, but then again I only *upgraded* to Feisty; I started out with Edgy. There seem to be bugs associated with a fresh install of 7.04. If you felt like it, you could download the Edgy images and upgrade to Feisty that way. 

Again, just a suggestion.

---

### Post by durrell on 2007-06-05
I definitely had problems with my first insall of Feisty, I'm on my 2nd install now and everything is working seamlessly. Windows even seems to be having less of an issue with dual-booting from the same hard drive now. I'd definitely say reinstall and see what happens.

---

### Post by Kaffekane on 2007-06-05
Reinstalling Feisty Fawn did indeed help, because now I'm on Ubuntu and not needing the Live CD for the time being.

I'll need to check up on Windows in a bit to make absolutely sure that everything's okay, but the first installation was to basically help re-size the NTFS partition since Windows XP didn't have any sort of way for me to do that.

And getting ahold of some third party program to do it would have still been just as much hassle as trying to partition through XP anyway...

---

### Post by Rocket2DMn on 2007-06-05
When I setup my dual boot a week and a half ago, I reformatted the whole deal.  I then proceeded to install XP first onto the NTFS partition (the only partition).  Before doing anything else with Windows I installed Feisty, giving it about 30 gigs (of the 80).  Everything went fine, and I was able to setup each OS to see and work with the other partition.  

If you need to start over, this might be a good path to follow.
Good luck!

edit: PS: check your md5sum for the ubuntu disk ISO!

---

