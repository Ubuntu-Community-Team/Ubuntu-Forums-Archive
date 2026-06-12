---
title: "hmmm.... Pieced together method...but will it work?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Jakkle on 2007-02-10
Hello all.
NOTE: This will not be put into practice now. This is in preperation for a possible dual-boot type thing in a couple months. Any 'how dod ot go?' type things are invalid and disregarded. I know thhis is premature but im one of the people who dont rest til they know what they want to know [which is why i hate physics. all those unanswered questions!] Right. On with the show.

I am going to buy a laptop. So far, so good. I want to dual boot Vista Home Premium with Ubuntu [Edgy or w/e the new one is]. So what i want to know is... as this is a prebuilt system, how do i go about it? Having trawled the net, i have so fargot the following together:
1] Load vista. get rid of unnecessary/unwanted crap, install wanted stuff. Defragment until reasonable. Back up.
2] Decide on partition size. I am thinking 80gb for V and 40 for U. Bear in mind i will get a 250gig external harddrive for files and the like.
3] Download and burn SystemRestore. Load this.
4] Create the two main partitions on internal HDD. Make 40gig partition bootable. Create 3 partitions on external: 122 gig each for V and U, 6gig for FAT-32 for file-swapping and the like.
5] Load U Live CD and install to internal drive.
6] Go to U terminal. 
   i]Enter: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
  ii]Enter: sudo gedit /boot/grub/menu.lst
7] Immediately under "## ## End Default Options ## ##", enter: 
    title Windows Vista

    root (hd0,0)

    makeactive

    chainloader +1 
8] Increase GRUB timeout to 15
9] Save & quit.

Restart. The job may or may not be a good'un.
Right, that's that. So what i want to know is:
a] Will it work? What are the risks?
b] Can i reinstall V if it goes tits-to-the-ceiling, bearing in mind i do not have the install disk? Will backup help me there?

I really want to dual-boot ubuntu, and any advice is appreciated. If you know of a comprehensive tutorial , please tell me!!!!

Thats all. Please Advise.

Jack

---

### Post by meborc on 2007-02-10
well... i would do it like this:

1) install vista
2) defrag defrag defrag until i see a white end in the drive
3) boot from ubuntu cd
4) start the installation and chose MANUAL PARTITIONING
5) make the win filesystem smaller as much as the defragment gave me
6) chose AUTOMATICALLY PARTITION THE FREE SPACE
7) let the ubuntu finish the installation
8) boot to ubuntu
9) sudo nano /boot/grub/menu.lst and change the default value to 4 (which is windows if you have only 1 kernel installed in ubuntu)

enjoy the magic

---

### Post by Jakkle on 2007-02-10
:D

cheers. thats certainly a lot lot easier.
Question: will this let me choos ubuntu or windows on boot up?
thanks again, probs a silly silly question i know haha.
Thanks  v much.
Jack

---

### Post by Happy_Man on 2007-02-10
Ubuntu automatically installs a bootloader called GRUB, which will give you the option to boot either Ubuntu or windows.

---

### Post by Jakkle on 2007-02-10
excellente.
Thanks for all your help guys
Jack

---

