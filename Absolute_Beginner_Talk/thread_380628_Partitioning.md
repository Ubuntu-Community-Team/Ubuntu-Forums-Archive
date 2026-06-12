---
title: "Partitioning?"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by sewercake on 2007-03-09
HI

  Ok, here is my problem. I looked in my computer today to see if I had any extra slots for another HDD and it looks like I don't, and I am hoping you guys could help me figure out if I do. so I will explain. On the motherboard, there are three slots, one, has my HDD, second has my Disc tray, and third, is green, and has my floppy disk drive. Now I heard somewhere that IDE jacks can have 2 pieces of equipment on them at the same time (i.e a Disc tray, and an HDD) is this true? The cords are wide, and thin, they are a grey colour. So is it possible to install another HDD on my computer?

   OK, now, lets say that I cannot get another HDD, I have an 80GB HDD, right now, and 20GB are free, is there anyway I could partition it with a litttle less than 20GB, and still be able to install programs on it and let it run fine?
thanks appreciated again,



-sewercake

---

### Post by Bachstelze on 2007-03-09
Yes, it is true. An IDE conector can have two IDE devices connected - usually hard or optical drives - which are the Master device and the Slave device. So, yes, it is very possible to install one - or even two - extra drives on your system.

If you decide to go on with just one drive though, it is fairly easy to resize your existing partition in order to make free space to install other OSes.



P.S. : this is my 2000th message, champagne to everyone :)

---

### Post by overdrank on 2007-03-09
> **sewercake said:**
> HI

  Ok, here is my problem. I looked in my computer today to see if I had any extra slots for another HDD and it looks like I don't, and I am hoping you guys could help me figure out if I do. so I will explain. On the motherboard, there are three slots, one, has my HDD, second has my Disc tray, and third, is green, and has my floppy disk drive. Now I heard somewhere that IDE jacks can have 2 pieces of equipment on them at the same time (i.e a Disc tray, and an HDD) is this true? The cords are wide, and thin, they are a grey colour. So is it possible to install another HDD on my computer?

   OK, now, lets say that I cannot get another HDD, I have an 80GB HDD, right now, and 20GB are free, is there anyway I could partition it with a litttle less than 20GB, and still be able to install programs on it and let it run fine?
thanks appreciated again,






-sewercake



Hi here is a link to help with your IDE hard drive question.
[http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html](http://www.mikeshardware.com/howtos/howto_connect_ide_hd.html)
And yes 20 gb of space is enough to install. Good Luck!:)

---

### Post by mikewhatever on 2007-03-09
20 GB is not a lot of space to consider installing another OS. Remember that you have to leave some free space for the present one. I would say it is barely enough, but you can't go wildly installing stuff.
About the IDE sockets, yes, I think you can have two HDDs or CD/DVDs on each, but it would be the best to consult your motherboard specs.

---

### Post by Bachstelze on 2007-03-09
Rubbish. Even 10 GiB is more than enough for Ubuntu. Just because Windows takes over an insane amount of diskspace to install it's useless crap does not mean all OSes do.

---

### Post by berylmichael on 2007-03-09
You are correct whe you say the "IDE jacks can have 2 pieces of equipment on them at the same time" Look for the gray cable that has the HDD connected to it. On the cable about half way between the HDD and the motherboard, there may be another connector. This would be used to connect another device such as another HDD to it. If there isn't a connector here, you can usually purchase this type of cable in most computer stores. In addition, when you connect another HDD to the system, it should be as a "slave" drive. Ask the computer store on how to set this up. And of course, you need space in your system to install another HDD.

If you don't have room for another HDD, and you have 20GB of space free, use Gparted on the ubuntu live disc to partition the drive. I recommend to read this user friendly dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing"). BACKUP your important files and data before you do this just in case.  

Hope this helps.
Michael

---

### Post by MgNate on 2007-03-09
All i have to say is don't be afraid of installing another HD, it's extremely easy. The hardest part is the jumper settings. I installed my first hard drive into my family computer when i was 10 years old.

Yes, it's elementary. :) 

Have fun,
Nathan

---

### Post by sewercake on 2007-03-09
OK

   first of all YAAAAAYYYYY! and second of all....? OK, i read over the little tutorial thingy and I was a little confused, from what I got, I would put the second HDD into, the other HDD where the IDE cable went in? then I would change the main, or the one I just connected to the slave drive. I know I could partition my original HDD, but I really want to install some hardware onto my computer, last year, around my 13th birthday, I bought a video card, but was too chicken to actually install it, and then it cost me 80 bucks, so I am really determined this time.
again, THANK YOU GUYS SO MUCH



-sewercake

---

### Post by berylmichael on 2007-03-09
Just make the second HDD the slave drive. Leave the master (80GB) alone.

---

