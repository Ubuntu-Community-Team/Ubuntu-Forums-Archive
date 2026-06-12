---
title: "? about dual boot with vista and ubuntu"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by ndrew2505 on 2007-07-02
i hae ubuntu on my dell(1505) which was originally vista. my ? is...i formatted the whole hd when i installed ubuntu so i need to find out how to reformat the drive back to ntfs from the other. i want to install a dual boot system since im used to using windows until i learn more about linux and the command codes because im a total n00b to linux but i like what ive seen...thanks in advance for any help.

any explanation on setting up the dual boot will also be helpful. do i just install windows and then install using the ubuntu cd and the partition and format options it has and if sohow would i choose between the two oss'?

---

### Post by rillip on 2007-07-02
There are many install guides out there for dual boot.  I'd suggest googling a little.  But the general process is this:

1) install Windows.  

a) If you're smart about it, you can manually create the partition you want to put Windows on from the Windows install.
b) if you're not, just let Windows take the whole drive.

2) install Linux
a) if you were smart about it above, go through the manual partitioning and you can chose to set up your partitions in the unallocated space
b) if you weren't, just go through the guided install, which will resize your Windows partition and create the partitions you need.

---

### Post by ndrew2505 on 2007-07-02
but how do i reformat to ntfs filesystem from the linux? i formatted the entire drive when i installed ubuntu? do i need a special program or will i have to pay someone to do it?

---

### Post by Vajra Vrtti on 2007-07-02
The Vista installer can handle that (at least the XP installer did). Probably the Vista installer will complain it has no ntfs partition to install and you will have the option to delete the current partition and create a new ntfs partition.

---

### Post by ndrew2505 on 2007-07-03
i put the vista disc in and chose to format the selected parition but it gave me this message:
FAILED TO FORMAT PARTITION[ERROR CODE 0X80004005]

do i need to just delete the partition and create a new one?

nvm i reread your last post. im gonna try it now.

---

### Post by Ocxic on 2007-07-03
yes try that, it'll prolly work

---

### Post by bradmayne on 2007-07-03
Dude download vista boot pro.  Follow the directions it's not hard.  That's what I did.  I have vista home premium and ubuntu.  Remember not to format after you resize your hard drive.

---

### Post by ndrew2505 on 2007-07-03
i got it! thanks for all the input. i gave about 40% of my hd to ubuntu and 60% to windows since windows is bigger but after i figure out the linux a lil more thats gonna change....thanks again.

---

### Post by bradmayne on 2007-07-03
Glad I could help ya! Oh one more thing DO NOT uninstall vista boot pro!!!!!

P.s. check out my how to view windows files on your ubuntu OS.  That will get you all set up to "see" your windows files!!!  Peace

screw bill gates linus torvalds is the MAN!!

---

