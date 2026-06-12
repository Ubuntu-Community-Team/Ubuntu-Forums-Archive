---
title: "Ububtu, Vbox and FreeNas"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by c1k2j3c4 on 2007-10-24
Hello,

last month I finially took the dive and built a Ubuntu/PCLinuxOS( I like them both)  pc to take over my daily email and web surfing or anything else I can do in linux and left my higher end pc for gaming and dvd backup. What I want to do is shrink the number of computers my family has by one(7 total). What I would like to do is get rid of my freenas server and move its 500gig hd to my Ubuntu  box since its on all the time. I was hoping that I could use my opty dual core processor in my linux box and  run freenas in vbox and still be able to run Ubuntu without any performance hit. Basicly I'm thinking that 1 core would run freenas and the other core run Ubuntu. Am I off base here in the way I'm thinking or is this doable?  Thanks.

AMD 64 3700 or opty 160
Abit AV8
Ultra PC3200 2 x 1024 (can add another gig if needed)
onboard gig lan
PCI Realtek gig lan
Audigy 2
BFG 7800gs
Seagate 160
HP DVDRW lightscribe

---

### Post by lazyart on 2007-10-24
My only gripe with virtual box (vbox) is what you have to do to allow it to be visible to other machines on your network.

I would tell you to consider vmware server for your freenas setup.  If your freenas drive is PATA, connect it to the same channel as your optical drive.  You'll get better performance on your host system as freenas data isn't trying to squeeze through the same pipe as your system data.

---

### Post by c1k2j3c4 on 2007-10-24
Thanks for your responce.

I was thinking of and can do vmserver since i do have a key. I was only thinking of using vitural box since i allready have it installed.

As far as my hard drives go, both of the system drives are pata and the drive I'm going to add is a sata drive. I wanted to use different types just so I didn't have them using the same channel. Still will I benefit from using a dual core processor?

thanks

---

