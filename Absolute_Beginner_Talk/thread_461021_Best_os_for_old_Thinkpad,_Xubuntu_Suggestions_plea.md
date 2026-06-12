---
title: "Best os for old Thinkpad, Xubuntu?? Suggestions please..."
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by SanjoEel on 2007-06-01
OK folks, here's what I want to do. I have an old IBM thinkpad 380XD with 64MB of ram. I would really like to breathe some new life into this so that my Mom can have a computer to surf with, that's really going to be it's ONLY function, a net surfer. I need some suggestions on what OS would be best for this dinosaur. My main issue is the nic card. My Mom can only get dial-up where they are at. So, I NEED nic card support so she can dial up. I somehow got Damn Small working and cable modem works fine but could not get anywhere with getting that nic card to work. Next I went for Xubuntu Edgy and, I couldn't even get it to connect with a cable much less dial up. So, I decided to go with Ubuntu just to see if it would work. It does, but it's VERY slow, and I haven't tried to use the dial up yet. So, how would you set this laptop up to surf? Go back to Xubuntu (Feisty this time?) Is there another distro that's really light and will recognize/use this (Xircom) nic? Remember, all I need it to do is dial-up and surf. You suggestions are **greatly** appreciated. :D I know this thing is an ancient relic, but I just can't afford to buy her a newer laptop right now. :(

---

### Post by kevinlyfellow on 2007-06-01
> **SanjoEel said:**
> OK folks, here's what I want to do. I have an old IBM thinkpad 380XD with 64MB of ram. I would really like to breathe some new life into this so that my Mom can have a computer to surf with, that's really going to be it's ONLY function, a net surfer. I need some suggestions on what OS would be best for this dinosaur. My main issue is the nic card. My Mom can only get dial-up where they are at. So, I NEED nic card support so she can dial up. I somehow got Damn Small working and cable modem works fine but could not get anywhere with getting that nic card to work. Next I went for Xubuntu Edgy and, I couldn't even get it to connect with a cable much less dial up. So, I decided to go with Ubuntu just to see if it would work. It does, but it's VERY slow, and I haven't tried to use the dial up yet. So, how would you set this laptop up to surf? Go back to Xubuntu (Feisty this time?) Is there another distro that's really light and will recognize/use this (Xircom) nic? Remember, all I need it to do is dial-up and surf. You suggestions are **greatly** appreciated. :D I know this thing is an ancient relic, but I just can't afford to buy her a newer laptop right now. :(

If it works with ubuntu, just press ctrl-alt-f1 and then apt get the needed desktop.  

Also you could give puppy linux a shot.

---

### Post by lazyart on 2007-06-01
Xubuntu is going to be a tough fit there.  MAYBE fluxbuntu.  Take a look at [DeLi]("http://delili.lens.hl-users.com/") instead.

---

### Post by SomethingCronic on 2007-06-01
You could try Xubuntu. I should imagine it would work and be half decent for basic internet access.

You may want to install ubuntu server, and then do an

```
apt get install xserver-core
```


```
sudo apt-get install fluxbox
```

You'll have the most basic system then that has a windows manager so you can use firefox. Configuring it for dial up access is something I'm not familiar with anymore :)

---

### Post by mooscape on 2007-06-01
Try Puppy Linux. It is worth having on (business card sized, about 50MB) cd at all times. It can bring old computers back from the dead and runs in ram so you can use a system without a working hard drive or OS on the drive.  (If you have less than 128 Mb RAM you must be able to see a hard drive to allow for a swap partition.) You must burn the cd in ISO mode so that it boots directly.

Check out:  [http://www.puppyos.com/](http://www.puppyos.com/)  and  [http://www.puppylinux.org/](http://www.puppylinux.org/)   If you have any problems check the puppy forums.   

If you really want to blow your mind, play with the puppy on a powerful desktop. It is EXTREMELY fast...  Enjoy! :lolflag:

---

### Post by SanjoEel on 2007-06-01
Wow, guys, thanks for the *FAST* responses and suggestions. I am going with Puppy. It is installed already (very quick and painless) and now I need to troubleshoot my connection. Thanks again!

---

### Post by tgalati4 on 2007-06-01
What is your nic-card?  If you can get any Linux to work with it, then you should be able to get DSL to work as well, and it will probably be the fastest.  You can load Opera (from myDSL) and that makes for a decent browsing machine.

You can get used 3COM pcmcia cards cheap these days.  Better yet, set up wireless for her so she can surf in the garden.

---

### Post by SanjoEel on 2007-06-11
Hey guys. Just wanted to say thanks for the recommendations. I went with Puppy and first, let me say that it is fast on this old thinkpad! Looks good too. I would def recommend it for older stuff. I had a few problems with dial up but the Puppy forum is great and we got it working. Thanks again!

---

### Post by lazyart on 2007-06-11
Thanks for the follow up.

---

### Post by thevenerablez on 2007-06-11
Maybe adding another 64MB of RAM would add more life to the machine. RAM that small is inexpensive these days. Check [www.newegg.com](www.newegg.com) and you can probably get away with spending less than $10. Half a gig is $20: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820161014](http://www.newegg.com/Product/Product.aspx?Item=N82E16820161014). This may help standard ubuntu to run faster.

_zach

---

### Post by bodycoach2 on 2007-06-11
We use Puppy Linux on any machine older than 300 MHz, or under 128 MB ram. I'd recommend dban the hard drive (Darik's Boot & Nuke), and run Puppy from the CD. Use the hard drive to save settings and files. Puppy seems much faster when running from the CD instead of those older hard drives. Also, when you go to upgrade the OS, you just pop in the newest CD.

---

### Post by SanjoEel on 2007-06-29
Thanks, but this thing runs great on the hard drive. I think it's faster than it ever was with windows. My parents just wanted to surf and email and maybe wp, and it is working great for that! After all the troublehooting and tweaks I had to do to get it running perfect I think I'll leave well enough alone! ;)

---

### Post by hyper_ch on 2007-06-29
well, I would have suggested DSL :)

But good to hear that an up-to-date linux is running faster than windows ever did and it's more secure :)

---

### Post by SanjoEel on 2007-06-29
Yeah, I like DSL as well. I tried that one first but I like puppy better because it looks nicer and runs really good.

---

