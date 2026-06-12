---
title: "no boot screen after upgrade"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-06-20
This isn't so much a "problem" as it is a curiosity.  I have a Dell Dimension 2300 and I recently hooked a 19" ws monitor up to it.  When I was using Dapper everything was fine, but  when I upgraded to Edgy (and to Feisty since then) I no longer got a boot up screen (or whatever it is you call the screen with the Ubuntu logo and the scrolling bar beneath it to show the progress of the boot).  It doesn't cause any problems, I eventually end up with a log in screen, I'm just curious as to why it isn't there anymore. Any ideas?

---

### Post by Happy_Man on 2007-06-20
Yeah, I have the same problem, and I don't know why. Perhaps the usplash was not loaded correctly upon upgrading?

---

### Post by e^(i*pi) on 2007-06-20
Glad to hear that I'm not the only one this has happened to.  It doesn't really hurt anything, but it is kind of annoying.  Does anybody have any ideas about how to fix it?

---

### Post by diatribe on 2007-06-20
check your /boot/grub/menu.lst and make sure that next to your kernel it says "quiet" and "splash", minus the quotation marks

---

### Post by e^(i*pi) on 2007-06-20
Thanks for the suggestion. I checked and it does say "quiet" and "splash".

---

### Post by diatribe on 2007-06-20
does it show text scrolling or just a blank screen?

---

### Post by Happy_Man on 2007-06-20
Text on bootup for me.... but on shutdown it just gives a blank screen. Not even a cursor. Quite odd.....

---

### Post by e^(i*pi) on 2007-06-20
blank screen on boot up and shutdown for me

---

### Post by Sipes on 2007-06-20
Same here, I'm also on a Dell Dimension 2400, seems ever since feisty no splash screen, I don't get text I just get a black screen until the boot screen finally appears.  Damned Odd.

---

### Post by e^(i*pi) on 2007-06-21
Damned odd indeed.  At first I thought it may have been something to do with Ubuntu, but then I upgraded on my laptop and everything worked perfectly.  It is interesting that this seems to be the only thing that stopped working after the upgrade.  Don't get me wrong, I'm glad it was only one thing and a trivial thing at that, but still strange.  I've been googling around for an answer, but nothing promising yet.  I will keep at it though, and maybe in the meantime this thread will catch the eye of someone in the know about this issue.

---

### Post by Sipes on 2007-06-21
Maybe it has something to do with the hardware then, possibly the on board intel?  I wonder if that other chap also has on board intel video?

---

### Post by Happy_Man on 2007-06-21
> **Sipes said:**
> Maybe it has something to do with the hardware then, possibly the on board intel?  I wonder if that other chap also has on board intel video?
Nope, a Nvidia card.

---

### Post by Sipes on 2007-06-25
Bump

---

### Post by Sipes on 2007-07-02
So I guess everyone in the community is at a loss?

---

### Post by 3ark on 2007-10-21
Same thing here. Although on feisty it worked just fine for me. Now that im on kubuntu gutsy its entirely blank on shutdown and boot up. ATI card, AMD Turion. I'm not too good with this stuff but is their a package we could reinstall or something?

---

### Post by arthur_kalm on 2007-10-22
I'm having the same problem here but I was sort of able to fix it (only in the shutdown it worked). The problem lies in the fact that usplash assumes that your monitor can handle a resolution of 1280x1024. However, my widescreen Inspiron 6400 only handles 1280x800.

If you edit '/etc/usplash.conf', you can set the xres and yres. I set my xres to 1280 and my yres to 800. Unfortunately this only worked on shutdown and not on bootup. I'll try with a lower res and post back.

---

### Post by arthur_kalm on 2007-10-25
Changing it to 800x600 resolution doesn't seem to have changed anything. The initial boot splash still doesn't show up. So any suggestions?

---

### Post by frankob on 2007-10-27
I found a solution in another thread of this forums...

After editing usplash.conf you should write: "sudo dpkg-reconfigure usplash".
And that should do it. It worked for me. :-)

---

### Post by executor on 2007-10-27
> **frankob said:**
> I found a solution in another thread of this forums...

After editing usplash.conf you should write: "sudo dpkg-reconfigure usplash".
And that should do it. It worked for me. :-)

it workt greate thanks  :)

---

### Post by PickPocket8686 on 2007-10-28
> **frankob said:**
> I found a solution in another thread of this forums...

After editing usplash.conf you should write: "sudo dpkg-reconfigure usplash".
And that should do it. It worked for me. :-)

Can you post a link to that thread?

It didn't work for me.  Something else I've noticed, if I use the 32 bit version of Gutsy Gibbon I get a boot screen, but when I use the x64 (live CD, or text CD) I get no boot or shutdown screens.

PC Specs.
AMD Opteron 165
DFI nForce4 Ultra-D
2x 1GB G.SKILL
XFX GeForce 8600GTS
Sound Blaster Audigy SE
Dell E228WFP 1680x1050 Resolution Monitor
Seagate 300GB IDE 7200.8
Western Digital 150GB SATA Raptor
Pioneer DVR-112L

I thought the problem might be with the widescreen resolution of my monitor, so I tried installing with a Dell E198FP 1280x1024 resolution monitor.  But I didn't get any change.

After that I thought it might be something wrong with the x64 disk I burned since I was getting a boot screen with the 32 bit version.  So I tried booting from the x64 disk on my Windows machine.  Sure enough, I get a boot screen on that computer.

Windows PC Specs
AMD Opteron 175
ASUS nForce4 A8N-SLI
2x 1GB Crucial
Some cheap ATI Video Card (I'm not sure exactly which ATI card it is and sense I'm reinstalling Windows on the PC at the moment I can't really find out.  But I'll update this post when I find out the model #)
Dell E198FP 1280x1024 resolution monitor
Western Digital 74GB SATA Raptor
Seagate 300GB IDE 7200.8
NEC ND-3500A

I'm going to try switching the 8600GTS with a 7100GT I have somewhere in the basement to see if that fixes it.

Anyone have any other ideas?
Austin

Edit: I also had the same problem with Feisty Fawn.

---

### Post by Crafty Kisses on 2007-10-28
> **frankob said:**
> I found a solution in another thread of this forums...

After editing usplash.conf you should write: "sudo dpkg-reconfigure usplash".
And that should do it. It worked for me. :-)

There's one fix. :)

---

### Post by PickPocket8686 on 2007-10-28
> **Codename said:**
> There's one fix. :)

Yes, but unfortunately it doesn't work for me.
I'm hoping "frankob" will post a link to that thread so I can do some more reading up on the subject.

---

### Post by gobuntu on 2007-10-28
THIS WORKED FOR ME:

I first changed my /etc/usplash.conf, from incorrect values put there by the installation, to 1440 x 900, which is what my HP laptop takes, and then did two console commands:

sudo dpkg-reconfigure usplash
sudo /etc/init.d/gdm restart

The first command updates the frames, as per other postsers do it manually (seems to me), and the second command RESTARTED the system in LARGE mono text-only letters, and actually hang up (froze) at some point, while trying to restart.

So I turned the laptop OFF by the switch (keep it pressed for a few seconds), and then switcheched it ON again. My pc goes to a double-boot GRUB menu, and from there, Ubuntu-Gutsy-Gnome was started perfectly A LOT FASTER, meaning that before this fix, my system was taking way too long to boot from the black screens.

It also shuts-down with correct screens now.

---

### Post by PickPocket8686 on 2007-10-28
> **gobuntu said:**
> THIS WORKED FOR ME:

I first changed my /etc/usplash.conf, from incorrect values put there by the installation, to 1440 x 900, which is what my HP laptop takes, and then did two console commands:

sudo dpkg-reconfigure usplash
sudo /etc/init.d/gdm restart

The first command updates the frames, as per other postsers do it manually (seems to me), and the second command RESTARTED the system in LARGE mono text-only letters, and actually hang up (froze) at some point, while trying to restart.

So I turned the laptop OFF by the switch (keep it pressed for a few seconds), and then switcheched it ON again. My pc goes to a double-boot GRUB menu, and from there, Ubuntu-Gutsy-Gnome was started perfectly A LOT FASTER, meaning that before this fix, my system was taking way too long to boot from the black screens.

It also shuts-down with correct screens now.

Nope, this didn't work for me ether.  It did seem to freeze when I ran "sudo /etc/init.d/gdm restart" and I had to eventually restart the computer.  But it still didn't give me a boot screen.

BTW: I forgot to add, that I installed Gutsy 64 Bit and I had boot and shutdown screens (with live CD, and without) but I had to reinstall Ubuntu..  Problem was since I reinstalled I don't have boot or shutdown screens anymore...  I've since tried to reinstall about 20 times but I still can't get the boot and shutdown screens back (Live CD or from a new installation).

---

### Post by frankob on 2007-10-30
Hi, "PickPocket"! Uff... I finally found it again... I lost the adress of that thread before, so I had to find it again and it wasn't easy, believe me...

Well, the link is [http://ubuntuforums.org/showthread.php?t=583876](http://ubuntuforums.org/showthread.php?t=583876) :-)

But, people on that thread agreed that the solution I wrote here before, too, works fine, so I'm not sure it will be of much help for you... :-/ But take a look anyway.

---

### Post by gobuntu on 2007-10-30
> **PickPocket8686 said:**
> Nope, this didn't work for me ether.  It did seem to freeze when I ran "sudo /etc/init.d/gdm restart" and I had to eventually restart the computer.  But it still didn't give me a boot screen.

BTW: I forgot to add, that I installed Gutsy 64 Bit and I had boot and shutdown screens (with live CD, and without) but I had to reinstall Ubuntu..  Problem was since I reinstalled I don't have boot or shutdown screens anymore...  I've since tried to reinstall about 20 times but I still can't get the boot and shutdown screens back (Live CD or from a new installation).

My laptop is also a 64 AMD computer.

However, I after much consideration to what I want to do in Linux, I did resolve not to use the 64 bit versions till compatibility problems with the things I want to explore are surmounted by development teams.

So far, it seems to me, 64 bit, for somethings, are not quite there yet.

In particular drivers for hardware. 

If drivers for hardware, being some proprietary, are not settled yet on 32 bit, much less-so in 64 bit.

If one wants to explore 64 bit, then the basic things will work fine.

I have setup my disk partitions so I can, using backups, explore various installations and versions.

But I, for now, feell I get the most of whatever I am interested in on the i686 architecture.

---

### Post by PickPocket8686 on 2007-10-30
> **frankob said:**
> Hi, "PickPocket"! Uff... I finally found it again... I lost the adress of that thread before, so I had to find it again and it wasn't easy, believe me...

Well, the link is [http://ubuntuforums.org/showthread.php?t=583876](http://ubuntuforums.org/showthread.php?t=583876) :-)

But, people on that thread agreed that the solution I wrote here before, too, works fine, so I'm not sure it will be of much help for you... :-/ But take a look anyway.

Thanks for the link.
I actually just switched my 8600GTS with a 7100GS and I get boot screens again.  Seeing as I don't plan on doing any gaming the 7100GS should be more then enough for me.
Also with the 8600GTS I couldn't boot into Ubuntu with the restricted drivers installed (x64 or x32) but it works fine now with the 7100GS.

Thanks again, for everyones help,
Austin

---

### Post by prankstar008 on 2007-11-02
> **frankob said:**
> I found a solution in another thread of this forums...

After editing usplash.conf you should write: "sudo dpkg-reconfigure usplash".
And that should do it. It worked for me. :-)

I don't know why I didn't think to do this earlier?  Thanks a lot, worked for me and decreased boot time...  Before, the only way I could boot was to hit ctrl+alt+F1 and for some reason that would unfreeze my boot.

---

### Post by piousp on 2007-11-14
dpkg-reconfigure usplash works really nice! :KS

Thank you frankob!!

---

### Post by frankob on 2007-11-28
No problem. :-)

---

