---
title: "Connecting after dial-up on ISP"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by drummer44 on 2005-12-19
Hi,
I just installed Breezy Badger and I am using Copper.net as my ISP.  I have entered my [email]username@copper.net[/email] as my logon ID/username, I have entered my password, I have entered copper.net as the domain name, I have added their primary and secondary DNS server IP addresses.  I have an access phone number for which I am putting a '9' prefix in for to call out of the office.

The external 56K modem is dialing the access number and I can hear the modem try to negotiate the connection.  But then the line is dropped and the redial feature kicks-in.  I never get an Internet session.

What am I missing?  I would LOVE your help...someone...

Thanks!

---

### Post by bscbrit on 2005-12-19
Is there an option to select PAP/CHAP and, If yes, try the other one.  I once had a username that did not need, if fact wouldn't work with, @........  Perhaps that is worth a try?  I'm afraid modems aren't my strong point.

---

### Post by drummer44 on 2005-12-19
Thank you for your update.  I have had someone else suggest using "CHAP".  Of course I first have to find it in the system in order to invoke it.  These are new waters for me...    ;-\
Thanks

---

### Post by unisol on 2005-12-20
using the system/adminstrator/network try copper.net\username in the username field fill in rest of info

---

### Post by Mustard on 2005-12-20
[QUOTE=drummer44]Thank you for your update.  I have had someone else suggest using "CHAP".  Of course I first have to find it in the system in order to invoke it.  These are new waters for me...    ;-\
Thanks[/QUOTE]

To set up a connection to use CHAP, you would open terminal and type this command below and then use the menus to create a connection.

```
sudo pppconfig
```

Rather than me typing all this out, I'll give you a link to a dialup how to. :)

This should cover any questions you might have, but the main thing is that pppconfig allows you to configure your connection to use CHAP.  The HOW TO instructions tell you to choose PAP, but in your case you would choose CHAP instead, it that is how you think the problem might be solved.  You might even try looking at the output of the plog command as your modem is dialing out to see if you can get an indication of what it is doing.

[https://wiki.ubuntu.com/DialupModemHowto#head-69395fb95485fa3173cb9251f910f3d278ee59a7](https://wiki.ubuntu.com/DialupModemHowto#head-69395fb95485fa3173cb9251f910f3d278ee59a7)

---

### Post by drummer44 on 2005-12-21
Thanks.  I tried [HTML]http://wiki.ubuntu.com/DialupModemHowto [/HTML] but I was still unable to keep a connection.  I can hear the modem dial-out and try to negotiate, but it eventually just hums with a carrier tone and disconnects.  

Being a newbee, I don't know how to log what is happening or what log file to review.  I have tried the administrator-networking dialup and command line way of dialing out.  I can see that the messages file has information in it but I do not see the plog output anywhere.  If I had a way of seeing what was happening with the connection in a log file, I think that would be helpful.  Right now, I am flying blind.

I have tried playing with the username, the options file, the resolve.conf file, the chat-isp file.  No joy.

Any ideas?
Thanks!

---

### Post by drummer44 on 2005-12-21
I saw in another thread that someone had to change /etc/ppp/options to "auth" from "noauth" and change /etc/ppp/peers/kppp-options from "#noauth" to "noauth".  

Also, on the logging thing, using "sudo plog" and then "sudo tail -f /var/log/messages" just before pon'ing will give the logging needed.

I am going to try both of these above actions and cross my fingers!!!

---

### Post by zman58 on 2005-12-21
Dialing 9 first implies that you are on a PBX. Do you know that you can actually connect modem through PBX? Make sure PBX is not prohibiting modem connections from being made to outside of your business. Can you perform a controlled test of some sort to prove that PBX exchange works with the modem on your physical line?

---

### Post by drummer44 on 2005-12-22
Update: Last night, I tried changing the above areas and the same problem occurred...the line was eventually dropped.  I did make one step forward...I was able to figure out how to use plog.  The difference was that I did it with super user priviledges...sudo plog.  This allowed me to see what was happening with the line when the modem dialed-out.  When the line was dropped it came back and told me "NO CARRIER".  So, now I need to understand why I am not getting a carrier.  Is that an ISP problem or am I not setting-up my modem properly for the communication?  

Anyone have this problem before out there???

---

### Post by bscbrit on 2005-12-22
It can mean that you modem is not connected to the telephone line, or that your telephone line is dead.  Connect a telephone handset to the same line and simply listen to it.  Do you hear the tones that you expected to hear?  Try dialing the same number that you modem dials, does it ring?  If the handset works then check your cable from the modem to the telephone socket.

---

### Post by drummer44 on 2005-12-23
bscbrit,
I checked-out my phone line with a phone and tried changing chords.  All checked-out OK.  I called copper.net and talked to the support guy, who made sure that I knew he couldn't support a "Linux" call, and then checked my access number.  He came back on the line and said that he dialed it and everything worked fine.  

I am currently using wvdial, after running the config script and setting-up my modem with it.  It dials and does what everything has done before...indicate that there is no carrier.  I'm stumped.  There must be some configuration problem at my end, but I don't know what.  Could it be my modem- itself?

I tried going back to using Pon, but it says that there is no secret password for the host to use to authenticate anymore.  I changed something, but I don't know what.

Yikes...I am running in circles, now.   Merry Christmas...Drummer44

---

### Post by L Campbell on 2005-12-23
[QUOTE=drummer44]bscbrit,
I checked-out my phone line with a phone and tried changing chords.  All checked-out OK.  I called copper.net and talked to the support guy, who made sure that I knew he couldn't support a "Linux" call, and then checked my access number.  He came back on the line and said that he dialed it and everything worked fine.  

I am currently using wvdial, after running the config script and setting-up my modem with it.  It dials and does what everything has done before...indicate that there is no carrier.  I'm stumped.  There must be some configuration problem at my end, but I don't know what.  Could it be my modem- itself?

I tried going back to using Pon, but it says that there is no secret password for the host to use to authenticate anymore.  I changed something, but I don't know what.

Yikes...I am running in circles, now.   Merry Christmas...Drummer44[/QUOTE]


Have you tried checking here:-  [http://linmodems.org/](http://linmodems.org/)

I have found these people to be quite helpful, although I'm not online yet but I'm getting close enough that I can smell it.   :-)

Good luck.

---

### Post by bscbrit on 2005-12-24
OK, Don't worry, we are now moving forward!  We can now rule out any problem with the telephone company, the number that you are dialling etc etc.  i.e. the problem is the configuration.

You have an external modem (so the previous link to linmodems will probably not provide the answer you are search for but, hey, go read what they have to say anyway).  Is it a USB modem or an RS232 (i.e. serial modem), what is the make and model?  (this is for my benefit only - you can hear the modem trying to dial so presumably you have made the correct connections to it!)

Try these links:

[http://makuchaku.info/amnesty/#networking](http://makuchaku.info/amnesty/#networking)

[https://wiki.ubuntu.com/DialupModemHowto#head-69395fb95485fa3173cb9251f910f3d278ee59a7](https://wiki.ubuntu.com/DialupModemHowto#head-69395fb95485fa3173cb9251f910f3d278ee59a7)
(You should have already tried this one from an earlier post)

Why?  Well at the moment I have no visibility on what you have tried or not tried.  You ask if the problem might be in your modem,  Well, yes, it might.  But until I (or anyone else) can be certain that you have 'pushed the right buttons' we need to work from a baseline that we both can understand.  If you follow the link and do as it says, when (if!) if goes wrong we will both know what has been done and what has not been done.

HTH - and thanks for the seasonal greetings.  Because I do not know every readers' religion or beliefs, I'll simply say 'Happy Ubuntu'.

---

### Post by drummer44 on 2005-12-26
Hey!  It's working!  After installing the Linux version of the Netzero dialer and the SAME problem happened with NO CARRIER appearing after dialing-in, I suspected the modem.  I then flashed the modem with the latest driver for the US Robotics modem that I was using.  After this, I used tne System-Networking dialer to connect and it did.  All this time, it was the modem.  

So heads-up if someone else has this symptom and they have checked-out their software settings and their modem connections.  It might be the modem itself...makes sense.  Half the battle was learning the LInux syntax for navigation and where stuff resided on the drive to make changes.  It has been a learning experience.  Cool!

Thanks for the help!

---

### Post by bscbrit on 2005-12-26
A pleasure! But you must take the credit - you fixed this one yourself.

---

### Post by zman58 on 2006-01-20
Drummer told me he got this working. PBX would not let him connect. It worked at home for him.

---

### Post by JNowka on 2006-01-20
I actually just fixed this problem tonight on my computer.

What I did -
goto /etc/ppp/

open the document "options" and edit it as root.

find auth and put a # in front of it.

I can now connect.

Just having problems now loading websites, I cant
any suggestions

---

