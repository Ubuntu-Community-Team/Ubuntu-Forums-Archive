---
title: "xserver not installed? (was: stupid guy needs help)"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-09-19
ok so i tried to get the eye candy. now ubuntu wont start, saying xserver not found and need to reconfigure my gdm. running ubuntu off the cd now. any idea how to fix this with having to reinstall?

---

### Post by dmichaels on 2006-09-19
without** having to re install

---

### Post by xpod on 2006-09-19
> stupid guy needs help

NO i DONT!!!!!WHO told you that???

I just re-installed for less than THAT....lol
Cant you just go revert to your backup x thingy????

You know what i mean:D .Im just guessing

---

### Post by dmichaels on 2006-09-19
i barely know any commands. and it wont load my desktop. im stuck in black screen command mode. so the best i know is:

sudo apt get-install xserver 

but then tells me to specify which one. or it tells me to configure the GDM setting what ever that is.

---

### Post by xpod on 2006-09-19
It`s not something ive got round to attempting yet.In fact i dont think it`s possible on either our Ubu OR Kubu sys.
Theer`s quite a few recovery guides out there as ive read them myself but it`s not something i know much about im afraid..

I just re-installed Kubun myself for a couple of minor reasons but i`d have probably took all the longer working round it:mrgreen: 

Easy option for moi!!...Good luck either way

---

### Post by kherim on 2006-09-19
similar thing happend to me when i try to install compiz.

i suggest

1) boot from ubuntu cd (like when you install) [read all first]
2) open gnome-terminal and type: sudo mkdir /media/data
3) then go to system -> admin -> disc
4) select the partition or disc where your ubuntu is
* you should recognize it by the size of the disk and free space. Also check the file System (Extended 3 or Ext3)
5) type /media/data and the Ok (or accept)

[http://img160.imageshack.us/img160/8436/pantallazogestordediscosdd8.png](http://img160.imageshack.us/img160/8436/pantallazogestordediscosdd8.png)

6) open nautilus and go to /media/data/etc/gdm/
7) erase gdm.conf and gdm.conf-custom
8) make a copy of factory-gdm.conf rename it to gdm.conf
9) boot without ubuntu cd

Feedback if works plz.

pd: sorry my english

---

### Post by dmichaels on 2006-09-19
i will follow as best as i understand. i only installed ubuntu 2 days ago. so i will try.

---

### Post by bulldog on 2006-09-19
Can you update us with what you have installed? [eycandy can be everything]

Mounting to media won't work,you have to mount to /mnt

---

### Post by dmichaels on 2006-09-19
what is nautilus...i cant seem to find it

---

### Post by dmichaels on 2006-09-19
i tried to to do the compiz and xgl install. i have 
nvidia N36 5700 256MB 
P4 2.5 Ghz

---

### Post by Brunellus on 2006-09-19
> **dmichaels said:**
> what is nautilus...i cant seem to find it
nautilus is the file browser.

Also:  the title of this thread has been changed to better reflect the nature of the help request.  In the future, please use the thread title to summarize (briefly) the type of problem.  You get no extra points for self-flagellation, and appeals to mercy are not likely to yield useful technical information.

What howto were you using to configure XGL?

It should be noted that XGL/Compiz are EXPERIMENTAL.  If you don't feel confident with the system, DON'T USE THEM

---

### Post by haxer on 2006-09-19
Where are you from? so i might help you in your language :)

---

### Post by bulldog on 2006-09-19
Well Nautilus is your 'browser' for your computer so to speak.

If you want eyecandy and not even can find Nautilus,I suggest you better read something more,to have a little understanding of your Ubuntubox.

---

### Post by dmichaels on 2006-09-19
sorry mr ubuntu master person. its just that windows crashed on me last week. i had very important files on there necessary for my work and livelyhood. i was recommended ubuntu by a friend and tried it out. i love it already, ok, but now i cant even get into with out the CD so do you see how i can be very frustrated at this time? im not a computer wizard. i will try to be as technical as possible in the future when posting to the forums. sorry to have mad you upset with my lack of knowledge,

---

### Post by msandoy on 2006-09-19
Not that this will help you, but I guess, since your Ubuntu install is only two days old, it should not take too long time to get the install back to where you messed up. I have learned from experience to make a separate partition for my home folder. This way you can re-install the OS without loosing anything from your account. :-)

---

### Post by dmichaels on 2006-09-19
> **bulldog said:**
> Well Nautilus is your 'browser' for your computer so to speak.

If you want eyecandy and not even can find Nautilus,I suggest you better read something more,to have a little understanding of your Ubuntubox.

yeah i realize that now, iw as told that i could install this stuff no problem by my friend, who i see now, is alot more proficient in computer usage than i. sorry

---

### Post by Brunellus on 2006-09-19
If you could post the URL of where you got the directions, we might be able to identify what went wrong and reverse it.

---

### Post by kherim on 2006-09-19
nautilus is the file explorer of ubuntu

open gnome-terminal and type: nautilus

---

### Post by xpod on 2006-09-19
[QUOTE]what is nautilus...i cant seem to find it[QUOTE]

Mabey you should have learned how to navigate the os before you got tooo
adventurous......
Least then you`d know where everything is when it comes to "recovery"

Just a thought....Im NO better:rolleyes:

---

### Post by dmichaels on 2006-09-19
i appreciate all the help...honestly. its hard to find support like this anymore. i tried to follow poofyhairguy's howto on installing glx and compiz. but im pretty sure i ended up doing something very wrong. just wanted to deck out my destop like my friend suggested.
 i just re installed ubuntu to get this over with. lesson learned. sorry we didnt get this resolved but i could only handle so much of rebooting and reconfiguring my xserver so many times without results. i guess ill have to keep my lame desktop for now. so where can i find a list of basic commands and essential files for ubuntu to get me started in the rght direction?

---

### Post by bulldog on 2006-09-19
This is one of many :D 

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

---

