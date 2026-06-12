---
title: "external modem can't connect to internet"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by gothdaddee on 2007-11-14
please help.  i can't seem to make my modem to work. it's a creative modem blaster DE5625 external (serial port). i was able to configure it (i think) using

$ sudo pppconfig

i tried to dial it using

$ pon

it then makes the familiar modem sound of connecting. after the sound, i'm not sure if i got connected to the internet or not. i tried to browse google with firefox but it seems that i still wasn't connected to the net. i got that familiar error screen that i get when i try to browse without the net connection. i also tried to configure using System>Administration>Network but somehow this method doesn't even give me the familiar modem sound. could you help me with this please.

---

### Post by gothdaddee on 2007-11-14
PS

i am posting this again because the answers i am getting at my previous post are for the question i have regarding nvidia drivers so i thought that i should post this question separately. sorry!

---

### Post by jpsimm on 2007-11-14
I think the modem program "wvdial" is the best there is.  It works easily with my external "Best" modem.  Using it I've successfully downloaded up to 5gig programs over about four days via dialup.  It redials and continues what it was doing if it gets dropped.

It's great.   Download it.  I think it's standard in Gnome.

---

### Post by Bartender on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)

---

### Post by peterjohn on 2007-11-14
try the help button on the launcher, it really helps with internet problem, no matter what kind of connection you have
-peter

---

### Post by ntu on 2007-11-15
I had the same problem and fiddled round with both pppconfig and System>Administration>Network>Modem connection and eventually it worked (external serial). I do not know which method worked. As far as I know they are still both setup to do the job.
I have no indication that I am online, blinky on the panel does not work. It has a red thing down the bottom of it stlll when I am online. The only way I know I am online is by knowing which lights on the modem are on when online and also whether I can renew web page in firefox.
Here, all 3 boxes in System>Admin>Network>Modem connection>Properties>Options are ticked.
Also the modem starts dialing before the desktop appears on bootup, but that is fine my me.
Oh yes, and I must have put the resolve.conf file in /etc (because i just checked and it is there) as advised in the first post on the link Bartender gives above.


Best wishes,

---

### Post by Bartender on 2007-11-15
It helps to watch the progress.  In KPPP or GnomePPP click on the "log" button.  In wvdial I think it shows you a log automatically, or it's very easy to ask for it.  It's late and my brain's not working.  

Even with pppconfig you can get a log - type plog into your terminal as you see the modem light up and you'll get a log.  At first it might all look like Greek but we need to see how far you got.  You might actually be connecting but your ISP doesn't recognize your password or username.

Sometimes tweaking on the init strings does it.  I haven't had to do that yet with my US Robotics modems, so I don't really understand what inti strings do or what to try changing.

Who's your ISP?  Some, like PeoplePC or AOL or Juno, get downright uncooperative when their servers see someone dial in without using their proprietary software.

---

### Post by gothdaddee on 2007-11-15
hah! now that was absolutely sweet!

thanks for the help! i followed Bartender's advice ([http://ubuntuforums.org/showthread.php?t=480717](http://ubuntuforums.org/showthread.php?t=480717)).  I downloaded gnome-ppp for gutsy ([http://packages.ubuntu.com/gutsy/net/gnome-ppp](http://packages.ubuntu.com/gutsy/net/gnome-ppp)), popped it in my ubuntu machine, and whadd'ya know! it was a piece of cake! i got my internet connection going and i got my graphics card's 3D capabilities enabled too! thank you so much everyone for the help!  i also got that icon thingy i could click when i want to connect or disconnect.

i was considering wvdial but from Bartender's thread, it used the terminal instead of the GUI and i wanted the GUI method to make things simpler for my wife and kids.

anyway, my remaining concern is that the gnome-ppp window didn't minimize or dock itself somewhere when i got connected.  it just stayed there in the middle of the screen saying "connecting..." or "dialing..." (i'm not sure which).  i wasn't sure if i was connected successfully.  there was no more sound coming out of my modem so i thought i'd try browsing and found out that i'm already online.  can the gnome-ppp be minimized or docked someplace after it has connected me? i already checked those tick boxes in the settings but the gnome-ppp window still remained there displaying "connecting..." or "dialing..." i want it to get off the desktop after it connects me to the net.

to ntu: yeah, maybe i'll just rely on my modem's LED lights for indication of modem activity if there are no other ways.  If there is some other way, anyone, please inform me also.

thanks!

---

### Post by Bartender on 2007-11-15
Hi, goth -
Pretty sure you can just minimize gnome-ppp after you're online and it'll go to the lower panel.  Try it and see what happens!  You know that you can also drop the icon into the lower or upper panel in case you don't want it cluttering your desktop?  
GNOME-PPP should show up when you go to Applications>Internet, then you can - dang it, I'm pulling a blank here - you can right click on it, or drag and drop it, or something.  It's not hard anyway.  If you got this far you'll figure it out.
I'm glad to hear it's working out for you.  Dial-up can be very frustrating.
EDIT:  Your description of GNOME-PPP's behavior, where it hangs at "Dialing", sounds quite a bit like what duncan describes in the dial-up thread.  I don't know if that's a bug or not.  But if you're connected and getting a decent speed I guess it's not a crisis, eh?

---

### Post by gothdaddee on 2007-11-16
yeah, i think it's just minor stuff too so i'll just minimize it. the important thing is that i get to go online and i don't know if it's my ISP or what, but i noticed that my speed is somehow faster than when i was using my other OS.

there's so many things to explore, and now that i've got everything set up (thanks again to everyone!) it's time to get in the water!

---

### Post by Bartender on 2007-11-16
You get better connection than with that other OS?  That's good to hear.  Who's your ISP?  I need to dump Juno.  It doesn't work with Linux.

---

### Post by gothdaddee on 2007-11-16
i dunno, i used to get frustrated waiting for a 5MB file to download and i always avoided downloading files greater than 5MB because it took me forever!.  but last night i was able to download a 10MB file in less than 30mins.  i dunno if it has something to do with ubuntu.  or is my windows already plagued with malwares that use up my net connection?  anyway, hopefully with ubuntu, i won't have to deal with malwares anymore.

my location is in the philippines so i guess my isp cannot be used from where you are. :)

---

### Post by hbbliss on 2007-11-17
Here's the deal. I have an ISP that I can actually talk to. They tell me that the dialup goes well and they are just waiting for some program (e.g., FireFox) to use the connection. The problem is that Ubuntu (7.04 et al) does not set "something" that tells the programs that there is actually a connection. Hence, FireFox or any other program will find that the "something" has not been set to indicate a connection. This results in an immediate "Server Not Found" message. The programs do not even try the actual connection. Hopefully this will help trigger a solution. When dialup occurs during logon this problem apparently does not occur. The problem is not the modem, the telephone line, the ISP, it is an Ubuntu problem---that can be solved.

---

### Post by mike555 on 2007-11-17
In the US I recommend " BasicISP " , it's just $6.95 a month and works with any OS ............ you don't even need a credit card if you pay 6 months in advance .........

---

### Post by Bartender on 2007-11-18
mike555 -
I shouldn't shanghai this thread but am always curious about dial-up ISP's - 
What can you say about Basic ISP's time-outs?

If you're trying to download updates, how long before they kick you off?  And what's involved in re-dialing and continuing with the download?

Also, what are their monthly useage limits?  Most of the ISP's I've looked into seem to allow roughly 300 to 450 hours a month.
Thanks!

---

### Post by mike555 on 2007-11-21
Most ISP's will list there rules on their site , you could check out them and of course make sure they have a phone number near your area ...   [www.basicisp.net](www.basicisp.net)    ..........

---

