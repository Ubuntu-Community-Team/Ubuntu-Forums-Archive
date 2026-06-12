---
title: "Install to Dell 'Multiboot' system?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by OZTack on 2007-07-31
G'day,
New to Linux - Got the live CD (Feisty) working - network no probs,Wide screen  monitor resolution ok, 5.1 Surround sound great and network printer works a treat  :) ( all needed a LITTLE tweaking....)

Now time for installation.......... <pause for effect>

Current system is an old Dell 8400.
It has 2 HDD.
1) The Master has:- dell utility Patition |  windows XP  pro Partition | restore partition
2) The Slave XP Data partition....(160gb)

Plan:-
Install Feisty to slave HDD  assigning it 40GB total.

Question......

At the moment, I can :
1) press Ctrl F11 at boot - this will boot me to the restore partition on the Main disk.
2) Press F12 at boot - this will allow  me to choose to boot to  the dell utility partition, the Win XP partition OR the boot sequence ( HDD / USB/ Floppy etc etc)


Will I still have the ability to do the above with the "routine' guided dual boot install in Feisty? If not - how will grub work with this system?

Spent quite some time looking at this in the forums - lot of info re:-dual HDD systems - but my issue is what will happen with the "boot loader" (Ctrl F11 , F12) - if that is what it is - that already resides there?
Thanks :-)

OH - and I am AMAZED at how easy it has been to get things working in Linux.......:D

---

### Post by ayenack on 2007-07-31
Take a look at [this]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Boot_Ubuntu_from_the_Windows_Bootloader"). It should leave all your XP boot up options as they are but you may have to do a minor edit of your XP boot.ini seems reasonably easy to me.

Best of luck. ayenack.

Let me know how it goes.

---

### Post by OZTack on 2007-07-31
Wow- looks ideal - I will report back .
I think I want you to have my babies!! Thanks :D

---

### Post by ayenack on 2007-07-31
LOL

But **NOOOOOoooooo.........** to the babies. My misses wouldn't be to happy. Then again........HaHa.

P.S. Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=512456") and if you feel like it put a post there. You'll see what I mean when you read the first post.

Best of luck. ayenack.

---

### Post by OZTack on 2007-08-01
Hi Ayenack
Reporting back - Decided that I couldn't bee the only one that had a Dell set up like this [doh!] and that - in the interests of experimentation - I would try the normal install -
All went flawlessly EXCEPT that GRUB did not include my Win XP as a boot option !
That was easy to fix with an edit to my menu.lst but I did wonder if this is a bug or not ( I have posted a thread asking this....)

As for the link to that thread you gave - I am taking my time to write a considered reply :D

Thanks so much for your help BTW
[ as for your wife - I spoke to her - she says the babies are OK as long as she is not involved - My wife mentioned divorce.....;)  ]

---

### Post by ayenack on 2007-08-01
Cool mate.

I'll talk to your misses:twisted:

---

