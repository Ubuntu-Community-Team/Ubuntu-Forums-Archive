---
title: "Taking the plung.. In reverse."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by DocBarleycorn on 2007-05-27
This one is a little weird, just let me warn you. I was big into UNIX back in the 80's and early 90's. Now I have a computer I can dedicate to Linux(as opposed to a shared one which must have Win) and I chose Ubuntu. All the old-school Unix commands I'm pretty hip to. While I've played with Linux many times, I will be taking the plunge soon as my disk arrives, and I'd like some feedback from the Ubuntu-studs and stud-etts. 

My first concern is the software/updates/librarys/etc. I live in a rural area with NO high-speed. How much stuff am I going to need to download to get the old girl doing the stuff I'm used to? Any tales from the dial-up ghetto?

Secondly, I tend to throw computers together out of spare parts. Is my mix-n-match parts list going to lead to issues? Will I be hunting for, and downloading tons of drivers? Refer to my first concern.

Lastly, can anyone think of common user mistakes that happen during installation and configuration? I'd like to do it right the first time. I've read a bunch of FAQs, but if you got any suggestions, I'd sure like to hear 'em. Thanks

-Doc

---

### Post by Zuuswa on 2007-05-27
Well, it all depends on what you are trying to do with your computer :) If you want it to play mp3s and dvds and the like, you will need an internet connection to install the proprietary codecs.  It might take a while with dialup, but I think its still a reasonable download.  And, if you want 3d accel. with your graffix card, you will need an internet connection as well.  otherwise, I dont think your 'mix 'n match' computer will have too many problems with drivers, etc.  Though, I cannot gaurantee you anything because I dont know the specs.  I believe you will find Ubuntu to be a great OS alternative!

---

### Post by seetho on 2007-05-27
After installation there's a long list of updates to download.  Eventhough I have a 1Mb internet line my (update) download speed normally drops to more like dialup speeds of 4k to 6k on average.  So this normally take hours and hours to complete.  I usually leave it on a go to bed and it's done the next morning.

If you start installing large packages then you are looking at long hours of downloads using your dialup.

Good luck.

---

### Post by Zuuswa on 2007-05-27
That sounds very strange . . . maybe you should contact your isp.  My downloads usually go anywhere from 100k to 400k a second, and Im using my neighbor's wireless.

---

### Post by seetho on 2007-05-27
Hmmm... maybe I should start using my neighbour's wireless.;)

Naaah!  It's not the line problem.  It's the repository servers in my area.  I guess they are heavilly loaded most of the time.  I get decent speeds sometimes.

---

### Post by paparucino on 2007-05-27
> **seetho said:**
>  Eventhough I have a 1Mb internet line my (update) download speed normally drops to more like dialup speeds of 4k to 6k on average.  So this normally take hours and hours to complete.  I usually leave it on a go to bed and it's done the next morning.

Did you try to change the repo server?
it's really strange you fall down to that speed.

---

### Post by houstonbofh on 2007-05-27
You can do an install elsewhere and grab your update cache. [http://kmandla.wordpress.com/2007/04/25/stash-your-cache/](http://kmandla.wordpress.com/2007/04/25/stash-your-cache/)
As to drivers, you should prepare yourself for a pleasant surprise.  Most drivers are included.  Older white-box stuff is most likely to be there.  However, pick your video and WiFi carefully.

---

### Post by DocBarleycorn on 2007-05-27
Thanks for the input. I'm looking forward to getting things set up. I just hope high-speed internet comes to the sticks soon. I just hate the idea of long downloads eating up the pathetic internet I do have.

> **houstonbofh said:**
> You can do an install elsewhere and grab your update cache. [http://kmandla.wordpress.com/2007/04/25/stash-your-cache/](http://kmandla.wordpress.com/2007/04/25/stash-your-cache/)
As to drivers, you should prepare yourself for a pleasant surprise.  Most drivers are included.  Older white-box stuff is most likely to be there.  However, pick your video and WiFi carefully.

---

### Post by seetho on 2007-05-27
> **paparucino said:**
> Did you try to change the repo server?
it's really strange you fall down to that speed.

My Feisty machine is no being updated with new kernel and some other stuff at just about under 30MB size download.  The speed started off OK but after a while it settles to around 5 - 10k now.

I'll changing the repo servers after this and see what happens.  Thanks.

---

### Post by ramjet_1953 on 2007-05-27
I'm not sure if it would be available in your area, but have you considered satellite Internet?

I live in Thailand and when I was living in one particular area, it was the only way that I could get high speed, as I lived more than 6 Km from the local telephone exchange and they don't seem to use RIM's (Remote MUX's) here.

Regards,
Roger :cool:

---

### Post by dpzektor on 2007-05-28
You can also ask someone to burn you the repositories on DVD's for you.

---

### Post by Bartender on 2007-05-28
Some folks have expressed the opinion that Ubuntu just isn't appropriate for dial-up because of the huge downloads.  Hard to argue with that.
Do you have broadband available to you at work or school or the library?  I'm stuck with dial-up or expensive satellite also.  It sucks. 
Every once in a while I unplug my PC and take it to a broadband connection.  If you can do this too just make sure to plug in the CAT cable before starting up your PC.  If you're at a friend's house, borrowing their router connection, you may have to unplug power to the router for a half minute so it clears its settings.  Turning it off isn't the same as unplugging.

---

### Post by houstonbofh on 2007-05-28
> **Bartender said:**
> Every once in a while I unplug my PC and take it to a broadband connection.  If you can do this too just make sure to plug in the CAT cable before starting up your PC.
The command you are looking for here is 'sudo dhclient' or disable and then enable your network card in the GUI config.  Minor PITA that Linux won't try DHCP on link detect.

---

### Post by DocBarleycorn on 2007-05-29
I'd love satellite but cost is an issue. Is there a system of mailing out updates and software on disk? The rural Ozarks bad connection speeds.

> **Bartender said:**
> Some folks have expressed the opinion that Ubuntu just isn't appropriate for dial-up because of the huge downloads.  Hard to argue with that.
Do you have broadband available to you at work or school or the library?  I'm stuck with dial-up or expensive satellite also.  It sucks. 
Every once in a while I unplug my PC and take it to a broadband connection.  If you can do this too just make sure to plug in the CAT cable before starting up your PC.  If you're at a friend's house, borrowing their router connection, you may have to unplug power to the router for a half minute so it clears its settings.  Turning it off isn't the same as unplugging.

---

### Post by irish_flu on 2007-05-29
> **Zuuswa said:**
> That sounds very strange . . . maybe you should contact your isp.  My downloads usually go anywhere from 100k to 400k a second, and Im using my neighbor's wireless.

:D  LMAO

---

### Post by Bartender on 2007-05-31
> **DocBarleycorn said:**
> I'd love satellite but cost is an issue. Is there a system of mailing out updates and software on disk? The rural Ozarks bad connection speeds.

No, doc, not that I know of.  You're pretty much on your own.  Linux and dial-up is just a poor combination, no way around it.  
If you have a good external modem and can find an ISP that understands Linux and won't cut you off in the middle of all-nighter downloads you might be able to get by.  But it's never going to be pretty.  I hauled my test PC into work the other night and downloaded the entire ubuntu-desktop package to a Xubuntu install.  Then downloaded OpenOffice and a few other odds and ends.  
Took about an hour or so all told.  Woulda been 20 or 30 hours on dial-up if I didn't get disconnected right in the middle.

---

