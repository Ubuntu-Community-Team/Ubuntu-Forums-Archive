---
title: "ipod touch, help me help a noob."
date: 2009-05-29
forum: Apple Hardware Users
---

### Post by veganbikepunk on 2009-05-29
[https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x](https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x)

using these instructions I was able to get the ipod touch v2.0 to work with my ubuntu.  It's not my ipod however.  It belongs to my buddy who just got ubuntu today. Through those instructions I was able to transfer music wirelessly to the ipod touch, but it won't play through the regular music player.  It plays through pwnplayer.  For me that's not a biggie, and I'm sure I can convince her that's fine, if that was the only issue.  The other issue is the difficulty it took me.  I think she's going to be scared off if she has to look up the ip for the iphone, go to places>Connect to server enter in some info.  Go to Nautalis, switch from button-based to text-based, type in sftp://root@[IP address]/var/mobile/media/music/, find her music, and drag and drop it into the folder.  Is there a simpler way?  Is there a way I could set the ipod touch to a static IP and then make /var/mobile/media/music a desktop icon on her laptop with the right permissions to be able to drag and drop?

Is there any way I can make this less garbled?  I feel like a representative of linux when I convince my friends to use it and I don't feel like I have the knowhow to make this uncomplicated.  It's always the worry that she'll see how much trouble it is and make the switch back to vista.

Thanks for your help,
paxana

---

### Post by JerichoDefeated on 2009-06-14
I'm sort of a noob but what I did to get around this was run WinXP in Virtualbox and mount the iPod into windows and use iTunes to sync your music. Right now I am looking for a way that I don't have to do that, but I am having trouble finding the location of the iPod's USB connection. I'll give you an update if i find something easier.

---

### Post by JerichoDefeated on 2009-06-14
Well it looks like I'm gonna have to use iTunes through wine or VB because I like the default player for the iPod Touch better than PWNplayer. And according to this [link]("http://ubuntuforums.org/showthread.php?t=991322&highlight=mount+ipod+touch")
I'll have to do that for a while if not forever. But I still SSH into my iPod every now and then so I'll look for a way to get a static IP for the iPod if you don't want to use iTunes. Maybe someone else has a better way, but your idea of a static IP is the best I've seen.

---

### Post by JerichoDefeated on 2009-06-14
Okay, I went into my wireless Netgear router's basic settings and set it to a static IP/ It seems to be working I've disconnected and reconnected a couple times and it's giving me the same IP every time so hopefully it will stay the same. Hope that helped. I know I'm a little late but if you didn't find an answer I hope this helped.

---

