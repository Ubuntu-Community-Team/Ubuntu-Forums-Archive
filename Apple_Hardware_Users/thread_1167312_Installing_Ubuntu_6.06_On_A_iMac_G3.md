---
title: "Installing Ubuntu 6.06 On A iMac G3?"
date: 2009-05-22
forum: Apple Hardware Users
---

### Post by BrandonG3 on 2009-05-22
[FONT=Comic Sans MS] Hello, I Am Absolutely New To This, And I Have A iMac G3 333MHz Processor, 384 MB Of Memory, And I Recently Burned A PowerPC Ubuntu 6.06 Desktop CD.

So, After I Burned The CD, Put It In And Held Down The C Key Like It Said To Do On Websites And Forms I Read Here. But It Just Boots To OS 9!

And When I Erased My Hard Drive And Re-Formatted It, I Only Get The Flashing Question Mark Folder With A Mac Icon.  ](*,)


If Anyone Can Help, I'd Be Really Happy!!! :popcorn:=D>:mrgreen:\\:D/:-P:-\"

Thank You For Any Help,

Brandon G3


Yum.... Yummy Popcorn.........:popcorn:
[/FONT]

---

### Post by anandrajny on 2009-05-23
> **BrandonG3 said:**
> [FONT=Comic Sans MS] Hello, I Am Absolutely New To This, And I Have A iMac G3 333MHz Processor, 384 MB Of Memory, And I Recently Burned A PowerPC Ubuntu 6.06 Desktop CD.

So, After I Burned The CD, Put It In And Held Down The C Key Like It Said To Do On Websites And Forms I Read Here. But It Just Boots To OS 9!

And When I Erased My Hard Drive And Re-Formatted It, I Only Get The Flashing Question Mark Folder With A Mac Icon.  ](*,)


If Anyone Can Help, I'd Be Really Happy!!! :popcorn:=D>:mrgreen:\\:D/:-P:-\"

Thank You For Any Help,

Brandon G3


Yum.... Yummy Popcorn.........:popcorn:
[/FONT]


First and foremost, download a 9.04 alternate CD and install with it. You'll see how wonderful the experience is.

---

### Post by Benboom on 2009-05-23
9.04 might not be that wonderful for him if he only has 384 megs of ram.

Brandon, will the iMac boot off a Mac CD, like an install disk or a utility disk?

---

### Post by BrandonG3 on 2009-05-23
Yes, It Will.

I've Installed OS 8 & 9 Many, Many, Times.

---

### Post by tiresia on 2009-05-24
I would have a try with Xubuntu 9.04 (Jaunty), if you are not experienced - the best solution for law Ram/Processor System being maybe a Debian Base System with LXDE as Desktop Environment (there are plenty of threads about it on this forum)
You find Xubuntu Jaunty here (there is even a LiveCD)
[http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/jaunty/release/)

Anyway, if you get the Flashing Question Mark, it means that the iMac can't read the CD. How did you burn the CD? You should not burn it as Data-CD. Make a copy of the .iso you downloaded at low speed

---

### Post by BrandonG3 on 2009-05-24
Funny..... Because When I Boot Into OS 9 It Shows The CD Named As " Ubuntu 6.06.1-desktop.iso " And Then It Shows All The Files! But It Doesn't Work!!!

---

### Post by BrandonG3 on 2009-05-24
I Also Used The program ubuntu recommended me!

---

### Post by BrandonG3 on 2009-05-24
Ok, I'm Trying Xubuntu, Is There Any Special Program I Should Use Or Should I Just Copy The iso file?

---

### Post by BrandonG3 on 2009-05-24
So, How Does The Desktop CD Work?

---

### Post by tiresia on 2009-05-24
Do you have another mac? Then you can use the Apple Disk Utility. Just make a copy of the iso image, without mounting it. And burn it at very low speed

---

### Post by BrandonG3 on 2009-05-24
I'm Installing OS 9 Right Now, Got The Xubuntu Desktop CD, And Going To Try And Install It. Wish Me Luck!

---

### Post by BrandonG3 on 2009-05-24
OK, Xubuntu 9.04 Has Started Up ( C Key ) And Is Now Waiting For A Command.

What Do I Type?

I'm Am Defiantly Not A Command Dude!

Help Please?

---

### Post by tiresia on 2009-05-24
You mean that you booted from the Installer CD? It's the alternate CD or the LiveCD?

---

### Post by BrandonG3 on 2009-05-24
Well, It Says Desktop CD Or Alternate CD And Downloaded The Desktop CD.


I Got That From The Site. Xubuntu 9.04

---

### Post by tiresia on 2009-05-24
Ok, what you got is the yaboot (the linux kernel bootloader for ppc) prompt.
Hit TAB to see the different options. For you iMac you could just hit ENTER, or if you want to see how the system boot write ```
live-nosplash-powerpc
```

---

### Post by BrandonG3 on 2009-05-24
I Went Ahead And Pressed Return, It Showed The Xubuntu Logo And A Scrolling Bar Like XP Starting Up, The Bar Filled Up, The Monitor Turned Off (Like It Was In Sleep Mode), Turned On For A Sec., Turned Back Off, And Made A Beep.

I've Left It Be For A While, And Now I'm Going To Check On It.

Let's See What Happens!!!):P

Didn't Work... That Stinks........ :(

---

### Post by BrandonG3 on 2009-05-24
I'm Starting To Lose My Patience Because It Won't Exactly Install, It Just Show A Standby Screen!

---

### Post by BrandonG3 on 2009-05-25
I'm Starting To Lose My Patience Because It Won't Exactly Install, It Just Show A Standby Screen! Any Help Please???

---

### Post by tiresia on 2009-05-25
Installing Linux on an iMac is not the easiest installing process. So, please, be patient.
And it's already a good sign that you can boot with the splash image
Let's try again with the LiveCD (but it would be easier with the alternate CD)
Try this way```
live-nosplash-powerpc video=ofonly
```

---

### Post by BrandonG3 on 2009-05-25
Yeah, The First Time I Tried It Didn't Work ( Left It Be For Like 5 Hours Just The Way It Was) So Let's See What Happens This Time.....

UUGGHHH!!!!!! It won't work no matter what I try!!! :arrow:](*,)](*,)](*,)](*,)](*,)](*,)](*,)


P.S. This Time It Was All Day!!!!!!!!!!

---

### Post by BrandonG3 on 2009-05-30
It don't work!!! :(

---

### Post by BrandonG3 on 2009-06-03
:!::?::?::?::frown::frown::frown::( I need help!!!!

---

### Post by matamoscas on 2009-06-03
I was thinking of installing a version of Ubuntu on my in-laws old G3 computer the next time I visit.

First off, I would discourage you from bothering with 9.  Even if it does install, it won't work very good with that hardware.  It is a great looking OS, I wish I had better hardware myself.  

I was thinking of perhaps trying a version of 6 or something like that...

I was gonna read around some more to see if anyone has had success with it.

That said, I would keep my head down, and try six or nothing =)  From my experiences, and what I have read, version 7, was rather problematic for PPCs - for whatever reason.  So, if six doesn't work, you could try 8.  But, really, I would guess 6 would be the best bet.

Think what would happen if you tried to install Windows XP on that old of a computer, that you bought with Windows 98 =)  Well, it wouldn't even install. So, I think you get my point. Even if it could, would you really want it to? =)  Installing modern software on a old computer can be problematic.  Newer is not always better.  Another example, image what your average prom queen will look like 20 years later trying to fit into the same outfits =) (if they even fit!)

---

### Post by BrandonG3 on 2009-06-04
wait...... how did you know I have a 98 computer and I want to put xp on it?

---

### Post by BrandonG3 on 2009-06-15
> **matamoscas said:**
> I was thinking of installing a version of Ubuntu on my in-laws old G3 computer the next time I visit.

First off, I would discourage you from bothering with 9.  Even if it does install, it won't work very good with that hardware.  It is a great looking OS, I wish I had better hardware myself.  

I was thinking of perhaps trying a version of 6 or something like that...

I was gonna read around some more to see if anyone has had success with it.

That said, I would keep my head down, and try six or nothing =)  From my experiences, and what I have read, version 7, was rather problematic for PPCs - for whatever reason.  So, if six doesn't work, you could try 8.  But, really, I would guess 6 would be the best bet.

Think what would happen if you tried to install Windows XP on that old of a computer, that you bought with Windows 98 =)  Well, it wouldn't even install. So, I think you get my point. Even if it could, would you really want it to? =)  Installing modern software on a old computer can be problematic.  Newer is not always better.  Another example, image what your average prom queen will look like 20 years later trying to fit into the same outfits =) (if they even fit!)



no, really how did you know?

---

