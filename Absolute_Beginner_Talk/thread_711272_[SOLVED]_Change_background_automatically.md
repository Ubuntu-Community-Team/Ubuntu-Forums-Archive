---
title: "[SOLVED] Change background automatically?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-02-29
Can anyone tell me how to change the background automatically? More specifically I want to automatically download a picture form [here]("http://xplanet.sourceforge.net.nyud.net:8080/clouds/tmp/200802291553.758979/clouds_2048.jpg") and then make it my background. It updates about every 3 hours, so I would like mine to as well

---

### Post by y-lee on 2008-02-29
How good are you at writing scripts?

Basically you could modify the script found in [Automatically changing wallpaper relatively to daytime in Ubuntu]("http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/") to [wget]("http://en.wikipedia.org/wiki/Wget") the image and make the changes.

Most of the work is already found in that script and while this is an interesting idea you have ***please ***don't ask me to write this script for ya.

---

### Post by slughappy1 on 2008-02-29
Thank you. If I can figure it out I will post what I did

---

### Post by y-lee on 2008-02-29
Cool it might be educational to share it. thanks :popcorn:

---

### Post by mister_pink on 2008-02-29
I think its just a two liner really!
```
#!/bin/bash
wget -O ~/clouds.jpg http://xplanet.sourceforge.net.nyud.net:8080/clouds/tmp/200802291553.758979/clouds_2048.jpg
gconftool-2 -t str --set /desktop/gnome/background/picture_filename ~/clouds.jpg

```
Save it somewhere, make it executable (chmod a+x)
Then make a cron job:
```
crontab -e
```

Add something like:
```
00 1,4,7,10,13,16,19,22 * * * /path/to/script
```

I think thats right, but I'm never very good with cron jobs. You could even try skipping making the script and put it all in the cron job, seeing as its so short:
```
00 1,4,7,10,13,16,19,22 * * * wget -O ~/clouds.jpg http://xplanet.sourceforge.net.nyud.net:8080/clouds/tmp/200802291553.758979/clouds_2048.jpg; gconftool-2 -t str --set /desktop/gnome/background/picture_filename ~/clouds.jpg
```

---

### Post by drubin on 2008-02-29
Something that might help you with cron

There is also an operator which some extended versions of cron support, the slash ('/') operator (called "step"), which can be used to skip a given number of values. For example, "*/3" in the hour time field is equivalent to "0,3,6,9,12,15,18,21"; "*" specifies 'every hour' but the "/3" means only those hours divisible by 3.

[http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

---

### Post by mister_pink on 2008-02-29
Ahh, I thought there was something like that but I couldnt remember what it was! Cheers

---

### Post by slughappy1 on 2008-03-05
So I finally got around to actually doing it. I used a script and a cron. I have a folder where I keep all my scripts that I have written, and I also used the website [here]("http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/") to help. This is how I did it.

```
cd Script
gedit change.sh
```
Inside of the change.sh script I have:
```
#!/bin/bash

sleep 45

wget http://static.die.net/earth/hemisphere/1600.jpg -O /home/jason/.CurrentDaylightMapOfEarth/1600.jpg && 
gconftool -t string -s /desktop/gnome/background/picture_filename /home/jason/.CurrentDaylightMapOfEarth/1600.jpg
```
save and close. Then
```
crontab -e
```
inside of cron I have:
```
* */3 * * * /home/jason/Scripts/change.sh
```
save and close. Then
```
chmod +x change.sh
```

Then I added one thing to the startup, so when I log in it gets the newest picture 
* System -> Preferences -> Sessions -> Click the Add Button
Name : Initializing Wallpaper
Command : /home/username/Scripts/change.sh
Click Ok

---

### Post by slughappy1 on 2008-03-07
For some reason the cron isn't working. Does anyone know why? I also tried to change the cron to: 
```
* 0,3,6,9,12,15,18,21 * * * /home/username/Scripts/change.sh
```

---

### Post by drubin on 2008-03-07
> * 0,3,6,9,12,15,18,21 * * * /home/username/Scripts/change.sh

change to 
Makes it go very 3 hours, just easier to read.
```
*  */3  *  *  *  /home/username/Scripts/change.sh
```

Does your script have execute rights?

---

### Post by slughappy1 on 2008-03-07
that is what I had it as, and yes it does. The post above the one I just made is what I did

---

### Post by slughappy1 on 2008-03-08
Ok, so it turns out my problem was I didn't fully understand the concept of a cron job. I thought that a cron job was like a script and you could have as many as possible. I didn't know that there was only one cron and that you can have multiple lines in it. So I will change my earlier post to make it accurate on what works.

---

