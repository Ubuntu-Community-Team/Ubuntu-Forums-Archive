---
title: "Powerbook 333 xubuntu fails al the way..."
date: 2006-12-11
forum: Apple PPC Users
---

### Post by bigbadben on 2006-12-11
[COLOR="red"]**I tried the install cd ( alternative ).**[/COLOR]
version 6.06-1 or 6.10.
None of them work....when installing, it fails at installing base system. at around 6%, and i dont remember dohw with files fail. If you ignore it always fail the rest of the install, so!!

[COLOR="Red"][B]Itried the live cd version 6.06-1 or the 6.10, but does not start..
[/B][/COLOR]It goes up to the splash screen and dies there.
So this type of install dont work...
*****************************************************************************
And the checksum of cd are ok btw :mrgreen: 
*****************************************************************************
powerbook 333mhz, 192md ram

---

### Post by Gen2ly on 2006-12-11
I could think of three things.  I use a 300mHz iBook so it's like it sorta.  Though I didn't have to do it, I've heard of others that had to update their firmware.

[Apple Documentation]("http://docs.info.apple.com/article.html?artnum=75132#English")

You might have to 'Zap your PRAM' this sounds worse than it is.  It just resets a few things in memory - like your MacOS system colors, some network settings.  
The way to zap your PRAM is to hold the following keys down 5 seconds after you hit the power button on your Macintosh:

command + option + p + r

Third, ru sure you burn the CD correctly?

HINT:  I've generally heard that the alternative CD worked better for most early G3 computers.

---

### Post by stream303 on 2006-12-11
Does it really fail or just seem to "hang" at 6%?  I recently installed Edgy Alternate to my firewire drive, and it too seemed to hang at 6%, but it was just thinking.

I killed the install a few times until I walked away from it, and lo, it would eventually finish.   At first I stared at the blue/red progress bar so long my eyes thought it was moving, but it wasn't :)

Does your install really error out - or just hang?  Maybe grab a cup of coffee...

---

### Post by bigbadben on 2006-12-11
btw.....ubuntu 606 or 610 installs fine....its just slow as hell.       loll..

I did try xubuntu by apt get install xubuntu desktop.
thats why i want to install a clean install..
i tried to erase ubuntu, and keeping xubuntu. but ubuntu was never completely gone.......


anyway, im trying what was told here.........ill give some feedback


thx

---

### Post by bigbadben on 2006-12-11
btw..............command option p and r did the trick.............

now the live cds work and boot up fast.....no need for cofféee.........dont even have time to pee.....lol


thz buddy


just need to know if the install will be successful.........

the answer to come...

---

### Post by bigbadben on 2006-12-11
i have succesfully installed xubuntu, by doing ( control+alt+p+r ).holding 5 sec. until shrime again.......let go the keys and press ( c ).

Dont know exactly why it work this time. But anyway it worked.( same cd )??

xubuntu 6.10 with live cd on a powerbook 333mhz + 192 ram, installation [SIZE="5"]went no problemmo[/SIZE]........:mrgreen: 


Thank you boys and girls........

---

### Post by Gen2ly on 2006-12-12
BigBad, you'll have to tell me it you like it.  With the ibook 300mHz I have, ubuntu runs good but is a bit sluggish.  I heard Xubuntu is supposed to be much better!?

---

### Post by bigbadben on 2006-12-12
> **Dirk.R.Gently said:**
> BigBad, you'll have to tell me it you like it.  With the ibook 300mHz I have, ubuntu runs good but is a bit sluggish.  I heard Xubuntu is supposed to be much better!?

yea......works fine, for the little i did with it.......speed is good........
im having starnge problem dohw. 
see 
[http://ubuntuforums.org/showthread.php?t=317142]("http://ubuntuforums.org/showthread.php?t=317142")
:confused: :confused: 

anyway.to make it short and sweet.......speed is good, but have not enjoy a lot cause i spent to much time trying to fix the dhcp problemmm

Hope it answer your query... :rolleyes:

---

### Post by krimson on 2006-12-13
well, i tried the ctrl, opt, p+r trick, and the rezap worked, but it didnt fix my installation...  it always hangs on the "packages selection and install"  it gets to 6% and then fails to install...  i install the bootloader and then i can at least log in, so i tried apt-get install ubuntu-desktop, but it starts crapping out at 9% complaining about a "Buffer I/0 Error on device hdb, Logical block ######"   i formatted to an empty drive, and as far as i knew, this ibook seems to be ok...  

i was hoping this rezap would fix it, but i guess not... its a ibook g3 600mhz?  (not sure)

---

