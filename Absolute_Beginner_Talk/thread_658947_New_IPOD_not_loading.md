---
title: "New IPOD not loading"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by CheeseEatingBulldog on 2008-01-05
I have just bought an ipod for my gf (a 4 gb silver ipod nano video)

And can't get past the following error in gtkpod:
l Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.

I have tried rythembox and Amorak but simply cannot load anything.

can anyone help?

---

### Post by The Cog on 2008-01-05
Try googling for ipod and linux. I read recently that the latest ipods need updated library files, but I forget the details or where I read it.

---

### Post by seventhc on 2008-01-05
I use gtkpod and everything works fine. I use it for a shuffle and a nano, they are older ipods but gtkpod was the only program that worked without errors for me. Maybe give it a try.

---

### Post by CheeseEatingBulldog on 2008-01-05
And what does that entail? That one can't load the new ipods under linux?

---

### Post by CheeseEatingBulldog on 2008-01-05
> **seventhc said:**
> I use gtkpod and everything works fine. I use it for a shuffle and a nano, they are older ipods but gtkpod was the only program that worked without errors for me. Maybe give it a try.

gtkpod was my first try as I have an older 30gb video that works fine under it, but that won't load it either gives:

Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.

---

### Post by seventhc on 2008-01-05
I was just re-reading through this post and I think The Cog is correct about the new ipods. There might be a work around but of that I am not positive, but I'd be pretty certain that soon the new gen ipods will work. I think it is something they are working on fixing.

---

### Post by CheeseEatingBulldog on 2008-01-05
How do I make the ipod not read only, I can't write anything to it. Many sollutions give the possibility to write the firewire code to SysInfo file on the Ipod, but I keep on getting the error that it is read only.

gtkpod also can't create the file structure as it gives:

Error initialising iPod: Problem creating iPod directory or file: '/media/disk/iPod_Control/Music'.

This is so frustrating!

---

### Post by Espreon on 2008-01-05
I think before alternative iPod managers can do things with your iPod, at least 1 song needs to be transferred to your iPod via iTunes.... But I am not sure...
But try creating the directories yourself before you give up or try to use iTunes...

---

### Post by CheeseEatingBulldog on 2008-01-05
How do I make the ipod writeable????!!

---

### Post by Espreon on 2008-01-05
Wait? You can't even write to it?

Try double-cliciking the iPod icon on your desktop (I am assuming there is one) and try creating a new folder. If you can't do it you need iTunes to enable your iPod for disk usage...

---

### Post by CheeseEatingBulldog on 2008-01-06
I can;t create a folder and iTunes just won't load under wine. It starts (I think) and then just gives a blank screen.

EDIT
I got an older version of Itunes to run, but can't find my ipod mentioned anywhere, nor can I find an option to format / reset it....where the hell do you do it?

---

### Post by CheeseEatingBulldog on 2008-01-07
Right, all is well and solved, the sollution:

Format iPod on a windows machine, upgrade gtkpod to the newest glibpod (or something) and connect iPod. Open gtkPod and set new repository / ipod to 3g nano silver. Load Pod and upload music (don't be too zealous when adding music as gtkpod sometimes crashes out, so add say a a few gigs at a time and save before continuing). Even album art works fine, although that does take more space than I expected.

Thanks for the help here.

---

