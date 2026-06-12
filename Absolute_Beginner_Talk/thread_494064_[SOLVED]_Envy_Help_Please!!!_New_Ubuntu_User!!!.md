---
title: "[SOLVED] Envy Help Please!!! New Ubuntu User!!!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by KuroRai on 2007-07-06
iWas having problems wiht my graphic card driver, and someone told me to install envy...

[http://ubuntuforums.org/showthread.php?t=493996](http://ubuntuforums.org/showthread.php?t=493996)

so iInstalled it, let it to the conf files and what not, then on tehrestart, it crashes!!!

so iLog onto my windows partition and check the site, it showed me how to get into the text version thingy of envy,

so iGo onto it, delete it, still doesn't wrk, so iDid the clean delete, still no wrky! so iReinstalled it and came here... HELP PLZ :'(

---

### Post by KuroRai on 2007-07-06
*** by "it crashes" iMean X Server  fails to start....

---

### Post by KuroRai on 2007-07-06
oh yes, andother bit of info iFound while searching the site... iDidnt enable extra repitories, what ever those are...

[http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by Wiebelhaus on 2007-07-06
Ubuntu will pick it up for you natively by applying desktop effects , it will then prompt you to install restricted drivers and then to restart , this will take care of your video drivers , but if your a noob and you haven't customized ubuntu yet and you have effectively killed it, just reinstall , it only takes 20 minutes or so.

---

### Post by Raineer on 2007-07-06
Please stop shouting in most of your posts.

If I were you I would wait until X crashes, if you are not at a command prompt then press Ctrl-Alt-F2 and login with user and pass.

At the command line type:
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the menus, try selecting "Nvidia" as your driver and starting X up again with ```
startx
```

If it still crashes run the same dpkg command again and try the "nv" driver. If THAT doesn't work, use the "vesa" driver.

One of those 3 selections should get you running.

---

### Post by lbelloq on 2007-07-06
Seconded. If you have important info to recover just use the LiveCD to access your Linux partition and copy the files somewhere else. And if you did install Ubuntu the 1st time without problems, go for a 2nd time.

---

### Post by KuroRai on 2007-07-06
if you checked out the above post,m you would ahve found out iDid do that, but those drivers cut off sound from my comp. also it stops video from playing, thus no media player frezzes when it trys to play any media...

---

### Post by Calash on 2007-07-06
Ok, this may just be sill of me, but why are people suggesting a full reinstall?  This is nothing more than a xorg problem easly fixed by the automated method already posted, or by editing the text file if you want to learn that part.

Hardly the stuff that would require a reinstall, even on Windows..there you would just boot into safe mode and remove/reinstall the driver.  Same concept here except it is a bit more typing.

---

### Post by lbelloq on 2007-07-06
We're lazy bums, thats why LOL.

---

### Post by Raineer on 2007-07-06
> **KuroRai said:**
> if you checked out the above post,m you would ahve found out iDid do that, but those drivers cut off sound from my comp. also it stops video from playing, thus no media player frezzes when it trys to play any media...

I did read that thread but I can't help you have 3 (or more) threads for one problem, I don't feel like reading them all..  Maybe you should find out why your video drivers are causing your sound to cut out, it could be that it's an application problem.  Have you tried VLC, or which media programs are you running?   It might help to just bump the original so people can see what has been done.

---

### Post by sab0403 on 2007-07-06
I think before playing media files or other things, it'd be healthy to install a generic driver, so X loads normally again, then install your appropriate driver correctly.

What model of video card do you have?

---

### Post by KuroRai on 2007-07-06
nVidia GX 4000

---

### Post by KuroRai on 2007-07-06
but how do iRestore the old xorg file?!?!!?

---

### Post by KuroRai on 2007-07-06
anda ctully, there are only 2 threds, teh original, which casued teh envy problem,a dn this one, to solve the envy problem

---

### Post by sab0403 on 2007-07-06
nVidia...

Well, I'd suggest using Method 1 of [this guide]("http://doc.gwos.org/index.php/Latest_nvidia_feisty"), because it goes step by step with you, so you know what you're doing.

I have an nVidia GeForce4 440MX, and it worked great for me.

---

### Post by sab0403 on 2007-07-06
To restore the old xorg.conf file, get to the command line and type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by sab0403 on 2007-07-06
As indicated before, choose either the "nv" or "VESA" options.

---

### Post by Raineer on 2007-07-06
> **KuroRai said:**
> anda ctully, there are only 2 threds, teh original, which casued teh envy problem,a dn this one, to solve the envy problem
[http://ubuntuforums.org/showthread.php?t=493608](http://ubuntuforums.org/showthread.php?t=493608)
[http://ubuntuforums.org/showthread.php?t=493996](http://ubuntuforums.org/showthread.php?t=493996)
[http://ubuntuforums.org/showthread.php?t=494064](http://ubuntuforums.org/showthread.php?t=494064)

Only posting it because you don't even take the time to spell correctly. Good luck with xorg

---

### Post by KuroRai on 2007-07-06
do you realise that of the 3 links you gave, one was the old one which was solved... this is a new problem, and of the other two, well iKinda said that there are 2 posts on my last statement about this didn't i?

---

### Post by KuroRai on 2007-07-06
THANKS SAB, it took me a while, but it wrks now!!! thank you soo much!

---

### Post by Wiebelhaus on 2007-07-06
> **Calash said:**
> Ok, this may just be sill of me, but why are people suggesting a full reinstall?  This is nothing more than a xorg problem easly fixed by the automated method already posted, or by editing the text file if you want to learn that part.

Hardly the stuff that would require a reinstall, even on Windows..there you would just boot into safe mode and remove/reinstall the driver.  Same concept here except it is a bit more typing.
 because I got the feeling that if he killed the xserver & his sound drivers and after 15 threads  i didn't feel like making it worse.

---

