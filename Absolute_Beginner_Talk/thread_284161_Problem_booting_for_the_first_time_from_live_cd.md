---
title: "Problem booting for the first time from live cd"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by anewbie on 2006-10-25
Last night I attempted to boot from the daily live cd (made last night - so it was the oct 23rd daily). 

I validated the md5 of the iso i downloaded and validated the md5 from the cd after it was burned. 

When I boot from the cd i get the start menu - if i hit return (to start) it shows the ubuntu logo for a while and then eventually a black screen with a single '_' in the top left corner. After that nothign happens. I tried to validate the cd (i think it was option 4 or 5) and it seems ok for a while but eventually i get a vbuff error. I tried to boot from the prompt (hit return to get a lilo prompt) and then gave the arguments "live noapic nolapic" but the same thing happened.

--
This is an older machine (nforce 2 athlon 1.7 eide drives). The iso was the iso.386. THe reason I'm trying the daily live cd is that I will be building a new machine next week with a p965 and I wanted to test the cd as well as test install - first time running linux at home.

Btw I seen similar problems ([http://kubuntuforums.net/forums/index.php?topic=9895#bot](http://kubuntuforums.net/forums/index.php?topic=9895#bot)) but no answers...

---

### Post by anewbie on 2006-10-25
Samll error in description of machine - it is not nforce2 but rather KT3 Ultra2 (msi). It is a desktop. Also it has 512 ram and I check the system under windows (ran prime95 for 5 hours and various other tests without issue).

---

### Post by Dr. Nick on 2006-10-25
Have you tried it with a final release version and not a daily cd? I dont think the daily cds go through the testing procedures like the final release ones do.

Not sure if thier is any one specific problem that would cause that to happen

---

### Post by IronArjen on 2006-10-25
I have the same problem and found out that although the new setup of 1 CD is easy going it has one problem. In order to install Unbuntu, you need to run Ubuntu from a live CD which requires 128 or maybe even 256  mega memory. My machine is old and does not have it, Yours is old and might not have it either. To me exactly the same happens, get the logo, it even changes a bit (adding two or three icons) but I end up with an empty screen.  

I am going to try the ISO image now

---

### Post by Bachstelze on 2006-10-25
> **IronArjen said:**
> IMy machine is old and does not have it, Yours is old and might not have it either.

That's what "alternate" CDs are for :)

---

### Post by Sef on 2006-10-25
If your computer has less than 128 mb ram, you have to use the alternate cd. It is text-based, but very easy to follow.  The only problem would be if you needed to partition your disk for a [dual boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Bachstelze on 2006-10-25
> **Sef said:**
> The only problem would be if you needed to partition your disk for a [dual boot]("http://users.bigpond.net.au/hermanzone/").

Why ? The text-based installer works pretty well for that too...

---

### Post by anewbie on 2006-10-25
This machine has 512MB. Shouldn't it work? This is the only cd i've tried. Can you provide a link if there is another cd i should try ? I can download it and burn tonight.

---

### Post by elchinovi on 2006-10-25
> **anewbie said:**
> This machine has 512MB. Shouldn't it work? This is the only cd i've tried. Can you provide a link if there is another cd i should try ? I can download it and burn tonight.

Your memory is more than enough for it to work...
I'd try getting a final release, like it was mentioned before, and try with it.
Just in case... did you burn the x386 version, right?
Good Luck!

---

### Post by bulldog on 2006-10-25
> **anewbie said:**
> This machine has 512MB. Shouldn't it work? This is the only cd i've tried. Can you provide a link if there is another cd i should try ? I can download it and burn tonight.

Choose your location and download what you want to have,

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by anewbie on 2006-10-25
Yes. It was iso.386 - not amd6 or powerpc. Will try a different version tonight (per link above). Hum... would like to get a daily to work so i'll have a chance with the new machine.

> **elchinovi said:**
> Your memory is more than enough for it to work...
I'd try getting a final release, like it was mentioned before, and try with it.
Just in case... did you burn the x386 version, right?
Good Luck!

---

### Post by Dr. Nick on 2006-10-25
You can always upgrade to the equivalent of the daily images once installed. The updates are all done online which will bring you up to the current ver

---

### Post by anewbie on 2006-10-25
My concern is device supported via the kernel. Per original subject this is a test install for a p965 system I will be setting up and I need the kernel to support the jmb eide device so i can boot (cd/boot disk will hang off the jbm 36[1 or 3] while the user data will sit on soft-raid 1 pair of sata drives (at least that is my hope)

---

### Post by anewbie on 2006-10-26
Ok using a release of dapper (per suggestion) fixed the problem. Only surprise was that i did not have an option to setup a software raid.

Now - how do i go about getting a working version of edgy - i'll need the newer kernel for the new hardware (p965 board). Do I just keep trying daily cd until one work or is there a better method ?

---

### Post by Dr. Nick on 2006-10-26
they just released edgy as a final version here
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

If dapper will install at all on the newer hardware, you can do that then if the network works you can then edit the file /etc/a[t/sources.list and replace all intances of dapper with edgy, then run **sudo apt-get update** and then either open synaptic nad hit upgrade, or run

**sudo apt-get dist-upgrade** and it will update to edgy.

It may just be easier to get a final release of dapper cd image though and use it.

---

### Post by anewbie on 2006-10-26
Ok thanks. Where are the release notes for 6.10 also why is 6.10 called edgy or is it now dapper? (I checked this link for release notes but 6.10 was not listed:
[http://www.ubuntu.com/download/releasenotes](http://www.ubuntu.com/download/releasenotes) - i looked ath the 6.10 file list but could not find the kernel version - to check if that kernel has the support i need for jbm 361 or jmb 363 (not sure which mb i will end up with but it will have either the 361 or 363)
--
Ok I foudn the release notes here:
[https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)
--
I guess the download page you posted confused me becausae it seem to indicate that 6.10 was now dapper but it is still edgy even though it was released :)

---

### Post by anewbie on 2006-10-26
Arrrrggggg - the release notes do not indicate which kernel. How can they leave this out :(

---

### Post by Dr. Nick on 2006-10-26
kernel on mine is  2.6.17-10-386, I imagine that is what is on the cd, or very close. I had a dapper install and updated online to edgy.

dapper was 6.06 
edgy is 6.10 
they dont change names once released.

---

### Post by anewbie on 2006-10-26
Ok thanks. I guess I will need a daily cd or something like that to get a newer kernel. I wonder if there is a boot floppy with  just enough foo'ish to copy the kernel from the floppy to the hard disk.

---

### Post by Dr. Nick on 2006-10-26
I doubt the kernel will fit on a floppy, its atleast 15mb or so.

---

### Post by anewbie on 2006-10-31
Now that edgy is out where are the daily cdroms? (What comes after edgy)? T

---

### Post by anewbie on 2006-10-31
One other question - when I try to login and gnome starts up is there a  log anywhere? What happened is I took an old .gnome2 directory I like a lot and hoped I could run it from a ubuntu install (er I mean configure the desktop un=ubuntu like but i couldn't log in - i figure something (like task applet) was unable to run but i cuoldn't figure out what).

---

### Post by Dr. Nick on 2006-10-31
> **anewbie said:**
> Now that edgy is out where are the daily cdroms? (What comes after edgy)? T

Fiesty Fawn 
[http://ubuntuforums.org/forumdisplay.php?f=177](http://ubuntuforums.org/forumdisplay.php?f=177)

will be the next version, They will probably start with the daily cd roms in a while.

Not sure about the gnome logs though

---

### Post by anewbie on 2006-10-31
Ok - thanks nick. I'll dig around. I think the problem is i want some of ubuntu extended menu but some of basic gnome2 flexibility/look - esp with the extended task bar. Not sure ubuntu supports that concept :) but i'll take a crack - need to search more of the forums i think and howto.

---

