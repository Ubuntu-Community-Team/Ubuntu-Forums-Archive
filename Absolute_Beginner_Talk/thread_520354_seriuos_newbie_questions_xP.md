---
title: "seriuos newbie questions xP"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by exido on 2007-08-08
ok i have a few question before installing can i add my mac adress?  can it support hp laserjet 1010 printer? :confused: can i load photoshop cs3 on it?  and with those partitions... you can select in what hdd disc you want to instal?l i have [c]'windows is in here' 90 gb and [d] 90 gb, what should i select to make the most apropriate for me? :popcorn: sory for asking dumb questions but i really gotta know :D

oh yeah and how can i change my monitor refresh rate in ubuntu? ;P

---

### Post by AlexenderReez on 2007-08-08
> **exido said:**
> ok i have a few question before installing can i add my mac adress?  can it support hp laserjet 1010 printer? :confused: can i load photoshop cs3 on it?  and with those partitions... you can select in what hdd disc you want to instal?l i have [c]'windows is in here' 90 gb and [d] 90 gb, what should i select to make the most apropriate for me? :popcorn: sory for asking dumb questions but i really gotta know :D

oh yeah and how can i change my monitor refresh rate in ubuntu? ;P

i don't know what kind of answers do you expect...if whether yes or no...then surely 'yes'.....and if 'how' is the question....tips and tutorial section can answer most of it....about photoshop,i don't sure is there linux version for it...but i guess wine can help you.....
and lastly...google is our friend :)

cheers....

welcome to ubuntu,king of distribution :)

---

### Post by BaffledMollusc on 2007-08-08
> **exido said:**
> ok i have a few question before installing can i add my mac adress?

Not sure what you mean. If you mean can you access the internet, then yes. If you want to bind your MAC address to a specific IP, that would be up to your router, not Ubuntu.

> can it support hp laserjet 1010 printer? :confused: 

It should work. See [http://www.linuxquestions.org/hcl/showproduct.php/product/2541](http://www.linuxquestions.org/hcl/showproduct.php/product/2541)

> can i load photoshop cs3 on it?

As far as I know, there is no version of Photoshop for linux. You might be able to run it under WINE; I don't know.

> and with those partitions... you can select in what hdd disc you want to instal?l i have [c]'windows is in here' 90 gb and [d] 90 gb, what should i select to make the most apropriate for me?

Yes, you can select whatever partition you want to install Ubuntu onto. For example, if you have two hard disks having Windows on one and Ubuntu on the other is no problem. If Windows is currently taking up all of your disk space, you can resize that Windows partition during the Ubuntu install process, and then create a new partition in the freed space where you can install Ubuntu. 

Needless to say, if you're going to play around with partitions, make sure you back up all your important data first!

>  :popcorn: sory for asking dumb questions but i really gotta know :D

No problem :)

> oh yeah and how can i change my monitor refresh rate in ubuntu?

I don't know - I use an LCD. Sorry!

---

### Post by B-777 on 2007-08-08
> **exido said:**
> oh yeah and how can i change my monitor refresh rate in ubuntu? ;P

Simply go to System>Preferences>Screen Resolution

You will be able to change your monitor refresh rate and resolution if need be.

---

### Post by thefoolisme on 2007-08-08
And if you did a search on this forum, I think you would find ample information about Photoshop and Wine.  I don't believe CS3 has successfully worked through Wine yet, but it's brand new.  If I'm not mistaken, there have been people who have successfully gotten CS and I think CS2 to work through Wine.  I would suggest researching through this forum, the Wine homepage ([http://www.winehq.org/](http://www.winehq.org/)), and Psychocats for all your partition questions.  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Hospadar on 2007-08-08
Also you should look into gimp instead of cs3, the latest version is very competitive with cs and I suspect you may find all of the features you want in a free software package if you are willing to learn the different software.

Also look into inkscape as a replacement for illustrator.

---

### Post by bwtranch on 2007-08-08
Gimp is an excellent program and has certain features that Photoshop does not. Photoshop will work under Wine with a noticeable decrease in performance. Good luck, it gets easier:)
But, you have to be patient, you can't learn it in one day and can be frustrating, but there are a lot of people out there that are willing to help. But you have to meet them something close to halfway.

---

### Post by Rhumbline on 2007-08-08
I used CS3 quite a bit & I intend to Give gimp a try. I've had a brief look at it & it seems fine. One of my concerns was the Wacom, would it work as good? . I installed the drivers with Synaptic and with some help from [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) and a little tweak of the config file my Wacom works OK and is pressure sensitive, but I havent figured out how to get the eraser on the pen to work. You,ve just got to have a little time & patience and be prepared for the learning curve!

---

### Post by Nedux on 2007-10-23
I had the same problem , I can`t set up the refresh rate, I tested ubuntu from the live cd, every think works just fine `, but it sets by default 1600x1200 with 75hz. I need it to work at 1600x1200 and 60hx
I won`t install ubuntu if i can`t fix this , and also  no visual effects working,`

---

### Post by GSF1200S on 2007-10-23
> **Nedux said:**
> I had the same problem , I can`t set up the refresh rate, I tested ubuntu from the live cd, every think works just fine `, but it sets by default 1600x1200 with 75hz. I need it to work at 1600x1200 and 60hx
I won`t install ubuntu if i can`t fix this , and also  no visual effects working,`

You can fix this.. What video card do you have (nvidia, intel, or ATI)? If its an Nvidia, just use the nvidia control installed with the glx drivers, and set the refresh rate there. If its an intel or ati, you can change the refresh rate in:

/etc/X11/xorg.conf

You can also adjust color depth and screen resolution here. Make sure to create a backup in case you make a mistake.. :)

---

### Post by Nedux on 2007-10-23
I have integrated intel video card. hmm it will work ? I need to keep 1600x1200 by 60hx.

---

### Post by GSF1200S on 2007-10-23
> **Nedux said:**
> I have integrated intel video card. hmm it will work ? I need to keep 1600x1200 by 60hx.

Yup.

sudo gedit /etc/X11/xorg.conf

Then edit the refresh rate section. Load the live cd and take a look before you install in case you have any questions...

---

### Post by Nedux on 2007-10-23
> **GSF1200S said:**
> Yup.
sudo gedit /etc/X11/xorg.conf
any questions...
sorry , how can I get to this location ? 
and the second question .. how do I set up my internet connection` ?
 I need to know this before installing `, :) thanks for helping me `,
I realy like ubuntu `, is some kind of love at first sight`,
I made a backup folder on my second partition`(D) is it ok ? or should I copy all my files on dvd`s ?

---

### Post by GSF1200S on 2007-10-23
you would type in the exact command i wrote at a terminal. Its easy enough to edit- just make a post if youre unsure.

Internet? Is it ethernet or wireless? Ethernet shouldnt be too hard at all. Wireless- it depends on the card. What card do you have?

It would be best to post the wireless thing in a different thread..

**EDIT** This community is all about helping :) so no prob!

---

