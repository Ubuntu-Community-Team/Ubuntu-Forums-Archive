---
title: "A future user's questions"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by krugman on 2006-07-25
Hello!

First post in the forum for me!
Indeed, I have recently heard about Unbuntu, and after having switched from IE to Opera then to opera to Firefox, I might be ready to make the big jump!
However, I have some questions, since I am not a typical user (well, who is?)

Indeed, I have some Windows apps that are totally critical for me, and I wonder how they translate in Unbuntu. For instance, as I am a chessplayer, I use Fritz 9 and Chessbase 9 on windows, so I wonder if they would work under Linux. For instance, I have heard about stuff called Wine, or Crossover Office that apparently allow you to use windows apps in linux...is that right?

Also, I use Mathematica for PhD, and I have read that there is an equivalent called Maxima if I recall properly, but I am not sure I want to learn a 'new language' again (I switched from Maple to Mathematica one year ago...). Can Mathematica work with Unbuntu? I am also a Tex user, but this is not going to be a problem although Winedt was quite user-friendly, compared to emacs for instance... 

Also, what about games? It seems that some games can work with Wine is that right? I am not a hardcore player, but there are games I particularly enjoy, like the forthcoming Dominions 3...I would really like to play this one! BTW, what abour ATI cards? I have an X1600, and I have read that Linux does not handle very well ATI cards...is that true?

Finally, do some of you use Unbuntu with a tablet pc? I have just got one also, and I was wondering if I could use Ubuntu. The thing is, I din't think there are writing recognition software in Ubuntu, so it is not very suited to tablet pcs...

well, sorry for so many questions;) but I feel a little lost for the moment!
Thanks in advance!:mrgreen:

---

### Post by richbarna on 2006-07-25
Hi krugman, you can take a look at my Blog if you want. I have tried to answer questions like yours, regarding software equivalents and hardware compatability. [Ubuntu Operating System]("http://linux-for-beginners.blogspot.com/2006_05_31_linux-for-beginners_archive.html")

Also, any criticism/ suggestions would be welcomed.

---

### Post by BoyOfDestiny on 2006-07-25
Hello and welcome.

I'm not familiar with some of the software, but I'll try and answer your questions.

[http://www.wolfram.com/products/mathematica/platforms/](http://www.wolfram.com/products/mathematica/platforms/)

There appears to be a version of mathematica designed for Linux. I believe other users here use it (or you can search ubuntuforums for mathematica), so I'm sure you'll get some more detailed responses.

As for running windows apps, you also have the option of dual-booting (but going cold turkey is more fun ;) ).

[http://www.winehq.com/](http://www.winehq.com/)

Check that site to see how well your software is supported. Maybe some people here will suggest some viable alternatives. For chess I've tried eboard, has online play and vs ai... Not sure if it'll fit your needs...

Google ubuntu on tablet pc

[http://tuxmobil.org/tablet_unix.html](http://tuxmobil.org/tablet_unix.html)

I'm not sure what model you have, but the results that come up may shed some light on what you can expect.

That said, good luck and hope you have a lot of fun.

P.S. Oh yeah ATi cards... Well earlier cards have open source drivers 2d and 3d, and I find the support great. Newer cards are at the mercy of the ati binary drivers, you'll need those if you want 3d acceleration on the high end cards... The best way to find out if you like it is to try it out I guess. :)

---

### Post by it.henrik on 2006-07-25
Mathematica for linux
[http://shum.huji.ac.il/cc/math42-linux.html](http://shum.huji.ac.il/cc/math42-linux.html)

chessbase 9 in wine seems to work
[http://ubuntuforums.org/archive/index.php/t-31659.html](http://ubuntuforums.org/archive/index.php/t-31659.html)

for windows games I have to point you in the direction of cedega 
[http://www.transgaming.com/](http://www.transgaming.com/)
but you should also take a look over here 
[http://gaming.gwos.org/](http://gaming.gwos.org/)

tablet pcs have very little support Im afraid

Hope you will like Ubuntu. The ubuntu spirit is great :)

---

### Post by krugman on 2006-07-26
Thx guys for the answers!

Right now I am trying to install unbuntu on my tablet, just to see!
But I tried to manually edit my partitions, and it seems that I have an hidden FAT32 partition that it does not like since it began to install and told me there was an error, so now I am doing the automatic partitioning...but I am still waiting...
once he told me he could not create enough space for installation...this is strange...I'll see...

---

### Post by krugman on 2006-07-26
Ok, in fact it works! It told me: "the test of the file system with type FAT32 in partition #3 of SCS1 (0,0,0) (sda) found uncorrected errors" but I asked him to continue and it did everyting right!

It seems that this partition contains my recovery data for Win XP tablet PC, and since I don't want to switch completely to ubuntu (at least on my tablet pc!), I will have to keep it!

So, now I guess I can try to install a few apps!

---

### Post by krugman on 2006-07-26
First problem: can't configure my wireless connection. I go to system->administration->Networking then I click on properties of my wireless connection. It sees my network, so I enter the WEP key, and it looks fine, but then, when I open Firefox I can't go anywhere...do I need a driver or something like that?
My laptop is an IBM X41t and I have a 2915ABG MiniPCI adpater as a wifi card.

---

### Post by krugman on 2006-07-26
Ok, so here is what it says:

fred@fred-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      unassociated  ESSID:"ALICE-0A0C15"
          Mode:Managed  Channel=0  Access Point: 00:13:CE:66:45:92
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

there was a problem with my access poitn which was not associated, but now its fine! But my network is still "unassociated"...
any ideas???

---

### Post by agc on 2006-07-26
A possible replacement of Mathematica (or matlab) that is
free and open source is SAGE:

[http://modular.math.washington.edu/sage](http://modular.math.washington.edu/sage)

It is written in Python, includes maxima, has plotting capabilities
from matplotlib, and supports algebra, geometry, number theory, etc.

Plus many of the developers (including me) use Ubuntu!

---

