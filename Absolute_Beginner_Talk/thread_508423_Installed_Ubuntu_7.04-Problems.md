---
title: "Installed Ubuntu 7.04-Problems"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Francis60 on 2007-07-24
I just installed Ubuntu 7.04 on my laptop and having problems with the internet and wireless- first I am on dial-up at home, so I guess that will not work. Now I am trying to get the wireless internet to work, which I guess i have to do where I get wireless service. I am completely new at this and also not that good with computers anyway, so this is a double problem for me. I just thought I would like to try Ubuntu as I have heard so much about it.
I guess Ubuntu is all about getting drivers from sources that enable it to work with different things.
Right now my lap top is in Business Staples and an tech there is going to install the wireless for me-I hope- this is the third time I took it there and get different stories each time on different things.They never tell me the whole story at once how it should be done. I ended up downloading Ubuntu myself and made it so that I can reboot with Windows or Ubuntu so I will have both until I get all this figured out.
Anyway for now I will read all I can and check your ideas and hope for the best.

Allan

---

### Post by sad_iq on 2007-07-24
Well we can't really help until you give us more details...like what hardware you have, what wireless card you have...and posting what thew repair guy told you could give some light here...maybe your card is not linux friendly...who knows? Or better yet...when you get your pc back open a terminal and post the output of ```
lspci
``` Maybe we can help you then!!!

---

### Post by Francis60 on 2007-07-24
Thanks- I will let you know and also will hope it works when I get it back.
I told you though I did not know much about computers- I see the word "Open Terminal" a lot- do not know what  that means or how to do it- sorry
Thanks
Allan

---

### Post by sad_iq on 2007-07-24
Well can't really tell you how to open the teminal because I don't use gnome...so...i don't know where it's placed...just look thru the menus...can't miss it!
Also...we make use of it and type a lot of commands because it's easyer, faster(faster than click that, click here then there..) and we don't need to know where all the programs are placed in the menus. But don't worry...usually just copy-paste should be enough to get you thru the day :)

---

### Post by Francis60 on 2007-07-24
Thanks for your help 
Allan

---

### Post by RomeReactor on 2007-07-24
Hi. As I understand this, your laptop is in Staples being fitted with a wireless card, and it has Ubuntu and windows in dual boot, correct? If this is the case, as you said yourself, for now all you can do is read information in these forums, so you'll be more accustomed to the way people will give you answers to your questions, and since I imagine one of your first priorities will be to enable wireless internet for your laptop, you'll be getting a quite a few commands to be entered into the terminal.

Just for future reference, ubuntu has three menus located in the top left of the screen:

* Applications
* Places
* System

The terminal will be located in **Applications->Accessories->Terminal**. When you get it back, be prepared to copy the commands posted and paste them in the terminal--either by using the mouse (right-click, "Paste"), or by pressing SHIFT+INSERT on your keyboard.

Since the tech people at Staples haven't told you what card you'll have, there's the possibility that it could turn out to be one of the supported models, so you won't have to fiddle with the command line to install drivers for it. We can only hope this is the case, for the moment.

Good luck, and welcome to the forums! :KS

---

### Post by Francis60 on 2007-07-24
Thanks for input- I will let you know what is what . i will be talking to tech soon to make sure all things will work before he does anything and try to get the answers up front instead of him telling me something after the fact that he could have done , but did not,because he did not know what i wanted. 
Allan

---

### Post by Bartender on 2007-07-24
It might be helpful if people could volunteer some popular wireless and dial-up PCMCIA cards for the OP.  I'm pretty sure there are hardware-based dial-up cards for lappies that work with Linux, aren't there?
Dial-up is possible, you'd just have to have either a PCMCIA card or a USB external modem.  A USB modem that works; most won't.  
There's some fussing around with software settings (here are some [ideas]("http://ubuntuforums.org/showthread.php?t=480717") from duncan and me), but nothing too difficult.  
The modem must be recognized and compatible, and your ISP must cooperate.  If you're on AOL, MSN, PeoplePC, Juno it'll be difficult to impossible.

Do you have broadband at home also?  Or is the wireless so that you can at least get online somewhere else, such as school, work, etc.?  I'm not clear on whether you'll happily abandon dial-up as soon as you get the wireless working, or if it'd still be nice to have dial-up too.

The Zoom 3095 looks like a really neat USB modem, especially for laptops.  It's a brand new product and I'm hoping to hear someone post with a report on how it works.

---

### Post by hyper_ch on 2007-07-24
As you are new to ubuntu I think you should have a read at this here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It's an excellent guide on getting to know the most important things the newbies have problems with.

It's not really helpful with your wifi problem but it will give you answers to lots of other questions that will arise ;)

Btw, once you know what wifi card you have, we can help you - if it is needed ;)

---

### Post by Francis60 on 2007-07-24
Thanks for those messages- when I get my lap top back-working I hope- I will look into these things.
Where I live I can only get dial-up, so when I do get my lap top to work wireless, it will only be good where i can get the air waves- this will help when I am holidays etc.
I have heard about the external USb for dial up and will look into your suggestions.
I am also hoping that when it works the Ubuntu will work with my wireless printer and D-Link wireless router at home. It does work in the window XP mode.
Anyway I will have to work on things like this and with everyone's help as I am very new at this.
Thanks to everyone
Allan

---

### Post by Francis60 on 2007-07-24
Hi tjhere
I got my lap top back with wireless working-My lap top is a HP Pav. ze2000 WindowsXP-AMD Sempron- Proc 3000- 1.79 GHz, 1g Ram- 40G hardrive.
Wireless does work now where I can get signal and it also works with D-Link wireless router at home. They installed  wireless modem- Ndiswrapper.
They could not get a dial up modem so I bought a external  modem- U.S. Robotics- 56K USB Faxmodem.Have not installed yet until I make sure it will not uninstall my data fax modem I already have in there which works with my windows. Not sure if I can have both in there and not sure if the new one will work with Windows and also my Hotfax program. at this point I do not want to mess up my windows.
Anyway for now things seem to be getting better and will have to just keep working on it bit by bit.
In the meantime I have lots of info to look into that everyone suggested to me.- Thanks
Allan

---

### Post by hyper_ch on 2007-07-25
Oh, you got a wifi card with ndis-wrapper... this means if you resetup linux you'll also need to install ndiswrapper again. I'd recommend you to ask the guys how they installed it, so that you can do it next time yourself. That way you can have a running ubuntu and have access to the internet where you can ask for help without being required to boot into windows :)

---

### Post by Francis60 on 2007-07-25
Hi there- good idea- it is working fine now, but ya if I have to reinstall for some reason I should know  all about it
Thanks
Allan

---

### Post by Francis60 on 2007-07-28
Hi there-just an update.
 First- The NDIS-Wrapper wireless was already in the add/remove program, but because I could not get on the internet I could not have installed it anyway. The tech hooked up to his ethernet cable service, which I do not have out in the country. It works fine now,where I can get waves.
As for dial-up the first external modem I tried did not work.
I got Zonet 56K V.92 PCMCIA Modem Card and it works fine  with Ubuntu. Someone earlier had mentioned about using these cards- so they do work- at least the I got does anyway. I had to buy this one, but maybe there is an open version which would be the same as this. I do not know enough about this to know that, but I am sure someone will be able to come up with one.
Thanks again for all your ideas.
Allan

---

