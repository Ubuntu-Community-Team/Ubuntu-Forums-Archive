---
title: "HELP!! what gives on install?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-01
Hi,  I am trying to install ubuntu on my laptop which has the following HD config:

hda1 1GB I have selected to be swap
hda1 55GB is my WINXP drive set to /media/hda2
hda3 8GB is my root I have set to /
hda4 24GB is my WinXP recovery drive set to /media/hda4

I have clicked Forward and it say swap and / will be reformatted but also that 'this will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted'

???? Does this mean if I click Install I am going to lose my WindowsXP drives?

I need a dual boot system as the laptop is used by me for work but I ubuntu for home use!

Any help please??

---

### Post by taurus on 2006-09-01
> **elpuerco said:**
> 
hda1 55GB is my WINXP drive set to /media/hda2

I assume this is a typo, right!!!  You meant /dev/hda2, not /dev/hda1, where your XP is...

And if you tell the installer to use /dev/hda1 as swap and /dev/hda3 as /, then it shouldn't destroys your XP partitions...

---

### Post by bodhi.zazen on 2006-09-01
If you partitioned prior to installing Ubuntu you should be fine. It looks like Ubuntu wants to format swap and /, both of which are normal and OK. Make sure you windows and restore partition are not going to be formatted.

---

### Post by elpuerco on 2006-09-01
hi, on the Prepare mount points screen I have the following:

swap 1GB Partition 1 Primary hda1  REFORMAT

/media/hda2 55GB Partition 2 Primary hda2

/ 8GB Partition 3 Primary hda3 REFORMAT

/media/hda4 24GB Partition 4 hda4

?? There is no /dev to select in the mount point combo box?

---

### Post by taurus on 2006-09-01
Don't worry about the /dev because the installer knows where each partition is.

---

### Post by elpuerco on 2006-09-01
Alas this is not as simple as ubuntu would have me believe?

I clicked Install the progress bar zapped for a while and now it is back at the desktop from the live cd.

If I try to mount or look at say my Windows drive I get the error

Unable to mount the selected volume

device /dev/hda2 is not removable could not execut mount.

CHE?

PS just rebooted and it goes straight to Windows and not dual boot selection??

---

### Post by elpuerco on 2006-09-01
Any one able to offer any help please?

I have rebooted to the live cd and ubuntu works fine.

I click the install icon and do what I have listed previously and all it does is a quick whizz on the progress bar and back to the desktop?

I reboot into Windows and look at the partitions and it shows the linux swap partition but nothing on the 8GB which I selected at / root.

I am not complaining, just want to install and get using ubuntu.

However I am yet to come across any distro that installs easy:( 

My hopes were raised at how amzing the live cd was, but have been dashed by trying to perform a permanent install:( :( :( 

Any help please?

---

### Post by Sabyre on 2006-09-01
I am having similar problems...

After a few attempts to install normally and having it freeze up after step 1. I started in "Safe Graphic Mode" to install. The installation did not hang and went a lot quicker than previous attempts.

After step 6 and partitioning 9 gigs for / and 1 gig for swap the installation continued. After the installation and without a prompt of any sort I found myself back at the Ubuntu desktop.

I rebooted without the disk and it booted xp without ever asking to.

I am using a Toshiba Satellite M35X
1.5 Ghz Celleron M
256 MB DDR
40 Gig HD
Shared Video

Onboard everything (/sigh)

Intel chipset for Video/Sound

Realtek Ethernet

I'm tring to get a dual boot going. 
Before I started my drive was already partitioned in the following way.

5 Gig for Windows C:
35 Gig for Data D:

I resized the D: to create the 10 gigs for Ubuntu

Any help on this would be appreciated.

---

### Post by elpuerco on 2006-09-02
Now it might be that Ubuntu like to hog the entire disk, which I will never know, but it doesn't like dual boot.

So Windows vs Linux?

Linux - ubuntu
started to try installing yesterday at 3:30pm, have not been to bed, have downloaded ISO and checksummed, reburned, reloaded, same ole same ole.  Get to step 6 click Install quick flash of progress bar and back to live cd desktop.
No network! No access to other drives apart from CD.  Not much use!  Total time spent 23hrs!  Result?  No real workable Linux.

Windows XP Pro
Whilst waitning for ISO to download etc erased my sons PC, formatted disk, installed XP Pro, complete.  Network online, all drives visible and accessible, total working order.  Total time spent 1hr 15m max!  Result?  100% usable OS.

Brief history:
Red Hat tried on at least 2 occassions in the past 8 years, none worked.
SUSE 8 Pro tried once, not complete but close, even a visit from a member of local User Group failed to get it to work!

In the last 8 years 4 different PC typs owned, 3 different laptops owned.  Current laptop is at least a year old, maybe a little longer, not cutting edge!

So you see, I am not slagging off Linux, just pointing out that from my perspective Windows has the edge.

I am totally shattered and deflated at wasting 23hrs of my life on yet another failed attempt at yet another distro.

Think I will go to bed now.....

---

### Post by missmoondog on 2006-09-02
definitely the worst part of ubuntu is the installer. this particular computer i'm on now, will not install kubuntu correctly for nothing. using ubuntu instead, which is no biggie, but i do prefer kubuntu.

---

### Post by dbd on 2006-09-02
> **missmoondog said:**
> definitely the worst part of ubuntu is the installer. this particular computer i'm on now, will not install kubuntu correctly for nothing. using ubuntu instead, which is no biggie, but i do prefer kubuntu.

If you want you can install kubuntu on a ubuntu system, details here:
[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by elpuerco on 2006-09-02
To be honest, after 23hrs on ubuntu I sure aint gonna waste more of my life on kubuntu, nubuntu, noubuntu etc etc!

I sure don't want an OS that fights me all the way in order for me to use it, especially seeing as Windows XP gives me everything I want ready to go.

The only down side of XP is that as it is works install it has all the corp desktop etc etc loaded on each start up.

Linux kind of gave me the hope of a nice clean OS to play with to my hearts content.  But I mean play, not fight!:(

---

### Post by unisol on 2006-09-02
23hrs! it took me a couple of weeks to get dapper installed (due to a hardware problem that is too detailed to discuss)but when i found the solution i was rewarded with dapper if you want to go to back to windows thats up to you but if it were me i would stick it out just a little bit longer it  may be well worth it

---

### Post by elpuerco on 2006-09-02
Yeah, that is all well and true but where do I go?

At step 6 I see a quick flash of text detecting hardware hda1 or something, the progress gets to 15% then back to desktop.

I have no clue where to look what to do or what to try.  I want it to work, but just ain't got a clue what to do to even try to see where it is going wrong:( :( :( :( :(

---

### Post by otherMark on 2006-09-02
I've decided to wait another couple of years for my 6th try at a linux distro now or I'll see where MacOS is at by then. I've started building a small wind turbine using old hard drive magnets instead.

---

### Post by Papa-san on 2006-09-02
I have been struggling with install and network issues all along as well. I was first introduced to linux with ubuntu Breezy (5.10) The install went well. The only issue I had to deal with was the wireless, and three quarters of the issue was that I had someone supply me with the incorrect driver. My honest opinion is that in my case, with my Dell Lattitude C-610, Dapper is several steps in the wrong direction:

It (Dapper) installs OK for me, but then I have issues with the wireless, (Compounded from last time because I need to figure out how to get rid of the built in Bcm 43xx driver thingy that doesn't work with my card...) Plus now my video needs a lot of tweaking to keep my system from hard lockup three to five times a day! (I now have it down to three or four times a week, but have to deal with a screen resolution much lower than I like, plus I get lots of 'garbage' over my buttons until my cursor passes over them.) Additionally, my sound is completely GONE! I have tried every how-to and have got nowhere but to have so much bad code deposited in many, many folders...

If I could make one suggestion, it would be to dl a copy of Breezy Badger, and install that. Go through the tweaks you need for your system, THEN upgrade to Dapper. When it is doing the upgrade, it will pause several times to ask if such-and-such should be replaced. ALWAYS keep your previous settings! The new stuff, though meant to be helpful, is just not working out.

---

### Post by elpuerco on 2006-09-02
Mmm? I have just downloaded the alternat cd and will give that a go but if that does not work than Linux can take a running jump as it is just toooooo much like hard work.

I want to use the computer for every day stuff not spend my life searching for this patch, that patch, this fix oh and don't forget to stand on one foot whilst keeping your fingers crossed!!

Until the Linux community comes up with a decent install that works first time it will never be a patch on Windows

All very well for those who enjoy getting their hands dirty trying to make it work, but user like me just want to use the computer as a tool to do everyday stuff, not to do a degree in how to patch an OS!


](*,) ](*,) ](*,) ](*,)

---

### Post by bodhi.zazen on 2006-09-02
Ouch....

General thoughts:

1. It will take time to learn a new OS. Dual booting seems a good idea.

2. Linux (Ubuntu) will co-habituate with Windows just fine.

3. Try the alternate CD.

4. If all else fails, try an alternate distro. When I first started Ubuntu did not play well with my hardware so I changed distro's. After almost a year I had learned how to fix the problem, takes less the 5 minutes. Problem is it takes time to learn and OS, windows included.

5. You may need to start a new thread, give a detailed description of your problem and any error messages. I's sure your problems can be solved and that you will find the Ubuntu forum knowledgeable and helpful.

6. Google search.

Now I am on to new hardware with dual monitors and 3d graphics. I am Linux only, except at work.

---

