---
title: "[SOLVED] Can this computer run Ubunto or is it to old like me"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by valleyman7 on 2006-09-24
:confused: OK folks I will try not to pester anyone on this forum, but I know from time to time I will have a question or two or maybe three. I will always try to find the answers here first before bugging you folks. I want to cram as much technology as I can before I go to the big computer land. My question is will my old Dell Latitude CPi  Pentiun II 2.33MHG (1999 Old Iknow) with 256mb ram run this version 6.06 LTS? I hate to trash this old computer as it has been very loyal to me. I just upgraded the ram and wow I didn't EDO ram was so costly, so all the more to continue using it. This is not my main computer it my learning toy. I have a Dell 9300 Inspiron, but I would prefer to use Ubuntu on my toy. I would really appreciate your advice. Maybe it's to old to run Ubuntu and that is why I have not been able to get the wireless card to connect. I will keep trying though. The card is a Linksys WPC54G and it worked great when the OS was Win2000Pro. I will be waiting to see if the old computer was worth the upgrade. Maybe I need to consider an up grade for the CPU. Thanks to any and all who may read and respond. By the way I did purchase the new book. The Official Ubuntu Book.
Lyle Hensley:KS 
[email]golddigr@gmail.com[/email]
Enjoying Every Breath
Retired  US Army
1957 - 1978

---

### Post by happy-and-lost on 2006-09-24
It certainly will run Ubuntu.
I got Ubuntu running on a 100mhz P1 with 32mb ram once, albeit very slowly!

If it seems a bit slow, use Xubuntu.

EDIT: NO computer is too old for Linux, in fact, the older ones have better hardware support than the newer ones.

---

### Post by valleyman7 on 2006-09-24
Me again:( 
Well this is about my Fourth or fifth attempt to install Ubuntu, Xbuntu and Freespire. And today I bit the bullet and cleaned the HD ran spinrite did a mem test. and started a nice clean install it got as far as the keyboard option and locked up I also purchased a new DVD Drive Bay as the old one was just for CD and sounded like a bucket of bolts. Try  try try .:confused: :confused: 
Also am I supposed to use Reply to follow up on my previous post?

Lyle Hensley:KS 
[email]golddigr@gmail.com[/email]
Enjoying Every Breath
Retired  US Army
1957 - 1978

---

### Post by happy-and-lost on 2006-09-24
Are you using an Ubuntu CD you burned from an .iso yourself?

---

### Post by valleyman7 on 2006-09-24
Thanks Happy and Lost. That is me:D

---

### Post by valleyman7 on 2006-09-24
No I am using the DVD that came with my book. Thanks for your help:KS

---

### Post by in2media on 2006-09-24
ive just installed ubunyu on a p3-450 processor with 128 sdram and although its not as fast i hoped it would be its fine for what i need
hope this helps a little

---

### Post by in2media on 2006-09-24
ive just installed ubuntu on a p3-450 processor with 128 sdram and although its not as fast i hoped it would be its fine for what i need
hope this helps a little

---

### Post by happy-and-lost on 2006-09-24
If you find Ububtu is going too slowly

```
sudo apt-get install xubuntu-desktop
```

When you get to the login screen, change the session type to XFCE and you're away :)

---

### Post by bulldog on 2006-09-24
Boot the DVD and see if you make it to the desktop.:D

---

### Post by Asham on 2006-09-24
> **bulldog said:**
> Boot the DVD and see if you make it to the desktop.:D

heh, yeah!
I tried to install **U**buntu on an old machine, a Intel Penthium 450 MHz along with 256 MB of RAM -- it halted somewhere while it was reading data from the CD. It didn't even make it to the UI. **X**Ubuntu installed fine though.

---

### Post by K.Mandla on 2006-09-24
> **valleyman7 said:**
> My question is will my old Dell Latitude CPi  Pentiun II 2.33MHG (1999 Old Iknow) with 256mb ram run this version 6.06 LTS? I hate to trash this old computer as it has been very loyal to me. 
It should run fine, but going with Xubuntu is the best idea. 233Mhz is a little bit slow for straight Ubuntu, because the Gnome desktop that comes with Ubuntu taxes a computer's resources more than others.

Xubuntu is the way to go with that machine. If that's still too slow, there are other, even lighter desktops you can try. ;) Have fun!

---

### Post by valleyman7 on 2006-09-24
Bull Dog I did get to the desk to and while I was there I played around trying a few different things like getting may wireless to work. No luck so then I clicked the install to go ahead and install. I know that it's very slow and I got as far as installing the keyboard and that's when it decided to lock up. I had waited as long as I could see the I will call it the wheel going then I noticed that it had stopped responding. The mouse locked and the only option was to hard shut down. So that is where I am at this point. I had the same results with Xbuntu. I might also mention that I have made quite a few of these CD's and I have even slowed them down to 2X when making them I am lost. :confused: 

Lyle Hensley
[email]golddigr@gmail.com[/email]
Enjoying Every Breath
Retired  US Army
1957 - 1978

---

### Post by JohnW on 2006-09-24
Valleyman, Here's a thread that should convince you it's not too old (and neither are you! :) ).

[http://ubuntuforums.org/showthread.php?t=259901](http://ubuntuforums.org/showthread.php?t=259901)

I'd recommend getting the Xubuntu alternate cd which is a (nice) text-mode installer, rather than the pretty gui installer that I've found gets really slow on a machine with limited ram (around 128Mb).

---

### Post by valleyman7 on 2006-09-24
Thanks John I will try Xbuntu again.

---

### Post by xpod on 2006-09-24
Try chosing "safe graphics mode "at start up.
That did it for me on a not as old as yours pc but you never know..mines used to freeze at the last stage too

If you`ve already gave up on ubunto Xubu should do the trick but theres many many different disto`s and there will be one to suit your systems needs...
Just a case of finding it....One of the ubunto family should go on it

---

### Post by valleyman7 on 2006-09-24
I tried installing Xbuntu as suggested and used the graphic install, and was able to load the live desktop. So I clicked on the install icon and nothing happened. So I used the drop down list System installe and this is the error I received.

      " Missing Command to run" 
Any suggestions?:( 

Lyle Hensley:KS 
[email]golddigr@gmail.com[/email]
Enjoying Every Breath
Retired  US Army
1957 - 1978

---

### Post by szf on 2006-09-24
I've installed Ubuntu 6.06 LTS successfully from CD-ROM on a Pentium II 350MHz, 384 MB RAM, 10GB Matrox 5400RPM IDE HDD, Matrox G400 AGP card 16 MB. There were a couple of minor gliches in the partitioning with the installer (it appeared to forget the root ('/') partition, but third time was the charm.

It runs the default Gnome Desktop. Boot is slow, but otherwise perfectly usable.

---

### Post by jimrz on 2006-09-24
> **valleyman7 said:**
> Bull Dog I did get to the desk to and while I was there I played around trying a few different things like getting may wireless to work. No luck so then I clicked the install to go ahead and install. I know that it's very slow and I got as far as installing the keyboard and that's when it decided to lock up. I had waited as long as I could see the I will call it the wheel going then I noticed that it had stopped responding. The mouse locked and the only option was to hard shut down. So that is where I am at this point. I had the same results with Xbuntu. I might also mention that I have made quite a few of these CD's and I have even slowed them down to 2X when making them I am lost. :confused: 

Lyle Hensley
[email]golddigr@gmail.com[/email]
Enjoying Every Breath
Retired  US Army
1957 - 1978

you might try it with the "alternate" cd. it uses the old text based installer and does not foul up on older equipment the way the "live" cd with it's graphical installer seems to

---

### Post by RRS on 2006-09-25
Second the recommendation to try the alternate CD for installation.

One of my machines has only 186 ram but runs Dapper fine. I couldn't install from the desktop cd though.

After installing you may have to use a wired connection to download drivers for your wireless card. There's allready several threads  on setting up wireless so it's likely someone with the same hardware has the answers for you to solve that problem. Sorry, I don't use wireless.

---

### Post by EddieA on 2006-09-25
Welcome from another relative newcomer!
Slightly off topic - referring to your first post
Were you really serving in the forces in 1957? I thought I was an old 'Newbie' (hate that term) but I was a mere sprog then!!
Also when we do finally shuffle off to the big Computer let's hope the OS in the sky gets us all installed nicely.

---

### Post by David Corrales on 2006-09-25
> **jimrz said:**
> you might try it with the "alternate" cd. it uses the old text based installer and does not foul up on older equipment the way the "live" cd with it's graphical installer seems to

I gotta say this is true. The thing is, since the livecd eats up your ram, installing will be a pain from the desktop. It's best to use the text based install.
Actually, if you edit the boot options of the livecd you'll see it creates a 100mb ramdisk by default. That's a huge hit if you have only 256mb.

---

### Post by CaveRat on 2006-09-25
First and foremost I want to say welcome to the land of "free as in beer" Linux. Like you I am not a sprig any more. At work and elsewhere I am known as Old Man. LOL I hope you get at least Xubuntu loaded. This distro is the bomb, and if it were not for all the youngster geeks in this forum, I would have givin up long ago. Because of them, my MS box has sat collecting dust for the last month and a half.

---

### Post by ske1fr on 2006-09-25
I second all the suggestions that you try Xubuntu installed from the "alternate" version CD.  This approach has breathed new life into a 300 MHz Pentium 2 laptop with just 128 MB of RAM.  Once you've got that working you may be able to install the Gnome window manager and applications as add-ons, but Xubuntu should get you started.  

Heck, even the sound works on mine now :biggrin:

---

