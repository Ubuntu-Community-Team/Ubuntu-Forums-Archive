---
title: "Thoughts on Making a Music Server on Mini-ITX"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2007-07-16
My project is as follows:

A customer wants to have his music files stored on a "little" computer with his high end stereo equipment.

He uses XP on his desktop and we just ordered him an XP laptop.

My plan:

Build a Mini-ITX system which we would put onto his LAN wirelessly. 

Install Ubuntu onto it, remove all programs except for a music player and Frostwire.  

Move all the music files from his existing XP Desktop to the music library on the mini (wirelessly of course)

He would VNC into this system from his laptop wirelessly and play his music through his stereo which would be connected to his mini system through the sound card. Also when he wanted to d-load music through frostwire he would go the VNC method.

I want him to be able to rip his existing CD's on either his XP laptop or XP desktop and have the output sent to his mini system wirelessly.

This of course would all have to be transparent to him as he has no desire to learn linux and does not want to bother with the ins and outs of his LAN.

Is this possible?  Please post any ideas on how to go about this or thoughts that may have not occured to me as far as configuration.

If anyone needs more info please ask...

Thanks,
Chuck

---

### Post by CrucifiedEgo on 2007-07-16
I would suggest something like jinzora -- a web-based frontend he can browse to from his laptop, and it will either stream to the laptop, or playback through the soundcard(and out to his stereo).  All you'd have to do is install a LAMP stack(or if it's a small system, go with Lighttpd instead of apache -- smaller and faster) and you'd be set.  negates the need for VNC, even less linux for him to learn, and he can access the music if/when he travels. I've got this setup at home, and it works beautifully.

to satisfy some of jinzora's requirements, you'll need to:

**Apache version(memory hog, less setup)**
```
sudo aptitude install lame sox apache2 php5 php5-mysql php5-gd mysql-server mysql-client
```

**lighttpd version(more setup, will work on slower box)**
```
sudo aptitude install lame sox lighttpd php5-cgi php5-mysql php5-gd mysql-server mysql-client
```

</j>

---

### Post by charles.g.moore on 2007-07-16
> **CrucifiedEgo said:**
> I would suggest something like jinzora -- a web-based frontend he can browse to from his laptop, and it will either stream to the laptop, or playback through the soundcard(and out to his stereo).  All you'd have to do is install a LAMP stack(or if it's a small system, go with Lighttpd instead of apache -- smaller and faster) and you'd be set.  negates the need for VNC, even less linux for him to learn, and he can access the music if/when he travels. I've got this setup at home, and it works beautifully.

to satisfy some of jinzora's requirements, you'll need to:

**Apache version(memory hog, less setup)**
```
sudo aptitude install lame sox apache2 php5 php5-mysql php5-gd mysql-server mysql-client
```

**lighttpd version(more setup, will work on slower box)**
```
sudo aptitude install lame sox lighttpd php5-cgi php5-mysql php5-gd mysql-server mysql-client
```

</j>

I looked at the jinzora website, it is open source right (free).  Do you see any issues with the wireless setup I outlined as far as him ripping cd's / downloading(limewire) from his XP box / laptop and having the data saved wirelessly to his mini ubuntu box?  Do you think it would be better to set up a system where he saves to the desktop/laptop locally then sync the files at a given time? This web-based frontend looks promising.

---

### Post by charles.g.moore on 2007-07-16
I'm a bit worried about the whole wireless issue...

---

