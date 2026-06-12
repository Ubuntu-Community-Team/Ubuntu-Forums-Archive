---
title: "help with downloading repo for gutsy"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by DestroyMicroshaft on 2008-01-04
is there a way for me to download the entire gutsy repository to put on dvds, I mean everything, universe multiverse, restricted everything, from gutsy?

---

### Post by forestpixie on 2008-01-04
right at bottom of the page are the dvd downloads

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

and I'd do it as a torrent as well

---

### Post by DestroyMicroshaft on 2008-01-04
At the bottom isnt that just to download ubuntu itself on a dvd? I want the repository.

---

### Post by llamakc on 2008-01-04
Google is your friend.

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

---

### Post by forestpixie on 2008-01-04
as far as I know that is the majority of it all - Ubuntu is the same size 700Mb, so would imagine the other 3.5Gb are the apps

but wait around - see if you get other replies

Edit - there you go - I know something new as well - don't think I'd be wanting to do 30Gb worth though :)

---

### Post by DestroyMicroshaft on 2008-01-04
i think the dvd is kde xfce and gnome it might have edubuntu too im not sure but the whole repo is I beleive in the ball park of 40gb, I know you can buy the repo without the restricted stuff on 5 dvds.

---

### Post by forestpixie on 2008-01-04
yea that's where the llamakc link leads

---

### Post by DestroyMicroshaft on 2008-01-04
well thank you llmakc but thats not really what Im looking for and ive googled believe me, apparently there is a problem with gutsy when downloading the repo, so thats why Im asking here.

---

### Post by DestroyMicroshaft on 2008-01-04
teeny bump

---

### Post by ugm6hr on 2008-01-04
Presumably this will work - but I have never tried it!

Do a fresh install of Ubuntu (whichever architecture / version you want to download the repo for).
Ensure all the repos you want are being used.
Open Synaptic Package Manager.
Click Reload to update the repo info.
It should be marked **All** in the left hand column.
Left-click the top Package
Scroll down the list of Packages to the bottom.
Shift & left-click the bottom Package
This should select all Packages
Right-click on any of the selected Packages, and select Mark for installation
Wait for a long time while Synaptic creates the list
File->Create Download Script

This should create a wget script for ALL the Packages in the repos you have selected.  You can then run this on any computer (including the Ubuntu one) to download the entire repo (excluding the default Ubuntu install packages).  I have no idea how long this will take though!  Perhaps worth dividing the 20,000+ packages into smaller blocks to make it manageable.

---

### Post by DestroyMicroshaft on 2008-01-04
> **ugm6hr said:**
> Presumably this will work - but I have never tried it!

Do a fresh install of Ubuntu (whichever architecture / version you want to download the repo for).
Ensure all the repos you want are being used.
Open Synaptic Package Manager.
Click Reload to update the repo info.
It should be marked **All** in the left hand column.
Left-click the top Package
Scroll down the list of Packages to the bottom.
Shift & left-click the bottom Package
This should select all Packages
Right-click on any of the selected Packages, and select Mark for installation
Wait for a long time while Synaptic creates the list
File->Create Download Script

This should create a wget script for ALL the Packages in the repos you have selected.  You can then run this on any computer (including the Ubuntu one) to download the entire repo (excluding the default Ubuntu install packages).  I have no idea how long this will take though!  Perhaps worth dividing the 20,000+ packages into smaller blocks to make it manageable.


Thank you for your help thats a great idea I had not considered, my only issue with that is how will I break the repo up into dvds once the repo is downloaded?

---

### Post by llamakc on 2008-01-04
> **DestroyMicroshaft said:**
> well thank you llmakc but thats not really what Im looking for and ive googled believe me, apparently there is a problem with gutsy when downloading the repo, so thats why Im asking here.

So post on the bug report about the problem, or research THAT problem. Stuff gets fixed fast when folks contribute.

---

### Post by Megaqwerty on 2008-01-04
If I'm not mistaken, I belive what you're looking for is this:
[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

Hope that helps,

Megaqwerty

P.S. Don't forget to change **--dist=dapper** in step 3 to **--dist=gutsy** and change **--section=main,multiverse,universe** to **--section=main,multiverse,universe,restricted**

---

### Post by DestroyMicroshaft on 2008-01-04
Awesome, thx a ton will report back once I get this rolling!

---

### Post by k3lt01 on 2008-01-04
This is an Ubuntu community how to on what you are wanting. It is right here on this forum in the "how to" or "tutorial" section. I am using it myself and with great success, it even tells you how to download other repos that you can use on Ubuntu as well.

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

P.S. If you use it be sure to say Hi and thanks to BobSongs as he has worked hard with this so the entire Ubuntu community can benefit.

Edit: The code you need to put in for Gutsy has changed for some repos and BobSongs spent some time finding the correct paths, for me actually, Having just had a look at the link in the post above it looks like what Bob initially used but the Ubuntu forum post has a thriving discussion and when problems occur, like they did for me, the community finds a way to fix it. I am not sure how many people are going to help you with the link in the post above if you come across a problem. Yes this is a blatant pulg for BobSongs thread.

---

### Post by DestroyMicroshaft on 2008-01-07
Awesome, thanx everyone for helping, downloading the whole repo now, will report on results when done!  :)

---

