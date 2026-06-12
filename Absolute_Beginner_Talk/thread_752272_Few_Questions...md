---
title: "Few Questions.."
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by 124C41+ on 2008-04-11
Hi there im new the the Linux scene and have a few questions. My roommate suggested Ubuntu to start on and theres a few driver questions I have to ask. I have an Nforce drivers on my motherboard and was wondering if that would be a problem because my roommate told me it might. I also want to know what I can do for my graphics card drivers. I have a Radeon X1950 and ATI Linux support stops at X1900's and I haven't been able to find any 3rd party video drivers that run on Linux. Any suggestions? Thanks:)

---

### Post by bt224 on 2008-04-11
I would run the LiveCD (it will not change anything in your computer) and then see what doesn't work. Go from there. You may get lucky and there are no issues.

---

### Post by herbster on 2008-04-11
The X1950 works. You can check [https://help.ubuntu.com/community/BinaryDriverHowto/](https://help.ubuntu.com/community/BinaryDriverHowto/)

As for your motherboard, which exact model do you have? It shouldn't be a problem.

---

### Post by rogun on 2008-04-11
I have nforce chipsets on my motherboard and have never had a problem with them, although they may be different then yours (it's an Asus A7N8X-Deluxe, if you want to check.)

I'd follow bt224's advice about trying out the live cd. Also, you might want to wait until 8.04 is released, to save from having to upgrade soon, and since newer releases normally offer better hardware compatibility.

---

### Post by 124C41+ on 2008-04-11
Im sure its supported in the actual OS but im also looking for somthing to control clock speed and fan speed that works in Ubuntu. I dont remember the exact model number of my motherboard ill test it in the live CD. Can i burn the live version of Ubuntu to a DVD or no..

---

### Post by Koybe on 2008-04-11
> **rogun said:**
> I have nforce chipsets on my motherboard and have never had a problem with them, although they may be different then yours (it's an Asus A7N8X-Deluxe, if you want to check.)

Same for me, it works quite well. No problem at all.
You can also check this : _[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)_

---

### Post by herbster on 2008-04-11
> **124C41+ said:**
> Im sure its supported in the actual OS but im also looking for somthing to control clock speed and fan speed that works in Ubuntu. I dont remember the exact model number of my motherboard ill test it in the live CD. Can i burn the live version of Ubuntu to a DVD or no..

Yes, you can burn the live CD to a DVD. Monitoring speeds/temps is easily accomplished, controlling them takes some tweaking. I have personally not done it, but search extensively for this and you can find ways, scripts, etc.

---

### Post by 124C41+ on 2008-04-11
okay cool Im in the live CD now... I know i cant install anything here. Sound drivers work... But im not 100% sure my video drivers are working although they seem to be.

---

### Post by bt224 on 2008-04-11
You can install as many things as your RAM will hold, they will just disappear when you reboot and remove the LiveCD. Unless of course you install the entire OS.

---

### Post by mikewhatever on 2008-04-11
> **124C41+ said:**
> okay cool Im in the live CD now... I know i cant install anything here. Sound drivers work... But im not 100% sure my video drivers are working although they seem to be.

How can you not be sure? If the graphics driver works you should see a brown desktop with panels, menus, mouse pointer, etc. If it doesn't, there should be a black screen with command prompt. The difference it so significant that it's really hard to get confused. You can install stuff while using a Live cd, but the trick with drivers is that you have to reboot to get them loaded, so it would not work with a CD.

> Hi there im new the the Linux scene and have a few questions. My roommate suggested Ubuntu to start on and theres a few driver questions I have to ask. I have an Nforce drivers on my motherboard and was wondering if that would be a problem because my roommate told me it might. I also want to know what I can do for my graphics card drivers. I have a Radeon X1950 and ATI Linux support stops at X1900's and I haven't been able to find any 3rd party video drivers that run on Linux

I am very confused about that post, could you clarify a few things. Is there a storage device on your motherboard that holds nforce drivers? Nforce = Nvidia, right?  Are these motherboard or graphics drivers, in other words, what do you use them for?
ATI Linux support does not seem to stop with X1900. It says on the site X1900 Series, which, in my understanding means X1900 - X1999 or whatever versions there are. X1950 seem to fall nicely into that category. [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by 124C41+ on 2008-04-11
Nforce drivers are motherboard drivers.Meaning its for sound and things of that nature. And yes it is from Nividea. And I believe the X1900 driver your looking at only applies to that specific model. When you look at the windows drivers it goes all the way up to X1950 thats what I was confused about. And yeah I tired installing the ATI drivers and it wanted me to reboot and so obviously there gone when you go back. So i cant really test what these drivers do exactly... Weather they have to ability to monitor fan and clock speed I don't know.

---

### Post by herbster on 2008-04-11
Well, like I said, you'll have to search. Install the base system and just try the driver, see that it works right. At least you can get the understanding and experience before grabbing the newer Ubuntu version coming soon.

---

### Post by 124C41+ on 2008-04-11
K thanks guys. Ill just message you if have need of some immediate help! Thanks again. :)

---

