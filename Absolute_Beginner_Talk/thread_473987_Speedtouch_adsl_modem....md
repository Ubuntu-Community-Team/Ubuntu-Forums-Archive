---
title: "Speedtouch adsl modem..."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by John CCC on 2007-06-14
Hi.. here's the situation.
I'm not a computer professional, but I do love messing around. My roomate is taking his pc away today and I've had another given to me.  No time like the present to set it up with Linux/Ubuntu.  The problem is, I need to get it online so that I can access forums and what not to figure stuff out, and it seems that getting this modem to run is not going to be as easy as I expected.  I am *extremely* new to this OS environment, and not quite sure what to do...
Any ideas?  I'd love to get the modem from the machine I'm currently using to the other in the next 4 hours if possible.
Possible?

---

### Post by Happy_Man on 2007-06-14
What kind of modem?

---

### Post by sebbouckaert on 2007-06-14
I think the answer is right above your question :-)

---

### Post by John CCC on 2007-06-14
Hey it's a speedtouch 330.
I did a bit of searching but, I'm not sure where to start really.

---

### Post by agurk on 2007-06-14
Tried [https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo](https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo) ?

---

### Post by redwinder on 2007-06-14
try this guide too [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch) its more detailed ,maybe we can help each other because i too have the same modem.

btw can anyone help me?, i am stuck in this step:

> Preparing the firmware

You now have the needed firmware - but that is not enough - the firmware file needs to be prepared and for this we will use a tool called firmware-extractor. The firmware-extractor splits the firmare file in two pieces so it vcan be loaded into the modem's memory. So  download the firmware-extractor and move it to the fresh created working folder: 
mv firmware-extractor speedtouch

Now we will split the firmware using the following commands depending on the modem revision: 
cd speedtouch
chmod +x firmware-extractor
./firmware-extractor KQD6_3.012

if you have a 0 or 2 revision modem or: 
cd speedtouch &&
[B]chmod +x firmware-extractor &&
./firmware-extractor ZZZL_3.012[/B]

if you have a 4 revision modem. After that you will have two files in the speedtouch folder: speedtch-1.bin & speedtch-2.bin is just the firmware splited in two parts.

i am supossed to put something in the x?, because when i run it it says that there is no directory, i should extract the firmware extractor `s files too?, please help

---

### Post by redwinder on 2007-06-14
bump

---

### Post by John CCC on 2007-06-16
Thanks for the links... unfortunately, I'm getting stuck on the early steps.. ie: which version of speedtouch adsl modem am I using.  Plugging the usb modem into the linux machine and then trying this:
awk '/4061/ { print $5 }' /proc/bus/usb/devices
in the terminal is supposed to tell me which version it is.  However, it yields, "directory not found"  
I still have access to a windows machine and the internet, is there another way to figure out which version I am using? and then, I am afraid, I am not altogether confident that I am using the terminal correctly.  Ideally, it would be nice if I could get that together before attempting any thing complicated (as it seems that this process is) however, So...
I found this link [http://linux-usb.sourceforge.net/SpeedTouch/docs/howto.html](http://linux-usb.sourceforge.net/SpeedTouch/docs/howto.html)  The speedbundle referred to here looks like it would be a simple solution.  However, I am having a hard time knowing where to find the right firmware (version??), and then where to put it once I do find it... (directions simply state "on the box")
thanks!

---

### Post by Rui Pais on 2007-06-16
Hi.
Another case for [USB ADSL Modem Manager for Gnome?]("http://ubuntuforums.org/showthread.php?t=445701")

Deserves a try.

---

### Post by John CCC on 2007-06-16
Butterflies in my stomach as I await to see if this really works....
It's so sad that I'm serious   :p

---

### Post by John CCC on 2007-06-16
haaaaaaaaaa lay   lu   yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu  yaaaah

haaaaaaaaaa lay   lu   yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu  yaaaah

haaaaaaaaaa lay   lu   yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu  yaaaah

I would just like to take this opportunity to thank all those who stood by me throughout this difficult ordeal....  redwinder, I may not know you... but through all this you've been like a brother to me!  I love ya man...

And, Rui Pais, bottom line... you came through for me man... (through tears)  You tha man!

And to all you other homeys and hommettes out there usin Ubuntu... keep on keepin on!

Peace out!

P.S. I got the modem to work!  :popcorn:

---

### Post by Rui Pais on 2007-06-16
you are crazy man...

(but what would we expect from a Scotch with butterflies in his stomach :lol:)

Anyway drop a word that it works on Steve thread his debugging and trying to get his (great) app accept for gutsy.

Have fun :)

---

### Post by John CCC on 2007-06-16
haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

haaaaaaaaaa lay lu yah
ha lay lu yah
ha lay lu yah
ha laaaaay luuuu yaaaah

I would just like to take this opportunity to thank all those who stood by me throughout this difficult ordeal.... redwinder, I may not know you... but through all this you've been like a brother to me! I love ya man...

Red Squirrel you gave it your all... and I won't soon forget that! 

Rui Pais, (pause for dramatic effect) bottom line... you came through for me man... (through tears) You tha man!

And to all you other homeys and hommettes out there usin Ubuntu... keep on keepin on!

Peace out!

P.S. I got the modem to work! I used:  [USB ADSL Modem Manager for Gnome?]("http://ubuntuforums.org/showthread.php?t=445701")  referred by Rui Pais. It's absolutely brilliant and hastle free! 
__________________

---

### Post by zidane2 on 2007-06-21
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) is the site i use to get online it is very easy to use even for a newbie like me
hope it helps

---

