---
title: "Deleting Apple_Bootstrap partition"
date: 2007-02-18
forum: Apple PPC Users
---

### Post by iAndy on 2007-02-18
Hey.

I've come to put Ubuntu (Feisty this time) back on my PowerBook 12" (again!), which was easy second time around.  I tried to installl Beryl and tweak it to work, but in doing so I made Ubuntu fail to log me on correctly.  As soon as Gnome loaded Beryl, it gave me a black screen with whtie writing on and logged me off.

I deleted my Ubuntu partition again (as I have OS X still there) and left it as free space and came to reinstall Ubuntu (Feisty) again, which went ok, but now whenever I boot up into Linux it gives me the very first initial UBUNTU splash screen, (with the scrolling progress bar at the bottom...all in horrible colours by the way, because of the poor graphics card support!) and it freezes there for a few minutes and then reboots my entire PowerBook.

Now what I am wondering is, is it something to do with the Apple_Bootstrap partition that I DID NOT delete, as I was unsure of how safe it was, I don't want to muck booting up into my Mac OS X partition.  What I want to do is start again from scratch, do a nice clean install (and try not to mess Beryl up this time!)  So...after this long and winding post, my main question is...

Is it safe for me to delete the Apple_Bootstrap partition that Ubuntu created?  
Will it leave OS X alone and still make me able to boot up into OS X fine with no problems as if Linux was never there?  I know it holds yaboot, but I just want to be sure.  Last time I played around with bootups on my Mac I lost everything!  So...not making that mistake again!

Thanks all!

---

### Post by grazie on 2007-02-18
There's no point in deleting the boostrap partition as it's working just fine. I don't know what version of Feisty you are using, but it seems like you're getting a kernel oops. You can view the boot messages by entering alt+F1. Maybe you'd be better with the stable Edgy release and updating when Feisty is released in April?

---

### Post by iAndy on 2007-02-18
Thanks.

I'll check the boot messages

Do I push alt+F1 before it reaches the boot screen or while it is on?

I'm using Herd 4 of Feisty.

Ye maybe I will try Edgy again.  It was the fact that Feisty did work, and then didn't!

Thanks a lot!

---

### Post by Pappa_Smurf on 2007-02-19
Also, you can fix the problem with horrible graphics support by compiling a custom kernel.  It will upgrade your graphics from horrible to not so bad.

At least the startup screen will look pretty!

---

### Post by iAndy on 2007-02-20
Ta guys. 

I've gone back to Edgy and things seem ok without deleting the bootstraps, however I now have 2 bootstrap partitions, which isn't exactly that untidy as they don't even take up 1Mb!

Just for future reference, would it still be ok for me to delete those bootstrap partitions safely if I was to delete my Ubuntu partiton again?

Hmmm...recompiling a custom kernel, sounds like fun!  Am going to have to read into that one and see what I can do.

Thanks!

---

