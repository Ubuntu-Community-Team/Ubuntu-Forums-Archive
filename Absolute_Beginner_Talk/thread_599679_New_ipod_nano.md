---
title: "New ipod nano"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by G. Cotgreave on 2007-11-01
Hi People!!!

I'm kind of new on ubuntu so here is my story so far...
Earlyer this evening i bought a brand new ipod nano 3rd Generation and since then i've been reading articles and posts in forums about ubuntu and ipods and concluded that the best thing to do is to install gtkpod, and so i did. My first problem is that i didn't read enyware something about connecting a brand new ipod on ubuntu. I read that i have to format it in a winbox or a mac first and then connect it on ubuntu, is it true? After installing gtkpod, ignoring the previous problem, i connected my ipod on my laptop and opened gtkpod. In the begining it asked me for the model of my ipod witch was not on the list so i wrote it myself ''ipod Nano 4Gb'' I started adding songs and everything seemed to work but when i dissconected the ipod it was empty!!! I got no messages from gtkpod about anything and i unmount it without any problem...
Any suggestions?

---

### Post by Inxsible on 2007-11-01
Have you tried using  other apps like Amarok or Rhythmbox?

I also heard that the newer iPods had compatibility issues with any other software than iTunes. Apple added some additional "security" feature, apparently. I am not sure of the current status of this. It might have been cracked already.

---

### Post by G. Cotgreave on 2007-11-01
I just tried amarok and i had the same results everything seems to work until i dissconect the ipod and discover that there is nothing inside...

---

### Post by Inxsible on 2007-11-01
Search for the new Apple restrictions. I have the 1st gen nano, and it didn't have any problems. 

Maybe you will find a way to get around the "security" feature.

---

### Post by adamklempner on 2007-11-01
I think you might be right in that you have to format it first in Windows or Mac with itunes.

---

### Post by Inxsible on 2007-11-01
> **adamklempner said:**
> I think you might be right in that you have to format it first in Windows or Mac with itunes.

I thought iPods always came "ready to go". I didn't have to format or anything. Unless they changed that policy :(

---

### Post by DGortze380 on 2007-11-01
Every one I've used had to be formated. Try to run iTunes in WINE, or possibly try to find out how it should be formated and use GParted to format if it's a common format. I would just connected to a machine with windows or mac first.

---

### Post by janko on 2007-11-02
Same problem here.
I red that new ipods have a sort of checksum that is calculated after they upload some files on the player, if you upload music with a program that doesn't caluculate the checksum songs would be there but the ipod would be unable to read his internal database. A couple of days after the new Ipod gen release someone already "hacked" the procedure to generate this checksum, but I'm still  waiting that someone implements that inside the libgpod (libraries in Linux that are used by the OS to communicate with the ipod).
Any news about that?

Janko

---

### Post by G. Cotgreave on 2007-11-06
Ok people first of all thnx for the help Unfotunantly though my new i pod still doesn't work with amarok or gtkpod (I would like it to work with amarok cause thats where i have all my collection) 
I formatted the nano at a winbox running itunes and i also added some songs from there. Today i connected my ipod and run amarok, it mounted the ipod without problems and i could also see the tracks that i have put there from the winbox. I followed the standard procedure for loading tracks on the ipod (not drag n drop) After i unmounted the ipod i saw that the free space of the ipod has reduced but now i could't see any of the tracks that i had inside not even the ones from the winbox.
I've heard about this ''restriction'' that apple added on the new ipods and unfortunantly many of the things that i read in this forum sounds a bit ''chinese'' to me since i have been forced to installed ubuntu on my laptop (It's a looooooong story)!!!!!! Is there any simple way to overide this restriction from apple and sinchronize my ipod with amarok? :confused: :confused: :confused:

---

### Post by llamakc on 2007-11-06
The 3rd gen. iPod Nano has encrypted firmware and does NOT work with Linux yet. You will HAVE to use iTunes, either natively in Windows or through a VM running WIndows.

I just bought the daughter one and had to reload XP for the time being until a workaround is figured out. (Yes, I tried it through VirtualBox but I could not get the iPod to be recognized.)

---

### Post by G. Cotgreave on 2007-11-06
Witch means that  i will have to go around friends with my hard drive asking them to use their winbox.....:(:(:(

---

### Post by HermanAB on 2007-11-06
Install Vmware Server and install Windows in that...

Otherwise, see this dejavu thread:
[http://forum.mandriva.com/viewtopic.php?t=74216](http://forum.mandriva.com/viewtopic.php?t=74216)

which leads to this:
[http://www.backdot.com/?p=50](http://www.backdot.com/?p=50)

At least, you are not alone with your grief...
;)

Cheers,

Herman

---

### Post by ramjet_1953 on 2007-11-06
I managed to get an iPod Shuffle working OK with gtkPod, after first setting it up on a Windows box.

Regards,
Roger :cool:

---

