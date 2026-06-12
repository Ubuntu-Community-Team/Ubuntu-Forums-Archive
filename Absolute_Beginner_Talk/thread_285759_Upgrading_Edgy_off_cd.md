---
title: "Upgrading Edgy off cd"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2006-10-27
HI,

I am a student and I need to buy data from my service provider. I have downloaded the alternate install cd for edgy in the hopes of upgrading from the cd as I was told by the wiki would work. It has cost me R 100.00(about $14.00 US) to download the ISO and now the thing doesn't want to work. Can Some one please tell me how to upgrade from the cd? Or at least check that the ISO is not corrupted? I have written it to disc twice already.

Thanks in advance for any help! 

Cheers,

Rudolf

---

### Post by RudolfMDLT on 2006-10-27
just restarted and did an integrity test. The disk is fine. Here is what I did and the errors that I get:

When i add the disc to the repo's everything seems fine. I click "mark all upgrades" and then when the upgrade should begin I get this error:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

Tried using upgrade manager:
gksu "sh /media/cdrom0/cdromupgrade"
and got this:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

---

### Post by RudolfMDLT on 2006-10-27
doing an upgrade via synaptic, downloading all 645 mb's. This sux. [-(

---

### Post by Wight_Rhino on 2006-10-27
Sorry Man,

My CD wouldn't boot as it wouldn't recognize my Nvidia Driver "No Screen Found"!

---

### Post by toasted on 2006-10-27
Sorry to hear that Rudolf. With all the good things you've done for people in Ubuntu I would think someone would help you now in return. I would, but I won't be updating my Dapper install anytime soon so I have no experience to work with. 

All I can say is use caution and maybe think twice about updating Dapper if it is anything that you rely on.

---

### Post by myname on 2006-10-27
> **RudolfMDLT said:**
> Tried using upgrade manager:
gksu "sh /media/cdrom0/cdromupgrade"
and got this:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

I haven't even been able to get the gksu "sh /cdrom/cdromupgrade" to work, all I get is:

bash: gksu: command not found

I am using Kubuntu, so I tried gksudo, and same thing, then I tried just sudo, same thing, I switched to /cdrom/ and saw the cdromupgrade file, ran sh on it, and got the following:

Could not find the upgrade application archive, exiting

Would be nice to be able to upgrade from the CD and not have to download the files AGAIN.

Sorry if that last sentence sounded harsh, but I am a fairly new user, was excited about Edgy, grabbed the ISO last night, and when I follow the upgrade steps here: 

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

DOH!  a co-worker just informed me that I don't have the Alternate install CD, but the desktop CD.. GARRRRGGGHHHHH!

--kevin

---

### Post by dupa on 2006-10-27
> **RudolfMDLT said:**
> HI,

I am a student and I need to buy data from my service provider. I have downloaded the alternate install cd for edgy in the hopes of upgrading from the cd as I was told by the wiki would work. It has cost me R 100.00(about $14.00 US) to download the ISO and now the thing doesn't want to work. Can Some one please tell me how to upgrade from the cd? Or at least check that the ISO is not corrupted? I have written it to disc twice already.

Thanks in advance for any help! 

Cheers,

Rudolf

try to use
apt-cdrom

---

### Post by dupa on 2006-10-27
Add the edgy repositories to sources.list

Insert the cdrom and try with:

```

sudo apt-cdrom add
sudo apt-get update && sudo apt-get dist-upgrade

```

---

### Post by RudolfMDLT on 2006-10-27
Hi guys! Thanks!:)  thats all I can say! Thanks, the people on this forum Rock!

As for upgrading off the cd. I found these to threads, needless to say, TOO late! If you wish you could try the following:

[https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)

The second one is just for interest.

The idea being, by using the top method, you should be able to copy all the deb files from the alternate cd(i am not going to be as bold as to say you could use this with the desktop version) to a folder on your computer and then synaptic should be able to do a version check and update all the necessary dependencies.

I would really appreciate it if a Old Hat Linux guru could maybe either call the above plausible(then I will try it tonight, I'm still downloading the update) or just shoot it down saying why.

Thanks,

Rudolf

PS: Sorry Dupa, tried that, no go.

---

### Post by RudolfMDLT on 2006-10-27
Myname,

Sorry, just read your post!

That line won't work, i don't know why the heck they put it in the wiki in the first place. 

Click in places, click on computer, open up the cd-rom drive that the ubuntu cd is in. press and hold Ctrl + L. copy the location of the cdrom and paste it in the terminal. Now add the cdromupgrade sh script to the end.

This:

sh /cdrom/cdromupgrade

should look something like this:

sh /media/cdrom0/cdromupgrade

Hope this sorts you!

Cheers!

EDIT: I run Ubuntu but use the KDE core files. IE, not Kubuntu, but an Ubuntu hybrid, ie I'm running KDE but not Kubuntu. If you are running kde be sure you downloaded the Kubuntu ISO as the Ubuntu Upgrade removes all KDE!

---

### Post by myname on 2006-10-27
I think my problem was that I didn't have the "alternate Install CD"  I am going to try that, as well as your suggestion.

As far as your running Ubuntu with KDE, do you see any problems with that, not being a "true" install (k)ubuntu?

I like the Ubuntu core, but the only thing I don't like is the way the toolbar rotates the applications when I move it from the bottom to the right side.  

--Kevin

---

### Post by RudolfMDLT on 2006-10-27
Actually, i read a post by Asui, the orange and white cat, that said that running Ubuntu and then installing the KDE core files afterwards makes "Kubuntu" run a lot faster. So I never really tried Kubuntu.

I saw that you didn't have the alternate cd, i just posted the link for interest. If the alternate also fails you then you might want to try it though.

Goodluck with that, I really hope that the alternate works directly! The one advantage with the Ubuntu install and then KDE you get the best of both worlds. i use KDE but I use the Terminal(gnome) instead of Konsole, open office comes with gnome and is Microsoft compatible where Koffice is not. Gparted is one of the best partition editors around in my opinion.

So yeah, I mix and match the two.

---

### Post by hkgonra on 2006-10-27
> **RudolfMDLT said:**
> HI,

I am a student and I need to buy data from my service provider. I have downloaded the alternate install cd for edgy in the hopes of upgrading from the cd as I was told by the wiki would work. It has cost me R 100.00(about $14.00 US) to download the ISO and now the thing doesn't want to work. Can Some one please tell me how to upgrade from the cd? Or at least check that the ISO is not corrupted? I have written it to disc twice already.

Thanks in advance for any help! 

Cheers,

Rudolf

I am still trying to wrap my mind around paying for data from your isp. That is a new one on me.

---

### Post by RudolfMDLT on 2006-10-27
hkgonra,

I live in South Africa, it's a great Country and all(And I'm quite a patriot), but it has the worlds highest crime rate and you pay your *** of for internet. We pay R 250/month for line rental and then a further R225/month for 2GB of data. We pay for having the ADSL(256 kb/s downstream, though you only every get 40kb/s international bandwidth) line and then again for using it. Now this line is purely for educational/academic purposes so for any "junk downloads" like a 700mb Update I need to purchase a 1GB "Booster package" for R 100.00. In US Dollar terms I pay $ 63.33/month for the line and 2GB of data and another $13.33 per gig. Does this make it a little clearer?

[http://www.mweb.co.za/home/join/adsl_pricing.aspx](http://www.mweb.co.za/home/join/adsl_pricing.aspx)
The exchange rate is about $7.5/R1.00

---

### Post by hkgonra on 2006-10-27
Thanks, I understood what you meant I had just never heard of paying for how much you use your internet. 
All I have ever heard of is you pay for x amount of pipe ( speed or bandwidth however you want to say it), whether you use it continually or hardly at all.

---

### Post by myname on 2006-10-27
> **RudolfMDLT said:**
> I saw that you didn't have the alternate cd, i just posted the link for interest. If the alternate also fails you then you might want to try it though.


Nope, the alternate CD did not work, I get a message saying that it can't find gksu.  Is that installed by default with KDE?  

Since I started the update via the web, and cancelled it, I can no longer connect to the net with my KDE box.  oy vey!

I may just bite the bullet and install (k)Ubuntu fresh on this box.  Since it's my alternate boot on my work machine, what I call my test rig, I won't muck up my home system which runs it full time.  :)

--Kevin

---

### Post by RudolfMDLT on 2006-10-27
Yes, we both pay the same amount for Pipe/bandwidth, i just get nailed on the amount! But hey! this thread is turning into a big negative on the forums!

---

### Post by hkgonra on 2006-10-27
BTW, I don't know what kind of firewall/router you have but if it is linux firewall you may benefit from this type of thing. 

[http://www.advproxy.net/update-accelerator/](http://www.advproxy.net/update-accelerator/)

It caches updates so that you only get them once and it caches them on the firewall and if you ever need them again or need them for another machine on your network it gets them locally.

---

### Post by RudolfMDLT on 2006-10-27
hkgonra,

Thanks, but we use a Netgear Wireless ADSL router. 

The problem was definitely the update manager or the ISO. as the ISO checked out I can only conclude that the Dapper upgrading "tool", be that synaptic, aptitude or what ever wasn't designed then, for now. or the ISO was released without conforming to a predetermined structure so that Synaptic could use it... :rolleyes:

---

### Post by myname on 2006-10-27
After a couple different attempts to get my Dapper upgraded to edgy at work I just did a fresh install of Edgy, nothing big to lose there since I used it as my test bed.  

As for my home machine, I use the general rule of thumb "If it's working, don't break it."  :)  I will wait a while before I upgraded to the latest version, since everythng here seems to be working fine.

Thanx for all your help, but I am unsure why I can't get the upgrade to work of CD, and I don't want to wait the time to have it re-download off the net.  

Quick question though, why isn't there an "upgrade" option on the boot menu when we boot to the CD?

--Kevin

---

### Post by RudolfMDLT on 2006-10-27
As for boot upgrade you'll have to ask the developers!? Sorry! :)

I'm running edgy now with Gnome and KDE. 7 hours of upgrade. Honestly, I see very little different! And now I have to get my ATI graphics working from scratch! If you want to know all the trouble that is check out the ATI link in my signature.

Anyway, good night to you! Today has been a Helova fight and a waste! But I'm glad I'm running the latest and the greatest! :)

Cheers,

Rudolf

PS: You don't sound like the ego type who need to run the latest and the greatest! :) Don't, it's painful! I have one rule i dish out to everyone else but never listen to myself: "If it's not broke, don't fix it" :D

---

### Post by myname on 2006-10-27
I did boot the live CD, and do like the little visual changes they have done, so a complete system install may be the way to go.

I didn't have as much trouble as you getting the ATI drivers installed, just read your link, so hopefully that would go smoothly, and I didn't understand half the stuff about rebuilding the kernal so who knows.

I may just wait it out a bit to see what other issues/fixes come out.  I really wish gnome would fix the window list issue, that's my biggest peeve about gnome.

Have a good weekend.


--K

---

### Post by toasted on 2006-10-29
Greets! Glad to see your thread take off 

Your ATI thread is the one that I finally used to get 3D in Dapper. Now Edgy won't work correctly. I installed the .28 drivers initially but they broke with an Edgy update and Ive yet to get them working again. 

How is your Edgy install working 3D wise and what did you use to get it working?

---

### Post by RudolfMDLT on 2006-10-30
I'm updating my post for edgy now, check out the first post.

---

### Post by toasted on 2006-11-01
> **RudolfMDLT said:**
> This sorted out my card but I have a severe fps drop! I would suggest sticking to Dapper until this is sorted out in Edgy.
(from ATI post)

I agree. In fact, Edgy seems to have way more trouble than its worth!

---

### Post by RudolfMDLT on 2006-11-01
It's okay once it's running but my system is still far from error free! I've sorted out most KDE bull, but I still can't start Gnome without that bug report thing popping up. And the fact that 3D isn't working is a real pain in the butt!

If you've got some trouble, write them down and lets see if we can't hack away at them! 

Shot!

Rudolf

---

### Post by toasted on 2006-11-02
I don't use it enough to discover bugs due to no 3D. I have read about lots of troubles though so maybe someone else will chime in. Video is my first thing to tackle. I plan to try the new 8.30 drivers later today. Just released - yesterday maybe.......

---

### Post by RudolfMDLT on 2006-11-02
Cool! I mist that! I'll download it aswell! Thank you!

---

