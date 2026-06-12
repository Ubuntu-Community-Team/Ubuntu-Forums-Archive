---
title: "How do I install the UBUNTU driver for my MFC-3240C printer?"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jsmkbunch2000 on 2007-02-20
I need to install the printer driver on my Brother MFC-3240C printer.  I went to the Brother website, however it doesn't seem to be correct for UBUNTU.  Can someone help with the entire steps that will meke sense to someone completely new to Linux????

---

### Post by ashmew2 on 2007-02-20
Have you tried clicking System > Administration > Printing ??
It is on the 3rd menu from the top left part of your gnome desktop.

Let me know if ur printer is listed in there

---

### Post by jsmkbunch2000 on 2007-02-24
Yes, however when I get to add the printer, it doesn't find the driver specific to my printer.  I tried a couple others, but they dont work.  How do I install the correct driver?

---

### Post by MichaelSM on 2007-03-10
Um this is always tricky. I used to be a Xandros person and I know full well the ascending order of Brother MFC-3240C imperatives. YES ubuntu and xandros are Debian derivatives. 
What completed my installation of my MFC-3240C was accomplished in Xandros simply(and it took a LOT of posts to understand it) was finally to log in as root and complete the installations there. 
The BrotherSolutions website is pretty easy to deal with. You basically follow the links to each and every application eg. Lpr's, cupswrappers, scanner stuff(br2scan) and follow the instructions. After that it's either easy or a ****-fight. 
Hopefully someone from UBUNTU will pick up this thread, and explain in SIMPLE terms how to log on as root and to execute the downloaded brother files. It's one thing to download and install them in the correct order as root which is all hunky-dory and looks like it's worked when the G-thingo installer runs through its protocols, except that the printer is busily accepting jobs and can't get actually printing. 
Look, it's a free OS. You can't expect too much. Eventually we'll all get there. 
Cheers, Mike.

---

### Post by phi1ip on 2007-04-28
It seems the brother website is giving instructions for debian but NOT Ubuntu.

Has anyone got this working? how?

---

### Post by MichaelSM on 2007-04-29
Hi Philip. I'd forgotten about this post.
Yes, I DID get it working VERY late one night, and like an idiot I didn't immediately post the way it occurred. 

Assuming you have downloaded and  installed the specific lpr driver and cups-wrapper from the BrotherSolutions site, and that your printer is plugged in and switched on .....OK here we go (this was the hard way to do it) Having read this again you might wanna jump a few paragraphs to *.

Go to [http://localhost.com](http://localhost.com) or something like that, which is the CUPS site for Linux computer printers. You should see your printer there. (It's an on-line dynamic database which interrogates your PC and enables you to make changes.)

Now, there's a series of selections under your Brother printer listing; click on Modify Printer. Most of it is basic commonsense, but the MOST IMPORTANT and fiddly bits are the following two :

You'll get to a section where you must input a couple of exact notices. One is Printer Location. My printer is located at  usb://Brother/MFC-3240C. Type it in, guessing you're the same set-up. By the way I think it's case-sensitive ....

Underneath that dialogue box is another which asks to be pointed to some sort of ppd  file. Anyway, it's there. There's a Browse button beside it. Click on it, which will give you access to your computer. The file you want is in File Systems on the left in your Places>Home Folder. In my case, the file name i needed to insert was   /etc/cups/ppd/Brother_MFC-3240C_USB_1.ppd. I recall navigating to it then whacking it in (I think there was a password required-use your Admin one) and it went through a bit of thinking then finally asked if I wanted a Test page printed. At 3.30 am, with a shaking hand, rather tired and pissed, I hit Yes. And it worked!  Hope it's as good for you......it was the first time I'd got a usb printer running on Ubuntu in six months. FAR OUT.

Back to logistics. You ought to be able to locate your Brother ppd file by clicking Places>Search for Files and when you get the dialogue window, input ppd into the search box. Underneath it is a drop-menu box, and use the down arrow to select File System. Enter. You just have to trawl through them as I did until I found the pertinent Brother one. 

* Come to think of it, maybe you don't have to go to Cups Localhost. Go Admin>Printing>New Printer. Follow the prompts and click on Install Drivers, where you'll be asked to supply the ppd file. Browse for it as above, then enter it.

Sorry I can't write like a geek. I'm slow-minded and I know how depressing it is to follow geeky instructions and stuff up on something the cybernauts took for granted and forgot to explain to newbies.

As an adjunct. Once the MFC 3240C was installed and working ...Hey Presto! my sidelined DCP-115C worked  off the same drivers. Way cool.

Take off your reading-glasses and have a drink. You deserve one!

Cheers, Mike.

---

