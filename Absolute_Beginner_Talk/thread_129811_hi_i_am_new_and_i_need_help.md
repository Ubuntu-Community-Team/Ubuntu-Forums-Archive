---
title: "hi i am new and i need help"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-02-14
When my laptop was running right I downloaded the newest ubuntu with the intentions of putting it on my old itel system but apparently I dont have enough gigs for that or the harddrive is damaged(kinda the reason I stopped using it) now my laptop is running superslow and I am fed up with windows I have an xp system amd sempron processor. I have been trying all morning to install ubuntu but the system just starts windows. On the defective intel box ubuntu started installing as soon as I put the cd with the iso on it after I restarted the system but not this laptop.

How can I get windows xp off and get ubuntu on?

Also I have found most of the alternative programs but will ubuntu recognize my cdrw burner/usb ports?

Also I connect to the internet via wireless connection on my laptop in my home dsl network, the system says its a broadcom 802.11(I think those are the numbers) internal wireless card. So will ubuntu also recognize that?

does ubuntu have a web browser built in b/c I want to be able to download the programs like burning software and opera and firefox and a mail program and gaim since there is no trillian for linux.

And one final question for now, what is a launcher? I read its to install programs but this will be like learning a new language to me.

Sorry for all the questions but I want to be sure I can dump windows once and for all starting with my laptop.

---

### Post by mednamot on 2006-02-14
well, my guess, on the first part of your post, is that you don't have the cd-rom set up to be your first boot place, which is done through the bios (on my gateway I hold F2 during boot).

For the rest - I have not had a single issue with anything being recognized, except for my 2wire wireless G card.  For that I'm thankful I have an Orinoco card (B) and I'm slowly working my way through getting the 2wire card to work.

I believe from what I've looked at your broadcom chipset should be supported.

Firefox comes packaged with Ubuntu, just without any plugins (I believe), but you can also use the Automatix script thing to install everything you want (saved me a ton of time from last time I ran Ubuntu)

I'm a pretty fearless guy when it comes to my computers, so I say go for it (one box at a time so you have access to the net with the other) as long as you have an XP disc to fix yourself if you find Ubuntu won't work

---

### Post by rfruth on 2006-02-14
Will the laptop boot *any* CD (ya may have to change the boot order in the BIOS)

Yes Ubuntu should / will recognize your cdrw burner/usb ports/ wireless card
and yea there is a built web browser (Firefox, but you can use pretty much any browser U like)  :???:

---

### Post by rjwood on 2006-02-14
I went cold turkey like you want to do. I do not regret it but, there is a learing curve. Be prepared to put in some time and effort if you want it working up to par. Alot of people wein themselves by dual booting. 

As for your install question. You may need to set your bios to boot from your cdrom. To do that, as the system is booting you will need to be pressing your 'esc' key or one of your 'f' keys to get into the bios. Once you are there you just need to set the boot to 'cdrom'.

If you install with your wireless card in the machine and are at home near the router,Ubuntu will probably set you up fine. But i'm not going to guarentee that.

Please make sure you take proper precautions by having your bootable disk or floppy for windows nearby incase you get stuck and are prone to panicking.. It may help to have another working computer nearby so you can log into the forums and get help.. Good Luck and welcome to Ubuntu:D

---

### Post by Sandlst on 2006-02-14
Hello, I can answer a few of your concerns here I think-

If the iso cd does not automatically come up when its in the cdrom drive when your computer starts, it makes me think your computer is not set up to boot from the cdrom drive first-to fix this, look for a message when your computer starts saying something along the lines of  PRESS (somekey) TO ENTER SETUP-this should take you into the bios setup of your computer, and looking around for a bit you should be able to find something along the lines of "boot order"- using whatever method is shown (probobly somewhere on the screen) move the entry you think is your cdrom to the top of the list-sorry I cant be more specific on this but there are many, many different bios(es?) out there and    each works diffrently.

If you do get to boot from the cdrom successfully I think it will have no problem recognizing your cdrw drive, as for usb ports I have 4 and it recognized all of mine with no problems.

Wireless network can be very tricky-its a real coin toss on whether it will work or not-if it is possible for you to "wire" it up manually starting out, then by following some instructions you hopefully can get wireless working, or it may work right out of the box for you, I really cant say.

Ubuntu does have an excellent web browser built in, however most of the software you download will not be from searching for it on the internet, but rather using the synaptic package manager or apt-get from a terminal, which is far, far easier.  Also I would recommend going to [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295) once you get it installed and internet working as this handy program will install many of the things you probobly will want (like cd burning, enabeling dma, being able to play dvds, etc).

Hope this helps!

ick in the 15 mins it took me to type that 3 other ppl answered.........wow, you gotta love this community :)

---

### Post by maddbaron on 2006-02-14
ahhhh boot from cdrom....i didnt do that. i assumed it would check the cd b4 proceeding...thanks for the heads up.

and yeah i am close to my netwotk b/c when i 1st started my laptop when i got it, my network was found right away.

i have my restore disks ready to go if need be.

is the Automatix script thing inside the iso also?


and cool it has firefox.

I think its best I go cold turkey, my windows is running so slow it won't even let me access my mp3's or wmv unless i wait a good hour. 

the music and films i can recover so i'll just start fresh my desktop is xp so if need be i can connect.

how much of ubuntu is command line? 

i think i'll spend the night reading the entire forum b4 i install...i just want my windows frustration to go away...

---

### Post by Bartender on 2006-02-14
madbaron -
Having your computer look to the cdrom before your hard drive is a function of the BIOS, that set of data stored on a little chip right on your motherboard.  BIOS is not dependent on your operating system or even your hard drive.  Pull your hard drive out entirely, start the computer, & you can still access the BIOS.
So, as the other guys said, you've got to get into BIOS and set the computer so that it looks to the CD drive 1st.  Otherwise it'll skip right by and go to your HDD every time.  Your other PC just happened to have the BIOS set up to go to the CD 1st.  Lots of people have their machines set up that way and either don't care or don't know enuf about BIOS to change it.

Just go to the sticky right at the top of the Beginner's forum and follow the post to Automatix.  It is not included in the install CD; arnieboy saw a need and addressed it.  There's a little bit of terminal work involved in starting Automatix.  Follow the directions carefully and you should be OK.  

You can use the command line for almost everything if you want or, once you have the machine set up the way you want it, you can pretty much mouse everything.  However, you'll do much better on these forums if you develop a working relationship with the terminal...

---

### Post by Derktoon on 2006-02-14
being a n00b myself (ive used fedora for about 4 months before scrapping it) MOST of linux seems to be in GUI form (Graphical user Interface) meaning that it looks all pretty with a mouse pointer and all. but im fair sure there are some things that only the command line are gonna do for ya.

---

### Post by mednamot on 2006-02-14
to be quite honest, I've found (both times I've installed Ubuntu, warthog and now breezy) that it's best to jump in with both feet (especially if you have a second computer that you can browse the net with) as there's no better way to fix something than actually HAVING to fix it.

Not that I've had any issues whatsoever...well, Breezy didn't like my way-way-outdated BIOS and it's APCI settings, but a quick BIOS update fixed it all.

---

