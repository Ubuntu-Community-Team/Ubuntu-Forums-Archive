---
title: "One DVD: Different Linux Distros including Windows XP installer"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-02-22
I wanted to compile different Linux distos (not iso) onto one DVD including one Windows XP SP3 installer.

The reason is that I am out of CDRs and burning one Linux distro onto one DVD is really a waste of money and SPACE.

I wanted to experiment at the same time, the best linux distro which will work on the old pc I am planning to install it to.

I would like that DVD to be bootable, similar to my Windows XP 6 in 1 installer. If the user wants the OEM or Volume License version, press 1 or press 2 ... similar to that.

Please reply immediately, I really needed your help, I have to burn everything after a few hours from now.

**Thanks in advanced.**

**ALSO,** most of them are on dial-up. Is it possible to download the most commonly used packages needed by an normal or average and newbie user of linux? Example, entertainment, the DVD restricted packages, so that they will be able to play DVDs, you know those kind of things.

I would like an offline installer of those commonly used and installed things, for sure there are or is no restrictions in our country.

---

### Post by Trail on 2008-02-22
Oh well, I *have* to reply immediately :)

No idea.

And, on another note, burning to DVD is not that much of a waste, if you think that it loads faster than CD :)

---

### Post by billgoldberg on 2008-02-22
No idea.

On the standard programs:

try linux mint, it's ubuntu with more things added (media support, ...).

I know that with remastersys you can make your own customized version of ubuntu with all software/packages and it's bootable. 

You can get them all on one dvd but it won't be bootable.

---

### Post by wirelessmonkey on 2008-02-22
Yes.  You have to burn each distro into a separate session on the dvd. Before burning them, you will have to customise a grub/lilo install that points to the appropriate disk sessions and their installers. Then make sure your custom grup is the 1st session on the dvd, and flagged bootable.
 
Don't ask me for technical details, it's been a looooong time since I last tried this, and google would be a better resource than I.

Also, APTonCD for standard applications, or burn a  copy of the .debs
Best of luck.

---

### Post by sandysandy on 2008-02-22
it is possible. Linux Bible 2007 edition has a similar DVD (with the book), which is bootable and lets u select different distros to install. 

but i don know how to burn such a DVD.

regards

---

### Post by notwen on 2008-02-22
I remember thinking the same thing when all the different Live distros came out.  This [link]("http://www.linux.com/articles/52927") may or may not prove to be useful.  I have seen it on the Linux Bible DVDs mentioned earlier, but have never made such a DVD myself.  It seems easy enough, best of luck and be sure to post back should you figure anything out. =]

---

### Post by bodhi.zazen on 2008-02-22
I do not think including the Windows XP installer is legal and as such is NOT SUPPORTED on these forums.

The question about multiple distros is valid so I will leave this thread open on those grounds. If if drifts to illicit distribution of windows -> Jail.

[http://www.linux.com/articles/52927](http://www.linux.com/articles/52927)

---

### Post by mgranet on 2008-02-22
You are perfectly legal in distributing the installer, as long as a key is not included. XP does come with a 30 day evaluation period built in.

---

### Post by gohanssjn on 2008-02-22
Plus you can make your own slip-stream disk's for service packs which is legal and supported by MS if I remember correctly.

---

### Post by jdong on 2008-02-22
> **mgranet said:**
> You are perfectly legal in distributing the installer, as long as a key is not included. XP does come with a 30 day evaluation period built in.
That is simply not true. You are not allowed to redistribute the XP installer, or for that matter even any Microsoft patches or anything not marked as a "Redistributable" (i.e. .NET Redistributable)

---

### Post by mgranet on 2008-02-22
> **jdong said:**
> That is simply not true. You are not allowed to redistribute the XP installer, or for that matter even any Microsoft patches or anything not marked as a "Redistributable" (i.e. .NET Redistributable)

Ahh, see, I used to do work with volume licencing installs, so this probably has something to do with it. I've looked around for redistribution on Retail, but can't find anything. Can someone point me to somewhere where I can get more info on this?

I was also under the impression that 'Redistibutable" meant other vendors (I.e, including .NET with a third part app). Please clarify.

---

### Post by mgranet on 2008-02-22
OK, I've spend the last 30 minutes looking through every EULA and searched microsoft.com thoroughly, and I can't find anything that says I can't redistibute the disk. I may end up calling Microsoft on this one to get clarification if no one else can find a definative answer on the subject,

OK, I just got off the blower with MS. The definative answer is NO, because a licenced copy of Windows MUST be accompanied by that little authentication sticker with the key on it. 

Sorry to get your hopes up :(

Not that I doubted you **jdong**, but I wanted to make sure there were no loopholes anyone was unaware of.

---

### Post by jdong on 2008-02-22
Indeed volume licensed copies are a bit different and various exceptions are granted in legalese for an admin wanting to roll out a huge patch via LAN, or slipstream a service pack CD.

More anecdotal history, a while back when SP2 came out for XP, a group tried to start up a torrent of the installer because akadns mirrors were being overwhelmed, and Microsoft actually responded with a cease-and-desist order.

---

### Post by mgranet on 2008-02-22
> **jdong said:**
> Indeed volume licensed copies are a bit different and various exceptions are granted in legalese for an admin wanting to roll out a huge patch via LAN, or slipstream a service pack CD.

More anecdotal history, a while back when SP2 came out for XP, a group tried to start up a torrent of the installer because akadns mirrors were being overwhelmed, and Microsoft actually responded with a cease-and-desist order.

I take it the worry is that someone will be distributing modified updates passed off as legit?

---

### Post by jdong on 2008-02-22
> **mgranet said:**
> I take it the worry is that someone will be distributing modified updates passed off as legit?

Right, that was the logical justification they gave. Of course, the lawyers gave a very different one to the torrent tracker admin (against EULA's redistribution terms)

---

### Post by mgranet on 2008-02-22
Well, thanks for clearing that up. It was MS activation terms that pushed me to Linux, but I still don't approve of pirating, and I'm glad we could clear this up before that happened.

---

### Post by jdong on 2008-02-22
> **mgranet said:**
> Well, thanks for clearing that up. It was MS activation terms that pushed me to Linux, but I still don't approve of pirating, and I'm glad we could clear this up before that happened.
It's okay, the intention was all good, just unfortunately strict licensing terms make it not possible. It's kind of silly what extents software authors can go to in order to limit the use of their product.

---

### Post by wirelessmonkey on 2008-02-22
Apologies, as the whole Windows thing just didn't register for some reason. I only processed the idea of multiple linux LiveCD/InstallCD's.

---

### Post by mgranet on 2008-02-22
The OP also wanted to include Windows SP3 to this master disk of operating systems, which we determined was illegal.

---

### Post by kaiju on 2008-02-23
wow, i think it's a really good idea to have lots of live distros on a dvd!
(except for the windows installer part, which besides being illegal to copy isn't really useful anyway :p )

i'm thinking of burning e.g. the gparted livecd ([http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)) and systemresquecd ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) for fixing things, cinemix (looks like their site is down for good) or geexbox ([http://www.geexbox.org/en/index.html](http://www.geexbox.org/en/index.html)) for an instant multimedia system, and a couple more live distros onto the same dvd.

i looked up the link posted by bodhi.zazen, but it seems that the script on Nautopia.net is not available anymore.
a quick search gave me this: [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html)

if there's somebody here who has already tried to do this sort of thing, i little help would be very nice :)

---

### Post by karlo on 2008-02-27
Ok, everyone come down. First of all if I AM going to burn Windows XP, i'll install it on my loved one or my relative's computer(s), so it's a PERSONAL BACKUP copy at the same time.

I will not release it in public so, nothing illegal is going to happen.

Here's the plan:

BOOT PROGRAM (let's the user choose which to install, what OS) > show the choices (a-linux b-windows c-freebsd) > show the installer for the chosen Item

or > Boot from hard disk

What do you think?

---

### Post by bodhi.zazen on 2008-02-27
> **karlo said:**
> Ok, everyone come down. <clip>  it's a PERSONAL BACKUP copy at the same time.

Making a "PERSONAL BACKUP copy" is gray at best, likely illegal

> **karlo said:**
> First of all if I AM going to burn Windows XP, i'll install it on my loved one or my relative's computer(s), so

Well, now it is not longer a personal copy is it ? That is definitely illegal.

---

### Post by jdong on 2008-02-28
A personal backup (i.e. archivial copy) is : 

**1. UNMODIFIED** from the original form. You cannot incorporate it into some other media or otherwise modify it and still claim it as a backup :)

**2. Not used** unless the original was destroyed for some reason.


You're right that it's none of our business what you do with your own copies of Windows. However, the kinds of questions you may be asking about how to do this involve committing an illegal act (repacking the windows installer onto a different medium) and we cannot provide support for this.

---

### Post by kaiju on 2008-02-28
we can probably all agree that this whole windows-part definitely is problematic.
besides, if someone is wondering about this kind of possibilities under linux, they should perhaps know better than to use that restriction-oriented os.

that said, someone with a bit of experience could really throw in some thoughts on how to make a nifty dvd with lots of mini distros :)

---

### Post by mgranet on 2008-02-28
One question I have is how to get all the live distro's to boot to a menu. For example, when I stick my Kubuntu disk in, and boot to it, it displays me a nice Kubuntu menu. However, if there are multiple distros on one disk, wouldn't they all be fighting to boot? Would some sort of wrapper program be needed to select which LiveCD to boot?

---

### Post by jdong on 2008-02-28
> **mgranet said:**
> One question I have is how to get all the live distro's to boot to a menu. For example, when I stick my Kubuntu disk in, and boot to it, it displays me a nice Kubuntu menu. However, if there are multiple distros on one disk, wouldn't they all be fighting to boot? Would some sort of wrapper program be needed to select which LiveCD to boot?


Well, ISOLinux clearly isn't gonna work anymore. Probably you are going to have to rewrite all of those menus into GRUB submenus. It shouldn't be hard to automatically sed isolinux.cfg into grub entries.

---

### Post by mgranet on 2008-02-28
So one would actually run GRUB off the disk? I.e., Boot into the discs GRUB, then select the LiveDistro, then load that? That sounds easy to do if that's what you meant.

---

### Post by jdong on 2008-02-28
Right, GRUB would be my #1 choice for the bootloader on the CD-ROM. Some LiveCD's (Kanotix?) already use GRUB as their bootloader, but for others we can adapt their isolinux.cfg to grub lines pretty trivially. Put each sub-distro in its own directory on the LiveCD.

The BIGGEST challenge will be negotiating with the distro to make it boot off the modified directory structure. Some distros have nice init scripts that take in as an argument where to find their home. Others guess at a hardcoded spot on the CD, which could be a big issue.

---

