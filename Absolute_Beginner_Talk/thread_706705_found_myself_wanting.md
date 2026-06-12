---
title: "found myself wanting"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by TechDragon on 2008-02-24
Hello,

I love ubuntu but I found myself wanting for three reasons.

1. I could not get NTFS external harddrives to work right.

2. USB devices seemed spotty, everytime I unplug one I get errors about unsafe removal.

3. Repository -- I would want something and download it from the repo only to find out that it was outdated.  I would then have to remove it and go to the site and download the never package and install it.


I would like to know if any one has any suggestions.

on problem number 1 -- I installed made sure ntfs-3g was installed, I also installed the ntfs-3g config tool.  I tried forcing the drives, and everything.  Sometimes it would work most of the time it wouldn't

On problem number 2 -- Nothing, any suggestions?

On problem number 3 -- I added all the repos in synaptic, is there an even more experimental repo?

---

### Post by Lysander10 on 2008-02-24
> **TechDragon said:**
> Hello,

I love ubuntu but I found myself wanting for three reasons.

1. I could not get NTFS external harddrives to work right.

2. USB devices seemed spotty, everytime I unplug one I get errors about unsafe removal.

3. Repository -- I would want something and download it from the repo only to find out that it was outdated.  I would then have to remove it and go to the site and download the never package and install it.


I would like to know if any one has any suggestions.

on problem number 1 -- I installed made sure ntfs-3g was installed, I also installed the ntfs-3g config tool.  I tried forcing the drives, and everything.  Sometimes it would work most of the time it wouldn't

On problem number 2 -- Nothing, any suggestions?

On problem number 3 -- I added all the repos in synaptic, is there an even more experimental repo?

1) Reformat your external harddrive with another filesystem. I would recommend ReiserFS, or FAT32 if it needs to be shared with a Windows PC.

2) Before removing USB drives, right-click the icon on your desktop and click "Unmount volume"

3) Do you really need to absolute latest version? Probably not. I would recommend you stick to the stable version in the repository.

---

### Post by mwanstall on 2008-02-24
Hi TechDragon,

1/ What (if any) errors were coming up when you were trying to mount your external drives? I've had a friend who had similar issues with external NTFS drives though, sometimes they'd work, sometimes they wouldn't mount...to the best of my knowledge he never found a work around.

2/ Are you right clicking on the device icon and choosing to Remove the device before you unplug it from your computer? Not doing so can mess up the file system on the key and it'll require a format to get it working again.

3/ Depends what you mean by outdated. Which version of Ubuntu are you using? A lot of the programs I use have newer versions available on their individual sites but the repo versions work perfectly so I'm happy to have the stability of easily integrated software and wait for the next Ubuntu release to get the new versions. If you still want bleeding edge you can just install the individual repos for each program.

---

### Post by seventhc on 2008-02-24
1 - if you look in add remove do a search for ntfs...you might have to change to  *all available software *that would allow you to read and write from ntfs.

2 - For usb removal it is best to right click on the icon and choose unmount volume. You do this in windows also but I think it says eject, so this isn't ubuntu specific.

3 - not sure about experimental repos but you can get a lot of good stuff from [http://getdeb.net/](http://getdeb.net/) usually having new versions available.

**Edit:** regarding #1, I just noticed it's for external, I'm not sure if the program I mentioned works the same for that or not. Never used it that way. Others should know though.

---

### Post by TechDragon on 2008-02-24
1. I have a 320gb external harddrive and an 80gb internal drive, so I cant just reformat it.  I have no where to put the data in the meantime. 

2. Yes, windows used to do this during the win2k days, but they remedied it with xp and it appears that other distros have fixed this some how.  I figured I may just need to download some piece of software.

3.  Yes, that is what I started to do, but even some of those are behind.

Thanks for the ideas so far.  I do like ubuntu's polish, and it feels like one of the most actively developed distros.  May just be me, I am a newb.  In fact I started out asking which distro is best and recieved the you must choose for yourself.  So I have been experimenting.  I have it down to 3 that I like, Mandriva cooker, Fedora, and Ubuntu.  Mandriva and Fedora, are pretty cutting edge but lack the software choices of ubuntu.

---

### Post by seventhc on 2008-02-24
>  Yes, windows used to do this during the win2k days, but they remedied it with xpin xp it still should be ejected, all data can be lost if not done properly.
I have had it happen, I was forunate enough to have a backup of everything.
This was for work and my usb had nothing but tools, so I didn't feel like ejecting from each machine so I would just pull it out and plug it into another machine.
On 2 occasions all data was lost. So I never heard that this was a problem, it's just a matter of correctly removing a device.

Yes as far as which distro to choose, it's mind boggling at the number of choices, but ubuntu does support a lot more out of the box than others I have tried...on my current machine anyway.
I personally like debian, but debian seems to have a problem with my vid card, I'm sure I could make it work but since ubuntu is debian based...tons of help here at the forums, I choose ubuntu. :)... and it works with my hardware.. :)

---

### Post by tango_ninja on 2008-02-24
for #3, have you tried force mounting the drive? (let's say the drive is **sda1**)

```
mount -t ntfs-3g /dev/sda1 /mnt -o force
```

As long as your drive contains only data it should be ok....if it contains a Windows OS partition do NOT do this !

---

### Post by Lysander10 on 2008-02-24
> **TechDragon said:**
> 1. I have a 320gb external harddrive and an 80gb internal drive, so I cant just reformat it.  I have no where to put the data in the meantime. 

2. Yes, windows used to do this during the win2k days, but they remedied it with xp and it appears that other distros have fixed this some how.  I figured I may just need to download some piece of software.

3.  Yes, that is what I started to do, but even some of those are behind.

Thanks for the ideas so far.  I do like ubuntu's polish, and it feels like one of the most actively developed distros.  May just be me, I am a newb.  In fact I started out asking which distro is best and recieved the you must choose for yourself.  So I have been experimenting.  I have it down to 3 that I like, Mandriva cooker, Fedora, and Ubuntu.  Mandriva and Fedora, are pretty cutting edge but lack the software choices of ubuntu.

1) Coincidentally, I have a 320GB external harddrive and an 80GB one, as well. I didn't want to deal with the NTFS filesystem that came on it by default, so I repartitioned it before I put anything on it...

2) Yeah, the "problem" you're referring to isn't actually a problem, it's just something you're supposed to do, in every OS, so you won't lose date.

3) Once again... why do you really need the absolute cutting-edge software? Usually, it isn't stable anyway. It's best to stick with the repositories unless you have some specific reason not to.

---

