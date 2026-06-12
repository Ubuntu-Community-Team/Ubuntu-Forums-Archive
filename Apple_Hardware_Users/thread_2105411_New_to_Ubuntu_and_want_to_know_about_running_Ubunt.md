---
title: "New to Ubuntu and want to know about running Ubuntu 12.10 on a MacBook Pro"
date: 2013-01-15
forum: Apple Hardware Users
---

### Post by Mike108 on 2013-01-15
Greetings to the Ubuntu Community,

My name is Mike ):P and I am currently trying to see how Ubuntu works for me. Yesterday, I went and tried to install Ubuntu on my MacBook Pro and ran it via VirtualBox in OS X. Unfortunately, performance was less than stellar on the VM so I decided that it might be best for my to try Ubuntu on my Mac hardware with the help of triple booting. I tried to follow your Mac installation guide on Ubuntu's website and I came up with a few questions.

[LIST=1]
[*]Is rEFIt safe to use on my Mac?

[*]Does rEFIt substitute the Apple EFI on my MacBook?

[*]Is rEFIt easily removable? Do I have to reflash my MacBook Pro's EFI?

[*]I have a mid-2010 MacBook Pro (6,2) with the nvidia 330m GT processor, do you recommend using the Nvidia Linux drivers located on their webpage or use an open source alternative?

[*]The only relevant [[COLOR="DarkOrange"]guide that shows how Ubuntu works on my MacBook Pro model (6,2)[/COLOR]]("https://help.ubuntu.com/community/MacBookPro6-2/Precise") shows a list of what is working in Ubuntu 12.04, however, I cannot find a similar guide for Ubuntu 12.10. Where can I find the appropriate information to install Ubuntu 12.10 on my MacBook Pro? 

[*]I have 4GB of RAM installed on my MacBook Pro, should I just bite the bullet and get the 64-bit version of the OS?

[*]I'd prefer installing Ubuntu from a USB drive if possible. Does my MacBook Pro support installation from USB drive (I can boot a USB flash drive where I have the installer of Mac OS X Mountain Lion 10.8 successfully)? And if so, what would be the appropriate procedure to conduct a USB install?

[*]For those Mac users that are using Ubuntu 12.10 (32 or 64-bit). How does Ubuntu perform? is it fast and snappy or there is some degree of sluggishness as I saw on my Virtual Machine installation with VirtualBox?
[/LIST]

Well, that concludes my round of questions. I thank you for your time and information on this matter!

Best Regards,
Mike

---

### Post by lael on 2013-01-16
Hi Mike

I've got a MacBookPro 6,1 that I run Ubuntu on (the 17" version of the 6,2)

1) Is rEFIt safe to use on my Mac?
- Been working great for me on 3 different Macs for me over the years. 

2) Does rEFIt substitute the Apple EFI on my MacBook?
- Not exaclty, the Firmware loads rEFIt once its installed/blessed

3) Is rEFIt easily removable? Do I have to reflash my MacBook Pro's EFI?
- [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)
I don't believe you have to reflash anything - you should be able to do this from within OSX. [http://www.youtube.com/watch?v=jxq8nLX-Uzw](http://www.youtube.com/watch?v=jxq8nLX-Uzw)

4) I have a mid-2010 MacBook Pro (6,2) with the nvidia 330m GT processor, do you recommend using the Nvidia Linux drivers located on their webpage or use an open source alternative?
- I've got the same card in mine.  I used the nvidia-current for a while and have been using the nvidia-experimental from [http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat)  You'll be able to use the package management to install drivers for the graphics card.


5) The only relevant guide that shows how Ubuntu works on my MacBook Pro model (6,2) shows a list of what is working in Ubuntu 12.04, however, I cannot find a similar guide for Ubuntu 12.10. Where can I find the appropriate information to install Ubuntu 12.10 on my MacBook Pro? 
- I'm still running 12.04. In the past I've found that most of the wiki items should be similar.

6) I have 4GB of RAM installed on my MacBook Pro, should I just bite the bullet and get the 64-bit version of the OS?
- Yes 64bit.

7) I'd prefer installing Ubuntu from a USB drive if possible. Does my MacBook Pro support installation from USB drive (I can boot a USB flash drive where I have the installer of Mac OS X Mountain Lion 10.8 successfully)? And if so, what would be the appropriate procedure to conduct a USB install?
- The Apple firmware apparently doesn't handle USB Booting very well for most Linux Distros. I've resorted to CD/DVDs & a USB Key (Ubuntu will recognize and use both after its booted)


Good luck!

---

### Post by Mike108 on 2013-01-16
> **lael said:**
> Hi Mike

I've got a MacBookPro 6,1 that I run Ubuntu on (the 17" version of the 6,2)

1) Is rEFIt safe to use on my Mac?
- Been working great for me on 3 different Macs for me over the years. 

2) Does rEFIt substitute the Apple EFI on my MacBook?
- Not exaclty, the Firmware loads rEFIt once its installed/blessed

3) Is rEFIt easily removable? Do I have to reflash my MacBook Pro's EFI?
- [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)
I don't believe you have to reflash anything - you should be able to do this from within OSX. [http://www.youtube.com/watch?v=jxq8nLX-Uzw](http://www.youtube.com/watch?v=jxq8nLX-Uzw)

4) I have a mid-2010 MacBook Pro (6,2) with the nvidia 330m GT processor, do you recommend using the Nvidia Linux drivers located on their webpage or use an open source alternative?
- I've got the same card in mine.  I used the nvidia-current for a while and have been using the nvidia-experimental from [http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat)  You'll be able to use the package management to install drivers for the graphics card.


5) The only relevant guide that shows how Ubuntu works on my MacBook Pro model (6,2) shows a list of what is working in Ubuntu 12.04, however, I cannot find a similar guide for Ubuntu 12.10. Where can I find the appropriate information to install Ubuntu 12.10 on my MacBook Pro? 
- I'm still running 12.04. In the past I've found that most of the wiki items should be similar.

6) I have 4GB of RAM installed on my MacBook Pro, should I just bite the bullet and get the 64-bit version of the OS?
- Yes 64bit.

7) I'd prefer installing Ubuntu from a USB drive if possible. Does my MacBook Pro support installation from USB drive (I can boot a USB flash drive where I have the installer of Mac OS X Mountain Lion 10.8 successfully)? And if so, what would be the appropriate procedure to conduct a USB install?
- The Apple firmware apparently doesn't handle USB Booting very well for most Linux Distros. I've resorted to CD/DVDs & a USB Key (Ubuntu will recognize and use both after its booted)


Good luck!

Thanks for all that information. I'll take a look at it shortly...

---

