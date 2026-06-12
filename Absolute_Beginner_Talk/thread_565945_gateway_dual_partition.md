---
title: "gateway dual partition?"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by masonjar chemist on 2007-10-02
I know all of these dual booting and multiple partition questions have been beaten to death over here, and i am terribly sorry for making another, but i searched through all of them and none of them seemed to be what i was looking for.

So heres the story, I loaded fiesty fawn on my girl firends gateway laptop on a 10 gb partition i made in the setup. the whole installation went off with out a hitch, but i cannot get the computer to boot form the partition with linux, it goes straight to the windows partiton. how do i tell it to look at the ubuntu partion to boot form?

sorry again for asking such a worn out question and thanks for any help :)

---

### Post by p_quarles on 2007-10-02
No need to apologize. Sometimes the information that's available out there can be overwhelming. 

From the sound of it, you might need to reinstall GRUB (the bootloader), which you can do by loading up the Ubuntu installation disk and choosing that option. 

The other possibilities (as far as I can think) are:
1) GRUB was installed, but configured to be silent; you can test this by holding down the 'esc' key right after the BIOS screen disappears
2) The Ubuntu installation didn't complete, or there was a problem with the installation disk. 

Any of these sound possible?

---

### Post by masonjar chemist on 2007-10-02
thanks for the help i really appreciate it

im not totally sure the installation was perfect. i did use the check disk option in the "start/install ubuntu" screen, and it was supposedly good. I also used the same disk to load it on to two other comuters and it worked fine.

I will definetly try to reinstall GRUB, but by pressing esc after the bios screen, are you saying to enter the bios menu? or does the show some other information (like the silent GRUB setting)?

thanks again for all of the help.

---

### Post by p_quarles on 2007-10-02
No, you don't need to enter the BIOS menu -- if GRUB is installed, you should be able to bring up the menu during a period of about 3-5 seconds directly following the BIOS boot screen (hard to describe -- basically, hit esc *after* the manufacturer's screen disappears). 

If the GRUB menu shows up, you'll be able to edit the system to automatically show the menu. If not, then, yeah, reinstall GRUB.

---

### Post by masonjar chemist on 2007-10-02
okay great, thanks alot for all the help and understanding. I wont get a chance to try it for atleast another day or so, but ill let you know how it worked as soon as i try it out.

---

