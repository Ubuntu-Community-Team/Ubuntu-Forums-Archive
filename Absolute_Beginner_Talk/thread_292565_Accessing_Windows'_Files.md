---
title: "Accessing Windows' Files?"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by numero9 on 2006-11-04
Sorry if this sounds stupid, bear with me...

Recently my copy of Windows XP got messed up to the point I couldn't boot at all (not in safe mode, etc.)

I tried everything, and I just couldn't get into to copy/backup some important files before re-installing XP.  

A friend said that I could try accessing my stuff in Windows from an Ubuntu start disc.  He gave me his copy, but had to leave -- so he didn't tell me how to get it going.  Besides, I don't think he was sure.

This begs the question -- I really want to copy some photos and documents from my Windows XP's "My Documents" folder.  Is there anyway I can access them (and copy them somewhere -- I have plenty FTP space...) through Ubuntu's start disc?

Any help or ideas would be appreciated.  I really don't want to lose these files! :(

---

### Post by Tamil on 2006-11-04
See [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Sef on 2006-11-04
I used [Knoppix]("http://knoppix.com") for to get a friends's files off his computer when it wouldn't boot.  Had a usb key in the usb port, started Knoppix, and once it was up and running, just opened the hard drive and the usb key icons, and then transferred the files from the hard drive to the usb key.

---

### Post by numero9 on 2006-11-04
Windows isn't on a separate partition, and I'm only running Ubuntu from the disc.

I don't think I can even run Knoppix because I need the Ubuntu disc to do anything.


Sorry if I don't make sense, Linux isn't something I have much of a grasp on and I'm just concerned about recovering a few things.  ](*,)

---

### Post by Sef on 2006-11-04
You could try using Ubuntu's Live CD to open the hard drive and transfer the files to a usb key.  However, I was told that Ubuntu did not work as well as Knoppix.  Do you have another computer you can download to?  A friend who will let you download Knoppix?

---

### Post by highneko on 2006-11-04
Probably. First you should mount your windows partition. Then get further help.

Try:
mkdir /windows; sudo mount hda1 /windows; cd /windows; ls

Sef: Why would you say that. I would think it's the same, I don't know what you're thinking he should do tho. Do you prefer KDE maybe?

---

### Post by hyper_ch on 2006-11-04
Another option would be to install windows in a different folder:
If you use XP then the default installation is in c:\windows but you could install another version in c:\winnt.
Just don't format anything... after windows is installed again you have access to your files again... or should have.

---

