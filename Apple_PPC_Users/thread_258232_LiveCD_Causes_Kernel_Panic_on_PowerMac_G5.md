---
title: "LiveCD Causes Kernel Panic on PowerMac G5"
date: 2006-09-15
forum: Apple PPC Users
---

### Post by mac57 on 2006-09-15
Hi all, I downloaded Dapper-Drake PPC from this very site and burned the live CD, hoping to try it out with my Mac. I have a new PowerMac G5, 2.3 GHz dual core, 2.5 GB RAM and 250 GB hard disk. The machine is only a few months old. 

I took the newly burned LiveCD and loaded it into my Mac. Then I restarted and after a bit offiddling (have to hold down the OPTION key while booting) I was able to select the CD and boot from it. 

The initial loader came up and so I
know that the CD burn was sane. I hit ENTER and off it went. It churned
through all the expected startup stuff, I saw X Windows come up (the
distinctive "X" cursor showed up in the middle of my screen) and
then....  well, it sort of stopped. The "X" was replaced with a proper
pointer arrow head, the screen painted itself a flaming red color, and
that was it. It just sat there, and sat there, and sat there. Finally,
I clicked a button on my mouse. 

Now I have never seen a kernel panic on
my Mac, but I am guessing that this is what happened at that point,
since immediately after clicking, the fans on my G5 suddenly revved up
to full throttle, making enough noise to drive any living soul out of
the room. The Mac did not respond to keyboard, mouse OR the on/off
switch. I had to turn off the power bar to kill the infernal noise.

So, not much success, and it left me a little scared. Would OS X boot
again? Thankfully it did. I am not sure I am going to take any further
steps with Dapper Drake!

...unless of course someone else has had this experience and knows just
what the trouble was. If so, please let me know.

---

### Post by mac57 on 2006-09-16
Bump.

Anybody? I can't be the first person to have tried to load the Dapper Drake LiveCD onto a bog standard PowerMac G5. Does anyone have any suggestions?

Thanks!

---

### Post by stmiller on 2006-09-17
The kernel image on the live CD doesn't support the thermal parts of the powermac G5. Nor sound, and not video for most.

To install ubuntu on a G5, you must use the alternative install CD, install in text mode, then download and compile a kernel from kernel.org with a g5_defconfig kernel config.

See my thread here:

[http://ubuntuforums.org/showthread.php?t=232908](http://ubuntuforums.org/showthread.php?t=232908)


And please use the search function of the forum. I searched for powermac G5 and got many threads:

[http://ubuntuforums.org/search.php?searchid=8224986](http://ubuntuforums.org/search.php?searchid=8224986)

---

### Post by kellogs on 2006-09-17
maybe its a mistake on the livecd, by default if your mac is dual, you need to start the cd with a different install option.

Press TAB at yaboot, and type install-powerpc64-smp (something like this you will see
 pressing tab).

If this does not work, procceed with the above instructions.

---

### Post by mac57 on 2006-09-17
Thanks all. I have been kicking around the world of linux for two years now and have configured and built just about everything at one time or another, right down to building KDE 3.3 from scatch once (took 11 hours!). However, one thing I have NEVER been successful with is building kernels. To date, every effort I have made has failed miserably. 

If I have to build and install a kernel to get Ubuntu running on my PowerMac G5, I guess I will have to let this idea go, which is a real shame. 

In producing a PPC version, who does the Ubuntu team think is going to be the prime audience if not Mac users on PowerMac devices? It seems odd that this sort of thing wouldn't be tested ahead of time and be made to work.

By the way, I did use Search, and found LOTS of articles as suggested. Most suggested I needed to build a kernel. I hoped there was a better way, perhaps a set of boot options, based on my above suggestion that surely the Ubuntu team would have tested their PPC version on a Mac, the most commonly available PPC platform. I am surprised (and saddened) to find that this is not the case.

Thanks again everyone. I guess I will have to wait for Edgy and try again then. Perhaps it will have been tested on a Power Mac by then.

---

### Post by stmiller on 2006-09-17
Compiling a kernel is not hard!!! Read post #5 in that link I gave you. I put down step-by-step instructions. It's not that bad, really. It just sounds scary.

Ubuntu is WONDERFUL on the powermac. The only other distro out there that I got to boot and work on a powermac G5 was Gentoo. If you think compiling a kernel is a headache.... try gentoo! It's a very involved process. 

Fedora may have better powermac support now. I'm not sure. But our choices are limited, unfortunately.

And: I DOUBT that edgy will suddenly support these G5 machines. In fact, I REALLY doubt it will all of a sudden 'just work.' Since these machines in general need a specific kernel config.

The ubuntu images for ppc in the past are just generic ppc kernel configs, that work for most G4 machines.

---

### Post by mac57 on 2006-09-18
OK, thanks. One last question. I want to continue to be able to boot Mac OS X, so I am looking for a dual boot setup. Can I force the installer to install onto an external firewire drive? I would then be in a the position of being able to boot Ubuntu by just turning on the external drive and rebooting. When I wanted to run just OS X I could leave the external drive off. 

Essentially, I am trying to recreate what I used to have for Windows. I lived and worked in Linux except for iTunes and Photoshop. iTunes was obvious as there just isn't a Linux equivalent. Photoshop was required vs. GIMP simply because it is so much more powerful AND (and key) it supports color management, one of Linux's last major downfalls.

So, I would like to live and work in Linux on my PowerMac G5, and just boot over to Mac OS X when I need to run iTunes or Photoshop. Does this sound do-able, or do I have to let Ubuntu take over my main drive?

---

### Post by mac57 on 2006-09-20
stmiller, I have now got Ubuntu running on my x86 PC, and I must say, I am impressed. Now I am really motivated to get it going on my PowerMac G5.

Did you use the exact "recipe" you gave in article 5 of the post you referenced above to get things going on your PowerMac G5 (you appear to have the same model I do, except with the 2.0 GHz chips instead of the 2.3 GHz)?

Thanks - I am about to take the plunge but REALLY don't want to screw up Mac OS X. Cheers.

---

### Post by stmiller on 2006-09-21
Ubuntu can install to a Firewire drive. You just have to make sure it is on and connected when the installer runs, and point to that drive. Might have to google that for more details. When it is all installed, to boot from it you may have to resort to holding down the 'Option' key on the keyboard, which would let you choose what disc you want to boot from.

I had my system partitioned, in my case. When installing OS X on the bare drive, I choose the disk utility at the start of the OS X installation (top menu option) and made a partition for Linux, leaving it as unformatted free space. Then installed OS X on the other HFS+ partition.

So I installed OS X, then installed Ubuntu, pointing ubuntu's installer to install in the free space.

I just compiled the latest 2.6.18 kernel. It has updated defconfigs for PPC, to take advantage of all new stuff. There is a new audio driver (snd-aoa) for the powermac sound card. It works much better than the previous driver, which had volume issues. You have to add snd-aoa to the file /etc/modules. And take out snd-powermac from that file, if it is listed.

And the fans are quieter with 2.6.18. The computer is VERY quiet. 

Sleep/suspend does not work with the powermac G5s, unfortunately. But Linux runs VERY well on the G5. More efficient that OS X, esp with recent kernels. I might do some Handbrake benchmarks in OS X vs. Ubuntu and see how the performance is.

---

### Post by mac57 on 2006-09-21
Thanks, I'll let you know how it goes. I will be installing to an external firewire drive, since I am loathe to do a clean install of Mac OS X at this point. I do plan to do that when Leapard arrives however, so at that time I will partition the main drive and get both OS-X and Linux onto the main disk. Thanks again for all your help!

---

