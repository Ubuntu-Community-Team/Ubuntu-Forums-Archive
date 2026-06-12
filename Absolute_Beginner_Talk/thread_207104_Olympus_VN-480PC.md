---
title: "Olympus VN-480PC"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Lifeatarmslength on 2006-07-01
When I was on the dreaded XP I was able to download and store recordings from my Olympus but the software disc is no good on LINUX.
Can anyone tell me what programs are out there that I can install to download recordings to. Thanks.

---

### Post by gingermark on 2006-07-01
Forgive me if you've already tried this, but as we're in "Absolute Beginner Talk" I'm gonna ask. Have you tried just plugging it in? A lot of the time devices like this will just be mounted as a storage device, which you can then browse, and copy the files from.

That said, I just read the drivers are proprietary, so that could be a problem.

---

### Post by Lifeatarmslength on 2006-07-01
Hi Gingermark
  Ys I tried that but nothing happens so I wondered what the best program was to install.

---

### Post by rasgward on 2006-07-25
please let me know if you found an answer to this, I have the same issue. -Greg

---

### Post by chele on 2006-08-08
What type of device is a VN-480PC? Is it a camera or an mp3 player?

---

### Post by rasgward on 2006-08-08
It records and stores wav files. -Greg

---

### Post by chele on 2006-08-08
> **rasgward said:**
> It records and stores wav files. -GregOK. So any audio player in Linux should have no problems playing standard wav recordings. 

Rhythmbox is the default application in Ubuntu that organizes and plays audio. Just save the files to your home directory or music directory and let Rhythmbox pick them up from there.

---

### Post by chele on 2006-08-08
> **rasgward said:**
> It records and stores wav files. -GregOops. It appears that Olympus has screwed up here, and used some secret format instead of standard .wav

[Olympus voice recorder - mystery codec]("http://music.columbia.edu/pipermail/music-dsp/2005-December/031545.html")

You might want to give Olympus a call and ask them what format or codec they are using. You could ask for a firmware upgrade to an open format, rather then a secret one.

Generally, one should be careful around stuff with "PC" in the name, as the manufactures seem to think the term PC is short for Microsoft Windows rather then Personal Computer.

---

### Post by rasgward on 2006-08-09
interesting. I checked out the link. I wonder if anything ever came about with that. -Greg

---

### Post by faraazs on 2006-12-02
Any updates to this? I'm facing a similar issue.

---

### Post by detroit/zero on 2007-12-13
Same problem here. I just got an Olympus VN-3100PC. The documentation with the device says it save .wav files. I plug the device in on a USB port, and Feisty does recognize the device, as it is listed in an lsusb output, but it isn't mounted and I can't browse the memory in the recorder like I would a flash drive or digital camera.

I've replied to a couple of other posts with the same theme. Is this issue going anywhere yet?

---

### Post by delon on 2008-01-01
There's some information here [http://htyp.org/Olympus_VN-480PC](http://htyp.org/Olympus_VN-480PC) unfortunately it doesn't lead to an answer.

---

### Post by jkeirstead on 2008-01-22
This is being discussed in another thread (whose link escapes me for now) but the point is there's a Google Code script that (almost) works. 

The software can be found here: [http://code.google.com/p/odvr/]("http://code.google.com/p/odvr/") and here's a copy and paste of the list of supported devices. Someone's also made a deb package for Ubuntu.

Device	Support
VN-120PC	Working
VN-240PC	Working
VN-480PC	Working
VN-960PC	Working
VN-2100PC	Broken* (Issue #6)
VN-3100PC	Broken*
VN-4100PC	Broken*

Hope that helps!

---

### Post by Jackfrost123 on 2008-04-18
Sorry for bumbing this up after such a long time, but I have downloaded the driver for my olympus recorder and it all installed fine. So far so good. Problem is I am a novice to linux and have just been using ubuntu a couple of days, so I don't really know HOW this driver is supposed to work, I plug in my recorder but nothing happens. I am looking for a folder or something...should I run the app. inluded by olympus in vine? Because I have and it didn't work.

It must have something to do with it being a "user-space driver" which coming from a windows background I really have no clue what it is, provides a space for the user like a virtual drive or something? And I couldnt find anything googling it.

Thanks! 
And I am happy joining your community!:guitar:

---

### Post by NET WT on 2008-04-19
I installed that driver just a few days ago. And it works good for me. 

After connecting the recorder to the computer, you will need to use the Terminal (Applications>Accessories>Terminal) and type:

 > odvr -h for help.
 
> odvr -l will list all the files on the recorder.

> odvr -e will download everything to your Home Folder.

I don't think that you need to use the Olympus software in wine.

---

### Post by Jackfrost123 on 2008-04-19
Thanks for the great help buddy! Thanks Net Wt.

---

