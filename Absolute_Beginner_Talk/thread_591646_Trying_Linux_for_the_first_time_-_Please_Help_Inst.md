---
title: "Trying Linux for the first time - Please Help Install"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by chunkylover21 on 2007-10-25
Hey guys this is my first time installing linux. I have the newest version of it downloaded from this site. I believe its Gutsy 7.10. I am installing it on a blank hard drive.

When I boot from CD I get the Ubuntu menu of options. I choose the top option to run/install. It loads for a while, then tells me the video settings were set to low and couldnt be loaded w/e no big deal. When I click continue though, it just takes me to a command prompt where I am able to type. It has the following lines, then the cursor at the bottom.

Starting differed execution scheduler atd [OK]
Starting periodic command scheduler crond [OK]
Checking battery state... [OK]
Running local boot scripts (/etc/rc.local) [OK]
_


Thats how my screen looks.

What do I do to get to the install for the Op Sys or atleast run it from the disc?

My system specs are

Gigabyte GA-P35-DS3L
C2D E6550
2gb Corsair DDR2 6400
160gb WD 7200 - IDE
ATI X1900 512mb

---

### Post by philinux on 2007-10-25
you need to post your full system specs for anyone to help.

---

### Post by taurus on 2007-10-25
If you want to install it on your machine, try using the alternate CD.  It's a text base but real easy to follow.  And what's the spec of your machine anyway?

---

### Post by lisati on 2007-10-25
> **chunkylover21 said:**
>  I believe its Gutsy 7.1.

BTW 7.10 actually.... the "0" is important because it was released in October, not Janurary

---

### Post by chunkylover21 on 2007-10-25
Alright I updated the original thread.

---

### Post by Technophobia on 2007-10-25
no video card? and did you "..try using the alternate CD.." ?

---

### Post by chunkylover21 on 2007-10-25
> **Technophobia said:**
> no video card? and did you "..try using the alternate CD.." ?

Fixed. ATI x1900XT 512mb

---

### Post by chunkylover21 on 2007-10-25
I used the alternate install disk, did the text based installation, and got this error: "Cannot install the base system. The installer cannot figure out how to install the base system. no installable cd-rom was found and no valid mirror was configured." What do I do now?

---

### Post by taurus on 2007-10-25
Did you run checksum to check the integrity of the CD and how fast did you burn it?

---

### Post by chunkylover21 on 2007-10-25
no i havent run the checksum. i burned it at 4x

---

### Post by taurus on 2007-10-25
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by chunkylover21 on 2007-10-25
its burned properly

---

### Post by twbdan on 2007-10-25
go into your BIOS and increase your video buffer from 1 to 8

---

### Post by chunkylover21 on 2007-10-25
im not getiing the video error anymore. just the cd rom one

---

### Post by chunkylover21 on 2007-10-26
I still have the problem guys. Cant install Linux... should it really be this hard..?

---

### Post by jd3010 on 2007-10-26
Did you try installing from a USB device, like a USB CD-rom  or even a USB HD.  Don't forget to change the Boot order in the Bios.

---

### Post by philinux on 2007-10-26
As you've got internet access. I would first check that you have the latest bios for your motherboard. If there is a new one download it on the machine your posting from and create a bios flash floppy as per the manufacturers instructions, and then use it on your proposed ubuntu machine.

---

### Post by candtalan on 2007-10-26
> **chunkylover21 said:**
> I still have the problem guys. Cant install Linux... should it really be this hard..?

Sorry to hear you are having such problems. No - it is usually trivially easy! I gave a live Cd to a (novice) friend recently in order to browse the web safely with it, and he went on to install it without knowing!...... :-)  :-( 

There are a number of usual issues - 
1) booting - is the CD booting ok - do you get the install choices menu etc etc?
2) the menu includes a 'check the CD' option. This is worth using (here because even if the CD is perfect, this test will help verify that the target CD drive can read it ok.)
3)  you said - "I used the alternate install disk, did the text based installation, and got this error: "Cannot install the base system. The installer cannot figure out how to install the base system. no installable cd-rom was found and no valid mirror was configured." What do I do now?"
Comment - this sounds like the CD contents are not seen as expected for a CD install (at least) and probably that an install over the net is not configured in its place - my guess. action - ensure CD and cd drive is ok.
4) your RAM is large so a normal live CD should work well. It may be worth trying - to verify things such as video settings - without committing to hard drive. Note there are many types of live cd, you could try ubuntu yes, also knoppix, and others. They may handle your machine slightly differently initially.
5) there are several things that can be simply done regards video settings: 
a) safe graphics mode (from initial boot menu) also:
b) at the base of the screen display there is a VGA option with alternatives. Might be worth a try at some time.

good luck

---

### Post by chunkylover21 on 2007-10-26
AT first I was using a IDE-UDB adapter for my DVD-Drive, but when i figured that may have been the problem i just ran the setup again with the DVD and Hard drive both on the same ribbon cable and still got the same error.

I have checked the CD condition and it said it was all good.

I do not have  a floppy drive to flash to a newer BIOS setting but the boards BIOS should really make the difference seeing as it runs the entire setup till that point.

Lastly do you think it may be the partition setting I am choosing? I choose the option that says something to the extent of "Use the entire drive"'

Should I be trying a different selection?

candtalan- i only got the video message when I was using the live CD, with the text based installer I dont get it. And when using the live cd i would be taken to a command prompt and it wouldnt load the OS.

Please guys I really dont want to spend $200 on windows and i want to try and learn a bit of linux.

---

### Post by candtalan on 2007-10-26
> **chunkylover21 said:**
> 
[snip]
candtalan- i only got the video message when I was using the live CD, with the text based installer I dont get it. And when using the live cd i would be taken to a command prompt and it wouldnt load the OS.


If it was a full command prompt that you can type into, then since this sounds like the stage of loading the video driver, then in theory it would be possible to do video configure stuff. However if as you indicated earlier you just saw a single flashing cursor, then it may not be a full command prompt, and I could not do much in that situation (recently). Except that is, to retry using Safe graphics mode (as I mentioned) and that did lead to a full command prompt, and I could then edit the driver. 
In my particular case the on board graphics was set to auto which was correct, but the PC had a separate graphics card which was being used. However, the on board graphics was not inhibited fully, not stopped from talking to the installer, so that is what it accepted. I had to tell the installed file that the driver should be for the separate video card, not the on board. In this case the lack of sophistication in the bios (otherwise working ok) probably caused the apparent problem. I have to admit that if I was a newbie I would have been well out of my depth at that stage!

good luck

---

### Post by chunkylover21 on 2007-10-26
> **candtalan said:**
> If it was a full command prompt that you can type into, then since this sounds like the stage of loading the video driver, then in theory it would be possible to do video configure stuff. However if as you indicated earlier you just saw a single flashing cursor, then it may not be a full command prompt, and I could not do much in that situation (recently). Except that is, to retry using Safe graphics mode (as I mentioned) and that did lead to a full command prompt, and I could then edit the driver. 
In my particular case the on board graphics was set to auto which was correct, but the PC had a separate graphics card which was being used. However, the on board graphics was not inhibited fully, not stopped from talking to the installer, so that is what it accepted. I had to tell the installed file that the driver should be for the separate video card, not the on board. In this case the lack of sophistication in the bios (otherwise working ok) probably caused the apparent problem. I have to admit that if I was a newbie I would have been well out of my depth at that stage!

good luck

right.. this has gotten me nofurther.

---

### Post by chunkylover21 on 2007-10-26
bump, please read through the thread to see the problem im currently on.

---

### Post by chunkylover21 on 2007-10-26
a friend of mine who actually knows what hes talkinga bot suggested trying another cd drive. a cd-rom instead of a dvd burner and its working now.

*installing*

---

