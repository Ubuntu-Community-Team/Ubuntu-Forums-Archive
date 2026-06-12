---
title: "ubuntu floppies?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by pickle521 on 2007-06-03
is there any way i can get an ubuntu install floppie or create some ? and if i do get some will that also install a cdrom driver?

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> is there any way i can get an ubuntu install floppie or create some ? and if i do get some will that also install a cdrom driver?

does your computer not have a working cd drive? because you'll probably need several hundred floppy disc's

---

### Post by pickle521 on 2007-06-03
i cant find the right driver so thats y i need floppies unless u can find me the right driver

---

### Post by overdrank on 2007-06-03
> **pickle521 said:**
> i cant find the right driver so thats y i need floppies unless u can find me the right driver

Hi and what driver are you looking for? For what piece of hardware I should ask?

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> i cant find the right driver so thats y i need floppies unless u can find me the right driver

are you sure the bios is set to boot from the cd drive first?

---

### Post by oilchangeguy on 2007-06-03
> **overdrank said:**
> Hi and what driver are you looking for? For what piece of hardware I should ask?

you might want to re-read the users first post. he mentions needing a driver for the cd drive.

---

### Post by Carbonfish on 2007-06-03
Does your CD-ROM drive work now, or with whatever OS you were/are using before you decided to try Ubuntu?

If so, you shouldn't need drivers. Just set your BIOS to boot from the CD-ROM drive before anything else and put the Ubuntu Live CD in the drive and hit the power button.  ;)

---

### Post by pickle521 on 2007-06-03
1 my bios is password protected and 2) my laptop is a dell inspiron 5000e so i dont no what driver to get and 3) its secondhand so i dont no the bios password finally 4) i reformated it because it had a virus that kept reseting so now my laptop is in ms-dos so i need a driver or a linux floppie

---

### Post by northicert on 2007-06-03
click system.
click preferences
click removable drives and media
select first 3 boxes to use floppy disks.

---

### Post by tdrusk on 2007-06-03
> **pickle521 said:**
> 1 my bios is password protected and 2) my laptop is a dell inspiron 5000e so i dont no what driver to get and 3) its secondhand so i dont no the bios password finally 4) i reformated it because it had a virus that kept reseting so now my laptop is in ms-dos so i need a driver or a linux floppie

In that case...

> Check it.

[http://home.eunet.no/~pnordahl/ntpasswd/](http://home.eunet.no/~pnordahl/ntpasswd/)

Download the cd iso and burn it to a cd using your favorite program. (I use roxio cause it came with my PC and i am cheap.)

Insert the CD into the drive and boot your computer. You will then be brought to a screen in which you will be asked to download the drivers, select your partition, select you username, and change the password.

THIS WILL ONLY ALLOW YOU TO CHANGE IT!

BTW Windows administrative password has a 120 day freezing period. If you dont use it for that amount of time IT WILL LOCK YOU OUT.

This program will allow you to disable the password lock so make sure you select this option.

Hope this helps 

copied from [http://www.techspot.com/vb/topic50281.html](http://www.techspot.com/vb/topic50281.html)

---

### Post by Carbonfish on 2007-06-03
Unfortunately, if you can't get at your BIOS due to password protection in order to change the boot order, I don't know of any way to help you. Perhaps someone else here is more creative than I am. 

Good luck.

---

### Post by Feba on 2007-06-03
you should be able to reset the bios by fiddling with the motherboard, if you can't do that it's probably a lost cause. Trying to install Ubuntu from floppies would be like trying to cook a buffet of fried rice one grain at a time.

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> 1 my bios is password protected and 2) my laptop is a dell inspiron 5000e so i dont no what driver to get and 3) its secondhand so i dont no the bios password finally 4) i reformated it because it had a virus that kept reseting so now my laptop is in ms-dos so i need a driver or a linux floppie

go to dell's website, and see if you can locate the owners manual for this computer. and find out how to remove the cmos battery. this should reset the bios to the default settings (no password), and floppie is wrong, it's floppy.

---

### Post by Chayak on 2007-06-03
Well I know that particular model will work with Ubuntu.  No driver is needed, but what you do need is to look on support.dell.com and find out how to reset your bios which will no doubt involve taking it apart.  On boot it should have no problem seeing the CD-ROM as it's simply bios at that point.

---

### Post by pickle521 on 2007-06-03
were can i get a cd driver for this type of laptop

---

### Post by Carbonfish on 2007-06-03
It might not hurt to take a couple of minutes and do a Google search for "reset BIOS password." Maybe also enter the model # of your Dell, etc.

I know that this won't be helpful, but it's a good idea to keep your passwords somewhere that you can retrieve them if something gets FUBAR.

Again, good luck.

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> were can i get a cd driver for this type of laptop

have you NOT been reading the previous posts? you DO NOT need a FREAKIN driver. you need to be able to reset the bios!!!!!!!!!!!!!

---

### Post by oilchangeguy on 2007-06-03
> **Carbonfish said:**
> It might not hurt to take a couple of minutes and do a Google search for "reset BIOS password." Maybe also enter the model # of your Dell, etc.

I know that this won't be helpful, but it's a good idea to keep your passwords somewhere that you can retrieve them if something gets FUBAR.

Again, good luck.

read post #13 for info on how to reset the bios password.

---

### Post by pickle521 on 2007-06-03
were can i find the cmos battery

---

### Post by Carbonfish on 2007-06-03
Thank you oilchangeguy for pointing out that you had already provided instructions on how to reset the BIOS.

I was just trying to gently let the OP know that this wasn't rocket science and that she (or he) could probably easily find the information he (or she) needed with a simple search.

KC

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> were can i find the cmos battery

in a laptop it's usually under the keyboard. somewhere on the motherboard, but you'll need to know how to take apart the laptop to get to the cmos battery. that's why i've, and other posters have suggested you go to dell's website to find info for your computer.

---

### Post by Carbonfish on 2007-06-03
Also, I just did a quick Google search for "cmos battery dell inspiron" and it came back with 157,000 links. I am sure that one of them will have very good battery  removal and installation instructions.

Continued good luck.

---

### Post by louieb on 2007-06-03
> **oilchangeguy said:**
> have you NOT been reading the previous posts? you DO NOT need a FREAKIN driver. you need to be able to reset the bios!!!!!!!!!!!!!
AMEN brother oilchangeguy! I haven't seen a CD driver since the days when the 486 was king.

---

### Post by Feba on 2007-06-03
Pickle, to be honest with you, your best chances are to either take it into a shop or just buy a new laptop. Your posts have shown that you either don't understand or don't care about instructions, and if you take it upon yourself to open your laptop, there's a very good chance you'll mess it up horribly.

---

### Post by oilchangeguy on 2007-06-03
> **Feba said:**
> Pickle, to be honest with you, your best chances are to either take it into a shop or just buy a new laptop. Your posts have shown that you either don't understand or don't care about instructions, and if you take it upon yourself to open your laptop, there's a very good chance you'll mess it up horribly.

RIGHT ON!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Synt4x_3rr0r on 2007-06-03
Why not use a bootfloppy or something? Then you could select to read from the cdrom drive instead of the harddrive.

---

### Post by oilchangeguy on 2007-06-03
> **Synt4x_3rr0r said:**
> Why not use a bootfloppy or something? Then you could select to read from the cdrom drive instead of the harddrive.

now that's just to helpful. "use a boot floppy or something". the users problem is the computer is set to boot from the floppy drive first. and this can't be changed because the bios is password protected. this has nothing to do with the hard drive. please read the entire thread before you post.

---

### Post by Chayak on 2007-06-03
> **oilchangeguy said:**
> now that's just to helpful. "use a boot floppy or something". the users problem is the computer is set to boot from the floppy drive first. and this can't be changed because the bios is password protected. this has nothing to do with the hard drive. please read the entire thread before you post.

People have explained what the solution is  There isn't very many installs anymore that will work off of a floppy.  If he wants to use Ubuntu then he needs to get someone with the tech knowledge to reset the bios as it appears he hasn't followed your and read the answers to his problem.

---

### Post by Lucifiel on 2007-06-03
Go bring it to a hardware shop. Ask them to reset the bios for you and tell them that you have been locked out of the bios.

End of story. You do NOT want to pull apart your own computer if you don't know how to.

---

### Post by oilchangeguy on 2007-06-03
> **Chayak said:**
> People have explained what you need to do.  There isn't very many installs anymore that will work off of a floppy.  If you want to use Ubuntu then get someone with the tech knowledge to reset the bios for you as it appears you haven't followed your own advise and read the answers to your problem.

and you're quoting me because? i'm not the one who started this thread. i'm one of many whose tried to direct the user in the right direction. maybe you also need to read the entire thread before you post.

---

### Post by pickle521 on 2007-06-03
i just have 1 more question is there a reset kind of button because i tried taking apart the laptop but the thermal cover wont come off

---

### Post by oilchangeguy on 2007-06-03
> **pickle521 said:**
> i just have 1 more question is there a reset kind of button because i tried taking apart the laptop but the thermal cover wont come off

no

---

### Post by Lucifiel on 2007-06-03
> **pickle521 said:**
> i just have 1 more question is there a reset kind of button because i tried taking apart the laptop but the thermal cover wont come off

Errrr... it seems you have no idea on how to take apart your laptop. Try reading some guide for your laptop model or bring it to a shop?

Because it's very easy to spoil the laptop by accidentally pulling apart the wrong things. If something broke, how're you going to put it back? Better to let a seasoned hardware guy have a go at resetting the bios.

---

### Post by southernman on 2007-06-03
Please OP, do NOT take your laptop apart. Do as many have suggested and take it to a shop... If you venture into these uncharted territories, you are really going to have an I-D-10-T error.

---

### Post by Lucifiel on 2007-06-03
> **southernman said:**
> Please OP, do NOT take your laptop apart. Do as many have suggested and take it to a shop... If you venture into these uncharted territories, you are really going to have an I-D-10-T error.

Or even worse, break something and end up destroying the entire laptop. Man, that'd be money gone down the drain!

---

### Post by HotShotDJ on 2007-06-03
I did a quick google search and found very explicit directions on how to disassemble an Inspiron 5000 and where to find the CMOS battery.  All on the very first page of search results.  I am not posting my search terms or any of the results simply because, based on this thread, I'm convinced that you will break your computer beyond any hope of repair if you attempt to do it yourself.  Do not feel put off by this observation.  Most people are not able to repair computers.  Please spend the money and have somebody do this for you.

(EDIT: removed gratuitous flame that after thinking about it was unattractive and rather smarmy on my part.  My apologies to the forum for that laps of judgment.)

---

### Post by southernman on 2007-06-03
Depending on where you are, I'll offer to do this for you. Just pay shipping both ways.

If interested, PM me.

---

### Post by Feba on 2007-06-03
honestly man... just take it to a shop. They can probably do it for you in a matter of minutes. Much better than breaking it.

---

