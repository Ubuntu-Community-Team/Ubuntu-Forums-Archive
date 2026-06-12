---
title: "New and Excited have a question"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by KatieCook on 2007-02-11
Hi, I am new here and to linux.  I have been wanting to do this for such a long time, and now I did!!! WHOOO HOOOO

  We have had 3 computers in our home from some time (one for hubby, me and kids all on XP) My neighbor just got her daughter a new laptop and gave me her old one. I mean old! LOL It was shipped with Windows ME  and she tried and tried to erase it and load it with another version of windows but could not get it to go.  She was going to throw it away and asked if I wanted it.. I really didnt need another computer but I have been so wanting to try Linux but was always afraid of messing something up and I thought this was the perfect way to play with out fear! (by the time I got it windows would not open half of the programs and couldnt even find out what it had in it..)  

How I got here...  I started out with Red Hat 9 years ago on another computer but could never get it to load and had to reinstall Windows :( For this computer I triedFreespire, I got it to wipe out windows (yeah) and install and it looked so pretty! The mouse moved freely UNTIL I clicked anything (even right clicking) then it would freeze up and I would have to shut it down.  After doing some reading, I decided it was too old and would not run with it) So I just burned a copy of ubuntu and loaded it up, without a single glitch. Wow I am so excited to play with this thing, but I need a pci card to add it to our network.. I have lived in a windows dependent world for too too long but am a quick learner and ready and willing to learn!  My first computer was a TI and then a Comador (where did all those tapes go??) :lolflag: I am really wanting to move all of our computers to Linux now more then ever after Vistas launch. So I want to learn as much as I can with this test machine so I can move forward and be able to change all of them over.    

My first question is which one is best. I have installed one on windows before and wanted to know if it will "notice" it or is there something I should do? 

Second question.. Is there a way to find out what I am dealing with (ram, ghz, etc..) 

Thanks in advance I am so excited to start learning :)

---

### Post by oilchangeguy on 2007-02-11
1st question-which one what is best?

2nd question-when the computer starts look for how to enter the bios (setup). if it goes by to quick to see an option, re-boot and hold down the esc key, and you'll get a keyboard error and press whatever key to enter setup

---

### Post by mrmonday on 2007-02-11
Hi

I am new to linux too.  On my PC windows didn't notice that I had installed Ubuntu at all. Something you need to make sure of though is how much space windows is using. On XP go to start>my computer. Right click on your hard disk (probably C:) and click on properties. Note down how much space windows is using. When installing Ubuntu make sure that you do not use up to much space!! On the repartitioning page of the install, the slider is the size of your windows partition, not the new Linux one (the mistake I made fortunately I had enough spare space...). When the install had finished I booted into windows, which ran check disk, don't worry about this, it is just realising the hard drive has shrunk. You can always change the partition sizes later on using gparted(I think, it is definitely something like that).

For help installing there are videos on google video (search for Ubuntu windows dual boot).

In answer to your second question I haven't found system requirements for Ubuntu, most modern/semi-modern PCs should run it... if it can run XP it can probably run Ubuntu. For older PCs try Xubuntu, see [http://www.xubuntu.org/get#requirements]("http://www.xubuntu.org/get#requirements")
for requirements.

Happy Linuxing.

---

### Post by mrmonday on 2007-02-11
For Question 1 if you meant which distribution, I can only account for Ubuntu. It is incredibly simple and easy to use, and I expect the other distributions will also be simple. I recommend reading reviews, looking which provide the most support, and whether the distribution is specific to home users. If your PCs are networked then I recommend checking if your hardware is supported, I am having problems...

See [https://wiki.ubuntu.com/HardwareSupport]("https://wiki.ubuntu.com/HardwareSupport") for supported hardware, other none listed models may also be supported.

---

### Post by TwistesdTexan on 2007-02-11
I guess you installed Edgy. Click Applications-> then Add/Remove Programs-> and then in the left catagory area click System Tools-> Scrool down to Sysinfo and click the box. Apply. Close this program and Click Applications-> System Tools-> Sysinfo this will open  tool to let you see speed memory and video plus a lot of other information you might want to know.

---

### Post by KatieCook on 2007-02-11
Thanks so much, 

  I am sorry, I didnt word that right.. LOL   I was wondering which PCI card to get so that I can try out the internet.  I already have Ubuntu install and running like a dream!  Everything so far was detected and runing great.  I was wanting to know what I had to do to go on the internet with it.. Do I install the PCI card and then turn it on and it will detect it and the connection to the network? or is there something I should comand it to do?

Thanks so much
Katie

---

### Post by oilchangeguy on 2007-02-11
you're using a laptop right? if so it won't be a pci card, it'll be a pcmcia card. when looking check the box to see if it will work with linux, and google the model to make sure it will work in linux. and no you should not have to enter a command to make it work.

---

### Post by nickoli_02 on 2007-02-11
From what I've heard, Intel is pretty good with getting open source drivers out to the linux community for their wireless cards. My laptop has an Intel wireless card and it worked just fine, no config needed. I believe there is a list of known working wireless cards in linux out there somewhere, try searching the forums ;)

welcome to linux, you're going to love it (but only if you have a little patience) :)

---

### Post by ahsile on 2007-02-11
I just gave away two old pcmcia cards: an old xircom modem/lan card and a linksys wireless-B card. They'll probably never be used by the person I gave them to either. 

Anyway, the xircom card worked perfectly most of the time. There was the odd time when I would get disconnected and have to restart networking manually to get it working again, but for the most part it was perfect.

The linksys card on the other hand was a royal PITA. I had to download windows drivers and use  them instead of some good open source drivers. It was not an experience I would wish on a newcomer at all.

---

### Post by igknighted on 2007-02-11
What distro to use?  There are a lot of choices.  While I mainly post here, I no longer use Ubuntu as my primary OS.  In fact, I don't normally recommend Ubuntu to absolute beginners unless they want a challenge... it is a lot more "text file editing" te get your configurations than other distro's.  However, the community support is tremendous here, and Ubuntu is THE BEST distro to learn on.  There are always people to help you when you have issues, and by not using a GUI for everything you learn much more about how the OS works.  People who learn on Ubuntu tend to be excellent linux users down the road.

Having said all this, you seem like you have a strong computing background, and good computing instincts.  I would say use Ubuntu, you might get bored with a distro like Suse that has a GUI for everything.

I feel where you are coming from with that laptop.  My laptop (my only Ubuntu run computer in fact) came with win98.  I know run edgy on it.  For wireless, I bought a cheap PCMCIA wireless card and rigged it up.  Wireless can be a pain, research what card you want to get and how it works in linux before you buy.  Your laptop probably has an ethernet jack you could use for internet in the meantime (needed to download wireless drivers/other needed apps).  The level of performace is tremendous... I went from barely able to surf the web in win98 to doing most of my software development on that laptop... incredible.

---

### Post by KatieCook on 2007-02-11
Ok I feel soo silly!!! First off it is a desktop. and I am using Ubuntu 6.06.  

 Now I really feel silly for taking my friends word! I went and bought a D-Link PCI card and went to take out the screws to install it and low and behold there was already one there!! When she said "I took out the PCI card" I think she meant wireless!  I was laughing and now I can go get my $20.00 back. :)  So I put my cat 5 wire in and connected it to my router and know what happened? I was on the internet!!!!  Nothing even came up to ask me if I wanted to do what I did, or if I REALLLLY wanted to do that..!! LOL 



  Thanks everyone I am checking out the links and I already started playing with the desk top and if I would have known it was this easy I would have switched a long time ago!

  I am so excited!  So what else should I do first? LOL 

Thanks again 
Katie

---

### Post by nickoli_02 on 2007-02-11
```
sudo apt-get update
sudo apt-get upgrade
```

:)

---

### Post by KatieCook on 2007-02-11
Nickoli , Thanks soo much for those codes but I have absoultly no idea what to do with them. :confused:  LOL  I am very very new to this ..

---

### Post by CroEragon on 2007-02-11
Let me explain it.
Thease are Terminal commands.
You just copy them in Terminal and hit Enter
First part (sudo) makes computer to ask you main administrator password that will alow you to change system wide settings. If you do not use it you will be able to change just settings for your non-admin account.

apt-get  is command line package manager. Program that handles installing. This stuff is littlebit different from Windows. In Windows when somebody gives you setup you get actual program and another program that installs first program (and it can be run without installing). In Linux you just get program, without helping program for installing, but apt-get handles installing. So, installing program in windows comes with setup, in Ubuntu you got it on computer installed.

Update and upgrade are commands for apt-get. Update checks is  any program needs update and if it left instructions where to fin them. If it did leave instructions and needs update, apt-get will handle everthing about it, from download to installation.

There is slight difference in upgrade, im not totally sure what it is, so i wont say something stupid.

Maybe somebody else may help.

---

### Post by KatieCook on 2007-02-11
Found it!!! I am loving this .. Ok whats next? LOL

---

### Post by KatieCook on 2007-02-11
WOW you people are so cool!  Thanks so much I am installing updates as we speak and I am looking for aim or yahoo messenger.. I am looking at Gaim but I do not know which one to get.. :)

Thanks soo much 
Katie

---

### Post by ahsile on 2007-02-11
Gaim is most likely your best bet. It will allow you to do many types of instant messaging including, but not limited to, AIM/ICQ, MSN, Yahoo.

The only gripe I personally have is that there is still no webcam support, that I know of, in gaim. I've been hoping that would be remedied for a while now, but it seems a long way off.

Open source programs such as gaim were actually a stepping stone for myself to swap over to linux. First I started using programs like gaim, thunderbird, the gimp, firefox, xchat, and other open source programs. Then I started using linux servers for some of the work I do. And then I just swapped to Ubuntu myself last summer. With so many programs I was already familiar with the switch was a breeze!

---

### Post by loell on 2007-02-11
if you just want yahoo chat without webcam and/or voice chat then gaim's versatility in chatting is enough , else you can consider [gyachi]("http://gyachi.sourceforge.net")

---

### Post by nickoli_02 on 2007-02-11
Kopete is also pretty good for webcam IM support :)

---

