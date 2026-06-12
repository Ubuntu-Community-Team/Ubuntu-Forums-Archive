---
title: "Gnome-System-Monitor/ATI"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-01-29
Hello Ubuntu Fans,
I have been using Ubuntu 6.06 for two months. After a slow start, I have done fairly well solving problems and making improvements using information found on the forums and in online documentation.  This time i'm stuck and not even sure I have a real problem (I only discovered the Gnome-System-Monitor about three weeks ago).

Here goes:  The Gnome-System-Monitor (ver 2.14.3) reports my CPU running at 100% virtually all the time. Returns from sudo top, sudo ps aux and the gnome monitor itself all show very little cpu used, usually about 20%. Same goes for memory usage.  CPU usage under XP is normal.  acpi reports temperature OK.

Many people have problems with ATI devices and I have tried the solutions I thought applied to me and I understood. None worked so I have also done a lot of "restores". I have also removed and reinstalled the Gnome-System-Monitor. No help.

What is different in my case is the gnome-system-monitor itself crashing. There are three options and I can leave it on Resources or Devices all day but when I select Processes it will always crash in less than three seconds.

I would sincerely appreciate any advice.  Sorry I can't provide the returns from Top, Aux etc.  I don't know how.

My System:
Dual-boot XP/Ubuntu 6.06 (50/50) on a 3 year old HP nx9010 notebook 
w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge 
[IGP 340M].

---

### Post by n8bounds on 2007-02-25
You are mistaking I/O wait or NICE with CPU utilization.  Change the colors in your gnome-system-monitor panel applet so you can see the difference.

---

### Post by ityro on 2007-02-25
Hello n8bounds and thank you for your time. I tried changing colors but that really is not the problem. I doubt I will ever find the problem but it's an easy one to live with.

If I just point to the panel applet it gives the following message: "Processor 100% in use". If I open the monitor and select Resources I get the same message.  Actual CPU usage is very low but I have caught Xorg at 100% for a second or two. The application crashes in 2-3 seconds.

Thanks again for your time.

---

### Post by halitech on 2007-02-25
could you open top and gnome system and take a screen shot

Applications - Accessories - take screenshot


and then post those here?

---

### Post by ityro on 2007-02-25
Hello Halitech, I can try. No I can't. Is there a place I can go to learn how to do it? I can't expect much help if I can not cooperate.

---

### Post by halitech on 2007-02-25
are you able to get the screenshots?

---

### Post by ityro on 2007-02-25
Yes. they are on my desktop.

---

### Post by halitech on 2007-02-25
ok, when you go to reply, go to the advanced and then look up at the top of the window and  you should see a paperclip, click that and you will be able to attach the files to the post so we can see them

---

### Post by ityro on 2007-02-25
I could not find advanced but I was led to another way to post the files. Did it work?

---

### Post by ityro on 2007-02-25
How about this? Advanced.

---

### Post by halitech on 2007-02-25
they both worked, looking now to see if anything stands out for me

---

### Post by halitech on 2007-02-25
only thing I see is that you have 4 perl scripts running. do you know what they are?

---

### Post by ityro on 2007-02-25
Halitech, Thanks for your help. I learned how to do attachments. Next comes the kind that can be scrolled!

But no, I have no idea what they are. Sorry I can't help you so you can help me. My problem not yours.

Thanks again.

---

### Post by halitech on 2007-02-25
if you don't know what they are then it should be able to kill it.

open a terminal

Applications -> Accessories -> Terminal

then type

```

sudo killall perl

```

and that should kill the programs from running and se eif that frees things up

---

### Post by ityro on 2007-02-25
Halitech, The thicken plots.  My password works for things like Admin>Disks and Admin>Update Manager but does not work with "killall perl". Pls see attachment.

---

### Post by ityro on 2007-02-25
Halitech, I think you found the problem although I don't know what it is.  I tried using the ROOT terminal and failed the password test over and over using "sudo killall perl" same for not using sudo except one time I made it through and when the cursor returned, I opened the monitor and CPU usage was way down and only two perls were running. But after 2-3 seconds the monitor crashes and when it restarts usage is back to 100%.

---

### Post by ityro on 2007-02-25
Halitech, I can't get past the password again so I looked at "htop" and "ps aux" and found no perls running.

I will now go away a lot. It's still noon O'clock here but quite late where you are.

Thanks again for your help,

---

### Post by halitech on 2007-02-26
question, is the user you are logged in as, is that the first user you created when installing? 

something doesn't sound right on those 4 perl programs running and the system monitor crashing all the time. I haven't been running Ubuntu long enough to know if there is a system restore but maybe do a search and see what you can find.

Edit: found this just after posting this

[http://www.ubuntuforums.org/showthread.php?t=370749]("http://www.ubuntuforums.org/showthread.php?t=370749")

---

### Post by ityro on 2007-02-27
Halitech,

First let me apoligize for my absence. No power since you heard from me last. I have a generator but my access to the internet is via CATV which is shutdown when the entire city is without power (Olongapo).

I have tried apt-get dist-update and everything else I have found out about from reading the Forums. On the password, Terminal accepts my password as the first and only user so I can use the terminal but after I enter the killall instruction I get the message shown below.

I will check out your reference and get back when I'm smarter.  I can not THANK YOU enough so I'll thank you again!

THANKS.

---

### Post by ityro on 2007-02-28
Halitech,

Well, I didn't get smarter so I restored a total system backup (Heliode Tar) taken before I even knew there was a System Monitor. No change so I restored my current home folder.

I suspect the problem is with the ATI. Thanks for your help. . . . .

---

