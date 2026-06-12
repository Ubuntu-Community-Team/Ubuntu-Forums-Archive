---
title: "Simply Can't Make nvidia-bl-dkms Work?!"
date: 2011-08-26
forum: Apple Hardware Users
---

### Post by _masterjonny on 2011-08-26
Hi! 

I like to think of myself as computer savvy, but when it comes to Linux I'm pretty much flailing in the dark. 

I'm trying to get Natty working on my Macbook Pro and so far have got every one of the main sections outlined in the Mactel Wiki working except for the screen brightness.

Now posting here isn't me being lazy, I like a challenge, and so far the whole process has been a good one, but this screen brightness has got me at my wit's end.

Things I've tried so far to get it working:

[LIST]
[*]Adding the registry dwords to the Xorg config
[*]Installing nvidia-bl-dkms before I install pommed
[*]Installing them the other way around
[*]Altering the config of nvidia-bl-dkms to change the module blacklist so that it loads the mbp one. And running update initramfs after this change.
[*]Adding mbp_nvidia_bl to my startup modules
[*]Adding nvidia_bl to my startup modules
[*]Tried to download the mbp-nvidia-bl-dkms package using the -t flag to force the Maverick version. It still claims the package can't be found.
[/LIST]
Pommed is working fine as my keyboard dims when I don't use it for a little bit, and all the other hot keys along the top row work.

And it's not just an unassigned hotkey, I can't see a slider for screen brightness in the power management preferences either.

Any suggestions!!??

I'm using the latest NVIDIA drivers (even though the additional drivers Window claims I'm not) and my graphics card is a GT330M.

My MBP is a 6.1 but there's no Wiki for me so I've been following the 6.2. Happy to provide as many logs/additional details as needed :)

---

### Post by lael on 2011-08-26
I have a mbp 6,1 and don't use nvidia_bl_dkms.  I use mbp_nvidia_bl
sudo apt-get install mbp-nvidia-bl-dkms

the 6,1 is similar to the 6,2:
[https://help.ubuntu.com/community/MacBookPro6-2/Maverick](https://help.ubuntu.com/community/MacBookPro6-2/Maverick)

I haven't upgraded to Natty though.

---

### Post by _masterjonny on 2011-08-26
I get the message:

E: Unable to locate package mbp-nvidia-bl-dkms

....as I'm writing edit....

I checked my software sources in Ubuntu software center and literally copied and pasted the Mactel line and shoved Maverick at the end of it.

Hey presto the package was found!!

Will post back shortly as to whether it actually works or not!

---

### Post by _masterjonny on 2011-08-26
Dude. I love you :)

Working like an absolute charm!

While your here....do you happen to have the Apple default color profile for our screens? Mines the anti glare but I doubt it makes a difference.

It's the last tick box I can't fill on the wiki pages. I deleted my Apple partition and it's gonna take me an aggeee to go through my time machine to find it!

If you can't don't worry, I can google all day long :D

---

### Post by lael on 2011-08-26
I've got the glass/glossy version.  

I've never done anything with the color profiles.  Still got OSX going, How do I get the color profile?

---

### Post by _masterjonny on 2011-08-26
[https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Colors](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#Colors)

---

