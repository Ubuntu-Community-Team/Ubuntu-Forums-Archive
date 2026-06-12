---
title: "[SOLVED] installed restricted ATI display driver now no monitor"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Shadowmeph on 2008-02-06
I got fed up with things from my fiesty to gutsy upgrade ATI driver problems  so I downloaded gutsy and did a fresh install then updated , I then turned on the accelerated driver rebooted but now I have no monitor, I did a quick search and found a post that had this in it 
> Cofigure your xserver. Once IN the system, you can fix things.
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Accept most defaulrs, choose 'vesa' as the driver
Then: startx
Or sudo /etc/init.d/gdm start
Go to your cards site and figure out what driver you need or can use.
Come back if you need more help.
I only go to > sudo dpkg-reconfigure xserver-xorg but i kept getting an error saying unknown command so I am not sure of what to do now

---

### Post by talsemgeest on 2008-02-07
Don't skip the  sudo /etc/init.d/gdm stop. 
Even though you screen goes black, the GUI is still loaded. You need to stop it before you can reconfigure.

Hope this helps :)

---

### Post by kesman on 2008-02-07
I suggest you to use a software called envy to install ATI drivers. You can find it from google.

---

### Post by talsemgeest on 2008-02-07
Envy still isnt 100%. The last time that I tried using it I ended up having to reinstall because it messed up my configuration

---

### Post by Shadowmeph on 2008-02-07
this is the first thing I put in sudo /etc/init.d/gdm stop and iot did its thing but when I typed in this sudo dpkg-reconfigure xserver-xorg it would give me a message of unknown command :(

 before I did the reinstall I tried envy and it didn't work, as of now I can't get see anything except from my tv that is hooked up also but that screen just keeps rolling like I have to set up the country ( nt what ever it is) or something either way I cannot see my desk top lol

---

### Post by obscur156 on 2008-02-07
ATI driver are just a pain on ubuntu,not stable and had to reinstall many times because of driver messing up the Xconf.

I am still a noob so reinstalling was my best option since it takes only 20 minutes.

I hope ATI will give us better driver for linux or i will go for NVIDIA next time.
I am not gonna go back on winblows because of that.Regards

---

### Post by phr0ze on 2008-02-07
type 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf

Then find the line that names the driver and set it back to the default ati or put in vesa to be sure. Also inspect the resolution settings to be sure those are correct. If you post your file, we can help.

John

---

### Post by Shadowmeph on 2008-02-07
> **phr0ze said:**
> type 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf

Then find the line that names the driver and set it back to the default ati or put in vesa to be sure. Also inspect the resolution settings to be sure those are correct. If you post your file, we can help.

John

thank you for reply I will try this . I just remembered ( and should have mentioned this from the beginning sorry about that )when I try to boot in my LCD monitor gives me an error saying it cannot display 33 khz/30Hz I think the lowers my LCD monitor to go is 60mh this is probably the actual problem

---

### Post by Shadowmeph on 2008-02-07
ok I tried this and it gave me a bad command error when I typed in sudo cp /etc/X11/xorg.conf/etc/X11/xorg.conf.bak

---

### Post by erfahren on 2008-02-07
Shadowmeph - I don't know if you're typing in the same thing here as you are in the command line, but you're leaving out spaces ...
```

sudo dpkg -reconfigure xserver-xorg

```
need a space between "dpkg" and the "-reconfigure" option in that
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
in that command you are copying the xorg.conf file and naming the copy "xorg.conf.bak" - there should be a space between the original and copy

in case you're interested - more info on dpkg -reconfigure xserver-xorg
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
[http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

doing what **phr0ze** mentioned should work though.

---

### Post by Shadowmeph on 2008-02-07
> **erfahren said:**
> Shadowmeph - I don't know if you're typing in the same thing here as you are in the command line, but you're leaving out spaces ...
```

sudo dpkg -reconfigure xserver-xorg

```
need a space between "dpkg" and the "-reconfigure" option in that
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
in that command you are copying the xorg.conf file and naming the copy "xorg.conf.bak" - there should be a space between the original and copy

in case you're interested - more info on dpkg -reconfigure xserver-xorg
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
[http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

doing what **phr0ze** mentioned should work though.

ok I will try this and thank you again for your replys to my posts :)

---

### Post by lavinog on 2008-02-07
> **obscur156 said:**
> ATI driver are just a pain on ubuntu,not stable and had to reinstall many times because of driver messing up the Xconf.

I am still a noob so reinstalling was my best option since it takes only 20 minutes.

I hope ATI will give us better driver for linux or i will go for NVIDIA next time.
I am not gonna go back on winblows because of that.Regards

I think that the restricted drivers in the repositories are way out of date...the current drivers work great.
AMD has really changed ATI's attitude about linux drivers...they have a goal of releasing a new driver every month.

This is a great instruction on how to install the most current driver:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

---

### Post by kesman on 2008-02-07
WHOAH THERE!
There's definately NOT a space between dpkg and deconfigure. dpkg-reconfigure and dpkg -reconfigure are two WAY separate commands. If you get complains about dpkg-reconfigure not being a command, you have mistyped it somehow.

---

### Post by Shadowmeph on 2008-02-07
ok I couldn't get it to work so I reinstalled no I am paranoid to use the restricted drivers "ATI accelerated graphics driver lol even though I think that I will definately need them if I want to get into gaming and also hooking up my TV so I can watch my downloaded videos .
> lavinog wrote
I think that the restricted drivers in the repositories are way out of date...the current drivers work great.
AMD has really changed ATI's attitude about linux drivers...they have a goal of releasing a new driver every month.

This is a great instruction on how to install the most current driver:
I looked at this guide but I am not sure if I should do the manual install or what any suggestions?

---

### Post by Shadowmeph on 2008-02-07
> **kesman said:**
> WHOAH THERE!
There's definately NOT a space between dpkg and deconfigure. dpkg-reconfigure and dpkg -reconfigure are two WAY separate commands. If you get complains about dpkg-reconfigure not being a command, you have mistyped it somehow.
thank you for your reply I finally just got poed and reinstalled it this time I download Envy and let it do all of the work which seems to be working this time, the reason it worked ( IMHO) was because I had installed Gutsy right from the beginning unlike last time I updated feisty to gutsy which seemed to create huge problems. I would like to thank everyone for there help and patience 
I know how irritating it can be helping a newbie because I used to help allot of peeps with Windows things and it used to get irritating repeating myself to everyone.

---

### Post by erfahren on 2008-02-07
> **Shadowmeph said:**
> thank you for your reply I finally just got poed and reinstalled it this time I download Envy and let it do all of the work which seems to be working this time, the reason it worked ( IMHO) was because I had installed Gutsy right from the beginning unlike last time I updated feisty to gutsy which seemed to create huge problems. I would like to thank everyone for there help and patience 
I know how irritating it can be helping a newbie because I used to help allot of peeps with Windows things and it used to get irritating repeating myself to everyone.
don't worry about it! no problem

yep, if you did an upgrade to Gutsy that very well could have been the main cause of the problems

I've used envy - it works pretty well. The driver I installed at that time using envy wasn't very stable, so I used envy's uninstall and it worked quite nicely. That's a sign of a good program when it can revert changes it makes without problems.

note: if everything is working well for you now and you consider this as "Solved" - you can mark the thread solved by going to the Thread Tools above the top post.

good luck! :)

---

### Post by obscur156 on 2008-02-07
Thanks lavinog,i will have a closer look to this.
Regards

---

