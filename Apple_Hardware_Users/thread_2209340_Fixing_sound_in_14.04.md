---
title: "Fixing sound in 14.04"
date: 2014-03-05
forum: Apple Hardware Users
---

### Post by rsavage on 2014-03-05
I have sound working on my iBook (late 2004 12") using snd-aoa.  Previously this used snd-powermac.  I want top submit a patch so this will work out-of-the-box.  For this I need the help of other users of *different machines*.  Particularly if you are a snd-powerrmac user and it all stopped working in 12.10.  Before I post longer instructions, I'm after volunteers to run a script and check out a few things for me. Please sign up here.

---

### Post by theos911 on 2014-03-05
Count me in if applicable. I've got:
Powermac G3 B&W
iMac G3 700
iBook G3 466
Powerbook G3 500

---

### Post by oibaf2 on 2014-03-05
I also have a iBook G4 12".

---

### Post by rsavage on 2014-03-07
Thanks Theos and oibaf2.  

I think to start with it would be good to get a list of device-ids that are affected by the problem.  On a working install (e.g. 12.04) open alsamixer, hit F2, select /proc/asound/cards.  Mine is listed as

PowerMac Snapper (Dev 38) Sub-frame 0

I think the 38 is the device id.


This script gives a bit more information:

```

#! /bin/sh

for dir in $(find "/proc/device-tree/" -type d); do
    name="$(cat "$dir/name" 2>/dev/null || true)"
    device_type="$(cat "$dir/device_type" 2>/dev/null || true)"
    compatible="$(cat "$dir/compatible" 2>/dev/null || true)"

    # sound/ppc, sound/oss/dmasound
    if [ "$name" = awacs ]; then
        # probably best to go for ALSA
        echo "awacs snd-powermac"
    elif [ "$name" = davbus ] || [ "$name" = i2s-a ]; then        
        for child in "$dir"/*; do
            if [ -f "$child/name" ]; then
                childname="$(cat "$child/name" 2>/dev/null || true)"
                if [ "$childname" = sound -a ! -f "$child/layout-id" ]; then
                    echo "no layout-id"
                    echo "child is ..." 
                    echo $child
                    echo "device-id is ..."
                    cat $child/device-id
                    echo ""
                fi
            fi
        done
    fi
done

```

e.g for me

```

no layout-id
child is ...
/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound
device-id is ...
&

```
If you look up the ASCII value for "&" it is 38 so that ties in nicely.

If you don't get any output then you are a snd-aoa user.

---

### Post by oibaf2 on 2014-03-07
Note: I have no idea if my iBook is affected by this audio problem, I am using 12.04 and never upgraded because I was affected of [bug 1066435]("https://bugs.launchpad.net/bugs/1066435")[ Fixing recursive fault but reboot is needed!]("https://bugs.launchpad.net/bugs/1066435"). So I don't really know if this info is really useful...

I get this on alsamixer:
```
PowerMac Snapper (Dev 44) Sub-frame 0
```

and this is the output of the script:
```
no layout-id
child is ...
/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound
device-id is ...
,
```

---

### Post by theos911 on 2014-03-07
Powermac G3 B&W 12.04:
PowerMac Burgundy (Dev 4) Sub-frame 0

```
no layout-id
child is ...
/proc/device-tree/pci@80000000/pci-bridge@d/mac-io@5/davbus@14000/sound
device-id is ...
```
The bottom line includes a small box with three zeroes and a 4 in the lower right corner.

---

### Post by rsavage on 2014-03-07
> **oibaf2 said:**
> 
I get this on alsamixer:
```
PowerMac Snapper (Dev 44) Sub-frame 0
```

A patch for you is already in the latest kernel.  You should be able to use snd-aoa in 14.04, so just make sure your aoa modules are not blacklisted.  You may have to modprobe snd-aoa-i2sbus.

---

### Post by rsavage on 2014-03-07
@ theos

When you try a recent kernel does alsamixer open?

---

### Post by theos911 on 2014-03-07
Do you want me to try a newer kernel on 12.04 or install 14.04? (Note: I'm not even sure what exactly we are testing or fixing. I'm just contributing whatever I can since I still have Xubuntu on it.)

---

### Post by rsavage on 2014-03-08
Have you got a live iso of anything beyond 12.04?  I don't need anything installing just a recent kernel to be run (can be on debian).  

If you try a live-iso from 12.10, maybe 13.04 or 13.10 then you might get a "fixing recursive fault reboot is needed".  This is the obvious sympton that something is wrong with sound.  If you do boot, open alsamixer.  If it doesn't open then you more than likely have a machine that used to use snd-powermac, but now probably should be using snd-aoa.

Since the debian-installer needs to be changed it is good to see your output even if you don't have the problem.  I think all the problematic machines will have i2s-a in the 'child is...' line, but you have davbus. davbus users will continue to use snd-powermac *I think*.

---

### Post by theos911 on 2014-03-08
I am currently downloading the PPC Lubuntu 13.10 Desktop ISO. I will try it on my B&W, but if I do not get stopped at the fixing recursive fault reboot is needed error I don't have high hopes that r128 is going to configure correctly for a live session.

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-27
Sound is not working for me on my iBook G3/800 Lubuntu 14.04

Here is why..

[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-27
Oh, one more thing alsamixer does **NOT** work in 14.04 for me

---

### Post by rsavage on 2014-04-28
> **TREESofRIGHTEOUSNESS said:**
> Oh, one more thing alsamixer does **NOT** work in 14.04 for me

Expected.

I wanted to submit a kernel patch to get this fixed on most machines, but I had virtually no interest at the time.  I submitted a patch for my machine, but received no feedback from the powerpc developers list and so don't think it got included in the kerenel.  Maybe I should of just sent it to the alsa developers list instead, but I've lost interest at the mo (I'm going to stick with 12.04).

---

### Post by TREESofRIGHTEOUSNESS on 2014-04-28
Are you using Lubuntu?  Or a mini iso install?  I had Debian on it earlier, but wanted to try out Lubuntu on it (I really like Lubuntu).  But, for a minimal environment I suggest JWM (don't forget to install menu), and you can use something like pcmanfm for the desktop and filemanager, or if you are really brave you can use ROX...
unless of course you have a machine powerful enough for something like Xubuntu...

Can you tell me the main gist of what I should look for.  I gather it is a kernel module that is not loading.  So, do I simply run a sudo modprobe model_name?  Can you give me a hint as to where to start?

---

### Post by rsavage on 2014-04-28
I'm not interested in a minimal install, I use compiz+mate with all its bells and whistles.  I do have the latest pcmanfm installed too, since caja can be slow (even on my faster intel machine).  

It is not the sound that is putting me off using 14.04, it is the slowness of xorg.  Window dragging seems to be on a go slow.  Scrolling in firefox is sluggish etc.  If I were to use 14.04 then I would use Xubuntu since at least radeon KMS seems to vaguely work in that when you turn the compositor on.

Re sound: I added another comment to the bug report that I hope gives somebody enough bread grumbs to follow.

---

### Post by John_Ross_Hunt on 2014-04-29
No sound with my machine either.

PowerBook G4 12"
PowerBook6,4

```
[FONT=Monaco]no layout-id[/FONT][FONT=Monaco]child is ...[/FONT]
[FONT=Monaco]/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound[/FONT]
[FONT=Monaco]device-id is ...[/FONT]
[FONT=Monaco]([/FONT]
```

---

### Post by este.el.paz on 2014-05-02
> **rsavage said:**
> 
It is not the sound that is putting me off using 14.04, it is the slowness of xorg.  Window dragging seems to be on a go slow.  Scrolling in firefox is sluggish etc.  If I were to use 14.04 then I would use Xubuntu since at least radeon KMS seems to vaguely work in that when you turn the compositor on.
Re sound: I added another comment to the bug report that I hope gives somebody enough bread grumbs to follow.

@rsavage:

Finally got around to booting the liveDVD of 14.04 in my G4 iBook again . . . wasn't following the thread when you first posted, but if you need another bash sample from my 12.04 savage edition system . . . let me know.  Actually I haven't had sound in 12.04 in the iBook, although I do in the G4 iMac . . . so maybe better to use the iMac.  ***Whenever*** you feel like playing with it again . . . .  

But, I'm with you on the "window dragging seems to go slow" comment . . . even for me, it's obviously slow in Lubun 14.04 . . . but scrolling in FF seems OK[edit: nah, you are right, scroll is slo].  I have a nice display using the "radeonfb" gambit, was thinking I might go for it, but, so far it's not a jump up, it seems like a "lateral" move . . . not enough time to fiddle with it.

Also got the "Alsa error: snd_mixer_attach failed.  No such file or directory"  And in FF tried to test Pandora and got a message "In order to use Pandora please upgrade to a more recent browser or install a newer version of Flash (v.10 or >)" . . . .

Seems like even the basics are not quite ready for the non-techie user . . . .

e.e.p.

---

### Post by TREESofRIGHTEOUSNESS on 2014-05-02
Hi,
Adobe is in charge of Flash, and do not make a version for PowerPC Linux.  You can install one of the alternative flash viewers like Gnash.  In fact adobe does not make flash for Linux any longer.
Since there is no powerpc build of Chrome(ium) with the Pepperflash plugin you must stick to HTML5 sites, or use something else like gnash or lightspark

---

### Post by theos911 on 2014-05-03
There are a number of desktop and command line tools for Pandora. They use less resources than the Flash site and work cross platform. I personally like pianobar.

---

### Post by este.el.paz on 2014-05-03
@ToR & theos911:

Thanks for the replies and the data on the flash alternatives . . . not a major issue for me, I was just reporting in this thread that not only was sound not working, but obviously Pandora reads the browser as "old" . . . whereas I'm pretty sure in 12.04 I can play videos in FF . . . but, as I mentioned sound is not working in the iBook . . . .  But good to know there are some work arounds.

While I was still booted in 14.04 I ran "lsmod" and quite a number of "snd" modules showed up in the list . . . seems odd that they aren't working?  Or, is it just some special module that works with Mac?  Anyway, no rush to 14.04 here . . . .

e.e.p.

---

### Post by TREESofRIGHTEOUSNESS on 2014-05-03
See this bug for sound:
[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)
This is inherited from Debian.
There are some instructions there for how to fix it...
Please mark the bug as affecting you

---

### Post by este.el.paz on 2014-05-03
@ToR:

Did that bug report thing . . . mentioning that this seems to have cropped up in the Xu 14.04 install I have on my MBPro . . . .

e.e.p.

---

### Post by rsavage on 2014-05-04
> **John_Ross_Hunt said:**
> No sound with my machine either.

PowerBook G4 12"
PowerBook6,4

```
[FONT=Monaco]no layout-id[/FONT][FONT=Monaco]child is ...[/FONT]
[FONT=Monaco]/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound[/FONT]
[FONT=Monaco]device-id is ...[/FONT]
[FONT=Monaco]([/FONT]
```

That's device id 40.  You must have the same machine as Stefan [https://lists.debian.org/debian-powerpc/2013/09/msg00031.html](https://lists.debian.org/debian-powerpc/2013/09/msg00031.html)

---

### Post by John_Ross_Hunt on 2014-05-09
> **rsavage said:**
> That's device id 40.  You must have the same machine as Stefan [https://lists.debian.org/debian-powerpc/2013/09/msg00031.html](https://lists.debian.org/debian-powerpc/2013/09/msg00031.html)

It is, except his patch is slightly wrong.  The PowerBook6,4 needs this:
[COLOR=#000000]
.connections = tas_connections_nolineout,

instead of this:
[/COLOR]
[COLOR=#000000].connections = tas_connections_all,[/COLOR]

[COLOR=#000000]There isn't a dedicated line-out on the PB6,4, it's a headphone jack that toggles with the internal speaker.  And the line-in toggles with the built-in microphone.  Stefan's patch works, but alsamixer displays a phantom line-out device that's not connected to any hardware.  PB6,4 is nearly identical to the PB6,8, which uses "tas_connections_nolineout".[/COLOR]

[COLOR=#000000]Now, the question is how to get the linuxppc-dev folks to accept patches.  I've seen several sound patches posted on their mailing list (a couple for my machine as well), but it doesn't look like they ever get committed.  It doesn't look like anyone is maintaining the sound drivers at the moment.[/COLOR]

---

### Post by rsavage on 2014-05-09
Well you could try sending the patch to the alsa-devel list instead - [http://mailman.alsa-project.org/mailman/listinfo/alsa-devel](http://mailman.alsa-project.org/mailman/listinfo/alsa-devel)

---

### Post by daniel_gustafsson2 on 2014-07-08
I have an iMac G4 (ilamp) and sound has been broken, in more than one way, since lubuntu 12.04 or so.
Spending the last few days trying to install a working distro again, 11.04 doesn't seem to be available.
Tried all the fixes I've read (using snd-aoa instead of snd-powermac, without success)

At any rate, MintPPC 9,3 works now.
cat /proc/asound/cards gives me:
PMac Snapper - PowerMac Snapper
PowerMac Snapper (Dev 33)  Sub-frame 0
**edit:** using snd-powermac

System specs are (iMac G4 1GHz/17"):
Machine Model: PowerMac6,1
CPU Type: PowerPC G4 (3.3)
CPU Speed (1 GHz)
Boot rom: 4.5.9f1

Any ideas what I need to do in order to get sound working under 14.04?

---

### Post by este.el.paz on 2014-07-09
> **daniel_gustafsson2 said:**
> I have an iMac G4 (ilamp) and sound has been broken, in more than one way, since lubuntu 12.04 or so.
Spending the last few days trying to install a working distro again, 11.04 doesn't seem to be available.
Tried all the fixes I've read (using snd-aoa instead of snd-powermac, without success)

At any rate, MintPPC 9,3 works now.

Any ideas what I need to do in order to get sound working under 14.04?

d_g2:

The problem with MintPPC 9.3 is that it is, uh, "old" . . . I think it was about 2 years ago when I first got into linux that I was installing MintPPC on my iMac/iBook . . . that's a loooonnngggg time ago . . . .

It's interesting, because when I first installed 12.04 on my iLamp sound worked fine . . . then a few months ago with a kernel upgrade it went away . . . due according to anonymous sources, to the Debian "hw-detect" bug . . . which means that the system doesn't recognize the machine . . . and so doesn't load the proper modules to bring full capacity . . . including sound.  So, then some folks are going back to earlier kernels to get function, but eventually that brings other problems with compatibility/dependencies . . . .

Possibly the 14.04.1 update due out later this month ***might*** bring some fixes for PPC . . . but, frankly it does seem like PPC is dropping lower on the radar screen . . . and stuff like these bugs and problems with sound aren't getting the attention needed . . . .  My iMac is running fine, probably has a few years left in it . . . what runs best on it?  Actually OSX 10.4.11 with Ten4Fox+perian is now doing better than 12.04, whereas a few months ago 12.04 had more capacity . . . on the iMac.  I'm looking forward to seeing how 14.04.1 does on the iBook . . . .

e.e.p.

---

### Post by rsavage on 2014-07-12
> **daniel_gustafsson2 said:**
> I have an iMac G4 (ilamp) and sound has been broken, in more than one way, since lubuntu 12.04 or so.
Sound should work in 12.04.  What is the exact problem you have? e.g. does alsamixer start?

> 
Any ideas what I need to do in order to get sound working under 14.04?
It could be the same as 12.04, it maybe more complicated.

> **este.el.paz said:**
> d_g2:
It's interesting, because when I first installed 12.04 on my iLamp sound worked fine . . . then a few months ago with a kernel upgrade it went away . . . due according to anonymous sources, to the Debian "hw-detect" bug . . . which means that the system doesn't recognize the machine . . . and so doesn't load the proper modules to bring full capacity . . . including sound.  So, then some folks are going back to earlier kernels to get function, but eventually that brings other problems with compatibility/dependencies . . . .

Hmm... not sure about that eep. It certainly will not be the hw-detect bug on an already working system.

> 
Possibly the 14.04.1 update due out later this month ***might*** bring some fixes for PPC . . . but, frankly it does seem like PPC is dropping lower on the radar screen . . . and stuff like these bugs and problems with sound aren't getting the attention needed . . . .  
This thread was started by me to fix sound in 14.04 before it was released.  Before that Stefan over on the Debian mailing list tried to get help.  Nobody contributed therefore it was not fixed.  The only people to blame are the ppc users.

> 
My iMac is running fine, probably has a few years left in it . . . what runs best on it?  Actually OSX 10.4.11 with Ten4Fox+perian is now doing better than 12.04, whereas a few months ago 12.04 had more capacity . . . on the iMac.  I'm looking forward to seeing how 14.04.1 does on the iBook . . . .

If you really must have the latest and greatest then I think openSUSE is probably a good option.  Otherwise, stick with 12.04 is my recommendation.

---

### Post by este.el.paz on 2014-07-12
> **rsavage said:**
> 
Hmm... not sure about that eep. It certainly will not be the hw-detect bug on an already working system. 

@rs:  Nice to hear a comment or two from you again . . . but, on the "hw-detect bug" issue, I'm just repeating what I saw said to others or to me on the lubuntu users list in terms of the recent sound thread there.  Like I said, sound was working fine . . . then, not???


> This thread was started by me to fix sound in 14.04 before it was released.  Before that Stefan over on the Debian mailing list tried to get help.  Nobody contributed therefore it was not fixed.  The only people to blame are the ppc users.

Always appreciate your efforts to help out . . . just in the last couple days your bug report on this topic is showing up by email . . . and reading through your first post you did mention ways of dealing with the "hw-detect" issue . . . so far have not have had the time or the need . . . sound seems OK in my MBPro edition of 14.04 . . . not had time to deal with installing 14.04 PPC on the iBook/iMac.  But, a tad "easy" to slough off blame on "ppc users" for problems in a particular distro, especially if it implies that one is "available for ppc" . . . .  I use the lubuntu users list as an example . . . a gentleman there called for testers for ppc . . . then a few days later said, "the iso is ready but not for ppc, nobody responded . . . ."   I posted back to the list and directly to him as well, suggesting that they post a "testers wanted" thread on this list . . . no reply from him, and within several days, nothing posted here . . . .  Can't call that due diligence . . . unfortunately I have to do other stuff in my life, and linux is a distant fourth or fifth in terms of hobbies . . . .  I know I'm not the only person running a PPC computer, looking for an up to date browser . . . basic function . . . w/o having to spend days just to get the functions viable . . . ????  Is the first step to my recovery to accept the blame for the ppc situation???  : - 0  


>  If you really must have the latest and greatest then I think openSUSE is probably a good option.  Otherwise, stick with 12.04 is my recommendation.

OpenSUSE . . . OK, might check it.  In terms of PPC, agreed right now the iMac is standing with 12.04, it's fine for the linux half, not worth the time and effort to get something newer . . . .  Might fiddle with 14.04.1 for the iBook . . . might need your help/insight to get the radeon thing straightened out, K???  Can I call you, at home . . . ???  : - ))))

e.e.p.

---

### Post by este.el.paz on 2014-07-17
> **rsavage said:**
> 
If you really must have the latest and greatest then I think openSUSE is probably a good option.  Otherwise, stick with 12.04 is my recommendation.

@rsavage:

I checked out the openSUSE site, looks nice enough on the desktop and creative use of the chameleon image, haven't had time to download the livedvd, but, even though they show a "PPC" disk image on the download link . . . it seems that they "no longer support ppc, since 11.xx" . . . now at 13.1??  

So might be an option for intel units, but probably would not be LTS for PPC, no?

e.e.p.

---

### Post by rsavage on 2014-07-17
> **este.el.paz said:**
> @rsavage:
So might be an option for intel units, but probably would not be LTS for PPC, no?

I'm not going to get into a discussion about openSUSE on this thread, but it is in the ports directory.  Like *ubuntu >12.10 you will have no sound, because the problem is with the kernel and is not distro specfic.  

> 
[COLOR=#000000]But, a tad "easy" to slough off blame on "ppc users" for problems in a particular distro, especially if it implies that one is "available for ppc"

All that needs to be done if for somebody to collate device ids of machines with a problem.  The only people who can provide the device ids are the users.  Therefore it is their fault.[/COLOR]

---

### Post by este.el.paz on 2014-07-17
> **rsavage said:**
> I'm not going to get into a discussion about openSUSE on this thread, but it is in the ports directory.  Like *ubuntu >12.10 you will have no sound, because the problem is with the kernel and is not distro specfic.  

All that needs to be done if for somebody to collate device ids of machines with a problem.  The only people who can provide the device ids are the users.  Therefore it is their fault.[/COLOR]

@rsavage:

I was just responding to your cue on the SUSE . . . and, don't know too much about the "ports" as indicated by my question about the "mactel ppa" more or less not too responded to . . . but assuming that you mean that it is available in the PPC friendly repository??  If so, it appears that that would be an "older model" on par with where 12.04 is for us now?  Or like going to "Squeeze" as an "upgrade"????  We could do it, but . . . .

But, main reason for replying is to again comment on this "blame the ppc owner" thing as "being their fault" . . . not entirely a logical conclusion; that conclusion assumes that all the ppc owners are in constant contact with some central ppc command, assumes that the central command can contact each of them . . . directly as per registered mail . . . and also assumes that the ppc owner is purposely ignoring this request . . . .  I don't sense that as being a correct assessment . . . given the many distros, the many linux forums . . . the disparate users of ppc items, etc.  

Given the relative simplicity of just gathering ID numbers of devices having problems, it shouldn't be that hard or time consuming for linux ppc users to do . . . but, like I said, this is sorta the first that I'm hearing this request . . . and then to where would I provide the ID numbers?  For example the iMac that now doesn't have sound, whereas previously it did . . . and nothing I purposely did to remove or change it, except regular upgrades, etc--I'm happy to supply my ID number . . . as long as it isn't a process that requires hours to register or do . . . .  I don't see that starting a massive rejuvenation of 'buntu for ppc, but . . . baby steps . . . .

e.e.p.

---

### Post by Terry_Britton on 2014-07-22
No sound here either.[COLOR=#006400]

cat /proc/asound/cards[/COLOR] gives me

[COLOR=#006400]0 [Snapper   ]: PMac Snapper  - PowerMac Snapper
PowerMac Snapper (Dev 22) Sub-frame 0[/COLOR]

System specs are (PowerMac G4 1.25GHz "Mirror" Mac):
Machine Model: PowerMac3,6
CPU Type: PowerPC 7455, altivec supported (1250.00MHz)

14.04 kernel 3.13.0-32-powerpc-smp

Anything you need me to try out, I'm happy to help.

Terry

---

### Post by rsavage on 2014-07-23
Unmute PCM channel? - [https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F](https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F)

---

### Post by reinhard-boris on 2014-11-10
> **rsavage said:**
> I have sound working on my iBook (late 2004 12") using snd-aoa.  Previously this used snd-powermac.  I want top submit a patch so this will work out-of-the-box.  For this I need the help of other users of *different machines*.  Particularly if you are a snd-powerrmac user and it all stopped working in 12.10.  Before I post longer instructions, I'm after volunteers to run a script and check out a few things for me. Please sign up here.

Hi,

same on my iBook G4 (PowerBook6,5), audio devide id 38: 
[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/17](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/17)

[https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373)

Would you consider returning to this patch effort please? Alone based on the views of this topic we can guess there is interest, as to why it went unnoticed on the ppclist I do not know but on the topic of the user base itself I would guess that quite a few Mac Users are not that tech-savvy and by that I do not want to offend anyone but I speak from experience. 

One of many examples is my own father, old school graphic designer, used Mac's for most of his career, now over 73 years old, he could not do this on his own. Neither could my old boss (even tho he is only around 40) but he would simply expect things to work and wait things out passively as he would never touch an otherwise running system :rolleyes: :? and stay clear of Linux (obviously the remaining ppc Mac folks that are more tech enthusiastic and -savvy must keep at it or otherwise nothing would happen) much more likely at some point the ppc Mac would be simply thrown out without further effort,... :mad:

I've updated the bug report and added some information on the ppc known issues wiki as well:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by rican-linux on 2014-11-11
I am running 12.04 on my PowerBook G4 and here is my /proc/asound/cards output

```
0 [SoundByLayout  ]: AppleOnbdAudio - SoundByLayout
                      SoundByLayout  
```

However the script did not work for me even when I tried it with sudo.

---

### Post by este.el.paz on 2014-11-11
@rsavage & Boris:

There were previously more serious problems to contend with in just getting 14.10 & .04 to even boot . . . but that seems to have been dealt with in my iBook . . . now in 14.04.  Launching Audacious I get the following error:

```
ALSA error: No suitable mixer element found.

ALSA error: snd_mixer_attach failed: No such file or directory.
```

Happy to offer any other information required, not sure how playing music would work out, as even typing in this post with the happy emoticons needing "energy" to wave at me . . . the fan is blowing extensively . . . .  iBook G4 933 Mhz w/640???  MB RAM.  Have not launched ALSA and checked for "unmute" etc, just responding to BR's recent post in an effort to keep PPC "alive" . . . .  The iMac 800 is once again in KP mode and probably "done."

e.e.p.

---

### Post by reinhard-boris on 2014-11-11
> **este.el.paz said:**
> 
(...)
Happy to offer any other information required, not sure how playing music would work out, as even typing in this post with the happy emoticons needing "energy" to wave at me . . . the fan is blowing extensively . . . .  iBook G4 933 Mhz w/640???  MB RAM.  Have not launched ALSA and checked for "unmute" etc, just responding to BR's recent post in an effort to keep PPC "alive" . . . .  The iMac 800 is once again in KP mode and probably "done."

e.e.p.

Thx for dropping by paz :KS

Please follow these instructions kindly provided by rsavage, you can run these off a booted 12.04 live-cd (there is a way to do this via a hex dump from within 14.04 and upwards but I don't recall it exactly from the top of my head at the moment but steps via a 12.04 live-boot are likely much easier to reproduce anyway and should suffice);

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)

> **rsavage said:**
> 

I think to start with it would be good to get a list of device-ids that  are affected by the problem.  On a working install (e.g. 12.04) open  alsamixer, hit F2, select /proc/asound/cards.  Mine is listed as

PowerMac Snapper (Dev 38) Sub-frame 0

I think the 38 is the device id.


This script gives a bit more information:

```

#! /bin/sh

for dir in $(find "/proc/device-tree/" -type d); do
    name="$(cat "$dir/name" 2>/dev/null || true)"
    device_type="$(cat "$dir/device_type" 2>/dev/null || true)"
    compatible="$(cat "$dir/compatible" 2>/dev/null || true)"

    # sound/ppc, sound/oss/dmasound
    if [ "$name" = awacs ]; then
        # probably best to go for ALSA
        echo "awacs snd-powermac"
    elif [ "$name" = davbus ] || [ "$name" = i2s-a ]; then        
        for child in "$dir"/*; do
            if [ -f "$child/name" ]; then
                childname="$(cat "$child/name" 2>/dev/null || true)"
                if [ "$childname" = sound -a ! -f "$child/layout-id" ]; then
                    echo "no layout-id"
                    echo "child is ..." 
                    echo $child
                    echo "device-id is ..."
                    cat $child/device-id
                    echo ""
                fi
            fi
        done
    fi
done

```

e.g for me

```

no layout-id
child is ...
/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound
device-id is ...
&

```
If you look up the ASCII value for "&" it is 38 so that ties in nicely.

If you don't get any output then you are a snd-aoa user.

On the second part of your message **este.el.paz**, If I understand you correctly you're struggling with performance on your system, this sounds to me like your not having Xorg conf set up and as a result are not using DRI, which has to be fixed manually. 

 Please follow these steps from an installed and logged in to Lubuntu 14.04 (and upwards) session:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/32) (link just for reference)

sudo service lightdm stop

 sudo Xorg -configure
sudo mv xorg.conf.new /etc/X11/xorg.conf
sudo nano /etc/X11/xorg.conf

 [Here some driver options could be set, eg. uncomment pageflip and set it to "True", save any edits and then reboot]

After the reboot you can check your acceleration with the commands  glxinfo and glxgears -info if it works you will notice the gears running  well even when quickly moving it's window.

While the Lubuntu UI likely will remain slowish (you could give a compositor a try but that on the other hand might affect your memory footprint further, may be worth a try) but browser (changing blacklistings and manually enabling/ forcing native OpenGL via about:config might be needed there), 2D as well as 3D stuff should work much better with enabled hardware acceleration ):P

Additionally you can try to adjust the swappiness value to 15 which should help to reduce sluggishness by avoiding too extensive writing to or reading from IDE disks (less usage of the slower swap partition/ virtual memory access):
 [http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by reinhard-boris on 2014-11-11
> **rican-linux said:**
> I am running 12.04 on my PowerBook G4 and here is my /proc/asound/cards output

```
0 [SoundByLayout  ]: AppleOnbdAudio - SoundByLayout
                      SoundByLayout  
```

However the script did not work for me even when I tried it with sudo.

Hi there again and thx for your participation, it's much appreciated! :guitar:

Mmh, I may be wrong but that could mean your sound might work out of the box-!? 
You could just give a 14.04.1 live-cd/dvd a try (without installation)!

[http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/)

---

### Post by rican-linux on 2014-11-11
really? I will download and report my findings! also off topic can you give me some advice of my suspend issues I post on another thread?

---

### Post by este.el.paz on 2014-11-11
> **rican-linux said:**
> really? I will download and report my findings! also off topic can you give me some advice of my suspend issues I post on another thread?

@r-l:  I also about ready to file a 14.04 bug report on recent upgrade(s) seeming to mess up the "suspend" on my iBook, such that the fan doesn't shut off after the screen has gone black . . . more or less meaning I have to reboot to OSX for sleep or shut down . . . .  As I get time to look into it I will ,and try to follow along on your thread . . . .

> **reinhard-boris said:**
> Thx for dropping by paz :KS
Please follow these instructions kindly provided by rsavage, you can run these off a booted 12.04 live-cd (there is a way to do this via a hex dump from within 14.04 and upwards but I don't recall it exactly from the top of my head at the moment but steps via a 12.04 live-boot are likely much easier to reproduce anyway and should suffice);
[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)
On the second part of your message **este.el.paz**, If I understand you correctly you're struggling with performance on your system, this sounds to me like your not having Xorg conf set up and as a result are not using DRI, which has to be fixed manually. 
Please follow these steps from an installed and logged in to Lubuntu 14.04 (and upwards) session:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/32](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878/comments/32) (link just for reference)
[Here some driver options could be set, eg. uncomment pageflip and set it to "True", save any edits and then reboot]
After the reboot you can check your acceleration with the commands  glxinfo and glxgears -info if it works you will notice the gears running  well even when quickly moving it's window.
Additionally you can try to adjust the swappiness value to 15 which should help to reduce sluggishness by avoiding too extensive writing to or reading from IDE disks (less usage of the slower swap partition/ virtual memory access):
 [http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

@Boris:  Thanks for the reply . . . I first thought that we were supposed to check in 14.04, but I get it now, a live boot of 12.04 is what we should use.  So, I'll try that when I get a moment . . . and post back.  On the other stuff, you offered the Xorg set up info on the Lu user list and I did that; except for the "pageflip" set to "true" . . . couldn't get that edited in various editors . . . nano, ????  But, I'll look into the "swappiness" thing . . . but, right now the very basic thing is that in 12.04 on iBook "suspend" worked "out of the box" . . . and that feature is one that I consider "mission critical" . . . .  The overall, "I'm going to take a minute to think about doing what you just clicked on" attitude of 14.04 . . . is not exactly conducive to "work flow" . . . but is somewhat "OK" . . . it's the suspend that on first install a couple two three weeks ago was OK, and after a few updates has gotten worse.  And, same with the suspend button in upper right of lightdm log in not working . . . .  So, logged in, click "suspend" . . . screen goes black . . . fan keeps blowing . . . wiggle mouse . . . lightdm log in window appears . . . click upper right power button for "suspend" . . . does nothing . . . have to log in again, and hit "restart" or "shut down" . . . that is most bothersome right now.  I do have some of the olde kernels still installed . . . but other business in regards to making a living that have to be covered . . . .

I'll post back with the rsavage requested info when I get a chance to boot the 12.04 DVD . . . .

e.e.p.

---

### Post by reinhard-boris on 2014-11-11
Thx guys!

On the suspend issues, I understand there are various longer standing bug reports on it, I haven't really looked into it yet but it's bound to come up some time. My understanding was suspend/ sleep won't work at the moment as it's relying on older framebuffers and the functions are not implemented in KMS (yet or potentially ever?). 

To me personally it's not much of an issue, as shutting down and when needed booting up is not that time consuming, so if you disable sleep and suspend as a workaround and get used to shutting down and booting up normally it's really not that much of a hassle and you won't run into issues for now.

---

### Post by rican-linux on 2014-11-11
OK I got lubuntu 14.04 loaded as a live image. I cannot open audacious without getting an error and I get the following when I try to load alsamixer

cannot open mixer: No such file or directory

I had some sound issues when I was on Xubuntu 14.04 but all I needed to do was adjust alsamixer setting as described in the wiki, I can try loading the live image of Ubuntu 14.04 and see what I find???

---

### Post by este.el.paz on 2014-11-11
Booted in the rsavage special release Xubun 12.04 CD . . . running through those choices brings:

```
&#9474; 0 [Snapper        ]: PMac Snapper - PowerMac Snapper      &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;                      PowerMac Snapper (Dev 44) Sub-frame 0
```

'04ish "Gen2" iBook 933 MHz  . . . 64x MB RAM . . . now has 14.04 Lu installed.

e.e.p.

---

### Post by reinhard-boris on 2014-11-12
> **rican-linux said:**
> I had some sound issues when I was on Xubuntu 14.04 but all I needed to do was adjust alsamixer setting as described in the wiki, I can try loading the live image of Ubuntu 14.04 and see what I find???

If it worked in Xubuntu 14.04 it will also in Lubuntu 14.04 You'd simply have to modprobe the device and remove or edit the module blacklist and potentially unmute the audio at the end. Your Mac apparently is not affected by the missing device id's and uses the older system.

---

### Post by reinhard-boris on 2014-11-12
> **este.el.paz said:**
> Booted in the rsavage special release Xubun 12.04 CD . . . running through those choices brings:

```
&#9474; 0 [Snapper        ]: PMac Snapper - PowerMac Snapper      &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;                      PowerMac Snapper (Dev 44) Sub-frame 0
```

'04ish "Gen2" iBook 933 MHz  . . . 64x MB RAM . . . now has 14.04 Lu installed.

e.e.p.

Perfect, exactly what we needed, wish the lingering about Mac Users would come forward as well (over 4000 views),..
yes YOU ):P

Seriously to whoever is reading this, if you want to get this fixed we need your help, it's all explained in easy to follow to steps, please take a look, register/ or log in on here and post your results:

> **reinhard-boris said:**
> 

Please follow these instructions kindly provided by rsavage, you can run  these off a booted 12.04 live-cd (there is a way to do this via a hex  dump from within 14.04 and upwards but I don't recall it exactly from  the top of my head at the moment but steps via a 12.04 live-boot are  likely much easier to reproduce anyway and should suffice);

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)



> **rsavage said:**
> 

I think to start with it would be good to get a list of device-ids that  are affected by the problem.  On a working install (e.g. 12.04) open  alsamixer, hit F2, select /proc/asound/cards.  Mine is listed as

PowerMac Snapper (Dev 38) Sub-frame 0

I think the 38 is the device id.


This script gives a bit more information:

```

#! /bin/sh

for dir in $(find "/proc/device-tree/" -type d); do
    name="$(cat "$dir/name" 2>/dev/null || true)"
    device_type="$(cat "$dir/device_type" 2>/dev/null || true)"
    compatible="$(cat "$dir/compatible" 2>/dev/null || true)"

    # sound/ppc, sound/oss/dmasound
    if [ "$name" = awacs ]; then
        # probably best to go for ALSA
        echo "awacs snd-powermac"
    elif [ "$name" = davbus ] || [ "$name" = i2s-a ]; then        
        for child in "$dir"/*; do
            if [ -f "$child/name" ]; then
                childname="$(cat "$child/name" 2>/dev/null || true)"
                if [ "$childname" = sound -a ! -f "$child/layout-id" ]; then
                    echo "no layout-id"
                    echo "child is ..." 
                    echo $child
                    echo "device-id is ..."
                    cat $child/device-id
                    echo ""
                fi
            fi
        done
    fi
done

```

e.g for me

```

no layout-id
child is ...
/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound
device-id is ...
&

```
If you look up the ASCII value for "&" it is 38 so that ties in nicely.

If you don't get any output then you are a snd-aoa user.

---

### Post by rsavage on 2014-11-12
Hi Boris, thanks for picking up the interest in this.  I have no plans at the moment to do further work on the patch (it was mostly Stefan's patch anyway).  As I think I've already said to somebody else in this thread, I probably should have submitted it to the alsa-devel list rather than the ppc mailing list.  Please feel free to write to that list and submit it yourself.  

I don't use ppc/linux much these days, and if I do then I pretty much only tinker with compiz ([http://forums.mate-desktop.org/viewtopic.php?f=16&t=3175](http://forums.mate-desktop.org/viewtopic.php?f=16&t=3175) ). That is another thing I couldn't get anybody interested in!

I've got other stuff I need to finish off too ([https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1332721](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1332721) ), but I have other stuff happening at the mo, computer stuff is not a priority.

Sorry, that is probably not what you want to hear!

@eep, you can get sound easy with your device id, you just need to modprobe the correct module and unblacklist the aoa modules.

---

### Post by este.el.paz on 2014-11-12
> **rsavage said:**
> Hi Boris, thanks for picking up the interest in this.  I have no plans at the moment to do further work on the patch (it was mostly Stefan's patch anyway). 

@eep, you can get sound easy with your device id, you just need to modprobe the correct module and unblacklist the aoa modules.

@rsavage:

Thanks for that info on getting sound working . . . like you I have a few other things taking priority over sound . . . like, "suspend" in 14.04 . . . .  But, maybe for a rainy day in SoCal (we're in the ten year drought phase) . . . I'll have something to mess around with . . . .  But, I do like MATE . . . have LM17 MATE running in my MBPro . . . .  There is more to living than messing with linux . . . one should live a well balanced life . . . exercise and so forth.  : - )

e.e.p.

---

### Post by rsavage on 2014-11-12
The fascination with suspend is lost on me, I even power down my tablet when I've finished using it.  Surely how to get suspend has been done to death though, and have you tried hibernate instead?  I'm sure the information is there for you.

---

### Post by este.el.paz on 2014-11-12
> **rsavage said:**
> The fascination with suspend is lost on me, I even power down my tablet when I've finished using it.  Surely how to get suspend has been done to death though, and have you tried hibernate instead?  I'm sure the information is there for you.

No empathy from you on that one?  : - 0  Problem is that it was working in 12.04; as I mentioned when I booted your CD last night . . . and now not.  Haven't had a lot of time to search for how to fix such a basic function . . . so perhaps the forum has the data . . . haven't tried the hibernate function, but certainly that would be easy enough.  But, to cold boot the iBook runs me several minutes . . . literally, Yaboot 2 windows . . . then black for a while, then a cursor . . . then the splash . . . and the various error comments . . . then the log in window . . . then the GUI loads . . . .  I don't often have extended work on a console wherein cold booting would pale in comparison to the endless hours . . . mostly check emails and forum posts then other thigs to do for awhile, then I want to check quickly, so reviving from "sleep" in OSX or "suspend" in linux will get me up quickly . . . .  Hope that helps . . . .  

e.e.p.

---

### Post by rsavage on 2014-11-19
You want the ppc (snd-aoa) version of this [http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers](http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers)

---

### Post by este.el.paz on 2014-11-19
> **rsavage said:**
> You want the ppc (snd-aoa) version of this [http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers](http://askubuntu.com/questions/163225/how-do-i-install-new-intel-hda-sound-drivers)

@r:

Don't know if that was for my benefit, or not, but if so, thanks . . . I went to that page, didn't see anything for "ppc" or "snd-aoa" . . . are you talking about the "ALSA daily builds for 14.04"???  Something that looks like  ```
[         oem-audio-hda-daily-dkms - 0.201411191501~ubuntu14.04.1       ]("https://code.launchpad.net/%7Eubuntu-audio-dev/+archive/ubuntu/alsa-daily/+sourcepub/4578468/+listing-archive-extra")
```???

I may get around to the sound thing in a bit . . . the "hibernation" thing does seem to work intermittently, which means I can spend more time in 14.04 . . . .  Also have to spend more time looking at the FAQ, so I can know what's there . . . for keeping PPC going . . . .

e.e.p.

---

### Post by rsavage on 2014-11-20
@eep, no it was not for you.  Yours is an easy fix.

It was an example for Boris et al, or any other motivated person to use DKMS - [https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS) .  They will have to create the ppc/snd-aoa package.

The links in the PowerPC Known Issues page are the best place to troubleshoot, but a generic Ubuntu one is [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Help on compiling just the sound modules is here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) .  More on module-assistant is here [https://wiki.debian.org/ModuleAssistant](https://wiki.debian.org/ModuleAssistant) .  

So lots of documentation and alternative ways of doing things for people to follow.  It is just a case of putting it all together to get sound working again.  

Don't fancy that?  Linux on PowerPC is not for you!

---

### Post by rican-linux on 2014-11-20
@rsavage- thanks for the info!

---

### Post by reinhard-boris on 2014-11-20
> **rsavage said:**
> Hi Boris, thanks for picking up the interest in this.  I have no plans at the moment to do further work on the patch (it was mostly Stefan's patch anyway).  As I think I've already said to somebody else in this thread, I probably should have submitted it to the alsa-devel list rather than the ppc mailing list.  Please feel free to write to that list and submit it yourself. 

(...) I have other stuff happening at the mo, computer stuff is not a priority.

Sorry, that is probably not what you want to hear!


Thx for getting back to me on this and the pointers on DKMS, of course I can not blame you for moving on. 

It's not particularly fun to keep working on something, on your spare time, that other ppl don't try the slightest to support to get done albeit them greatly gaining from the results but still them just passively lingering/ lurking about in hopes it eventually will work out fine, not even participating with what little is required in this case, frankly it's frustrating and very likely will be the final nail to the coffin of ppc mac's, it's Users, the irony,...

It is a shame really because it wouldn't have to be, some of that hardware is still quite capable but without enough users stepping it up, just expecting things to work without any will to participate the slightest in the effort to keep it running/  supported/ tested, I'm afraid the outlook is rather grim.

---

### Post by rsavage on 2014-11-22
I've been playing with DKMS tonight and think I have it sorted now in my head.  I probably could get a deb out to fix this soonish (next week?) depending on when I get to next sit down and work on it.  I would still like somebody else to take up fixing this permanently though....

---

### Post by rican-linux on 2014-11-22
Which powerpc machines are effected by this? Just curious.

---

### Post by reinhard-boris on 2014-11-23
> **rsavage said:**
> I've been playing with DKMS tonight and think I have it sorted now in my head.  I probably could get a deb out to fix this soonish (next week?) depending on when I get to next sit down and work on it.  I would still like somebody else to take up fixing this permanently though....

I believe we've been able to gather some attention on the matter, things move slowly of course but keep in mind nobody get's paid anymore to fix stuff on our old Apple hardware. :(

I've contacted Michael Ellerman a few weeks ago and he mentioned he recently got an iBook himself and plans to have look (no promises made tho). He also said it can easily happen that stuff on the list get's missed and that if a patch exists like with as many device id's as we could collect and get's send in well documented things of course would happen sooner rather than later. 

A deb would certainly help to raise our numbers of used ("usable" for many with less experience on Linux) more modern/ recent Lubuntu releases, sound is an important part of typical everyday usage scenarios so this would really help as intermediate solution to keep ppc Macs alive where manual tinkering is next to impossible so that would be great! What made you change your mind if I may ask?

 [IMG]http://ubuntuforums.org/images/smilies/guitar.gif[/IMG]

---

### Post by rsavage on 2014-11-24
> **reinhard-boris said:**
>  What made you change your mind if I may ask?


It's good to try new stuff.  I knew DKMS would be useful for other apple modules (e.g. the trackpad on later powerbooks/ibooks) so it was good to figure it out.  It's been on on my to do list.

BUT, that is all I'm doing.  I can't be doing with mailing lists etc, so a permanent solution will have to be sought by somebody else.

---

### Post by rsavage on 2014-11-24
Before installing the attached deb file please read [https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/14](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/14) .  You will probably have to add snd-aoa-i2sbus to /etc/modules - if that is the case then comment on the bug so that it can be fixed!!!!!

Help on installing can be found here [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If you have a diferent device id to me (38) then I constructed the package so you should be able to change it pretty easily.  The PowerPCFAQ has help on compiling packages if you want to make your own.

---

### Post by rican-linux on 2014-11-24
Thanks! I just recently moved to Debian Jesse and had sound issues. All I needed to do was add the module and load it to get sound working. I am going to forward this to someone I know who may have a similar issue.

---

### Post by dr.david.maloney on 2014-11-30
> **rican-linux said:**
> Thanks! I just recently moved to Debian Jesse and had sound issues. All I needed to do was add the module and load it to get sound working. I am going to forward this to someone I know who may have a similar issue.

Hallelujah. There is a God, someone got sound working in Jessie......may actually give Jessie a try now.

---

### Post by mcdonnell2 on 2014-12-02
Just converted an IBook G4 to Lubuntu 14.04 two weeks ago and could not get the sound card to be detected.  Found this forum supporting PPC and was a little down with the possibility of no/delayed support of this when I finally got some useable data.  I have been wrestling with this over the entire weekend and finally noticed your post with the patch .zip file.  The sound device enum. matched, so I tried it, and success on the first attempt.  I now have a working alsamixer, Gmerlin mixer (speakers and headphones auto detect) alsaplayer, etc.    I want to say THANK YOU for your time and wonderfull contribution to keeping the PPC distros alive.  I use this IBook for a traveling laptop due to size and weight, and your fix has been the final link in moving away from MAC and their lack of support for this platform.   Is there anything I can do in return?

---

### Post by rsavage on 2014-12-03
@mcdonnel2 glad it worked for you!  It is great to get feedback.  From the download numbers I thought nobody was using it.  Can you leave a comment on the sound bug, we need to build up confidence in the patches?

The next challenge to tackle in 14.04 is to get the various packages of webkit (used by midori/qupzilla/lots of other stuff) patched.  Fixes are there I think, we just need to request them!  You could help with that if it is something you use.

---

### Post by mcdonnell2 on 2014-12-04
Comment done.  I am a little new to the internals of gui-based linux distros.  Was reasonably proficient back in the console linux days (early slackerware), but went to the dark side around Windows NT 4.0 for work reasons. Finally started coming back with live distros like Knoppix, mephis, & puppy, but haven't taken my involvement seriously till now.  Once Win 7 is NLS, I will be mostly free of me Win addiction.  

I will take a look at webkit and see what I can do.  I assume I should see if I am impacted by any of the currently reported bugs, capture any additional symptom or configuration specific info, apply the pending patches and report which worked and to what success level?

---

### Post by rican-linux on 2014-12-04
I think there may be a similar bug in Jessie. I use surf it has been crashing along with midori. Here is an error. I do not know if it is GTK related. 

(surf:4687): Gdk-CRITICAL **: IA__gdk_gc_new: assertion 'drawable != NULL'
failed

(surf:4687): Gdk-CRITICAL **: IA__gdk_gc_set_rgb_fg_color: assertion 'GDK_IS_GC
(gc)' failed

---

### Post by dand1972 on 2014-12-04
> **rsavage said:**
> Before installing the attached deb file please read [https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/14](https://bugs.launchpad.net/ubuntu/+source/hw-detect/+bug/1296373/comments/14) .  You will probably have to add snd-aoa-i2sbus to /etc/modules - if that is the case then comment on the bug so that it can be fixed!!!!!

Help on installing can be found here [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

If you have a diferent device id to me (38) then I constructed the package so you should be able to change it pretty easily.  The PowerPCFAQ has help on compiling packages if you want to make your own.

I downloaded the deb file, and my device id is 28 (iBook  G3 700MHz 14 inch).  How exactly do I edit the patch file?

Thanks.

---

### Post by Dukenukemx on 2015-01-09
Getting sick of trying to fix sound on my PowerBook G4.  And yea FireFox scrolls like a slideshow.  I have 14.04 with Mate installed.  Anyway to fix sound and speed up scrolling speed?  Or recommend me another distro that isn't broken for PPC?

---

### Post by rican-linux on 2015-01-09
Did you try to load the snd-aoa-i2sbus module?

---

### Post by Dukenukemx on 2015-01-09
I did and the screen was all messed up and sound still didn't work when I rebooted.  Was barely able to remove it from terminal.  It was placed in /etc/modules .  The module I tried to load was snd-aoa-i2sbus .  

All I did so far was fix wifi and run update manager to get all the updates.

---

### Post by rican-linux on 2015-01-09
Did you do a clean install of 14.04 or did you upgrade from 12.04? Also you also can try Debian stable. I am running it on my powerbook g4 and am pretty happy with it.

---

### Post by Dukenukemx on 2015-01-09
I tried Debian 7.7 and it worked with no sound as well, but I didn't check about the Radeon 9600 was working.  I switched to Ubuntu to see if it was any better.

---

### Post by rican-linux on 2015-01-09
In Debian all you need to add the modules then in the terminal enter aslamixer and set the PCM channel to 80. That should have worked in Ubuntu as well. See [here]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F")

---

### Post by este.el.paz on 2015-01-09
> **Dukenukemx said:**
> I did and the screen was all messed up and sound still didn't work when I rebooted.  Was barely able to remove it from terminal.  It was placed in /etc/modules .  The module I tried to load was snd-aoa-i2sbus .  

All I did so far was fix wifi and run update manager to get all the updates.

@D:

You might need to set up or "get" an xorg.conf file for your machine to handle the messed up screen.  But, in terms of PPC support, you have to understand that most of the world has "moved on" from PPC, particularly the devs would want the latest technology, so either you have to be willing to make your own adjustments, or keep a sense of humor about "sound" and/or the glitchy window scrolling . . . enjoy the game as we struggle along in PPC, etc.

e.e.p.

---

### Post by Dukenukemx on 2015-01-09
> **rican-linux said:**
> In Debian all you need to add the modules then in the terminal enter aslamixer and set the PCM channel to 80. That should have worked in Ubuntu as well. See [here]("https://wiki.ubuntu.com/PowerPCFAQ#Why_do_I_have_no_sound.3F")

I installed Debian XFCE 7.7 to give it another try.  Tried to fix sound, then reboot and XFCE would freeze as soon as you saw the screen.  No text or icons though.  Tried undoing everything I did and nothing.  So I figured I did something that I don't remember, and reinstalled.  This time I just focused on changing the XFCE theme so that it's not ugly.  I had Orta working and looking nice and decided to reboot anyway.  Same as before, froze when it hit XFCE UI except now with the Orta theme.  No sound or wifi was attempted to be installed.  

Debian sucks to install cause it also doesn't operate any of the fans to cool the laptop during the installation.  So the laptop is boiling hot until it finishes and boots into Debian.  What Debian do you use cause the one I use sucks?

---

### Post by Dukenukemx on 2015-01-09
> **este.el.paz said:**
> @D:

You might need to set up or "get" an xorg.conf file for your machine to handle the messed up screen.  But, in terms of PPC support, you have to understand that most of the world has "moved on" from PPC, particularly the devs would want the latest technology, so either you have to be willing to make your own adjustments, or keep a sense of humor about "sound" and/or the glitchy window scrolling . . . enjoy the game as we struggle along in PPC, etc.

e.e.p.
I'm just putting together an old laptop for my neice.  Something I don't mind breaking in the hands of a 7 year old. :p  But things like sound would probably be needed.  Also these are things I don't get to do with Ubuntu or Mint.  Kinda spoils me.

---

### Post by rican-linux on 2015-01-10
> **Dukenukemx said:**
> I installed Debian XFCE 7.7 to give it another try.  Tried to fix sound, then reboot and XFCE would freeze as soon as you saw the screen.  No text or icons though.  Tried undoing everything I did and nothing.  So I figured I did something that I don't remember, and reinstalled.  This time I just focused on changing the XFCE theme so that it's not ugly.  I had Orta working and looking nice and decided to reboot anyway.  Same as before, froze when it hit XFCE UI except now with the Orta theme.  No sound or wifi was attempted to be installed.  

Debian sucks to install cause it also doesn't operate any of the fans to cool the laptop during the installation.  So the laptop is boiling hot until it finishes and boots into Debian.  What Debian do you use cause the one I use sucks?

I am using Debian 7.7 LXDE I also have XFCE installed and run that with little issues. I understand the heating issue what you need to do is set up CPU frequency scaling to help with the heating. There are instructions [here]("https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F") and [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#cpufreq"). Those two places have been a great help to me getting Linux running on PPC. e.e.p. is right, if you want to use powerpc you will need to do a lot work. However Linux will give you tools to do it. I strongly recommend this [piece]("http://powerpcliberation.blogspot.ca/2012/09/claim-your-computing-freedom.html"). Do not give up!

---

### Post by Dukenukemx on 2015-01-11
> **rican-linux said:**
> I am using Debian 7.7 LXDE I also have XFCE installed and run that with little issues. I understand the heating issue what you need to do is set up CPU frequency scaling to help with the heating. There are instructions [here]("https://wiki.ubuntu.com/PowerPCFAQ#How_can_I_use_powernowd_for_CPU_frequency_scaling.3F") and [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#cpufreq"). Those two places have been a great help to me getting Linux running on PPC. e.e.p. is right, if you want to use powerpc you will need to do a lot work. However Linux will give you tools to do it. I strongly recommend this [piece]("http://powerpcliberation.blogspot.ca/2012/09/claim-your-computing-freedom.html"). Do not give up!

I just removed the power and battery and now it boots.  When I restart it doesn't.  It seems random when I can and can't boot into XFCE.  Think I'll try Ubuntu again with XFCE this time.  I'll do it tomorrow unless someone has a solution for debian?  Also does anyone know how to get OpenGL working properly in Ubuntu?  [This old fix did work for 12.04 but you need need xorg back.](http://ubuntuforums.org/showthread.php?t=1460926&page=2&p=9194781#post9194781)  Not sure if it'll work for 14.04.  

I was able to fix sound by black listing snd-powermac, then loading snd-mixer-oss and snd-pcm-oss modules. 

Wifi was fixed by loading this into the source.list.  Then installing firmware-b43-installer.  
deb [http://http.debian.net/debian/](http://http.debian.net/debian/) wheezy main contrib non-free

---

### Post by Dukenukemx on 2015-01-11
Put back Ubuntu and so far so good.  Sound doesn't work the same way as Debian, as you just load only these modules. I actually got sound working with just snd-aoa-i2sbus but I loaded up the other modules anyway.  

snd-aoa-soundbus 
snd-aoa-i2sbus 
snd-aoa-fabric-layout
snd-aoa

Now I just gotta get 3D acceleration working with the 9600.  Created a xorg.conf file and added the below in. I also disabled KMS by going into the /etc/yaboot.conf and adding "radeon.modeset=0"  Nothing I do changes that I get software rendering.  Did they remove Radeon 9600 drivers in 14.04?   

```

Section "Device"
Identifier "Radeon 9600"
Driver "ati"
## BusID "PCI:0:16:0"
Option "DynamicClocks" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "UseFBDev" "false"
Option "DRI" "true"
Option "GARTSize" "64"
Option "AddARGBGLXVisuals" "true"
Option "XAANoOffscreenPixmaps"
Option "DisableGLXRootClipping" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

```

---

### Post by este.el.paz on 2015-01-20
@Duke:  Yes, they removed the radeon drivers in 14.04.

@the list:  Spent a few minutes looking at this sound problem in my iBook . . . and looking at the FAQ wiki, it says "old" computers use "sound-powermac" and "new" use "sound-aoa."  My device I think is "44"??  Looking in /etc/modules it shows "sound-powermac" and over in the "blacklist" it shows all the "sound-aoa" modules.  No "alsamixer" . . . .

So, I'm assuming that I want to "modprobe" sound-aoa??  and/or add it to /etc/modules ??  And then "delete" the black list . . . completely?  Or put "sound-powermac" there?  I saw some posts about "sound-i2bus" or something as solving the sound problem, but I don't think I saw that in the blacklisted items; but an error about i2bus seems to show up when launching the 14.04 system . . . .

Blowing fan noise is a bit more of an issue for me than sound, but any specifics on getting sound going would be appreciated.  Thx.

e.e.p.

---

### Post by Dukenukemx on 2015-01-25
I did a quick reinstall of 14.04 and had to resetup sound.  For me all I need is  snd-aoa-i2sbus loaded in /etc/modules to get sound working.  Then go to alsamixer and raise the PCM audio, cause for some stupid reason it's 0 by default.  If that doesn't work then use snd-powermac instead of snd-aoa-i2sbus.  One of those twoi should get sound working but you need to start up alsamixer and raise volume for PCM.

---

### Post by rsavage on 2015-02-24
> **dand1972 said:**
> I downloaded the deb file, and my device id is 28 (iBook  G3 700MHz 14 inch).  How exactly do I edit the patch file?Thanks.
dand1972 (aka ppcluddite), the reason I didn't answer this is because you write for and support zen's blog - a blog that actively discourages (in the most rude and insulting way) people from using Ubuntu.  It does puzzle me that a website run by self-styled linux experts should need help on this.....

I don't want my work posted on or associated with that website thank you very much.

So dand1972, this reply is not for you, but I have been asked by others, so here is a very very quick guide.....

The deb package essentially contains the aoa sound module source code for the modules we want to compile, a patch for device id 38, the debian package files and a dkms.conf file.  When you install the debian package, these files are copied to /usr/src/snd-aoa-device-id-38-fix-1.1~14.04.1 and dkms automatically adds, builds and installs the module.

So if, for example, you have device id 40 then the first thing you need to do is tell dkms to remove the module that was patched for 38:
```
sudo dkms remove -m snd-aoa-device-id-38-fix -v 1.1~14.04.1 --all
```

Now we need to edit the patch.  A quick and dirty way is just to open the file and change everywhere it says '38' to '40'.

```
sudo nano /usr/src/snd-aoa-device-id-38-fix-1.1~14.04.1/patches/device_id_38.patch
```

We haven't changed the file name because this is a super quick fix - it is not something you would publish.  

The most complicated bit is telling the module what connections the computer has, so you will have to look at the code in /usr/src/snd-aoa-device-id-38-fix-1.1~14.04.1/sound/aoa/fabrics/layout.c at this point to work out what you want to write.  

From comments made previously in this thread, device id 40 should have

```
+        .connections = tas_connections_nolineout,
```

Save the device_id_38.patch file and run
```
sudo dkms add -m snd-aoa-device-id-38-fix -v 1.1~14.04.1
sudo dkms build -m snd-aoa-device-id-38-fix -v 1.1~14.04.1
sudo dkms install -m snd-aoa-device-id-38-fix -v 1.1~14.04.1
```
Reboot, and as long as you've got your modules unblacklisted and the correct one placed in /etc/modules as previously advised then alsamixer should now work.

If you are running something newer than 14.04 then you need to make more changes.  For example the file aoa.h has been changed in newer kernels so you'll need to update that to get it to compile.  You'll also have to adjust the dkms.conf file, updating or removing the BUILD_EXCLUSIVE_KERNEL line (note dkms, rather confusingly also uses the term 'package', this is not the same as the debian package). 

If you want to do it properly then you would change the package names, and sort out a proper patch so that the device id was under the correct computer model.

All of the above could of been worked out by looking at the dkms manual or wiki pages (e.g. [https://wiki.ubuntu.com/Kernel/Dev/DKMSPackaging](https://wiki.ubuntu.com/Kernel/Dev/DKMSPackaging)).... it's not really that 'opaque'.  Obviously I can't guarantee this will work for every device id, but hopefully it will for some.

---

### Post by este.el.paz on 2015-02-28
> **Dukenukemx said:**
> I did a quick reinstall of 14.04 and had to resetup sound.  For me all I need is  snd-aoa-i2sbus loaded in /etc/modules to get sound working.  Then go to alsamixer and raise the PCM audio, cause for some stupid reason it's 0 by default.  If that doesn't work then use snd-powermac instead of snd-aoa-i2sbus.  One of those twoi should get sound working but you need to start up alsamixer and raise volume for PCM.

@Duke && rsavage:

Finally found time to mess with this, between the FAQ and "rm" the blacklisted aoa items, and Duke's insights here I got Alsamixer to show up and raised PCM . . . .  First time I tried to add the "aoa" list to /etc/modules it wasn't working to add lines for some reason . . . after I "modprobe"d the "snd-aoa-i2sbus" module, then when /etc/module opened, it had the snd-powermac line, which I removed and added all the items from the FAQ . . . viola, Gypsy Kings playing on Pandora!!!!  Relatively simple for my iBook device #44 . . . precerate it, y' all.

e.e.p.

---

### Post by Artemis3 on 2015-05-13
Hello, i tried this in a PowerBook G4 with 17" screen to no avail. 
I guess it is not device 38? how can i tell the number when i only have 14.04 running?

---

### Post by rican-linux on 2015-05-13
This should work on a PowerBook. On mine just needed to do the following

make i deleted the blacklist.local.conf file
add this to /etc/modules snd-aoa-i2sbus
then execute sudo modprobe snd-aoa-i2sbus
then execute alsamixer and set PCM channel to 80

---

### Post by este.el.paz on 2015-05-13
> **Artemis3 said:**
> Hello, i tried this in a PowerBook G4 with 17" screen to no avail. 
I guess it is not device 38? how can i tell the number when i only have 14.04 running?

@Artemis:

Best thing is to read through the PowerPCFAQ on "sound issues" . . . or read through this thread and find the place where rsavage shows how to figure out which "device" your computer is . . . .  For my iBook it was pretty easy, once I got around to it . . . but you should do some reading to get it figured out . . . then start clicking on stuff . . . .

e..

---

### Post by Artemis3 on 2015-05-14
> **este.el.paz said:**
> @Artemis:

Best thing is to read through the PowerPCFAQ on "sound issues" . . . or read through this thread and find the place where rsavage shows how to figure out which "device" your computer is . . . .  For my iBook it was pretty easy, once I got around to it . . . but you should do some reading to get it figured out . . . then start clicking on stuff . . . .

e..

Have you noticed the FAQ tell us to do exactly the opposite? (blacklist snd-aoa etc). The default config had those blacklisted, and alsamixer had the same error (cannot open mixer: no such file or directory) which is why I started searching and found this thread.

I commented out the blacklisted snd-aoa entries from blacklist.local and tried with and without loading snd-aoa-i2sbus and still can't get a soundcard (yes it chimes when powering on).
I also installed the .deb from page 7.

aplay -l says no soundcards found...

Since it doesn't work, i can only guess it is not ID 38.


Unrelated: the PPCfaq is also incorrect in the boot parameters for fixing graphics, but i found the solution in another thread and also got rid of xserver-xorg-video-fbdev. 2d now works great with radeon.

---

### Post by este.el.paz on 2015-05-14
@Artemis:

Yes, I noticed . . . but main thing is you have to compare what you have now . . . which isn't working . . . and then make the changes such that it does work.  The FAQ has data from across a time span and multiple OS upgrades, but if you read through this thread and particularly the rsavage comments you should find your answer.

Did you run "lsmod" and see what is listed for sound?  And did "alsamixer" open up a window showing various sound controls?

I made a number of attempts to get sound running in U-MATE 14 and then it dismantled itself . . . so, not having sound is again an issue . . . but, also having a system that doesn't crash as it does in 15 would be nice . . . .

Enjoy the process,

e.e.p.

---

### Post by Artemis3 on 2015-05-14
> **este.el.paz said:**
> Did you run "lsmod" and see what is listed for sound?  And did "alsamixer" open up a window showing various sound controls?

I made a number of attempts to get sound running in U-MATE 14 and then it dismantled itself . . . so, not having sound is again an issue . . . but, also having a system that doesn't crash as it does in 15 would be nice . . . .

lsmod shows the modules, alsamixer doesn't work.

I installed to minimal and then into lubuntu-desktop (14.04).
"Run alsamixer in 12.04 to find the ID" is what i mostly find :(

I plan to leave this on 14.04 LTS because the install process is very time consuming and nearly nerve breaking (fiddling with openfirmware command mojo).

PowerBook G4 17"

---

### Post by este.el.paz on 2015-05-14
> **Artemis3 said:**
> lsmod shows the modules, alsamixer doesn't work.

I installed to minimal and then into lubuntu-desktop (14.04).
"Run alsamixer in 12.04 to find the ID" is what i mostly find :(

I plan to leave this on 14.04 LTS because the install process is very time consuming and nearly nerve breaking (fiddling with openfirmware command mojo).

PowerBook G4 17"

@Artemis:

Ah, right, "run alsamixer in 12.04" . . . that is what I did . . . your sig shows you have "12.04" . . . but, if not, it's very easy to download a 12.04 desktop for ppc iso . . . and burn it to DVD . . . and boot it up in your computer and then follow the instructions on what to do in Alsamixer to get the ID.  It took me a few months to get the time to work on the sound issue in my iBook . . . I don't "need" sound . . . .  But, point being, you don't have to install 12.04 to run alsamixer in the machine.

Agreed, that the install process from the mini installer is "time consuming" . . . and staying with the LTS version is probably your best choice . . . not sure where the "openfirmware commands" would be necessary . . . but, whatever your process was . . . right, try to maintain your system for as long as you can . . . Lubuntu 14.04 is fine . . . you could always add XFCE4 as a DE option to provide a bit of variety to your sessions . . . shouldn't be too much "conflict" between the dependencies of those two DE's . . . .

e..

---

### Post by Artemis3 on 2015-05-16
I used a method that involved placing a file in the root of the installed OSX partition and use openfirmware to boot to it (and i had to guess the partition number at the end)

It's because no matter what i did, this thing refused to boot from usb. Who knows if the optical drive even works?

But thanks anyway, i guess it ill remain mute for the time being.


The sign refers to my x86 machines, it is outdated, actually.

---

### Post by este.el.paz on 2015-05-16
> **Artemis3 said:**
> 

It's because no matter what i did, this thing refused to boot from usb. Who knows if the optical drive even works?

But thanks anyway, i guess it ill remain mute for the time being.


@Artemiss:

Of course the optical drive is working . . . it's a powerbook . . . .  It's only the newer stuff, like my '09 MBPro where the optical drive is already crapping out . . . .  Try it . . . .  

But, right, depending on what year your PB is, might determine whether it can boot from USB . . . supposedly my iBook from circa '04 might boot from usb, but I couldn't get it to do it, trying various commands in openfirmware . . . I gave up on that.  Fortunately the optical drive still works.  Did you not install Yaboot as boot selector?  I just did an install of U-MATE 15 using "automatic" "install alongside OSX" . . . and in powerpc it made the partition for Yaboot . . . and when I choose OSX, the system boots, when I choose "Linux" . . . the system crashes . . . Yaboot is very handy . . . .

But, right, sometimes a silent computer is a good computer . . . .

e..

---

### Post by Artemis3 on 2015-05-24
Very well. After making a coaster and finding out my desktop burner might not be quite right after being unused for years, i figured the drive of the machine could actually still burn discs and managed to make a 12.04 cd to boot from.

Lo and behold, it booted!, into a console... But who cares?, alsamixer worked, and ran the fancy script and gave me these results:

PowerMac Snapper (Dev 39) Sub-frame 0

```
no layout-id
child is ...
/proc/device-tree/pci@f2000000/mac-io@17/i2s@10000/i2s-a@10000/sound
device-id is ...
'
```
Perhaps it means 39? Now to patch the thing that needs patching and see if i can now get lucky with 14.04...

Reminder: Its a PowerBook G4 17".


Done, i made the manual dkms install according to rsavage instructions, sound is working now.

---

### Post by este.el.paz on 2015-05-24
Artemis:

Great work, yes "device 39" . . . way to pull it together . . . 14.04 should be fine . . . .  Did you make or have to make an xorg.conf file?  If "graphics" problems start happening . . . odd behaviors with windows and poor res . . . try to "configure xorg" (see instructions in FAQ) . . .  should be all you have to other than adding wifi driver, etc.

e..

---

### Post by Ben_Kuo on 2015-07-14
Hi guys, newbie to Ubuntu (and it's been a LONG time since I was mucking around at this level at Linux) but wanted to tell you that installing this patch fixed sound on my PowerMac G4 on 14.04 (20 inch "Flower Pot" I picked up off the curb for free yesterday :-). Initially no discovery of the sound card, and then -- before the patch -- it would load alsamixer but no sound ouput. Patch -- whether appropriate or not -- fixed whatever hardware discovery there was.

Powermac 6,3 MacRISK3 Power Macintosh 
298 (Flat panel iMac)

---

### Post by este.el.paz on 2015-07-14
> **Ben_Kuo said:**
> Hi guys, newbie to Ubuntu (and it's been a LONG time since I was mucking around at this level at Linux) but wanted to tell you that installing this patch fixed sound on my PowerMac G4 on 14.04 (20 inch "Flower Pot" I picked up off the curb for free yesterday :-). Initially no discovery of the sound card, and then -- before the patch -- it would load alsamixer but no sound ouput. Patch -- whether appropriate or not -- fixed whatever hardware discovery there was.

Powermac 6,3 MacRISK3 Power Macintosh 
298 (Flat panel iMac)

B_K:

Welcome to the forum, we need more people willing to play and test PPC iso's, so stick around. And, good job on getting 14.04 to produce sounds.  What about sights?  I had to do a bit of fiddling to get "video" going on my 800 MHz iMac G4 . . . what driver are you using? Did you set up an xorg.conf file for it?  Or "borrow" one from "linuxjemac"?? 

e..

---

### Post by lennart7 on 2015-07-21
I also wanted to report that I got sound working on a PowerBook6,5 (a white iBook G4 12 inch 1.2 GHz M9623LL/A) under Lubuntu 14.04 (kernel 3.13). 

Under 14.04.2 LTS I was getting "no card found" in /var/log/boot.log and no combination of /etc/modules and blacklisting in /etc/modprobe.d/blacklist.local.conf of snd-powermac and the 5 snd-aod-modules would allow me to run alsamixer. Since 14.04.2 has kernel 3.16, I was unable to install the patch as it is specified to be EXCLUSIVE to 3.13*.

# /etc/modules: kernel modules to load at boot time.
apm_emu
#snd-powermac
snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa
therm_adt746x

and have no /etc/modprobe.d/blacklist.local.conf. And graphics and wireless work, so I'm a real happy camper. 

Thank you for the patch.

Note that on my silver PowerBook5,6, M9676LL/A, PowerBook G4 1.5 MHz 15 inch, sound works (as well as graphics and wireless) with these same 5 snd-aoa modules under 14.04.2 LTS. The touchpad however can't distinguish between single and two-finger swipe: what a pain.

Lenn

---

### Post by lennart7 on 2015-07-21
I also wanted to report that I got sound working on a PowerBook6,5 (a white iBook G4 12 inch 1.2 GHz M9623LL/A) under Lubuntu 14.04 (kernel 3.13). 

Under 14.04.2 LTS I was getting "no card found" in /var/log/boot.log and no combination of /etc/modules and blacklisting in /etc/modprobe.d/blacklist.local.conf of snd-powermac and the 5 snd-aod-modules would allow me to run alsamixer. Since 14.04.2 has kernel 3.16, I was unable to install the patch as it is specified to be EXCLUSIVE to 3.13*.

# /etc/modules: kernel modules to load at boot time.
apm_emu
#snd-powermac
snd-aoa-codec-tas
snd-aoa-fabric-layout
snd-aoa-i2sbus
snd-aoa-soundbus
snd-aoa
therm_adt746x

and have no /etc/modprobe.d/blacklist.local.conf. And graphics and wireless work, so I'm a real happy camper. 

Thank you for the patch.

Note that on my silver PowerBook5,6, M9676LL/A, PowerBook G4 1.5 MHz 15 inch, sound works (as well as graphics and wireless) with these same 5 snd-aoa modules under 14.04.2 LTS. The touchpad however can't distinguish between single and two-finger swipe: what a pain.

Lenn

---

### Post by rsavage on 2015-07-27
For those wanting to use snd-powermac....

The attached deb will auto-magically recompile the module in 14.04 with the latest patches.  These should eventually make their way into the ubuntu kernel builds, but until then you can use dkms:

sudo apt-get install dkms

Then install the attched deb.

---

### Post by rsavage on 2015-07-28
The above won't work in debian jessie or newer versions of ubuntu, because the kernel source code has changed.  

For example, changes from 3.13 (used in 14.04) to 3.16:

```

diff -uprN linux-3.13/sound/ppc/powermac.c linux-3.16.7-ckt11/sound/ppc/powermac.c
--- linux-3.13/sound/ppc/powermac.c    2014-01-20 02:40:07.000000000 +0000
+++ linux-3.16.7-ckt11/sound/ppc/powermac.c    2015-05-12 09:34:49.000000000 +0100
@@ -58,7 +58,7 @@ static int snd_pmac_probe(struct platfor
     char *name_ext;
     int err;
 
-    err = snd_card_create(index, id, THIS_MODULE, 0, &card);
+    err = snd_card_new(&devptr->dev, index, id, THIS_MODULE, 0, &card);
     if (err < 0)
         return err;
 
@@ -122,8 +122,6 @@ static int snd_pmac_probe(struct platfor
     if (enable_beep)
         snd_pmac_attach_beep(chip);
 
-    snd_card_set_dev(card, &devptr->dev);
-
     if ((err = snd_card_register(card)) < 0)
         goto __error;
 

```

Changes from 3.13 to 3.19:

```

diff -uprN linux-3.13/sound/ppc/pmac.c linux-3.19.0/sound/ppc/pmac.c
--- linux-3.13/sound/ppc/pmac.c    2014-01-20 02:40:07.000000000 +0000
+++ linux-3.19.0/sound/ppc/pmac.c    2015-02-09 02:54:22.000000000 +0000
@@ -887,8 +887,7 @@ static int snd_pmac_free(struct snd_pmac
         }
     }
 
-    if (chip->pdev)
-        pci_dev_put(chip->pdev);
+    pci_dev_put(chip->pdev);
     of_node_put(chip->node);
     kfree(chip);
     return 0;
@@ -992,9 +991,9 @@ static int snd_pmac_detect(struct snd_pm
         return -ENODEV;
 
     if (!sound) {
-        sound = of_find_node_by_name(NULL, "sound");
-        while (sound && sound->parent != chip->node)
-            sound = of_find_node_by_name(sound, "sound");
+        for_each_node_by_name(sound, "sound")
+            if (sound->parent == chip->node)
+                break;
     }
     if (! sound) {
         of_node_put(chip->node);
diff -uprN linux-3.13/sound/ppc/powermac.c linux-3.19.0/sound/ppc/powermac.c
--- linux-3.13/sound/ppc/powermac.c    2014-01-20 02:40:07.000000000 +0000
+++ linux-3.19.0/sound/ppc/powermac.c    2015-02-09 02:54:22.000000000 +0000
@@ -58,7 +58,7 @@ static int snd_pmac_probe(struct platfor
     char *name_ext;
     int err;
 
-    err = snd_card_create(index, id, THIS_MODULE, 0, &card);
+    err = snd_card_new(&devptr->dev, index, id, THIS_MODULE, 0, &card);
     if (err < 0)
         return err;
 
@@ -122,8 +122,6 @@ static int snd_pmac_probe(struct platfor
     if (enable_beep)
         snd_pmac_attach_beep(chip);
 
-    snd_card_set_dev(card, &devptr->dev);
-
     if ((err = snd_card_register(card)) < 0)
         goto __error;
 
@@ -170,7 +168,6 @@ static struct platform_driver snd_pmac_d
     .remove        = snd_pmac_remove,
     .driver        = {
         .name    = SND_PMAC_DRIVER,
-        .owner    = THIS_MODULE,
         .pm    = SND_PMAC_PM_OPS,
     },
 };
diff -uprN linux-3.13/sound/ppc/tumbler.c linux-3.19.0/sound/ppc/tumbler.c
--- linux-3.13/sound/ppc/tumbler.c    2014-01-20 02:40:07.000000000 +0000
+++ linux-3.19.0/sound/ppc/tumbler.c    2015-02-09 02:54:22.000000000 +0000
@@ -795,16 +795,11 @@ static int snapper_set_capture_source(st
 static int snapper_info_capture_source(struct snd_kcontrol *kcontrol,
                        struct snd_ctl_elem_info *uinfo)
 {
-    static char *texts[2] = {
+    static const char * const texts[2] = {
         "Line", "Mic"
     };
-    uinfo->type = SNDRV_CTL_ELEM_TYPE_ENUMERATED;
-    uinfo->count = 1;
-    uinfo->value.enumerated.items = 2;
-    if (uinfo->value.enumerated.item > 1)
-        uinfo->value.enumerated.item = 1;
-    strcpy(uinfo->value.enumerated.name, texts[uinfo->value.enumerated.item]);
-    return 0;
+
+    return snd_ctl_enum_info(uinfo, 1, 2, texts);
 }
 
 static int snapper_get_capture_source(struct snd_kcontrol *kcontrol,


```

So you'll have to update the dkms package if you don't use 14.04.  It is well worth it though, as compiling one module using dkms takes seconds, whereas a whole kernel takes hours and hours.

---

### Post by fidelis2 on 2016-02-18
How would we make the sound to work with *Ubuntu 15.10* on a PPC Apple machine ?

In the other [thread here]("http://ubuntuforums.org/showthread.php?t=2196554&p=13435011#post13435011") concerning sound problems on PPC Apple machines with Ubuntu, a poster reported a week ago that he made his PPC Apple to play sound with Ubuntu 15.10, but his instructions don't work on my PPC iBook G4 so far. :-(

Some kernel log file lists the exact machine ID as: G4 iBook2 (PowerBook6,5)
According to some [Debian PPC audio list]("https://wiki.debian.org/PowerPC/SoundCards"), my audio chipset would be "Snapper", and via some other information I found the audio ID being hex 26 aka decimal 38.

Any help much appreciated.

---

