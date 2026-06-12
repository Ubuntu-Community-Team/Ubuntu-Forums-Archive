---
title: "Internet"
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Grandpapop on 2006-02-25
I have Ubuntu 5.04 loaded on a drive by itself.  I have looked and looked for the thing that I hit to link to the internet.  I can't find PPP or anything that says link to internet.  Please tell me if I have to download some program that will do that for me with this software.  I read the FAQ but it says nothing in there about that unless I am so frustrated I missed it. I am finding linux very frustrating to use.  Thanks in advance for telling me.  Grandpapop

---

### Post by Jason_25 on 2006-02-25
Welcome to the forum.  Do you use dialup internet?  If not, tell us a little more about your internet provider.

---

### Post by Grandpapop on 2006-02-25
Hi Jason,  I am using a computer I had built with 900 mhz AMD chips and the modem is an outboard U.S. Robotics Sportster with a 33.6 Faxmodem to an extremely slow dialup provider.  I link at either 24,000 bps or 21,600 bps.  I have used Mandrake and Red Hat and have been able to get on the internet with both of them with the computer and modem as I have them now.  I have been trying to figure out how to download plug-ins and get the browser to recognize them with both Mandrake and Red Hat.  Red Hat I have totally struck out and Mandrake I have some plug-ins but not the right ones so I can make the sites that I go to on the internet work correctly.  I read in PC World that either ubuntu or xandros are the distributions to try that are the most user friendly.  I have Xandros but can't make it work either so now I am at Ubuntu trying to see if I can make it work.  I can't even get it on the internet.  I can't find what I have to hit to get there.  I suspect there is something that I have to download.  Thanks for answering me.  
Cordially,
Grandpapop

---

### Post by xhie on 2006-02-25
[QUOTE=Grandpapop]I can't even get it on the internet.  I can't find what I have to hit to get there.  I suspect there is something that I have to download.  
Grandpapop[/QUOTE]

LOL...

nah the fine people at ubuntu are nicer than that. 

um... I have nothing helpful to offer though..

---

### Post by Jason_25 on 2006-02-25
I believe gnome-ppp is the program you need to get connected.  You'll need to click system > administration > synaptic package manager.  Once it opens, search for gnome-ppp.  Once you find it, right click and choose install.  Then hit apply.  Synaptic should then install it from your ubuntu disc.  You should then be able to find it in your menus.  If not, you can always open it from the terminal by typing gnome-ppp.

---

### Post by Grandpapop on 2006-02-25
Hi Again Jason,  I did exactly what you said and no luck.  For some reason it's not on the cd that I have or at least I can't find gnome-ppp.  For some strange reason I get frustrated with linux and then I lose it all together.  I think I better set this stuff aside again for a while and come back to it later.  I have been on this earth just about 66 years now and I think that linux and freeBSD are the most frustrating things I have run into since digital.  I know analog with no problems and I can fix that but digital is another story.  Now I am finding linux and freeBSD to be of that same ilk and it doesn't seem to make any difference  what distribution I use, they are all the same.  Not user friendly enough for me.  I have wanted to get away from windows for a long time so I guess I better dig up a can of money from the back yard and go buy an Apple.  Have a great day and thanks so much for being nice to me and answering my question. 
Cordially, 
Grandpapop

---

### Post by nikopol on 2006-02-25
Does System > Adminstration > Networking not give you anything?

---

### Post by Jason_25 on 2006-02-25
I think the source of your frustration is that most os'es, linux in particular due to being network-centric, have moved away from dial up.  Basically, if you want things to be easy, just use broadband like many others.  Dial up has officially become a niche category.

---

### Post by Grandpapop on 2006-02-26
Hi Jason,  This is a different day now and it doesn't quit look as bad this morning.  I live way in the boondocks in Minnesota and I can't get anything but dialup unless I go to the satellite.  I don't want to pay $59 a month for just downloading.  From what I  understand I have to have a dialup also for uploading with the satellite.  Way to much money for this retired old man.    You are right about not wanting dialup any longer.  If I buy an Apple I would have to get a special modem so I could have dialup with that.  They are made for the fast internet now.  I can get two other internet providers besides satellite but they are both dialup at $19.95 a month.  I guess soon I will beable to get WMconnect at $9.94 a month.  I will look at another distro of linux and see if I can figure it out.  Thank you so much for answering my question and also for being nice to me.  On one of the other distro beginners places all they are is mouthy kids on there and come back with wise answers.  I appreciate you being nice to me.  Have a great year and again thanks.  Grandpapop

---

### Post by Grandpapop on 2006-02-26
Hi Nikopol,  I went to where you said and the dialup connection is there and now I have to figure out how to fill it in and when I do that, I would guess I will be able to connect.  Thanks so much for the information.  Have a great year.  Grandpapop

---

### Post by CYb3R on 2006-02-26
I have ubuntu 5.04 i modem Agere Lucent... I hear that i can't do anything to install modem... Is that true?!

---

### Post by nikopol on 2006-02-27
[QUOTE=Grandpapop]Hi Nikopol,  I went to where you said and the dialup connection is there and now I have to figure out how to fill it in and when I do that, I would guess I will be able to connect.  Thanks so much for the information.  Have a great year.  Grandpapop[/QUOTE]
I you need any help filling it in, please ask us here :) Will be glad to help you if I can...

All the best

---

### Post by nihilocrat on 2006-02-27
From the Network settings screen you should see "Modem connection" available. Click that, click "Properties", and in the window that pops up, click "enable this connection". Fill in the fields in this window with the information you get from your ISP (phone number, login name and password). Click on the "modem" tab and make sure "modem port" is "/dev/modem". Look at the other tabs and see if there are any settings you want to turn on or off. If you're not sure what they do, then just leave them.

Click "OK" and then, with "Modem connection" still selected, click "activate" in the network settings window.

I hope this helps.

---

### Post by stanz on 2006-02-28
Hi All, Hi Grandpapop,
I hope your having SOME FUN, learning...a new trick!
I hear your words, about user friendly...but- the words- "More Secure & Stable",
keep me "Linux".
I've got both, Xandros & Ubuntu, working from my box, and straightout 'buying' a 'external serial modem', made everything easier.
As a 'newbie' myself, I'ld tell ya to read this guide first- "[Click Here]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialupmodemhowto%29")" - then decide for yourself.
I WANT to learn command line more... so "wvdial" was my first try, & a very easy one!
From there, ya can pick your panel launcher of choice.
Most of all, Grandpapop... try to have fun!    \\:D/
Hope it goes well- check ya later!

---

