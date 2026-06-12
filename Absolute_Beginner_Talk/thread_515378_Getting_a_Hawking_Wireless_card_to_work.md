---
title: "Getting a Hawking Wireless card to work"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by maven2k on 2007-08-01
I am a total newb with Ubuntu and I am trying to get my Hawking wireless card to work.  It's a HWC54D and it shows up in Device Manager as a RaLink RT2500 802.11g Cardbus/mini-PCI.  Now, it is not a mini-PCI card (as far as I know) it's a PCMCIA card.  I've read a few things about doing a ton of command line stuff and I am not opposed to doing that it's just that I really don't know what it is that I'm doing.  Anyway, any help would be much appreciated.  BTW, I am working with a Sony laptop if that is of any use.  Thanks...

---

### Post by anewguy on 2007-08-02
Please do the following and post the results back here:


(1) click on [COLOR="Red"]"Applications"[/COLOR] on the top bar, move down to [COLOR="Red"]"Accessories"[/COLOR], then over to [COLOR="Red"]"Terminal" [/COLOR]and click.  This will open a terminal window, which we need in order to use the command line

(2) type:

[COLOR="Red"]lspci[/COLOR]  and press [COLOR="Red"]enter[/COLOR]

copy all of this (you can use your mouse to highlight and copy)

(3) type:

[COLOR="Red"]exit[/COLOR] and press [COLOR="Red"]enter[/COLOR] to close the terminal window


You can now post a reply here and just use your mouse to click and paste the results of the lspci back here.  We'll see what we can or can't do from there, ok?:)


EDIT:  you may also want to check this link: [http://ralink.rapla.net/]("http://ralink.rapla.net/")

---

### Post by maven2k on 2007-08-02
Thanks for the help.  Here is the info:

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
00:0a.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)


Thanks again.....

---

### Post by anewguy on 2007-08-02
You might want to check this page, if you have questions afterward let me know:)

---

### Post by anewguy on 2007-08-02
AFter looking some more on the net, I gather your wireless adaptor plugs into the pcmcia slot on your computer, correct?  Also, what version of Windows are you running?

Thanks!:)

---

### Post by maven2k on 2007-08-02
There is no link in that reply that you told me to check a web page in.  I am not running windows on this machine, but I have other computers with XP & 2000 pro.  Thanks again...

---

### Post by anewguy on 2007-08-02
Guess I messed up and didn't get the link in as I thought I had.  Basically, the link said to either use ndiswrapper or to put a bin file in the firmware folder.

I downloaded your driver (it's an exe that I couldn't get into with normal extract tools in Linux).  I used WINE to execute it so I could see the files it creates.  So, I have those files on my PC now and I think I know the files you need, but it wouldn't let me attach them to this post.  Do you have email available where I might be able to email them to you?  You then could burn them on a CD and take to the PC you're having the problem on (unless, of course, you have internet access on the PC that you're trying to get the wireless working on!  if so- let me know:) ).  You can use the private message function in to send me the email address if you don't want it public and known by thousands of people!:)

Also, what version of Ubuntu did you install?  7.04?

Start up your synaptics package manager and use the search function to look for ndiswrapper.  Post back here what packages are shown with a green box.:)

---

### Post by anewguy on 2007-08-02
Wanted to post this here so people following the thread would not be confused.

Note:  This is a copy of an email I sent privately to this user.  The email had 2 files attached.

I believe the 2 attachments are the files you need.  Put them on your
desktop, then do the following in a terminal window:

sudo ndiswrapper -l   <-- lower case "L"

sudo ndiswrapper -r  xxx  <-- any driver that is returned in the list
above.  Repeat this if needed until the "ndiswrapper -l" list is empty.

sudo ndiswrapper -i ~/Desktop/Rt2500.INF   <-- be REAL careful with the
case of letters in this string!  It should return a couple of things.

sudo ndiswrapper -l  <-- lower case "L" again.  Should show Rt2500 or
RT2500.

sudo modprobe ndiswrapper

sudo depmod -a

sudo ndiswrapper -m

Now see if your wireless networks are available.  Please post back to
the thread with your results!:)

---

### Post by anewguy on 2007-08-04
I think someone helped me figure out how to attach the files, so I'm trying again.  If a tar file shows as an attachment, just download it and use archive manager to extract them to your desktop, then follow my previous post.:)

---

### Post by lorenzo111 on 2007-09-24
I just wanted to say this post is spot on thanks again. Left linux for awhile got fed up with all the hacks to get things to work so I bought the 24" imac love it to death but still cant shake off the linux itch. Was browsing the net and saw debian finally made a update was like Oh yeah!! The only thing that burned me about debian was the lack of there hardware detection. Loaded debian up on a spare notebook went and bought a Hawking Mac compatible wireless thinking I could get one to work right out of the box. Well debian found it and was working great for two days then all of a sudden my PCMIA slots stopped working. Said okay debian is out gave ubuntu a try intstalled it and it detected my hawking as a toshiba wireless card for some reason. Started to get frustated did some searching and found this post followed everything to the letter and Bam it works great. Will keep ubuntu on this labtop for sure now proabbly will take windows off it. Was checking out the program Democracy TV really nice. Well long story short thanks again for this A+++ post.

---

