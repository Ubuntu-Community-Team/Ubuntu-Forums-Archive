---
title: "Reinstall - Ubuntu6.10"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by justoneman on 2007-04-09
I can't figure out how to do a clean reinstall from my install disk - i.e. install 6.10 over 6.10 as I want to 'start again' without the changes that I've made while playing around with my 'first Linux'.

I don't mind if everything I have saved goes with the new install - want to start again fresh.

Dan

---

### Post by aktiwers on 2007-04-09
Most of the stuff you have done should be in your Home Folder.
If you back up your home folder, must settings should be saved. 

Though I did this onces, and it didnt work out perfect. Maybe you also need to backup /ect
but I dont know. Hopefully others can answer that.

Also, if I was going to do a reinstall, I would go for Feisty. Its only 9 days to the release, and it really looks completely awesome!

Good Luck!

---

### Post by tgm4883 on 2007-04-09
When you boot, does it give you the cd boot options?

---

### Post by justoneman on 2007-04-09
> **tgm4883 said:**
> When you boot, does it give you the cd boot options?

Thanks tgm.  Yes, and it does reinstall but it keeps all of the settings (like wireless, and files etc.). I want a 'brand new' install with none of the stuff I've fiddled with saved.

Dan

---

### Post by aktiwers on 2007-04-09
> **justoneman said:**
> Thanks tgm.  Yes, and it does reinstall but it keeps all of the settings (like wireless, and files etc.). I want a 'brand new' install with none of the stuff I've fiddled with saved.

Dan

Sorry then I misunderstood you.
Then while installing, when you get to the partitioning  you should pick "manually partitioning".

Then Delete your current Ubuntu Partition.

Create a swap drive on 1gb (what I normally do, could be more or less depending on how much space you have. But 1 gb is good)

Then create a / partition for your system. I usually use ext3 filesystem and about 25gb.
Again you can make this a lot smaller if you want to create a separate /home partition or want to use less space, though I wouldnt use less than 8-10gb. 

then you just follow the rest of the installation.


If this seams too hard, you can also use gparted on the live CD. 
Then format your Ubuntu drive, and after that do a normal install.

---

### Post by tgm4883 on 2007-04-09
> **justoneman said:**
> Thanks tgm.  Yes, and it does reinstall but it keeps all of the settings (like wireless, and files etc.). I want a 'brand new' install with none of the stuff I've fiddled with saved.

Dan

hmm, when you boot the live cd, go into system > administration > gparted.  delete all the partitions and write that to disk.

Then when installing, make sure it formats the partitions is makes

---

### Post by justoneman on 2007-04-09
Thanks to all - greatly appreciated. I understand now, at least I think I do!

Dan

PS  Do I need to 'end' this thread now that I have the info I requested?

---

