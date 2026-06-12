---
title: "OMG! SO MUCH TO DO, YET I CAN'T GET ANYTHING DONE! Help!"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by FlashEng1 on 2006-09-10
I hope my post follows the rules of this forum, I am very strict myself about posting in the wrong areas, but since I am a COMPLETE newbie at Linux, Ubuntu, and everything else included, I assumed this is the place to beg assistance for.

AHH!! First I become overwhelmed with "Shell this, tar.gz that, ADC ADHD FYI PCP" and EVERYthing.. There MUST be a guide (perhaps I am not looking hard enough throughout this forum and more?) that explains to the windows savvy how to completely understand the terms and usage in Linux! (Anyway, this isn't what I'm asking for, sorry for my complaining, and yes I have read a many articles).

WHAT I AM ASKING HELPPPP FOR! :

I have a CTX EZbook 800 series. It used to have Windows 98 on it, then I formatted and tried, but NO luck getting the video drivers or the usb jumpdrive drivers to work. So I figured "Windows 2000!" And read somewhere to just go with linux! Soooo HERE I am, a COMPLETE and utter noob to linux, it's shell and it's possibilites. Thank GOD the video drivers work (10x better thanks to linux), HOWEVER the following do NOT =( :

**1**. Sound Card (Honestly have NO clue the exact card type, but if Windows 95 can find it and assign it, I KNOW Linux can (something like a Creative AWE Wave blah blah blah))
**2**. NetGear Wireless PC Card 32-bit CardBusWG511 v1 (I can get that fixed, I might not be searching hard enough.)
**3**. Cruzer Micro 1.0 GB UBS JumpDrive... DOES NOT COME UP! I have to personally sit EVERYtime I connect it, and mount it myself to make it work, there HAS to be an automount program I have not found or something???

Well... Aside from my current mood and anger right now, I do apologize if I have violated any rules or guidelines... Problems 1 and 3 I feel are more important (as #2 I need to learn how to use Wifi in linux, along with how to even compile programs or use Python and all this crazy stuff I keep reading about), and if I could get assistance in finding SOME sort of article or another.

Thank you **ANYONE** for any assistance soooo much!!!!!!

---

### Post by Fingolfin269 on 2006-09-10
I was frustrated like you a couple of days ago.  I actually reinstalled Windows in frustration and then came to my senses, wiped Windows, and tried again.  I'm still having trouble with adapting to Ubuntu but now I'm looking at it as more of a challenge.  Hopefully you will get everything worked out. :)

I'm working on getting my Wifi up right now and if I finally figure it out I will let you know.  I've actually got the Wifi up and running (I assume this is the case since my network manager is detecting wireless networks) but am having trouble getting WPA capability installed and going.

---

### Post by catlett on 2006-09-10
Linux is an entirely different OS from windows. It is tailored after unix not windows. Unix is for giant computers. The mainframes of old and the servers of today. The system is for system administrators that are upkeeping multiple servers and hundreds of users. It is not mnade to be easy it is made to be powerful. That is why a unix administrator takes years of college courses in computer science. 
Windows is for the masses. The people who want to surf the web, play an mp3 or open an office document. It is a terrible operating system but it is 'easy' for the non-educated to use. 
The point is if you think you are going to just install and run linux or read one web page and understand the intricacies of the system, you are wrong.
So either prepare to open your mind and do some work or go back to windows. If you are deternmined to run linux, pay $40 and get Xandros. It is not free like Ubuntu but it is the easiest linux OS for a windows user to run, If you buy the premium edition for $80 you will get the most informative guide book any linux OS puts out. [http://www.xandros.com/products/home/products_home.html](http://www.xandros.com/products/home/products_home.html)

---

### Post by FlashEng1 on 2006-09-10
> **catlett said:**
> Linux is an entirely different OS from windows. It is tailored after unix not windows. Unix is for giant computers. The mainframes of old and the servers of today. The system is for system administrators that are upkeeping multiple servers and hundreds of users. It is not mnade to be easy it is made to be powerful. That is why a unix administrator takes years of college courses in computer science. 
Windows is for the masses. The people who want to surf the web, play an mp3 or open an office document. It is a terrible operating system but it is 'easy' for the non-educated to use. 
The point is if you think you are going to just install and run linux or read one web page and understand the intricacies of the system, you are wrong.
So either prepare to open your mind and do some work or go back to windows. If you are deternmined to run linux, pay $40 and get Xandros. It is not free like Ubuntu but it is the easiest linux OS for a windows user to run, If you buy the premium edition for $80 you will get the most informative guide book any linux OS puts out. [http://www.xandros.com/products/home/products_home.html](http://www.xandros.com/products/home/products_home.html)


I asked for possible assistance with articles or links to resources that I perhaps missed, not a speech as to why Linux is the way it is.. I'm pretty sure I read that part when I clicked the first link in Google after searching "Why choose linux over Windows." 

I'm not complaining in a sense that "omg this is too hard, someone baby me or connect to my laptop so you can tell me what hardware I have and download it for me so all I have to do is click the link!" I'm complaining in a sense of what my topic actually says... "SO MUCH TO DO, YET I CAN'T GET ANYTHING DONE" =) Meaning, I understand linux's possibilities and how I have complete control over this. But at the same time, as stated before in my post, I am completely lost because about 90% of the articles I have read and referred to assume you know what the heck Python, sudo, root, filesystem, admin, and all that means... 

I am SO overwhelmed about what I want to do and NEED to do, that I cannot get done what I need to do. And that is to get the 3 situations above resolved. $40, $80, I'll gladly pay whatever (so as long as it is below the price of Windows XP hah), I just wish to SOMEhow get assistance or a better understanding of what I am even doing, because I have tried searching high and low (yes, even in the OLD Ubuntu Forum archives, for the previous versions I've never heard of!) to find even the most generic of audio, usb, and wireless drivers. I'm not looking to have my 300 mhz laptop act like it was the latest g4 with intel processor, dual os for osx panther/unix shell. I just want the bare minimum to work so that I can begin exploring more and fully understanding what is going on (because I'm AMAZED how such a slow system looks so ... GORGEOUS right now; I'm almost proud enough to take her out to Starbucks and show her off!). 

Long story short, I'm only asking is there some END ALL guide that I have not found through these forums, google or the net, to basically get anything bland, generic, or simple, to work plain and simple. And perhaps in the future upgrade, research more, or add on!

---

### Post by seshomaru samma on 2006-09-10
I'm sorry I cannot help you with those 3 questions but Ican suggest the following:
Put your questions in the forum search option - it is likely that people encountered these problems before. For example try running this command:
```
lspci
```
it will show you your hardware, then put the name of your sound card in the search box of the main Ubuntu forum page. 
Another option is to log on to Ubuntu's IRC channel
go to Applications>Internet>XchatIRC
(Icant remeber if Xchat is intalled by default , if you cant find it put this in the terminal:
```
sudo apt-get install xchat
```)
then when the Xchat screen comes up choose 'freenode' and 'connect' , after a while (sometimes even 30 seconds) another screen will come up and then you choose "join this channel " and write "ubuntu"
In the IRC channel there are often very helpful people who can help you solve your problem in real time.
Hope this helps.....

---

### Post by rokknroll on 2006-09-10
On the wireless issue, try finding the windows driver for your wireless card and using ndiswrapper, avail from sourceforge.  needs a little bit of command line to get it working, but i've had success in the past.
For the bash help, type man bash, or man whatever where in windows you would type help or /h.
the best place to find info is on google, subject by subject, line by line.
myself, im coming back to linux after a few years, and on ububtuyour best friend is Automatix, after you get the wireless working or whilst your attached to a lna via ethernet (as i am now...using automatix to update ndiswrapper)

---

### Post by Stew2 on 2006-09-10
Closest I can think of for an end all guide is the [unofficial ubuntu Dapper guide]("http://ubuntuguide.org/wiki/Dapper"). It has a lot of good information in one spot. I use that guide and the forums here to find my answers. Hope that helps.

Regards,
Stew2

---

### Post by jbonll05 on 2006-09-10
Reference recent Ubu guides;
 While shopping in a"Book Stop" for the "unoffical guige" that they did not have - i bought,"Ubuntu Hacks,Tips & Tools for Exploring, Using, and Tuning Linux". It is a June 2006 publication and has helped me. Pages 154 to 158 deal with setting up a problem wifi card.
JB, Ubuntu since Oct05, It just works for me.

---

