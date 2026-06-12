---
title: "Need Help Shrinking Partition"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by agaetis on 2008-01-30
I'm using [this](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) guide to dual boot using Ubuntu.  When I first tried shrinking ( C: ) it said there was a certain amount of space available to be freed up, I don't remember the exact number but I think it was around 50GB.  I hit shrink and my cursor changed to the "busy" cursor and stayed like that for a couple minutes.  Nothing was happening, no progress bar, no unallocated space was showing up etc. so I exited out of disk management.  I restarted my computer and tried it again, but now it says there's no space available for shrinking.  

Here's some screenshots so you can get a better idea of what's going on:

[http://img82.imageshack.us/img82/4365/partition1ge0.jpg](http://img82.imageshack.us/img82/4365/partition1ge0.jpg)

[http://img82.imageshack.us/img82/5811/partition2cb8.jpg](http://img82.imageshack.us/img82/5811/partition2cb8.jpg)

Also, I'm not good with computers at all, so I might not understand all the computer jargon.  Thanks for any help.

---

### Post by seventhc on 2008-01-30
Hi, I think first you should defrag the partition you want to shrink, Then I would use the live cd to do the shrinking for you.
Boot into the ubuntu cd then go to Applications>accessories>terminal
and type this in
```

sudo gparted
```
you will see your ntfs partitions, and you will be able to shrink it from there.
there is a button that says "Shrink" so once you have it open it is fairly intuitive and easy to understand. :)

---

### Post by agaetis on 2008-01-30
Will that allow me to dual boot and will it keep all the files I currently have on my computer?  Sorry if this all sounds stupid, I'm just completely new to this and I don't want to ruin my laptop.  Thanks again.

---

### Post by oedha on 2008-01-30
maybe....maybe you have shrink it....
you can also check by using gparted
or just run the ubuntu live cd.......do like sventhc said
or i usually click install then stop at step 4 of 7 ( partition step )
see what happen with your disk partition there......

every linux allow you to dual boot......maximum quad boot on a machine

~E~

---

### Post by seventhc on 2008-01-30
> **agaetis said:**
> Will that allow me to dual boot and will it keep all the files I currently have on my computer?  Sorry if this all sounds stupid, I'm just completely new to this and I don't want to ruin my laptop.  Thanks again.
If you shrink the partition leaving space for ubuntu, then you can dual boot.
a few things first. after you 'shrink the partition' then "create" a partition for ubuntu to use, no need to format it..Ubuntu will do this for you during the install.
**Important: When you install ubuntu, read the screens. **:) there will be a screen with a slider bar, this is the screen you need to not just click next. You have to choose "_Use largest continuous free space_" Then it will install on the empty partition and when you reboot you will have ubuntu and xp. :)
If you don't choose this and just click next you will lose windows. :(
The install goes quickly and after that choice is made you can walk away and let it do it's thing.
As a precaution I would still back up any important files just to be safe.
If you don't understand or need it explained more clearly let me, I'm happy to help. :)

---

### Post by agaetis on 2008-01-30
Let me see if I've got it right:

-Defrag the C: drive
-Shrink the C: drive
-Install Ubuntu and choose largest continuous free space

If that's right, I have an issue with the shrinking part.  I've tried to shrink it, and at first I thought something went wront since I didn't see any unallocated space, just blue ([http://img82.imageshack.us/img82/4365/partition1ge0.jpg](http://img82.imageshack.us/img82/4365/partition1ge0.jpg)).  But when I look at my C: drive in My Computer it shows only 74GB total when it sed to be in the 90s. ([http://img145.imageshack.us/img145/4229/partition3oi9.jpg](http://img145.imageshack.us/img145/4229/partition3oi9.jpg))  Does this mean that when I tried shrinking it for the first time it worked and I now have 20 gigs or so of continuois free space?

---

### Post by seventhc on 2008-01-30
> 
If that's right, I have an issue with the shrinking part.  I've tried to shrink itThats why I say to do it from the live cd using gparted. If you have free space then gparted can shrink it for you.
other than that, everything else you said is correct.
I have never shrunk a partition with xp so I'm not sure how reliable it is, I have had success using gparted. There is still a small chance for something to go wrong though as with any major system change. ( thats why I say back everything up) But I am confident you should have no problem. :)
now heres the list again :D
1: defrag windows
2: boot to ubuntu live cd
3: open terminal type in sudo gparted
4: shrink partition <click apply>
5: create partition on the free space, don't format it <click apply>
6: install ubuntu choosing option 'largest continuous free space'
7: enjoy your dual boot computer :)
wow, I made it look like to many steps. :D

---

### Post by agaetis on 2008-01-31
Alright, is there any way to "un-shrink" my harddrive so I have to 99GB or so back instead of the 76 I currently have?  It seems to have disappeared and I have no idea how to find it.

---

### Post by seventhc on 2008-01-31
In the screenshot it shows as 99.74GB, if it is different now, you should also be able to do that with gparted. It can resize.
I see you have a recovery partition, do you also have a windows xp cd? Just in case or can you make a copy with that partition?
Thats how my sony was, it came with vista, had a seperate partition..I made the DVD's then got rid of vista and that partition.(purposely)

---

### Post by agaetis on 2008-01-31
In [this](http://img145.imageshack.us/img145/4229/partition3oi9.jpg) screenshot it used to show 99 something gigs instead of 76.  When I shrunk it I think it did so by 23 gigs, which makes me think I have 23 gigs of unallocated space that I don't know how to access.  I think I have a Vista CD somewhere, but as long as I choose the most continuous free space option I should be pretty safe, right?

---

### Post by b0b138 on 2008-01-31
nm, i cant add

---

### Post by seventhc on 2008-01-31
Yes you should be safe,  I just mention those things b/c nothing is 100% full proof. there's always at least a 1 % chance margin for error. 
I think gparted will find your lost space too.
The things I mention with the backups are just precautions to be taken. But I wouldn't worry to much. :)

---

### Post by seventhc on 2008-01-31
> **b0b138 said:**
> NO You have no unallocated free space. Your C: partition is a total of 99gigs, 76.7g used 22.4g free.

Gparted has NOT repartitioned anything.
there is another 20 gigs or so that isn't showing in windows, and he's going to resize windows

---

### Post by b0b138 on 2008-01-31
yeah... i a mo' ron

i am curious about that 2gig partition though?

---

### Post by agaetis on 2008-01-31
Alright, I think I almost have it.  I'm running in the Live CD now but I'm not seeing a shrink option for the drive.  Here's some screens:

[http://img238.imageshack.us/img238/7532/gparted1sp8.png](http://img238.imageshack.us/img238/7532/gparted1sp8.png)
[http://img149.imageshack.us/img149/4719/gparted2pw4.png](http://img149.imageshack.us/img149/4719/gparted2pw4.png)

Would the resize/move be the thing I'm looking for?  And if so what values do I put in for free space preceding and free space following.  Thanks.

---

### Post by seventhc on 2008-01-31
sorry I was sleeping :D
you click the resize/move
Now you see that yellow portion....thats where your windows and other data are.
Instead of entering values I would suggest using the mouse. place your cursor on or near those arrows and drag.
you will do it from the right side and drag it to the left, don't drag it into the yellow. nothing will happen until you click apply, so if you did go over the yellow just move it back out. Now once you have it set, you click apply. when it finishes the process you will have a blank area, highlight it, click 'new'
apply, then you can close it and install.

---

### Post by dstew on 2008-01-31
> Alright, is there any way to "un-shrink" my harddrive so I have to 99GB or so back instead of the 76 I currently have?Your problem might stem from the original attempt to shrink the partition using the Vista disk management tool. I don't know about Vista, but in gparted it can take a long time to shrink a partition. I have had to wait for an hour before, on a slower computer. Is it possible that you might have damaged the partition table by aborting the original resize attempt? If so, you might first attempt disk repair on that partition. Maybe that is why the partitioner shows 99, but the disk window shows 76.

Also, I think it is risky to shrink a Vista partition using gparted, although some people have done it successfully.

---

### Post by agaetis on 2008-01-31
> **dstew said:**
> Also, I think it is risky to shrink a Vista partition using gparted, although some people have done it successfully.

What is the problem people get when shrinking a Vista partition?  I did it yesterday and everything seemed to go fine but I haven't been off the Ubuntu live disc since that.

I think this should be my last install related question, it's just that I want to be sure before I install it.  When I choose [use the largest free space](http://img222.imageshack.us/img222/9966/install2tm1.png) I get [this](http://img222.imageshack.us/img222/9175/install3tf0.png) screen as the last step.  I wasn't sure what all the SCSI stuff was and whether or not it was going to erase all my information.  When I tried choosing manual I chose the free space I got yesterday using gparted but got [this](http://img218.imageshack.us/img218/7977/install1qp0.png) screen.

EDIT:  I forgot to ask how I would go around backing up files that would allow me to re-install Vista if anything should happen.  I don't really care about losing all my pictures and documents, but I'd like to be able to re-install Vista if anything should happen.

---

### Post by seventhc on 2008-01-31
I won't address the manual install since you'll be doing the guided free space. The screenshots you show are normal, it is only showing you what it's about to do. It looks fine to me, but wait for a second opinion here if you are nervous.
That screen is not an error or anything, it is a perfectly normal screen that everyone else gets. it shows your partitions as #6 and #7 so I would think your windows partition is not getting touched. It is before those, but again wait for a second opinion. :)
If you really want to make certain open gparted and post a screenshot of that so everything shows.
or open a terminal and paste the output of this:
```
sudo fdisk -l
```If that command doesnt show your windows, then do the screenshot with gparted.

[COLOR=Red]**Edit:: **[/COLOR]I just looked at your 3rd screenshot, I am not sure on that one. I think wait until someone else sees that first. I don't remember what screens show up during a manual, so I can't verify what is normal situation there. Did you do as posted above by dstew? check your disk first.

---

### Post by seventhc on 2008-01-31
I can't remember how I made my back ups of vista, maybe look in control panel and look around, or tools or saomething, there should be a link for it. You paid for it so if they didn't give you the disks then there should be a way of making them. You can always call the manufacturer of the comp. I made mine the first day I got the comp then reinstalled vista to verify they worked, then removed vista and replaced it with vista. If you can't lose vista, and you don't have the vista cd you really should not make any system changes. As I stated earlier there is always a chance (no matter how small) that something could go wrong. make sure you have your vista disks before installing ubuntu. Thats my opinion.

---

### Post by agaetis on 2008-01-31
sudo fdisk -l:

[http://img231.imageshack.us/img231/1301/disk1kj3.png](http://img231.imageshack.us/img231/1301/disk1kj3.png)


gparted:

[http://img231.imageshack.us/img231/8962/disk2kw8.png](http://img231.imageshack.us/img231/8962/disk2kw8.png)

---

### Post by seventhc on 2008-01-31
Whats the fat 16 for???
I assume you are installing on the 16 gig partition, I would highlight that and click 'New" "Apply" no need to format it just create it.
did you read previous post?

---

### Post by agaetis on 2008-01-31
I'm not sure what the fat16 is for, the only one I messed around with was the 16GB unallocated parition.  I'll try to find my backup disk before installing it, hopefully it won't be too long because even the live version is very nice.

---

### Post by seventhc on 2008-01-31
I think you'll love it. I don't even like getting behind any windows machines anymore...I get depressed :(

---

