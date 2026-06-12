---
title: "AOL Help (I have searched high and low)"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by aandeuk on 2006-08-22
Im a bit of a noob to linux and installed ubuntu a few days ago on my system and have managed to get most things to work, but not this. I have searched both this forum and the net for most of the day, but cant find a solution anyware. Let me explain.

Im on AOL in the uk using a "BT Voyager 190 ADSL **Modem**" (taken right of the modem). But...it connects to my computer via the ethernet post. Im in a bit of confusion over this point because i thaught it was just router thru ethernets, but anyway....

Im not such a noob, in the fact that i know that AOL software wont work on linux. I just cannot find a work around/way to get AOL to work with this modem/router, that is if there is a way.

I have tried to enter my username and pass into it, but when i use the [http://192.168.1.1](http://192.168.1.1) (or whatever the ip is) i just get an aol test page with noware to input details. This is why i am confused as to weather it is a router or not.

Any help on the topic would be great as i cant get it to work at all. Even if its only to tell me its a lost cause.

Thank you either way

Anthony

p.s - i love ubuntu, big thank you to all the developers :KS :KS

---

### Post by msak007 on 2006-08-22
I would try the Technical Help Center (link is in the pink banner on the [BT homepage]("http://www.voyager.bt.com/index.html")). I couldn't find any references to the 190 modem, but I took a quick glance through the help center and saw a few useful guides and answers. I know you already tried the 192.168.1.1 thing, but that's really the only way to get to the configuration page if you're plugging in using ethernet. Clear out your internet cache, power cycle the modem, make sure the DSL light is on, then try again. [Here]("http://www.voyager.bt.com/selfhelp/shc/ethernetinstall/connect.htm") is what they have to say about connecting to your ISP - if you're plugging your modem in via ethernet, there's no software to install and it's all a matter of configuring it via your browser. If that doesn't work, post a screenshot of the page you get when you go to 192.168.1.1 (the one you say is just an info page).

EDIT: Didn't realize it was your first post :). Welcome to the forums and Ubuntu.

---

### Post by aandeuk on 2006-08-22
As far as i have been able to find out, the 190 was discontinued and replaced by the 205 (which i have found a guide for by the way). The only real difference i think is the fact that the 190 does not have a usb port. trust aol to give away old hardware. :twisted: 

I did the [http://192.168.1.1](http://192.168.1.1) trick, but it just comes up with a cannot find server. If i delete a .1/ i get the below screen.

[IMG]http://i96.photobucket.com/albums/l199/aandeuk/screen.jpg[/IMG]

Weather im signed on of not makes no difference

Thank you for your help and the welcome. I get the feeling i may be here quite a bit :D :D :D 

Anthony

EDIT - I have just found this site - [http://www.routertech.org/viewtopic.php?t=372&sid=fc81663cada0c414c6492cbee158ed85](http://www.routertech.org/viewtopic.php?t=372&sid=fc81663cada0c414c6492cbee158ed85) - and aparently AOL 190 modems were locked????? what does this mean in real terms, dosnt sound too good to me ](*,)

---

### Post by msak007 on 2006-08-22
I'm not sure I understand then...are you online or not? Not sure why 192.168.1.1 would say page not found though - mine does because my router's IP is 10.x.x.x but it seems the default for the Voyager's is the same as Linksys (192.168.1.1). Anyway I've never known ISPs to lock their modems / routers to their services (until now), but that makes sense if you're not able to configure anything because your account was hard-coded into the router (that's how I understood it anyway). It reminds me of evil cell phone companies that lock their phones so you can't hop to another provider :twisted:. 

So anyway hopefully you are online and posting from your Ubuntu machine :). And don't worry about posting lots of questions...as long as you've made a genuine effort at searching first (see the 2nd link in my sig below :biggrin:) then people will go out of their way to help you.

---

### Post by aandeuk on 2006-08-23
Ive given up with the router. Im just goin to dig out my old voyager 105. At least i will be online that way.

luckly i hade the fore sight to dual boot.

Cheers for your help mate

Anthony

---

### Post by msak007 on 2006-08-23
Have you tried contacting their technical support to inquire about configuring the modem? Maybe there's some sort of master reset you can do that'll reset everything back to default so you can reconfigure it. If you have another device you can connect with I wouldn't worry about it for now, but I'd still look into finding out why it's not working.

---

