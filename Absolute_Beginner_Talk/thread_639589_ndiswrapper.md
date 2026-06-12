---
title: "ndiswrapper"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by chips24 on 2007-12-13
need windows for my school that requires IE., and my wireless dosnt word on linux and im too afraid that if i install NDISwrapper i wont be able to use the wireless card on windows.
__________________

---

### Post by Het Irv on 2007-12-13
Install away.  I was using NDISwrapper in 7.04 and did not have any problems with it working in Windows afterwards.  Even using the restricted drivers in Gutsy did not interfere with my Windows Wireless Cabilities.

---

### Post by Flare183 on 2007-12-13
I agree. I had some problems with my broadcom wireless card on ubuntu, but now it works on both windows and ubuntu.

---

### Post by chips24 on 2007-12-13
how do you install it

---

### Post by zeller on 2007-12-13
If I understand you correctly (implied), you have a dual boot setup? When Windows is running Ubuntu isn't and vice versa. Whichever you decide to boot into will be using the driver while the other OS is basically comatose.

That said, once you're done using Ubuntu and boot into Windows, Ubuntu will give up control of the driver weather wrapped with NDIS or not. Why shouldn't it, right?

I had NDISWrapper working in Ubuntu, briefly, and it never affected my Windows wireless experience.

---

### Post by chips24 on 2007-12-13
thankyou, this helps:)

how do you installit?

---

### Post by chips24 on 2007-12-13
how do you install ndiswrapper?

---

### Post by chips24 on 2007-12-14
thankyou, i got my nvidia card working, i still need to install ndiswrapper though, compiz is sweet!!!


happybuntu lol

---

### Post by chips24 on 2007-12-15
ok, i tried to install ndiswapper, but i wont show up on my menu, ive tried reinstalling it, checking the menu settings,... but nothing.

---

### Post by Flare183 on 2007-12-16
Join me in the IRC on #ubuntu ask there or more specifically you can talk to me directly on the irc on #ubuntu-us-sc

---

### Post by chips24 on 2007-12-18
ummmm, gibberish:-k:-k?

---

### Post by anewguy on 2007-12-18
If you installed ndiswrapper and the utilities (you need both) from the synaptic package manager, or for that matter from any other source, it doesn't show in the menu's because it is really sort of a set up once run forever kind of thing.  You access it through a terminal window.  Be sure to have a copy of the windows driver (assuming a .sys and a .inf - yours may have more) installed temporarily to your desktop, then do the following in a terminal window (Applications/Accessories/Terminal):

gksudo /etc/modprobe.d/blacklist <- press enter

  In that file, scroll to the end and add the following:

# blacklist the default bcm43xx driver
blacklist bcm43xx


  Then save the file and exit. 

- if you have not already done so, check in synaptic package manager to be sure network manager is installed (I think it will be called network-manager-gnome).  If not, install it.

- in the terminal window do the following:

sudo ndiswrapper -l   (that's a lower case "L") and press enter

if anything is returned, do the following:

   sudo ndiswrapper -r xxxxxxxxxxx  (xxxxxxxxxxx is what showed above) and press enter

sudo ndiswrapper -i  ~/xxxxxxxxxxx   (it's a lower case "I", and xxxxxxxxxxxxx is the name of the windows driver file you placed on your desktop)

sudo depmod -a

sudo modprobe ndiswrapper

Just for the heck of it - reboot now.

When you come back up the network manager "icon" should be in your upper bar.  Click on it to see if your network is now listed - this would indicate your wireless is working.  Just click your network and enter any WEP or WPA key you may set up (watch the default - it defaults to 128 bit encryption on the screen, and most I have seen are still 64 bit).

Let us know what happens.:)

---

### Post by chips24 on 2007-12-19
ok

---

### Post by chips24 on 2007-12-19
this isnt worth it.#-o

---

### Post by anewguy on 2007-12-19
Open the terminal, type it in and try it first - if it don't work THEN complain.

---

### Post by chips24 on 2007-12-19
ok

---

### Post by chips24 on 2007-12-19
i dont know what my Windoez driver is, all i know is that is that i have wireless card

---

### Post by anewguy on 2007-12-19
this probably seems like a real pain, and if you scan the forum for people with wireless problems with the broadcom 43xx series, you will see you are far from alone.  The process seems tedious, but it's what we have to do to try to get that chipset to play with Linux.:)

---

### Post by anewguy on 2007-12-19
> **chips24 said:**
> i dont know what my Windoez driver is, all i know i that is a wireless card

That's okay - let's try to find out - 

(again in a terminal window)

lspci


copy/paste the output from the back here and we'll try to see where to go from there!:)

EDIT:  I guess I jumped the gun on bcm43xx series - reviewed your post and found nothing was id'd yet, so if you post back what I requested with this entry we can hopefully go from there!

---

### Post by chips24 on 2007-12-19
> **anewguy said:**
> That's okay - let's try to find out - 

(again in a terminal window)

lspci


copy/paste the output from the back here and we'll try to see where to go from there!:)

EDIT:  I guess I jumped the gun on bcm43xx series - reviewed your post and found nothing was id'd yet, so if you post back what I requested with this entry we can hopefully go from there!


I DONT KNOW THE DRIVER !

---

### Post by anewguy on 2007-12-19
> **chips24 said:**
> I DONT KNOW THE DRIVER !

You need to calm down - my last post was NOT asking you to TELL me what your driver was!!  I was ASKING you to have Ubuntu LIST ALL OF YOUR PCI DEVICES (lspci) so we could see what the system thinks your PHYSICAL CARD is.  Once we find that out, WE CAN SEARCH for a driver.

You need to understand you are dealing with something a little more involved than going into a Windows machine and shoving in a CD.  If you are not willing to do this, just post back that you quit and close this thread.  Otherwise, PLEASE TRY TO FOLLOW WHAT IT BEING ASKED OF YOU.

---

### Post by chips24 on 2007-12-19
ok, first or all, i dont have any internet on  my Ubuntu,i using vista right now, i dualboot,i dont know how to find my "list of PCI devices",so i need detailed instructions.. I need to know how to find the names of the hardware im using, exactly what to do with that information, and how to use it, i dont know even the name of my wireless card, can you please help me find the name of the card, heres my stats; HP pavalion DV2000. AMD 64 Turion processor.
nvidia geforce go 6150, ok ... you get it, i will do some research some more, but i need you to be specific.

( i selected the wrong quote) sorry.:oops:[IMG]http://www.cnet.co.uk/i/c/blg/cat/laptops/dv2000.jpg[/IMG]

---

### Post by chips24 on 2007-12-19
found it ... Broadcom BCM94311MCG internal wireless card.

---

### Post by anewguy on 2007-12-19
> **chips24 said:**
> found it ... Broadcom BCM94311MCG internal wireless card.'

Okay, now we can start searching.  Just for your info, since you are dual-booting but have no internet access as of yet in Ubuntu (I assume the laptop doesn't have an ethernet port or you have no way to directly wire to the router),  doing the   "lspci"  in Linux will show all of your PCI devices and what they are for.  You wouldn't be able to copy/paste, but it will show you that information.

Thanks for getting the info ------  I'll do a little searching and get back to you hopefully in a few minutes.:)  Hang in there!

---

### Post by anewguy on 2007-12-20
Okay, I found a step-by-step guide for you.  It is for a different laptop brand, but that doesn't matter - the important thing is BCM94311MCG.  Now, before I post this link, I have to give you some bad news and a suggestion:

- it will require internet access on your laptop in order to do the install (not wireless, just access)

-So, do you have a friend or perhaps even someone at your school, who can help you by just running an ethernet cable from the router to your laptop?  If so, you can get on that way and then follow the instructions.  I sincerely hope you can find someone to get you hard connected via an ethernet port - do you have physical access to a router at home?

Okay, now that I'm done with the bad news and suggestion, here is the link.  If you have any questions at all, don't worry about feeling stupid or anything (it's called just a lack of knowing, and that isn't stupidity - we've all been there with one thing or another with Linux), just post back here.  We can help you get through it all.


here's the link:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

I sincerely hope you can find a way to hard wire your connection to do this.  Maybe if you took it to school and explained what you are doing they would help you there.

If you were close to me I would help you here, but since you appear to be in a different state it would be a little difficult!!

BTW - what part of MInn. are you in?:)



EDIT:  You may want to check with a local library - if they have public internet access maybe some tech there will hook you up to do what you need to.

---

### Post by chips24 on 2007-12-20
> **anewguy said:**
> Okay, I found a step-by-step guide for you.  It is for a different laptop brand, but that doesn't matter - the important thing is BCM94311MCG.  Now, before I post this link, I have to give you some bad news and a suggestion:

- it will require internet access on your laptop in order to do the install (not wireless, just access)

-So, do you have a friend or perhaps even someone at your school, who can help you by just running an ethernet cable from the router to your laptop?  If so, you can get on that way and then follow the instructions.  I sincerely hope you can find someone to get you hard connected via an ethernet port - do you have physical access to a router at home?

Okay, now that I'm done with the bad news and suggestion, here is the link.  If you have any questions at all, don't worry about feeling stupid or anything (it's called just a lack of knowing, and that isn't stupidity - we've all been there with one thing or another with Linux), just post back here.  We can help you get through it all.


here's the link:

[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")

I sincerely hope you can find a way to hard wire your connection to do this.  Maybe if you took it to school and explained what you are doing they would help you there.

If you were close to me I would help you here, but since you appear to be in a different state it would be a little difficult!!

BTW - what part of MInn. are you in?:)



EDIT:  You may want to check with a local library - if they have public internet access maybe some tech there will hook you up to do what you need to.


thanks , the library sounds best for me. thanks for youre help. i also have an older friend across the street that can help me, i have church friends that work at IBM, so i have resources. i usually use this site to  get preferences from other linux users, to double check, or hard core stuff that windozers dont know.  


BTW- i dont give my exact location to people, even to people i trust, hope you understand...:biggrin:



thanks again!

---

### Post by anewguy on 2007-12-20
> **chips24 said:**
> 
BTW- i dont give my exact location to people, even to people i trust, hope you understand...:biggrin:

thanks again!

Not a problem!!  When I was a kid back in the very early 60's we lived in Edina, then built a house in Brooklyn Center (that was out in the country then) and eventually built a house in Coon Rapids (WAY out in the country then).  We also lived in Fargo, ND, so I am a little rusty but still remember a lot of Minnesota.  I have a sister and her family that live near the twin cities, and my other sister and her family live near Fargo.  I used to love camping up north in the woods and fishing up there, but I understand all that has changed now.  Even my last visit, probably 8 years ago by now, things around Brainerd and Bemidji had changed a lot.

Please don't hesitate to ask any questions!  I was thinking of having you download the stuff on a Windows PC, burn a CD, take it to the Linux side and install everything, but that would be quite a bit more involved than if you can just get a hard wired link.

Let us know how it turns out!

---

### Post by chips24 on 2007-12-20
i do use my mp3 player to move applications to linux, its very quick.

---

### Post by chips24 on 2007-12-20
> **anewguy said:**
> Not a problem!!  When I was a kid back in the very early 60's we lived in Edina, then built a house in Brooklyn Center (that was out in the country then) and eventually built a house in Coon Rapids (WAY out in the country then).  We also lived in Fargo, ND, so I am a little rusty but still remember a lot of Minnesota.  I have a sister and her family that live near the twin cities, and my other sister and her family live near Fargo.  I used to love camping up north in the woods and fishing up there, but I understand all that has changed now.  Even my last visit, probably 8 years ago by now, things around Brainerd and Bemidji had changed a lot.

Please don't hesitate to ask any questions!  I was thinking of having you download the stuff on a Windows PC, burn a CD, take it to the Linux side and install everything, but that would be quite a bit more involved than if you can just get a hard wired link.

Let us know how it turns out!

got my dog in coon rapids.

---

### Post by chips24 on 2008-01-16
ok, i got my driver for my wireless installed, but i have no software to handle the internet connection...

---

