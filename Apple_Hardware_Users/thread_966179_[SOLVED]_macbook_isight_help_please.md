---
title: "[SOLVED] macbook isight help please"
date: 2008-11-01
forum: Apple Hardware Users
---

### Post by alwayshere on 2008-11-01
I have just moved on to hardy 8.04 from 7.04 fiesty and im having no luck getting isight going with cheese on my ubuntu only black macbook gen 1.
I have spent hours trying different things from forums but no luck .
it seems i need the firmware anyone know how where to get it .

>  sudo apt-get install isight-firmware-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package isight-firmware-tools

i have these repositories 

# deb [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/mactel-support/ubuntu](http://ppa.launchpad.net/mactel-support/ubuntu) hardy main

---

### Post by cyberdork33 on 2008-11-01
[http://www.rickycampbell.com/isight-intrepid/](http://www.rickycampbell.com/isight-intrepid/)

You can get ift from the Intrepid repos. It was removed from the mactel-support ppa.
[http://packages.ubuntu.com/intrepid/isight-firmware-tools](http://packages.ubuntu.com/intrepid/isight-firmware-tools)

Why are you using 8.04? 8.10 was just released.

---

### Post by alwayshere on 2008-11-01
Hey thanks for the info ill try it out and post how it goes . 

I have only just upgraded from 7.04 because it not supported i had every thing working fine ,but got to move on to 8.04 which is supported till 2011 8.10 only supported till 2010 so ill stay with 8.04 .I have found virtualbox a new toy to play with in 8.04 which helped me reluctantly move on from 7.04. I just find upgrades bring more trouble than they worth ,I say if its still supported and is not  broken don't fix it .

---

### Post by alwayshere on 2008-11-01
Ok I now have isight-firmware-tools  installed but its not doing me any good because im using a ubuntu only macbook with no other os at all so i have no osx to extract from . there must be another way because i managed to do it on my old fiesty install some how ?

any ideas

---

### Post by cyberdork33 on 2008-11-01
> **alwayshere said:**
> I have only just upgraded from 7.04 because it not supported i had every thing working fine ,but got to move on to 8.04 which is supported till 2011 8.10 only supported till 2010 so ill stay with 8.04 .
That is only applicable if you *purchase* support. The community really focuses support on the later version.

> **alwayshere said:**
> I have found virtualbox a new toy to play with in 8.04 which helped me reluctantly move on from 7.04. I just find upgrades bring more trouble than they worth ,I say if its still supported and is not  broken don't fix it .

While this is true, I just thought it was odd that 8.10 was just released but you just upgraded to 8.04 instead of to 8.10, but your prerogative.

> **alwayshere said:**
> Ok I now have isight-firmware-tools  installed but its not doing me any good because im using a ubuntu only macbook with no other os at all so i have no osx to extract from . there must be another way because i managed to do it on my old fiesty install some how ? Nope that is the only place you can find it.

---

### Post by alwayshere on 2008-11-01
I must be doing something wrong?? because I did have isight working with chesse on 7.04 with out any other os installed  ,I wish I could remember how i did it:lolflag: I'll post a how to when I sort it .

Any help please

---

### Post by cyberdork33 on 2008-11-01
> **alwayshere said:**
> I must be doing something wrong?? because I did have isight working with chesse on 7.04 with out any other os installed  ,I wish I could remember how i did it:lolflag: I'll post a how to when I sort it .

Any help please

I think there used to be a package of files that had the firmware on it back then. If you scour the archive of the old forum you might find the link.

---

### Post by alwayshere on 2008-11-01
OK all is sorted heres how i did it may not be as pure as it should ? but hey im no wizz

> ***** This is what worked for me on myblack  macbookgen 1. ubuntu only os  isight/cheese *****

Make sure your all updated and go to
Applications /add remove
search "cheese"
Install it.

Put below in your repositories
deb [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) intrepid main multiverse

Open terminal and put

sudo apt-get update

then 

sudo apt-get install isight-firmware-tools

then 

sudo apt-get update

Go to this address  
[http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt)
and download "AppleUSBVideoSupport"
save it to your desktop

open terminal and put below  command   
PLEASE NOTE the xxxxx is where you need to put your user name

sudo ift-extract -a /home/XXXXX/Desktop/AppleUSBVideoSupport

push enter 

and all should be good go to Application then graphics and fire up cheese .



---

### Post by alwayshere on 2008-11-02
cyberdork33 has convinced me to upgrade to 8.10 all is good and above post works for it to .

---

### Post by eltoroloco on 2008-11-02
I've attempted the steps outlined in the previous posts and am still unable to get my isight camera working.  I have a macbook 2nd gen running ubuntu 8.10.  I also tried the instructions given at [http://www.rickycampbell.com/isight-intrepid/](http://www.rickycampbell.com/isight-intrepid/) .   

Can any one point me in the right direction?  

Thanks :)

---

### Post by alwayshere on 2008-11-02
do you have a file called isight.fw in your /lib/firmware folder

if not go to [http://rapidshare.com/files/160127491/isight.fw.html](http://rapidshare.com/files/160127491/isight.fw.html)
and download it 

use 
sudo nautilus

to go to lib folder then to firmware folder and then copy and paste the isight fw file there

then fire up cheese

---

### Post by cyberdork33 on 2008-11-02
> **eltoroloco said:**
> I've attempted the steps outlined in the previous posts and am still unable to get my isight camera working.  I have a macbook 2nd gen running ubuntu 8.10.  I also tried the instructions given at [http://www.rickycampbell.com/isight-intrepid/](http://www.rickycampbell.com/isight-intrepid/) .   

Can any one point me in the right direction?  

Thanks :)
can you verify that there is a file called isight.fw in the folder /lib/firmware ?

If so, please shutdown your computer completely, then start it up again and it should work. (not a reboot).

---

### Post by cyberdork33 on 2008-11-02
> **alwayshere said:**
> do you have a file called isight.fw in your /lib/firmware folder

if not go to [http://x]("http://rapidshare.com/files/160127491/isight.fw.html")
and download it 

use 
sudo nautilus

to go to lib folder then to firmware folder and then copy and paste the isight fw file there

then fire up cheese
I don't think you need to go posting that around as I am pretty sure it is illegal to redistribute that in most countries.

---

### Post by teklife on 2011-02-21
> **cyberdork33 said:**
> I don't think you need to go posting that around as I am pretty sure it is illegal to redistribute that in most countries.

that's petty and absurd. i don't think even the litigation happy apple would give 2 twats about posting a link to their firmware file, especially since the only use for it would be on apple hardware. correct me if i'm wrong.

i need this file to get the isight working on my macbook, but cannot find it anywhere. currently i'm running os x.6 so i cannot use the appleiousbblablabla from my is x partition.

what to do?

---

### Post by jezgordon on 2011-02-25
> **teklife said:**
> 

i need this file to get the isight working on my macbook, but cannot find it anywhere. currently i'm running os x.6 so i cannot use the appleiousbblablabla from my is x partition.

what to do?

[FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]I didn't have the isight.fw file on my mac either (did full install of ubuntu and wiped the osx, fail) but managed to get it by just googling "AppleUSBVideoSupport" and downloading the medifire file from there.

Then followed the instructions at [https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight](https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight?action=show&redirect=AppleiSight) which got the isight.fw file into the lib/firmware folder.
Made a script as outlined on the link above to make sure the isight.fw file was put into the folder every startup (and it is, that works fine).

...unfortunately even with everything seeming to have worked and the .fw in place I still can't seem to detect the webcam with cheese [/SIZE][/FONT][FONT=Verdana][SIZE=2]or gstreamer-properties.

I've done the full shutdown (not reboot) and startup several times and sifted through quite a few forums but can't seem to figure it out, any help would be greatly appreciated!

Running Ubuntu 10.10 on an intel macbook 1gb ram, single os.

Now have  video through Ekiga but skype still doesn't detect the isight.
used [http://ubuntuforums.org/showthread.php?t=225621](http://ubuntuforums.org/showthread.php?t=225621) to get ekiga working (though not sure if this was what fixed it or the previous steps)

final edit: got everything working now, needed to install pulseaudio and play with some of those settings to get mic to work properly for skype but that and a final shutdown/restart and everything works perfectly now.
[/SIZE][/FONT]

---

### Post by alexmoon on 2011-03-09
Was there anything else you did? I've followed all of these steps and it doesn't seem to be working...

---

### Post by beatskobe on 2011-03-10
that script should be run using linux.
[[img]http://www.monsterkobestudio.com/pic/kobe3.jpg[/img]](http://www.monsterkobestudio.com/)

---

