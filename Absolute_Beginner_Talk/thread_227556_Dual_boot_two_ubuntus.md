---
title: "Dual boot two ubuntus?"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2006-08-01
I want to let my kids play on a computer during the day and work on it at night trying different things. Tonight I gave everyone their own usernames and passwords but I also want to do other things also. I was wandering if I could dual boot ubuntu so I would be able to not mess up what I do for them. Or is there a better way to do this?
I have searched "dual boot" and only come up with ubuntu and windows.


Thanks
Teddy

---

### Post by GStubbs43 on 2006-08-01
I've never done this, but I don't see why you couldn't... just make a new partition with another ubuntu isntall. I'm not sure if you need another swap partition. Get another opiniont on this though because I'm not 100% sure. :-\" :roll: 

> **Teddy_P said:**
> I want to let my kids play on a computer during the day and work on it at night trying different things. Tonight I gave everyone their own usernames and passwords but I also want to do other things also. I was wandering if I could dual boot ubuntu so I would be able to not mess up what I do for them. Or is there a better way to do this?
I have searched "dual boot" and only come up with ubuntu and windows.


Thanks
Teddy

---

### Post by professor_chaos on 2006-08-01
If they dont have an administrative account there is not much they can mess with, unless you allow them to. Set there accounts up and limit the privilages they have during the user setup. Also, you can change permissions and such even in their directories to keep things unmodified.

However to answer your question, yes, setting up a dual boot linux box is possible and easy. Run the installer twice, and choose a different partition on the second install. However, for your reasons, I would probably just administer their accounts.

---

### Post by professor_chaos on 2006-08-01
No second swap partition is needed, you can reuse the same swap.

---

### Post by Teddy_P on 2006-08-01
I am not worried about them messing me up I am worried about messing them up.lol:D 

thank you for the replies
Teddy

---

### Post by professor_chaos on 2006-08-01
If you don't mind me asking, what is it they would mess up for themselves?

---

### Post by Teddy_P on 2006-08-01
Well the oldest is only 5 and they go on different web sites and I have every thing working so they can do this. They don't do anything other then fire fox and games that are in the games menu. In the evening I read on line and want to try different things with the system and I am scared that I might mess up some of the settings. I am new to linux or anything other then windows and I want to try out different things I figured if I could have two ubunuts then I could try ubuntu / edubuntu next.

---

### Post by bobpur on 2006-08-01
I have Ubuntu Dapper and Kubuntu Dapper installed in a six year old Compaq. It works great.I don't use it for anything but learning the OS and surfing. Oh yeah, e-mail too.
In mine each OS is on a different Hard drive.
5WV252 Compaq Presario (much modified) with two 60 gb harddrives, 448 mbs RAM, PNY Verto video card, Soundblaster 5.1 X-Gamer sound card and 1 ghz AMD Duron CPU.

---

### Post by cstudent on 2006-08-02
I have a computer with two drives setup dual boot with Ubuntu installed on both drives. I use one drive for developing and the other drive for testing.

---

### Post by VirtuAlex on 2006-08-02
> **bobpur said:**
> 5WV252 Compaq Presario (much modified) with two 60 gb harddrives, 448 mbs RAM, PNY Verto video card, Soundblaster 5.1 X-Gamer sound card and 1 ghz AMD Duron CPU.
And you still call it Compaq? What is left - case and mother board? Or you just forgot to mention them in the list of your modifications ;)

---

### Post by Teddy_P on 2006-08-02
I have some other hard drives around but the one thats in there is plenty big enough do I need to use two?


Teddy

---

### Post by Teddy_P on 2006-08-02
Also I don't do anything productive on the computers just like playing with them and maybe if I learn some when the kids get older I am sure they will catch up and pass me but if I start now I will have a 5 or so year start. So I am just tring different things to see how they work.


Teddy

---

### Post by VirtuAlex on 2006-08-02
> **Teddy_P said:**
> I have some other hard drives around but the one thats in there is plenty big enough do I need to use two?

You do not have to. One separate partition is enough. You can even share your /home if it is on separate partition (which is not default case though) and defenitely you can share swap.

---

### Post by Teddy_P on 2006-08-03
I tried this last night:
I installed ubuntu again and let the partition tool do it. It looked like half for each so I clicked forward. At the end I took the CD out and pressed enter nothing happened. So I forced a quit and restarted and now I get Grub error 18. So I figure I would give the kids something to play with today I was going to try it again and erase entire drive and install. Well I did that and after taking out the CD it shuts down and tries to restart and then Grub error 18.
Did I mess their computer up?



Teddy

---

### Post by VirtuAlex on 2006-08-03
Try to search forum for "grub error 18." It seems to be not so uncommon issue. Maybe that one [http://www.ubuntuforums.org/showthread.php?t=43061]("http://www.ubuntuforums.org/showthread.php?t=43061") would work for you?

---

### Post by Teddy_P on 2006-08-05
Well I give up...
I have tried every thing that I can find on the fourms. I am still getting error 18. With this old computer I think the solition that worked the best is when some how the partioner gave some space to boot. Any way now nothing seems to work and I want to just wipe every thing out and read more on Grub and partitioning before I try it again.
Is there a way to erase everything and start over? I can run the live CD but when I try to install anything it lockes up at different points.


Thanks
Teddy

---

### Post by VirtuAlex on 2006-08-05
Install from an alternate CD, it is more stable

---

### Post by Teddy_P on 2006-08-05
I put Edubuntu Breezy on and it worked like a champ.

I will do some more reserch before I do anything else.

My first search is going to be "alternate CD" I didn't know there were any others then the one I was using.


Thank you for your help
Teddy

---

### Post by reacocard on 2006-08-05
the alternate cds are on the same dowload page as the regular ones. just scroll down a bit.

---

### Post by cjm5229 on 2006-08-05
When you Install it, use the manual partitioner, first delete the partitions you have. then create two partitions of about 8GBs each, These will become the Root Partitions for each  Ubuntu. Then  what is left you can use as  "Home" Leave enough to create a "Swap" Partition. With the Alternate cd mount one of the 8GB part. as root. then mount the Biggest one as home then mount the swap Partition.  Let the other  8GB Part. mount in media. Then Install. Then do the same things with the other 8GB part. Mount as root,big part. as home, and swap as swap. Install You will have 2 Ubuntus that share the same home. I do that for testing Edgy, so that if it gets competely messed up I still have my main OS to use. Also by having a seperate "Home" part. you can reinstall Ubuntu without losing anything. You just have to reinstall your apps which doesn't take long. 
Good Luck.:)

---

### Post by Teddy_P on 2006-08-05
> **reacocard said:**
> the alternate cds are on the same dowload page as the regular ones. just scroll down a bit.

Do you have a link because I don't understand.


Teddy

---

### Post by Teddy_P on 2006-08-05
Do you mean Ubuntu derivatives?
If so this is fine with me which one would you suggest?


Teddy

---

### Post by reacocard on 2006-08-05
get cd isos here: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
choose a mirror and then scroll down to the section for the alternate cd. download it (~650MB), burn it to a blank cd and then use it to install.

---

### Post by Teddy_P on 2006-08-05
OOOO I SEE..  Thank you. I did not know I had to click on a mirror. I will try this tonight.

Thank you
Teddy

---

### Post by shanepardue on 2006-08-05
i have an ubuntu partition already running smoothly with everything configured the way i want it..i don't want to delete that partition...

when i manually edit the partitions, how do i make the new partition ready for another ubuntu installation for edgy testing without messing up the other partitions? do i mount it something other than just "/"? or am i to have two partitions mounted on "/"?

thanks

---

### Post by reacocard on 2006-08-05
>  i have an ubuntu partition already running smoothly with everything configured the way i want it..i don't want to delete that partition...

when i manually edit the partitions, how do i make the new partition ready for another ubuntu installation for edgy testing without messing up the other partitions? do i mount it something other than just "/"? or am i to have two partitions mounted on "/"?
just create a new partition and tell the installer that that is root instead of your current root.

---

