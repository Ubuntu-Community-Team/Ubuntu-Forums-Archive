---
title: "Can't Start X After Power Outage"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-04-28
Hi guys,

I'm in quite a fix here, so I'd really appreciate any help I can get.

Last night I was using my PC through th heavy rains (so far my house hasn't had anything fried by lightning yet). Then as usual, there was lightning and a power outage.

When I woke up this morning (after restoring the power to the house), and tried to turn on my pc, I could boot ubuntu (had the ubuntu logo, and the progress bar etc). But when it got to the login screen part, there would be no video output. My LCD would say "no signal". But if I typed in my user name and password (blindly), I could login, and hear the login sounds which means I could login to my deskop. :(

I tried booting from recovery mode, and startx, but that didn't work either. I thought the graphic card might be having problems, so I tried running the Feisty LiveCD, which I could boot into the desktop, and fortunately access my data/home folder with "gksudo nautilus". 

I'm not sure whether its a hardware failure(I hope not) or a configuration issue. The fact that it happened straight after a power outage would point towards a hardware failure (IMO), but its funny that I would be able to boot into a GUI desktop from the LiveCD. 

Any suggestions guys? I'm realli worried about this, mainly cause this is the first day (of about 2 weeks) that I don't have my backup hard disk, where I normally backup my data. Sent the stupid thing for warranty, so I don't have any backups of my data :( 

Any way to diagnose, resolve this?

Much thanks in advance !
Kinson

---

### Post by LuisGMarine on 2007-04-28
I had the same problem under windows and it turned out to be my video card got friend.  I was able to see the windows logo and everything, but when I got to the login screen my LCD too said that there was no signal.  Do you have any old video card that you know works that you can swap out to test if it works or not?  For me I didn't have one, I had to pay some tech guy $50 U.S Dollars to come over and just swap the video card to find out that was the problem.

---

### Post by kinson on 2007-04-28
It could be the case. Just curious if my video card was toasted, whether I would be able to boot into the LiveCD GUI desktop though( I currently *can* boot into the LiveCD GUI desktop. ).

Of course, if its a hardware failure, anything can happen. Thanks for the suggestion. Fortunately I deliberately picked a board that uses an AGP port, and I have a couple of GeForce 2's sitting around, I'll give them a try when I go home though, thanks :)

I'm outta the country at the moment..damn, this had to happen the morning I was leaving :( Anyways, I'll give it a try when I get home on Tuesday, thanks :)

In the meantime, any other views and suggestions are welcome :)

Thanks,
Kinson

---

### Post by Loki-uk on 2007-04-28
Have you tried roconfiguring the xserver?

Boot to a console and use sudo dpkg-reconfigure xserver-conf

See here > [http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm)

Fialing that you may need to reinstall x or your grappics card driver  as it may have been corrupted by the power outage.

Loki

---

### Post by kinson on 2007-04-28
Sounds like a good idea, I'll give that a try when I get home, thanks :) 

Hope that solves it, as its probably the most painless solution. No pain = my gain :P

Now I'm just worried that my pc might have some weird hardware failure that I have no way of detecting :( (And not way to check/determine it).

Cheers,
Kinson

---

### Post by Loki-uk on 2007-04-28
No if your PC is booting fine off the live CD the most likely problem is that a file got corrupted when the power wont out. I doesn't sound like a major problem if you can still boot into fiesty and hear the sound from your HD and the Live CD boots then I'd be supprised if you had any serious hardware problems. If the power went out when the disk was being written to then you might have some small corruption of a file or of the file tables. You might want to do a disk scan with 'fsck' just to be sure.

Loki

---

### Post by kinson on 2007-04-28
Sounds good, thanks :)

I was worrying my socks off this morning, cause I didn't have any backups of my data inside :)

I'll do what you suggested :) Reconfigure xorg, and scan disk :)

Thanks again :)

I'll post the updates here :)

Cheers,
Kinson

---

### Post by kinson on 2007-05-02
> **Loki-uk said:**
> Have you tried roconfiguring the xserver?

Boot to a console and use sudo dpkg-reconfigure xserver-conf

See here > [http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm)

Fialing that you may need to reinstall x or your grappics card driver  as it may have been corrupted by the power outage.

Loki

Thanks a lot :) I'm happy to let you guys know, that after poking around a bit with the "sudo dpkg-reconfigure xserver-xorg" command, I've managed to get my GUI desktop back :) It was probably as you said, just a corrupted settings or something :)

thanks a lot ! :D

Btw, you mentioned "sudo dpkg-reconfigure xserver-**conf**", and that wasn't a valid command I think. 

Alls well that ends well though :D

Cheers,
Kinson

---

### Post by Loki-uk on 2007-05-02
Hi yeah sorry its xserver.xorg isn't it? I keep doing that I think I must always be thinking about the file it writes which is xorg.conf.  Anyway I'm glad it got you sorted in the end :)

Loki

---

### Post by kinson on 2007-05-02
> **Loki-uk said:**
> Hi yeah sorry its xserver.xorg isn't it? I keep doing that I think I must always be thinking about the file it writes which is xorg.conf.  Anyway I'm glad it got you sorted in the end :)

Loki

yeah, its "sudo dpkg-reconfigure xserver-xorg" :p But as long as its sorted out, I'm happy :) thanks again.

Cheers,
Kinson

---

