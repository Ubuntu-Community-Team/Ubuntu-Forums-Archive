---
title: "data dvd running in windows, but not in ubuntu"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by cyneuron on 2007-09-18
hello there

i got five dvd's from my friend containing few folders with movies in them. 

3 of them run fine in ubuntu, but 2 of them are not running in ubuntu. By running i mean ubuntu doesn't even mount the drive, as if there is no media in the drive.

 while running ok in windows xp. these dvd's have been burnt using Nero in windows xp.

dvd drive LED lits up when i insert the dvd, then it blinks up like normal, then for some time LED remains on, and then goes off, without opening up the window. 

i have tried to manually mount the drive from computer window, but it says there is no cd/dvd in drive.

same dvd's run ok in same drive on my windows xp partition.

how is this possible ? 

please someone tell any fixes because i am gonna remove windows xp from my computer in few days, so need to make sure same thing doesn't happen in future.

---

### Post by LaRoza on 2007-09-18
> **cyneuron said:**
> 
same dvd's run ok in same drive on my windows xp partition.

how is this possible ? 

please someone tell any fixes because i am gonna remove windows xp from my computer in few days, so need to make sure same thing doesn't happen in future.

They are probably burned in the weird Windows format, especially if your friend is using Vista, which hides the option to burn in the standard (Mastered) format.

---

### Post by cyneuron on 2007-09-18
thanks for reply, but they have been burnt in windows xp with nero, just after burning the 3 dvd's which are running fine.

---

### Post by LaRoza on 2007-09-18
> **cyneuron said:**
> thanks for reply, but they have been burnt in windows xp with nero, just after burning the 3 dvd's which are running fine.

If they work in Windows, but not Linux, it is a format issue. I am not familiar with Nero, but I have heard it does things differently from those who do use it.

---

### Post by cyneuron on 2007-09-18
> **LaRoza said:**
> If they work in Windows, but not Linux, it is a format issue. I am not familiar with Nero, but I have heard it does things differently from those who do use it.


thanks, but other three dvd's have also been written with nero only....do you mean some problem with the dvd themselves?

but physically dvd's are ok as they are running on windows ?

then this problem will make complete Ubuntu transition difficult, as this is a windows world still (though unfortunately !!!!).

anybody got any help...

---

### Post by LaRoza on 2007-09-18
I didn't burn the disks, nor do I use Nero, so I can't say for sure, but since you didn't burn them either, you have no way of knowing what happened.

My experience with burning is that if you use standard formats the disk can be read by any OS, regardless of where it was burned.

---

### Post by qamelian on 2007-09-18
> **LaRoza said:**
> I didn't burn the disks, nor do I use Nero, so I can't say for sure, but since you didn't burn them either, you have no way of knowing what happened.

My experience with burning is that if you use standard formats the disk can be read by any OS, regardless of where it was burned.

This isn't always the case. Nero does use ISO standard formats for burning CD/DVDs, but that doesn't seem to matter. I have several discs myself that will read fine on Windows, but not in Linux on the same PC. Two of the are straight ISO 9660 data CDs burned without eith Joliet or Rockridge extensions for long file name handling. They are 100% ISO standard.

---

### Post by cyneuron on 2007-09-18
> **qamelian said:**
> This isn't always the case. Nero does use ISO standard formats for burning CD/DVDs, but that doesn't seem to matter. I have several discs myself that will read fine on Windows, but not in Linux on the same PC. Two of the are straight ISO 9660 data CDs burned without eith Joliet or Rockridge extensions for long file name handling. They are 100% ISO standard.

this is what i had in my mind.. nero also uses standard formats........

did you find any solution to this problem.... or even before, did you get where does the problem lie.......?

this gotta be solved otherwise its difficult to be completely on Ubuntu as we still live in windows world unfortunately (and will keep getting such cd/dvds)......

---

### Post by stchman on 2007-09-18
> **cyneuron said:**
> hello there

i got five dvd's from my friend containing few folders with movies in them. 

3 of them run fine in ubuntu, but 2 of them are not running in ubuntu. By running i mean ubuntu doesn't even mount the drive, as if there is no media in the drive.

 while running ok in windows xp. these dvd's have been burnt using Nero in windows xp.

dvd drive LED lits up when i insert the dvd, then it blinks up like normal, then for some time LED remains on, and then goes off, without opening up the window. 

i have tried to manually mount the drive from computer window, but it says there is no cd/dvd in drive.

same dvd's run ok in same drive on my windows xp partition.

how is this possible ? 

please someone tell any fixes because i am gonna remove windows xp from my computer in few days, so need to make sure same thing doesn't happen in future.

I have had this problem before.  I went back to Windows and burned the data DVD using iso9660 format.

---

### Post by gary0 on 2007-09-18
> **LaRoza said:**
> They are probably burned in the weird Windows format, especially if your friend is using Vista, which hides the option to burn in the standard (Mastered) format.

Well bugger me! My mate did a copy of win server 2003 for me. He copied it in Vista, all appeared well until I got the discs home and they were blank. Vista's great innit?

Gary.

---

### Post by cyneuron on 2007-09-19
guys i think its an important issue to be looked upon....

some expert advice needed here.........


please........

---

### Post by geo909 on 2008-02-10
Hello everybody, sorry for bringing this back to life, but I had the *exactly *same issue (DVD burned in XP, plays fine in XP but not in Ubuntu) and I thought It wasn't needed to start a new thread since this one isn't closed.

 Is there a solution? 
Should we dual-boot forever in case such an issue arise?

If there's no solution, are there any development plans of adding supported formats in the future?

---

### Post by geo909 on 2008-02-10
By the way, some (hope useful) info.

Here's what I get when I throw the DVD in:

[CENTER][[IMG]http://www.imageshack.gr/files/wqwwcb8v4irjoy4yizou.png[/IMG]](http://www.imageshack.gr/view.php?file=wqwwcb8v4irjoy4yizou.png)[/CENTER]

---

### Post by cyneuron on 2008-02-11
this really bugs me....forcing me to keep dual booting with xp....

---

### Post by geo909 on 2008-02-11
> **cyneuron said:**
> this really bugs me....forcing me to keep dual booting with xp....

Yeah...
There should always be Windows around.
I'm not a "M$ SUX LINUX RULEZ" type of guy and I just want to do my work whatever OS is inside but dual-booting has several disadvantages (especially when it comes to reinstallation) and it's sad I have to keep it that way for "just in case" issues, like this...


 BTW have you tried installing XP in VirtualBox? They saw the DVD even if they run inside Ubuntu (disks don't have to be mounted in Ubuntu to be seen by VirtualBox).

 But this thread is not about alternative solutions, it's about something that looks like a bug(?)

 Could anyone say if we should submit that as a bug? Any info about that matter?

---

### Post by seshomaru samma on 2008-02-11
I had the exact same problem with a DVD that was burned on an XP box, not sure using which software.
Interestingly, I could read the DVD on XP through VMware. 
I copied the data with Xp and then dragged it into Ubuntu.
The DVD had one of those autostart.exe files that they sometimes have in windows, at the time I thought that was the reason ,  Ubuntu simply didn't mount it (but Vmware did...strange....)
I haved Damn Small Linux on another laptop and it couldnt read that DVD as well.

---

### Post by cyneuron on 2008-02-12
launchpad has this bug reported, rather two duplicates are there.

there is some confusion over the bugs, one say that this problem patch has been released.

---

### Post by geo909 on 2008-02-14
Thanks for the info!

Could you please give a link?
I'm not so familiar with bug-reporting and stuff...

---

### Post by cyneuron on 2008-02-15
please go to launchpad.ubuntu.com and search for the related bug.

and don't forget to confirm there that the bug is not solved

---

