---
title: "Wine"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-28
On this computer im running Windows XP and i was wondering if there is a way to download wine to a CD/Floppy/USB Flash Drive then put it onto my other computer (the other computer is running ubuntu 7.04)?

---

### Post by redfox1160 on 2007-08-28
sry, i didn't think anyone was gonna answer my other post...

---

### Post by elusive_elf on 2007-08-28
can't you connect your other computer with linux to the internet? makes it much easier

---

### Post by redfox1160 on 2007-08-28
wouldnt i have to install the verizon software that i installed on this computer to use the internet, cause i dont want to do that...

---

### Post by Fixman on 2007-08-28
Well, I don't see mutch a problem. Just download the .tar.gz to windows, put it on a memory drive, and pass it to the other computer, and execute it there. Did this not work for you?

---

### Post by mysticmatrix on 2007-08-28
You can always get latest-1 version of wine from here. [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

However there might be any dependency that is required. If anything like such pops up, you can download required packages from packages.ubuntu.com

---

### Post by redfox1160 on 2007-08-28
> **Fixman said:**
> Well, I don't see mutch a problem. Just download the .tar.gz to windows, put it on a memory drive, and pass it to the other computer, and execute it there. Did this not work for you?

where can i get this file? is this the place: [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803")
If it is, which file do i download. THANKS!

---

### Post by mysticmatrix on 2007-08-28
> **redfox1160 said:**
> wouldnt i have to install the verizon software that i installed on this computer to use the internet, cause i dont want to do that...

Well Ubuntu will most probably detect your internet automatically, except for hardware problems. I am not a US/EU resident, but a intelligent guess is that Verizon would not be offering a active linux support/any support. In either case, you'll not have to install software from Verizon.

So if you don't have hardware troubles, you'll automatically connect to Net.
From your other posts, it looks like you haven't installed Ubuntu yet. Give Live CD a try, and then come back.

---

### Post by redfox1160 on 2007-08-28
i have it installed on another computer, but i just need to know where to get the file so i can put in on my USB drive and install it on my other computer that has ubuntu (7.04)

---

### Post by mysticmatrix on 2007-08-28
> **redfox1160 said:**
> where can i get this file? is this the place: [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803]("http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803")
If it is, which file do i download. THANKS!

Those are OLD version of WIne for OLD versions of Ubuntu. Also, Ubutnu way of installing softwares is a little different. Find out some time to read official support page at 
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by mysticmatrix on 2007-08-28
> **redfox1160 said:**
> i have it installed on another computer, but i just need to know where to get the file so i can put in on my USB drive and install it on my other computer that has ubuntu (7.04)
 In that case, my other post would work. Download the .deb file of Wine(Similar, but not same, as an .exe file of Windows).
Try double-click to install it. If it asks for any dependency(additional packages), download them from packages.ubuntu.com. Then install those packages by double clicking, and at last install Wine packages.

I would also suggest you to find DVD of repository of Ubuntu(search google, not best reply but I really can't tell you out of my memory where to go) so that you don't have to take so much headache everytime you install a software. Add DVD and all required packages will be installed.

---

### Post by redfox1160 on 2007-08-28
what file is it?

---

### Post by mysticmatrix on 2007-08-28
> **redfox1160 said:**
> what file is it?

Ok to make it easy. Go to this page. [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
Click on version of wine you want. Then see carefully which version of Ubuntu you have(Feisty, Dapper, etc). Also see if you have installed a 64 bit Ubuntu or 32 Bit? 

Match all combination and click on correct link. Downlad the file(which would be a .deb), take it to your Ubuntu PC and follow as I posted before.

---

### Post by redfox1160 on 2007-08-28
how would i know if i want the i386 or the amd64?

---

### Post by redfox1160 on 2007-08-28
> **mysticmatrix said:**
> Ok to make it easy. Go to this page. [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
Click on version of wine you want. Then see carefully which version of Ubuntu you have(Feisty, Dapper, etc). Also see if you have installed a 64 bit Ubuntu or 32 Bit? 

Match all combination and click on correct link. Downlad the file(which would be a .deb), take it to your Ubuntu PC and follow as I posted before.

how do i know if i have 64bit or 32bit (is 64bit amd64, and 32bit i386?)

---

### Post by redfox1160 on 2007-08-28
can someone please help me???

---

### Post by Mogurijin on 2007-08-28
What is your processor?

---

### Post by redfox1160 on 2007-08-28
> **Mogurijin said:**
> What is your processor?

im not exactly sure... i think its amd (it says something like that at the start up screen...

---

### Post by Mogurijin on 2007-08-28
How old is the processor?

EDIT:
Also, what other words do you see? Athlon, Duron, Sempron, Optron?

---

### Post by redfox1160 on 2007-08-28
i think its 1999 (AMD athlon)

---

### Post by Mogurijin on 2007-08-28
Grab the i386 Feisty Fawn one.

---

### Post by redfox1160 on 2007-08-28
thanks!

---

### Post by redfox1160 on 2007-08-28
I have it on a Flash Drive, but i dont know how to get it off of the flash drive, can someone help me?

---

### Post by VoiceOfTheSoul on 2007-08-28
Once we have it on the flash drive and onto the computer, how is it installed?

---

### Post by redfox1160 on 2007-08-28
i need to know how to get files off of my flash drive...

---

### Post by splintercellguy on 2007-08-28
Once you plugged in your flash drive, Ubuntu should have automounted the device. If not, an ls /media or fdisk -l would help. Do sudo dpkg -i thdebfile.deb. I'm assuming you're using the deb from Wine's repo?

---

### Post by redfox1160 on 2007-08-28
i dont know anything u just said...

---

### Post by splintercellguy on 2007-08-28
Ubuntu should have automounted the device. If this is not the case, post the output of ls /media and sudo fdisk -l (sudo = superuser do, when prompted, enter your user account password). Once you've copied the deb to wherever (you did get it from Wine's Budgetdedicated repository right?), then do sudo dpkg -i nameofthedeb.deb in the directory where you copied it.

---

### Post by VoiceOfTheSoul on 2007-08-29
I tried to install it, but the file I was given doesn't work. Are they any other places I could get the file?

---

### Post by redfox1160 on 2007-08-29
Does anyone know if Final Fantasy 7 will run without WINE?

---

### Post by Mogurijin on 2007-08-29
> **redfox1160 said:**
> Does anyone know if Final Fantasy 7 will run without WINE?
No, it won't. WINE allows you to use exes and dlls, which it probably requires to run. Unless your talking about the pxs version, which would need a psx emulator. Now, when you plug your flash drive in, does anything come up? Like a screen with your files? Also, what filesystem does it have (I don't think this will matter but it might help)? It nothing autoruns, go to places, computer. Then you should see disk or something. Double click on that to open your flash drive. Now Double click the .deb package. A screen should come up and click the install button. Most likely you'll have to enter a password, which will be your account password. Then go [here]("http://ubuntuforums.org/showthread.php?t=497332") to get wine configured. Have fun ^^

---

