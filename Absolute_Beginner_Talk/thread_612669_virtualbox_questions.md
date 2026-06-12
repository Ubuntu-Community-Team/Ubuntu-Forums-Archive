---
title: "virtualbox questions"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by natehatewindows on 2007-11-14
I am thinking about doing the whole virtual box thing so i can get rid of my vista partition. The only major question that i have is about my vista install cd. The only cd i have with vista on it is the 2 disks that came with my computer (Toshiba recovery disks). is there anyway i can use these disks to install vista onto ubuntu with virtual box?

thanks :)

---

### Post by bulldog on 2007-11-14
Don't think you can,but maybe you can download a copy?
You have your license and a key,so it would be legal,I suppose.

Or ask the vendor of your machine a copy,but I doubt if he will respond to that.

The reason I doubt it will work,is that the recovery cd will restore your Vista  and hdd to their default settings,don't think you can do that in VirtualBox.

---

### Post by de_valentin on 2007-11-14
Indeed you will need a full Vista **** version. It is as if you would make an install on a blank disk and that's not what the cd's are for. Ans to make it even worse in the EULA it probably doesn't even allow you to make a clean install, because if you wanted to do that you would need to buy a  full version. But that's exactly what m$ is all about, helping you wherever they can.

I guess in the end it will be more of a moral question whether you will download a full version and use your 'wrong' license or not.

---

### Post by natehatewindows on 2007-11-14
so you think it would work to download a version and use my key? god im glad im getting away from MS.....im actually starting to wonder if i even need windows at all.....i NEVER use it......hmmmmm???  It would be i guess nice to have in those "just in case" but really i guess it might be a waste of disk space (like windows usually is 99% of the time ;)

---

### Post by bulldog on 2007-11-14
> **natehatewindows said:**
> so you think it would work to download a version and use my key? god im glad im getting away from MS.....im actually starting to wonder if i even need windows at all.....i NEVER use it......hmmmmm???  It would be i guess nice to have in those "just in case" but really i guess it might be a waste of disk space (like windows usually is 99% of the time ;)

You can install two different linux distro's,so you have always a working OS.
Installing in a vitualbox is useless,if your ubuntu has crashed btw,you can't run Vista either in such a case.
A second partition with linux,using the same /home and swap is much more usefull I guess.

---

### Post by de_valentin on 2007-11-14
> **natehatewindows said:**
> so you think it would work to download a version and use my key? 

Yeah I think it would work if not 100% legal and if it doesn't I have noticed that a lot of the downloadable versions of windows have their own keys[-( with them

---

### Post by Harpoon on 2007-11-14
A cuation is in order regarding bulldog's suggestion.  If you make two installs of linux, you **can** have them share the same home partition, but be sure you use two different usernames.  Otherwise you have the chance of one install overwriting the settings of the other, and perhaps leading you into a unrecoverable situation.

---

### Post by Harpoon on 2007-11-14
On another front, if you are going to consider using an alternate to your vista recovery cds, then you might want to consider installing a lighter weight version like xp or even win2k.  This is especially attractive if you don't really expect to connect the the net with the win install - - so no need to worry about security or contact MS for those rarely isued securty patches.

---

### Post by de_valentin on 2007-11-14
Yes I fully agree on that one, the lighter the virtual windows is to run the more is left to the application you actually want to run.

---

### Post by natehatewindows on 2007-11-14
i see where this is going now,,,,,yes i agree that vista is to heavy for this. the only problem is that i dont have xp and i only have dialup (so i cant download it) here (im living in ukraine and cant get dsl or anything where i live. I think what i wil do is wipe windows and maybe install mandriva and dual boot with ubuntu. I wish i have a separate /home but i dont....is there any way i can make it without doing a fresh install in gusty? I dont want to go through all the crap with getting my modem to work and stuff again, im going to start a new thread about how to wipe windows...im not sure how to do that and keep ubuntu.

---

### Post by de_valentin on 2007-11-14
By wiping windows you will have a lot of free space maybe you can probably create a /home 

[http://ubuntuforums.org/showthread.php?t=611450&highlight=separate+%2Fhome](http://ubuntuforums.org/showthread.php?t=611450&highlight=separate+%2Fhome)

on another pc I have a link to an howto create separate /home if there is no answer before i get to it i will post it

---

### Post by bulldog on 2007-11-14
Here you can find the solution to move your /home to another partition.

[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)

---

### Post by Duck2006 on 2007-11-14
Yes it can be done, You will have to shirnk your vista partition from with in vista. Then use the rest of the free space for your linux install. Then install virtualBox, when it comes to where you want your virtual partition point it to your vista installation. I have never done this but i have heard of it been done.

---

### Post by de_valentin on 2007-11-15
Seems like you have all the info you need, let me know if it worked.

good luck

---

### Post by natehatewindows on 2007-11-15
when  do this will it change and of the sda1, 2 ,3 numbers? if so what file(s) do i have to change?

---

### Post by natehatewindows on 2007-11-15
also how wil i shrink the 22 gig partition i have now so my root is only 8 gigs? im getting confused i guess
sorry an thanks

---

### Post by CatKiller on 2007-11-15
Actually, the Windows Vista EULA prohibits you from running Vista in a virtual machine. So you can't do what you want and still remain within the agreement.

Whether the Windows Vista EULA is a legal contract probably varies by country, and it is unlikely that you'll be able to find out whether it was legal or not without Microsoft suing you, and you winning.

---

### Post by natehatewindows on 2007-11-15
ok i just made my separate /home with the link above but i did the partitioning a bit different, just deleted windows with gparted in ubuntu, made the /home partiton and then booted from the live cd and did all the code stuff with the phscocats link. but when i booted back into unbuntu all my settings were different..should this happen? i am having to redo all my program settings..is this normal? its ok if it is but i just want to make sure it worked right.

---

### Post by Newbie1978 on 2007-11-15
> **natehatewindows said:**
> I am thinking about doing the whole virtual box thing so i can get rid of my vista partition. The only major question that i have is about my vista install cd. The only cd i have with vista on it is the 2 disks that came with my computer (Toshiba recovery disks). is there anyway i can use these disks to install vista onto ubuntu with virtual box?

thanks :)
I think you can install it from your repository disc, but since those disc have all the drivers and configuration of your machine it actually work better than a regular vista dvd, the problem will be that you will consume more HD space and over all resources running Vista instead of using this resources running programs and aplications on vista, (since I never done it I have no way to be sure this is just an opinion)

---

