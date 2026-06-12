---
title: "Uninstalling Ubuntu?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by deaddylan123 on 2006-03-19
How do I go about deleting Ubuntu Linux? I want to be able to just use Windows   Xp again. I can't boot windows...it just sits on a black screen with some text and does nothing. Please help me, I dont want to have to do a whole system recovery, etc... 

Thanks,
     Jeffrey

---

### Post by el3ktro on 2006-03-19
There's nothing to "uninstall". Well about your Windows problem, I don't know, perhaps you can put in your Windows CD and start this Windows setup repair thingy, so that it writes back the Windows boot manager. What error message do you get? "Some text" doesn' tell us much :-(

Tom

---

### Post by hobbit1983 on 2006-03-19
Hi deaddylan123,

Sorry to hear that you feel you have to back to windows.  Is there any problems you are having with ubuntu that perhapes we can fix for you.

If however you are convinced that you must go back to windows here's what to do.  Insert your windows install media and enter the "recovery mode" from there you can use the fixmbr command to change your PC to boot into windows automatically (assuming you had linux and windows duel booting)

Once you are in windows you can then use the disk management tools (or a partition manager) to reclaim the space ubuntu used.

But if there were any issues stopping you from using ubuntu let us know - perhapes there is an easy answer

---

### Post by deaddylan123 on 2006-03-19
The text sais this:
> Booting 'Microsoft Windows XP Home Edition'
root (hd0,0)
  Filesytem type unknown, partion type 0x7
savedefault
makeactive
chainloader +1

And if I do but the cd in andboot windows off of that, would I be able to delete the part of my harddrive that Ubuntu is partioning?

Thanks

---

### Post by hobbit1983 on 2006-03-19
put in the windows disk and boot from it.  This will give you the option to enter "rescue mode" from there you will be able to issue the fixmbr command - this will remove grub (the linux bootloader) from your hardrive. This means that next time you reboot windows will boot by defualt.  Once you have windows back you can use a partitioning tool to reformt the linux partion and then increase the size of your windows partition as required.  

But why not stay here - the party has only begun, why do you feel the need to move from ubuntu

---

### Post by el3ktro on 2006-03-19
OMG i've read over my post again, uh I hope my first sentence didn't sound rude to you in any way. I've just posted this from work and was in a hurry. With "there's nothing to uninstall" I meant that you can't, well "uninstall" Linux by putting the install CD in and press an uninstall button, as others have posted already you just have to re-format the partition that Ubuntu is on to make it usable in Windows again, or you can use a partitioning tool to make your exisiting Windows partition bigger, using the space that is now occupied by Ubuntu.

But besides that, I'm also interested in what kind of problems you had with Ubuntu - perhaps it's a problem that is not as hard to solve as you may think, and we can help you. If you just didn't like Ubuntu, then well thats your decision then :-?

---

### Post by incubus on 2006-03-19
jeffrey,

One of the best programs for partitioning in windows is Partition Magic. It should make it very easy reclaiming the space occupied by your Ubuntu installation. It's really graphical (but sure you can control values if you prefer). I don't think they have a free version, though. 

But of course there are also some linux-based CDs that are designed for the purpose of partitioning, and these are free. Check distrowatch. 

Remember to backup things first, you never know.

Good luck!
incubus

---

### Post by dueY on 2006-03-19
[QUOTE=deaddylan123]The text sais this:


And if I do but the cd in andboot windows off of that, would I be able to delete the part of my harddrive that Ubuntu is partioning?

Thanks[/QUOTE]


I think you can partition with the Windows CD.  Just take the partition that had Ubuntu on it and partition it as NTFS.

---

