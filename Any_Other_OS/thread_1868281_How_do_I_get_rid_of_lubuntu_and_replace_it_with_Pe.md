---
title: "How do I get rid of lubuntu and replace it with PeppermintOS?"
date: 2011-10-24
forum: Any Other OS
---

### Post by brawnypandora0 on 2011-10-24
What do I copy and paste into the command line? I want my files to all still be there.

---

### Post by Elfy on 2011-10-24
Thread moved to Other OS/Distro Talk.

---

### Post by Lars Noodén on 2011-10-24
> **brawnypandora0 said:**
> I want my files to all still be there.

You have a separate /home partition, right?

---

### Post by crazy bird on 2011-10-24
If you want to replace Lubuntu completly with PeppermintOS, you could do it following the below:
 
- first backup all your important data such as files, bookmarks, emails onto a usb disc or memory stick or burn it on a cd/dvd if it is not that much.
- then download a live-cd of Gparted and burn it onto a disc.
- restart your pc with the Gparted live-cd in the cd/dvd drive.
- when Gparted is up-and-running, remove the partition on which Lubuntu is installed.
- then reboot your machine.
- you will get a message saying to remove your Gparted live-cd, this is a good time to swap the Gparted live-d with the installation disc/live-cd of PeppermintOS.
- after your machine is rebooted, follow the installation instruction given by PeppermintOS.
 
Good luck!

---

### Post by brawnypandora0 on 2011-10-24
> **Lars Noodén said:**
> You have a separate /home partition, right?

I don't know. How do I find out this?

---

### Post by Lars Noodén on 2011-10-24
There are several ways.  One is to run [df -h](http://manpages.ubuntu.com/manpages/oneiric/en/man1/df.1posix.html) and see if /home is on a line of its own.  Another is to look in /etc/fstab and see if /home is on a line of its own.  Another is to run [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html) and see if /home is on a line of its own. And so on.

---

### Post by brawnypandora0 on 2011-10-24
> **Lars Noodén said:**
> There are several ways.  One is to run [df -h]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/df.1posix.html") and see if /home is on a line of its own.  Another is to look in /etc/fstab and see if /home is on a line of its own.  Another is to run [mount]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html") and see if /home is on a line of its own. And so on.

No, I don't have a separate home partition!

---

### Post by boydrice on 2011-10-24
> **brawnypandora0 said:**
> No, I don't have a separate home partition!

Just backup your data on an external hd or whatever it is that you use to make backups.  Then do a clean install of Peppermint OS.

---

### Post by crazy bird on 2011-10-24
> **boydrice said:**
> Just backup your data on an external hd or whatever it is that you use to make backups. Then do a clean install of Peppermint OS.
 
Like i already mentioned: [http://ubuntuforums.org/showpost.php?p=11386525&postcount=4](http://ubuntuforums.org/showpost.php?p=11386525&postcount=4).

---

### Post by Lars Noodén on 2011-10-24
> **boydrice said:**
> Just backup your data on an external hd or whatever it is that you use to make backups.  Then do a clean install of Peppermint OS.

Be sure to test the backups before doing the clean install.  Also when doing the install, this is a good chance to make a separate /home partition!

---

### Post by boydrice on 2011-10-24
> **crazy bird said:**
> Like i already mentioned: [http://ubuntuforums.org/showpost.php?p=11386525&postcount=4](http://ubuntuforums.org/showpost.php?p=11386525&postcount=4).
Right, except I left out the needless part of using a GParted CD.

---

### Post by amjjawad on 2011-10-24
> **brawnypandora0 said:**
> How do I get rid of lubuntu and replace it with PeppermintOS

Any reason(s) why you want that?
I'm one of Lubuntu Team Members and I'd like to know what thing(s) that you didn't like about Lubuntu :)

---

### Post by brawnypandora0 on 2011-10-28
> **Lars Noodén said:**
> There are several ways.  One is to run [df -h]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/df.1posix.html") and see if /home is on a line of its own.  Another is to look in /etc/fstab and see if /home is on a line of its own.  Another is to run [mount]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html") and see if /home is on a line of its own. And so on.

I don't understand these instructions. What does it mean to "run mount" and "run df----h"???

Also, when I type in /etc/fstab, I get a message that says directory doesn't exist!

---

### Post by Lars Noodén on 2011-10-28
> **brawnypandora0 said:**
> I don't understand these instructions. What does it mean to "run mount" and "run df----h"???

Also, when I type in /etc/fstab, I get a message that says directory doesn't exist!

You have to run them in the terminal.  /etc/fstab is a file, you can read it with Gedit

---

### Post by MG&amp;TL on 2011-10-28
> **amjjawad said:**
> Any reason(s) why you want that?
I'm one of Lubuntu Team Members and I'd like to know what thing(s) that you didn't like about Lubuntu :)

Peppermint OS looks a lot cooler. I think Lu- needs a graphic designer to give it a going-over-I'm not sure the blue does any favours. Sure, yopu can tweak it, but that's not the point.

Just my suggestion. :)

---

### Post by MG&amp;TL on 2011-10-28
```
gedit /etc/fstab
```

---

### Post by amjjawad on 2011-10-28
> **MG&TL said:**
> Peppermint OS looks a lot cooler. I think Lu- needs a graphic designer to give it a going-over-I'm not sure the blue does any favours. Sure, yopu can tweak it, but that's not the point.

Just my suggestion. :)

I do respect your opinion and suggestion but let's look at it from another side. Lubuntu is an official variant of Ubuntu and the support that you can get for Lubuntu compared to the support you may get for Peppermint is much more IMHO :)

By the way, we do have a Graphics Designer obviously and the blue is, if you ask me, like our trademark.

With Linux, everything/anything is possible. You can change the default look of any OS the way you want and like. I don't care whether it's blue, red, green, yellow, etc ... I just need something super light and simple :)

---

### Post by MG&amp;TL on 2011-10-28
> **amjjawad said:**
>  support that you can get for Lubuntu compared to the support you may get for Peppermint is much more IMHO :)
 I just need something super light and simple :)

...two very good points. I have it running on old hardware. So your efforts have not gone to waste by any means. :D

---

### Post by amjjawad on 2011-10-28
> **MG&TL said:**
> ...two very good points. I have it running on old hardware. So your efforts have not gone to waste by any means. :D

One for Linux and Linux for all :P

Glad to see you active on the Forum, my friend :)

---

### Post by MG&amp;TL on 2011-10-28
I note Lubuntu development release? Where do you get that? I can run off a USB or virtualbox...

I know mine says ubuntu dev release too, but I just haven't been bothered to change it yet...I followed the alphas and betas of 11.10.

---

### Post by amjjawad on 2011-10-28
> **MG&TL said:**
> I note Lubuntu development release? Where do you get that? I can run off a USB or virtualbox...

I know mine says ubuntu dev release too, but I just haven't been bothered to change it yet...I followed the alphas and betas of 11.10.

If you check my signature, you'll find "Lubuntu Team Member".
I have joined Lubuntu and LXDE Team back in August :)
Before the final release of 11.10, I was testing so I changed that to Development releases :)

I didn't sleep for the last 25hours or perhaps more? sorry if there are some spelling/typo :P

---

### Post by MG&amp;TL on 2011-10-28
Off to bed with you! :D

---

### Post by brawnypandora0 on 2011-10-28
I want to replace lubuntu with Peppermint by typing something into the command line--I heard that's an alternate way of installing. I don't have any blank CDs or USB drives.
 
So what's the code I have to type in?

---

### Post by tartalo on 2011-10-28
> **brawnypandora0 said:**
> I want to replace lubuntu with Peppermint by typing something into the command line--I heard that's an alternate way of installing. I don't have any blank CDs or USB drives.
 
So what's the code I have to type in?

Lubuntu and Peppermint share a lot, and I guess that one could change the sources.list and try migrating that way, but I doubt that there's any guarantee of success and most probably you will land in a package dependency hell and end with a Frankenstein that has neither the advantages of Lubuntu nor PeppermintOS. I haven't tried it myself though.

My advise? Wait until tomorrow, buy a CD and do a clean installation.

---

### Post by brawnypandora0 on 2011-10-28
Does anyone know what the code is for lubuntu to PeppermintOS conversion?

---

### Post by MG&amp;TL on 2011-10-28
I'm sorry, brawnypandora, but I don't think anybody does, and it is likely to leave you with a BROKEN system. 

However, one thing you could do is manually download the packages that peppermint uses, install them (carefully, one by one), and remove the ones that lubuntu uses. The forums are happy to help with that, but it will require a lot of effort on your behalf as well. It is not a simple as typing a few things in the terminal. You are replacing an OS (albeit with a similiar one).

What have you got against a CD or USB?

---

### Post by MG&amp;TL on 2011-10-28
You might, however, want to look here:

[http://peppermintos.net/]("http://peppermintos.net/")

They may have more answers than we do.

---

### Post by brawnypandora0 on 2011-10-29
When I switched from ubuntu to lubuntu all I did was copy and paste code in the terminal.

Why can't I now switch from lubuntu to Peppermint using the same method?

---

### Post by wolfen69 on 2011-10-29
Best thing to do is backup your stuff....then reinstalls don't matter much.

---

### Post by Elfy on 2011-10-29
> **brawnypandora0 said:**
> When I switched from ubuntu to lubuntu all I did was copy and paste code in the terminal.

Why can't I now switch from lubuntu to Peppermint using the same method?

I assume you did something along the lines of

sudo apt-get install lubuntu-desktop

You can't do that with peppermint as it's not in the repositories.

---

### Post by Lars Noodén on 2011-10-29
> **brawnypandora0 said:**
> When I switched from ubuntu to lubuntu all I did was copy and paste code in the terminal.

Why can't I now switch from lubuntu to Peppermint using the same method?

As forestpiskie pointed out, it's not in the Ubuntu repositories.  What that means specifically is that Peppermint is a completely different distro and has its own repositories.  From what I read, it also uses APT, so it *might* be possible to do an upgrade.  It is also possible that such an attempt would render your system unusable and in need of a clean install.

You'd need to download and add the PGP key for the Peppermint repositories.  Then you'd have to change /etc/apt/sources.list to point to the Peppermint repository then you'd try update and then dist-upgrade and cross your fingers.

I wouldn't advise it unless you're ready to do a clean installation of ubuntu again if it fails.

---

### Post by amjjawad on 2011-10-29
> **brawnypandora0 said:**
> What do I copy and paste into the command line? I want my files to all still be there.

**Long story short**, [COLOR=Red]BACKUP[/COLOR] your important files, download the latest Peppermint OS iso from its website, check MD5SUM, create the Live Media (CD or USB - I don't know other ways, sorry), format Lubuntu and Install the new one. Mission Accomplished.

[COLOR=Red]** How to backup your files?**[/COLOR]

First of all, backup your home folder. Your home folder must be: 

[COLOR=Red]/home/yourname

[COLOR=Black]Directories and Files inside the above path are your files that you may need to backup.

If you have another partitions, make sure to backup the files stored there.

Just for the record, [Peppermint OS]("http://en.wikipedia.org/wiki/Peppermint_OS") is based on Lubuntu.
See also: [http://distrowatch.com/table.php?distribution=peppermint](http://distrowatch.com/table.php?distribution=peppermint)
[/COLOR][/COLOR]

---

### Post by Lars Noodén on 2011-10-29
It's also possible to use Grub to boot directly from an ISO cd image on the hard drive.  I've never done it, but if it works that would be one way to avoid burning a cd or making a bootable usb stick.

---

