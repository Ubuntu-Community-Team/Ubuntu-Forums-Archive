---
title: "A few Generic Questions, Printer, Kernel, and Byrle"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-06-05
Hello everybody, Unfortunately I am back, and probably asking some really dumb questions.

The good news is I have been primarily running strictly Ubuntu for a month now due to the fact the windows install did not go so well [Link to what that is all about in case some one wants to try there hand there also]("http://ubuntuforums.org/showthread.php?t=463549&highlight=Sabar") but that is another story.

First question

 I have is about Drivers for printers, specifically about an HP Photosmart 3210.  The driver I currently have for that is > hpijs ( Recommended ). The other day while looking around at different things ( you see Curiosity is not always a good thing ) I went to [HP's Web Site]("http://h10025.www1.hp.com/ewfrf/wc/genericDocument?lc=en&cc=us&docname=bpu00659") and I found a page saying they had drivers for there products and windows. Hemm... wonder what they are.

After following the links, they led me to a driver named > hplip-1.7.4a.run Well I downloaded this. Now what do I do? I dont want to screw things up when I have them working. here is the bad thing I dont know if they really are. the printer works fine but I have an all in one and I have been scared to try the scanner and see if it works. the other thing is with windows the HP stuff has a lot of "features" like telling me the ink is running low. was wondering if that was available here. 

So the question is should I use this new driver? if so How do I install it? right now it is downloaded and sitting on my desktop. so where do I go from here?

Second Question 

This one is probably really dumb. I think after trying 6.06 I downloaded and installed Feisty fawn 7.04. and thats what i am running now so why is it on start up when the grub comes up and asks me what I want to run it says Kernel 2.6.20-16-generic? and there is no 7.04 listed any were?

Third and last for this string

Byrle. I have heard a few little things about it and I have even seen the clip of it being used ( set to music and all ) on another web site. So my question is how do I know if I have a 3-d Accelerator ( I think thats what its called ) that will work for it? I have an ATI Radeon X550 256MB PCIE Graphics Processor ( thats how it is listed from Alienware).  I tried to look it up once before but couldn't understand if my Video card was good enough. If it is good enough. how do I get it and install it onto my Ubuntu? 

Thanks any one for your responses. I know most of my questions are probably a little silly but please keep in mind I am so new at this and after running windows for so long ( and not really understanding that so well half the time ) I am kinda at a loss here every so often.

And remember. A little bit of knowledge can be a very very scary thing. 

P.S. accidentally added a word to spell check. is there a way to remove it from its library?

---

### Post by FleetAdmiral74 on 2007-06-06
About the driver thing, if the one you have seems to work, they by all means keep it. Was not to clear if that was a Windows only driver, or a linux driver.

About Beryl..
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
Is a pretty good guide, just make sure you follow nvidia or ati depending on what you have. It has fallback instructions in case you mess it up completely, these will SAVE you.

and btw there is a command, something like beryl --check, that only does tests to see if everything is ok, but try the guide, it worked well for me.

edit: same thing on bootup happens to me, seeing the two diff. kernals...just kinda annoying haha, no damage I guess...

---

### Post by Sabar on 2007-06-06
FleetAdmiral74

Well to answer your first question, about weather or not it is a windows or Linux driver. They are both Linux drivers. the reason I was asking about it was because I don't know if some of the features that are present when running windows would maybe be available then with Linux.  Like how much ink I have available in each of the tanks. 

The other thing is, I am not sure how to scan using Ubuntu. but that is for later.

After going to the Wiki guide for Beryl I have another question. 

> Step 1 : Edit your sources.list file adding

deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main 

to the bottom of it.

Whats a sources.list and how do I edit it?

---

