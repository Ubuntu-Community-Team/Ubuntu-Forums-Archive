---
title: "Vista ate my ubuntu"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Rollotamasi on 2007-02-18
I recently installed vista and all of a sudden my grub loader was gone.  Someone directed mt to a walk through here [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I used the Super Grub disk method.  Well, My grub loader is back and I can load windows however I get a "Error 17, Cant boot from this partition" When I try to load Ubuntu.  Any advice?

Thanks

---

### Post by kamaboko on 2007-02-18
I'm pretty green here, but my understanding is that Ubuntu should be loaded after MS OS's.  It sounds like you loaded Vista after Ubuntu.  Is that the case?  From what I know that will kill your Ubuntu install.

K

---

### Post by Rollotamasi on 2007-02-18
> **kamaboko said:**
> I'm pretty green here, but my understanding is that Ubuntu should be loaded after MS OS's.  It sounds like you loaded Vista after Ubuntu.  Is that the case?  From what I know that will kill your Ubuntu install.

K

I was under the impression that it just kills the GRUB loader on the MBR, not the entire install.

---

### Post by bulldog on 2007-02-18
> **Rollotamasi said:**
> I was under the impression that it just kills the GRUB loader on the MBR, not the entire install.

You're right **if you did not format or changed your disk space,specially the space were ubuntu is installed to** with installing Vista.
If you didn't do so,you'll have to take a look at your menu.lst and see if grub is pointing to the right partition to boot ubuntu.

---

### Post by bodhi.zazen on 2007-02-18
> **Rollotamasi said:**
> I was under the impression that it just kills the GRUB loader on the MBR, not the entire install.

That is correct. It looks as if grub needs to be configured ...

You can take a look at supergrub : [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Or post the output of :

```
sudo fdisk -l
```

and /boot/grub/mneu.lst

---

### Post by Rollotamasi on 2007-02-18
> **bulldog said:**
> You're right **if you did not format or changed your disk space,specially the space were ubuntu is installed to** with installing Vista.
If you didn't do so,you'll have to take a look at your menu.lst and see if grub is pointing to the right partition to boot ubuntu.


Well, I changed the disk but I didn't do it during the Vista install.  I did it with GP parted before I installed Vista. I made a new partition (From my old XP partition) for Vista. However after I changed the partition with GP Parted But before I installed Vista (When the grub loader was still working) I  checked to make sure that I could still boot into Ubuntu and I could.  

How do you look at the menu.lst file?


Thanks for the help!

---

### Post by Maestro23 on 2007-02-18
> **Rollotamasi said:**
> Well, I changed the disk but I didn't do it during the Vista install.  I did it with GP parted before I installed Vista. I made a new partition (From my old XP partition) for Vista. However after I changed the partition with GP Parted But before I installed Vista (When the grub loader was still working) I  checked to make sure that I could still boot into Ubuntu and I could.  

How do you look at the menu.lst file?


Thanks for the help!

cat /boot/grub/menu.lst (lower case L).

Copy and past the output here for use to look at.

---

### Post by bulldog on 2007-02-18
You can't boot ubuntu,so use the live cd.
Now I think about it,it can be much easier to reinstall GRUB with the live cd.
Try this,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by Rollotamasi on 2007-02-18
> **bulldog said:**
> You can't boot ubuntu,so use the live cd.
Now I think about it,it can be much easier to reinstall GRUB with the live cd.
Try this,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

I followed those instructions but I still get a error 17 "Cant boot to that partition"

---

### Post by xpod on 2007-02-18
> Vista ate my ubuntu

I`m not  suprised......it`s a hungry bugger eh:)

---

### Post by bulldog on 2007-02-18
Did you put the answer you get with the find command in the next command?
Replacing the question marks,or did you get any error in one of these commands,and if so,what where the errors?

If there wheren't any errors and you did replace the question marks with the answer you've got with the find command,I don't understand why it won't boot.

EDIT,
Hehehehe,LOL,I was thinking were is xpod when you need him.
Hi xpod,all well with the bunch?

---

### Post by Rollotamasi on 2007-02-18
> **bulldog said:**
> Did you put the answer you get with the find command in the next command?
Replacing the question marks,or did you get any error in one of these commands,and if so,what where the errors?

If there wheren't any errors and you did replace the question marks with the answer you've got with the find command,I don't understand why it won't boot.

EDIT,
Hehehehe,LOL,I was thinking were is xpod when you need him.
Hi xpod,all well with the bunch?

Followed the directions to a T and got no errors.  The grub loader shows up and I can select ubuntu I keep keep getting that blasted Error 17: Can not mount selected partition. :(

---

### Post by xpod on 2007-02-18
> Hehehehe,LOL,I was thinking were is xpod when you need him.
Hi xpod,all well with the bunch?

Hi yerself m8.
Was just wondering about you ourselves the other day.Me and master bondi there(with dogo :)) hadn`t seen you for a while and thought mabey you`d installed Vista and found some other haunt to hang out:) ......or hang out to haunt:wink: 

Young un`s are all fine thanks mate although my lads 14 next week so some are not so young anymore...Dont time fly when your enjoying yourself eh ..damn Ubuntu

---

### Post by bulldog on 2007-02-18
> **xpod said:**
> Hi yerself m8.
Was just wondering about you ourselves the other day.Me and master bondi there(with dogo :)) hadn`t seen you for a while and thought mabey you`d installed Vista and found some other haunt to hang out:) ......or hang out to haunt:wink: 

Young un`s are all fine thanks mate although my lads 14 next week so some are not so young anymore...Dont time fly when your enjoying yourself eh ..damn Ubuntu

I'm a little busy lately with work and all that stuff,so I'll be a little less on the forums.
Don't worry about Vista,I won't install it again!
But you have learned it by now,so you can answer the questions when I'm not around.:) 

@TS,
I can't think of anything else what can be wrong,you can take a look at your fstab to see if the right partition to boot from is listed there as well.

---

### Post by kvorion on 2007-02-18
Even I have had problems restoring my grub after a failed windows xp install on my hard disk. The grub installation used to happen properly, but still, when I start my machine, I would get an error saying it cannot boot. Then I had to do a phony ubuntu installation on a free partition of my hard disk and it somehow installed grub back on.

What are the chances that you install grub on your MBR and it still doesnt show up?

---

### Post by macogw on 2007-02-18
When Vista ate my Ubuntu back in October, I booted the live cd and ran fsck on the partition where Ubuntu was.  Vista had rearranged some blocks and I had to hold down enter to make it say "yes" about a 1000 times as it fixed all the memory addresses.

---

### Post by Rollotamasi on 2007-02-18
> **macogw said:**
> When Vista ate my Ubuntu back in October, I booted the live cd and ran fsck on the partition where Ubuntu was.  Vista had rearranged some blocks and I had to hold down enter to make it say "yes" about a 1000 times as it fixed all the memory addresses.

I'm sorry, I'm a pretty serious Ubuntu newbie.  How do you run fsck on the partition?

Thanks

---

