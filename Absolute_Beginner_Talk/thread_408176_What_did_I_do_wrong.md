---
title: "What did I do wrong?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Lepht on 2007-04-13
Hi, I am a first time user and already having some troubles. Here is what I did (On XP).

-First, I Downloaded Ubuntu 6.06 LTS
-Burned to Cd with this guide [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
-Burning speed was on Max (might matter?)
-Before restarting my computer, the CD was visible under my computer. I open it and it talked about Firefox, Gimp and some other things.
-Restarted my system with CD in side. 
-When rebooting, system did not reboot as ubuntu. It just went straight to XP.
-Restarted system again, same thing.

So, I don't know what I did I did not do. Please help out :o 

Thanks for reading.

---

### Post by deadgobby on 2007-04-13
For one do not burn the ISO at max speed. That is no no no. A nice slow burn at 10X is nice. It takes a little longer to burn, but all of the ISO data will be retained. Data can be lost when you burn too fast. The other thing to do is go into your BIOS and set up the CDROM to boot up first. 
3rd if you run a AMD. You need to do some mojo for the CD to boot up. If you are using Intel. You'll be fine.
Gobby

---

### Post by Lepht on 2007-04-13
Thanks for the quick reply.

"The other thing to do is go into your BIOS and set up the CDROM to boot up first"

No idea how to do this :confused: , maybe a quick walkthrough ^.^?

I am running intel btw.

---

### Post by punong_bisyonaryo on 2007-04-13
You could check the boot order in your BIOS settings. To go into BIOS, press DEL during startup. Try moving up the CD drive in the boot order so that it would check the CD drive first if it's bootable before booting from the hard drive.

On some computers, you can also press a button during startup to open the boot device selection window. What button exactly depends on the computer/BIOS. Some use ESC, or one of the function keys, etc.

---

### Post by matthekc on 2007-04-13
you need to change the boot order when the computer first starts up the first black screen says push f2 or f12 for options.  Use f12 if you have it then just select boot from cd.  if you use f2 change the boot order in the bios put cd before hard drive.  if you use f2 you can leave it like that when you take the cd out it will move to the next item in the list if there is no boot cd in the drive.

hope this helps

---

### Post by matthekc on 2007-04-13
three of us replied :D  nice

---

### Post by deadgobby on 2007-04-13
Different comps have different ways to get into the BIOS. Some call it set up and other call it BIOS. It could be F10, Delete key, space bar, and so on. So when you boot up you system it will ask to you to press this key to get into the BIOS or Set Up.
[https://help.ubuntu.com/community/BootFromCD?highlight=%28cd%29](https://help.ubuntu.com/community/BootFromCD?highlight=%28cd%29)
Gobby

---

### Post by Lepht on 2007-04-13
I checked, and for me it was F12. So I changed the order, and it worked! Ubuntu is now running!

I did not make a new CD, but what the heck, it work :D 

Now, here is another question. I am running a widescreen monitor, but Ubuntu is running at 1024X768, so everything is stretched out. I looked under system>pref>Reso, and only saw more 4;3 ratios... Is there a patch for WS support? What should I do?

---

### Post by freebird54 on 2007-04-13
What you should do is tell us as much about your specifications as possible.  What your video card is - and what your monitor is supposed to able to do.  You are NOT the first!  Lots of help is available!

The best bet is to locate as much info as you can, then start a new thread headlined Widescreen with <insert video card name/model here> for the fastest response :)

Welcome - and enjoy!

---

### Post by Lepht on 2007-04-13
Thanks, I'll take your advice :D

---

### Post by GSF1200S on 2007-04-13
> **Lepht said:**
> Thanks, I'll take your advice :D

How old is your computer by the way? What wireless card do you have? What Video card do you have?

Im all for a new user- I was myself less than a month ago.. but I noticed you are installing 6.06 LTS.. Dapper is cool and all, and it will probably work fine with an older computer, but the hardware support in Feisty or even Edgy is alot better- Many things I couldnt get to work in Edgy work great in Feisty..

---

### Post by freebird54 on 2007-04-13
Hey GSF1200S - how come no bike specs in with the comp specs? :D

---

### Post by GSF1200S on 2007-04-13
> **freebird54 said:**
> Hey GSF1200S - how come no bike specs in with the comp specs? :D

ROFL!! I dont have enough room for half of what the bike has...:biggrin:

---

### Post by Lepht on 2007-04-13
Wireless card? Firefox ran fine. I use a wired connection.

My system is around 2 years old, well, it's the XPS200 (right before the release of 210), yes guilty as charged, I am running a Dell :( 

Here is my other topic on screen resoultion, take a look ^.^ :

[http://ubuntuforums.org/showthread.php?t=408204&highlight=lepht](http://ubuntuforums.org/showthread.php?t=408204&highlight=lepht)

---

### Post by sailor2001 on 2007-04-13
to gsf:  warn noob's that they can only upgrade one step at a time..........cannot jump from dapper to feisty.   also all iso should be burnt at 4x

---

### Post by Mana82 on 2007-04-13
hey dude, i had the same problem as i just installed ubuntu 2 days ago and then beryl...

i finally have my system all setup but when i first booted into ubuntu after installing i was in 1600x1200 when i wanted 1920x1200...

my monitor is a dell 2405fpw... i searched these forums (imagine that!!! :P) and i found the answer... u have to edit something called xorg.conf... remember to backup.  sorry i cant be more help than this as like i said i am so new to linux and over the last few days my brain is friend from learning all these commands and how linux works.  pretty proud of myself tho, i mounted my nfts drives in linux, installed vmware, foudn some bugs in beryl and fixed them.  its all good.

one word of advice, do not hit shift + backspace in beryl, it will mess u up.  search for that stuff on the forums to find out how to disable it!

---

