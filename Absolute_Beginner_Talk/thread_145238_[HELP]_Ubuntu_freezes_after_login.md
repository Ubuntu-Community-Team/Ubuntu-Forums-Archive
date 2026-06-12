---
title: "[HELP] Ubuntu freezes after login"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by youBun2 on 2006-03-15
Hi folks,

I’m a new Ubuntu user and have decided to try out Linux for the first time after a lot of research. To cut to the chase, I have Ubuntu successfully installed on my computer. I choose the start-up and away it goes loading everything up. The login in screen displays and I am greeted by a pleasant and simple design.

After loging in, a thin banner appears aligned centre and vertically-aligned middle of the page. Everything locks up, mouse, keyboard, etc. and then I have to restart.

I have tallied 32 attempts of a reboot to get Ubuntu to load up after the initial log-in and it doesn’t work.

What is it? I defined a network during set-up, like it asked me to, could it be that as I left it as default with ‘ubuntu’ as the host name?

Regards,

youBun2

---

### Post by youBun2 on 2006-03-15
I would also like to point out that even loading the Live CD this happens. My PC is quite fast as well.

---

### Post by youBun2 on 2006-03-16
Bump

---

### Post by Mustard on 2006-03-16
What hardware are you using?

---

### Post by henriquemaia on 2006-03-16
Try this thread, see if it helps you:

[http://ubuntuforums.org/showthread.php?t=144448&highlight=system+freezing](http://ubuntuforums.org/showthread.php?t=144448&highlight=system+freezing)

---

### Post by youBun2 on 2006-03-16
Could you define what you mean by what hardware I am using? I thought this forum was for help - I've had this topic on auto-refresh for around 12+ hours now and only one reply!?

If anyone could tell me how to get my Windows XP setup back as when I try to log on to XP via the options when I can either load Ubuntu or Windows, it doesn't do anything - as if it doesn't have the boot-up protocal loaded.

All I basically want is to remove Ubuntu now and return to my Windows desktop. Right now I can't - I have a near new PC (just over a year old) stuck.

Please, I beg for help or any direction in returning to my Windows setup without re-installing Windows itself.

Regards,

youBun2

---

### Post by youBun2 on 2006-03-16
I would like to make a note that the Live CD just stalls. It loads up, shows an image, freezes my cursor and keyboard input... what the hell is going on here!?

---

### Post by youBun2 on 2006-03-16
I will quote what I have said in another topic.

Alright, I am in the same boat as you all but far worse.

I currently run Windows XP Home Edition on my desktop that was bought last February. The file system on my main and only hard drive of 200 GB is NTFS.

Yesterday a friend gave me a copy of Ubuntu (official copy from the website) and I decided to load up the Live CD. Without a result I found that perhaps it is just the Live CD and so I went ahead and started with an installation.

Using a partioning program I managed to create a 10 GB partition for Linux etc. I carried on with the install and towards the end it asked me if I wanted to have the GNU GRUB installed on my C: (with Windows XP) as to have a choice in OS when at boot-up.

Innocent me went ahead with that choice and enjoyed the first few steps at seeing Ubuntu. I managed to create myself a user account and I logged in... it froze. I then decided to restart and load up Windows XP instead. It won't load. When I select Windows XP Home Edition it has:

root (hd0,1)
savedefault
makeactive
chainloader +1

and stops. When I checked out the same boot-up process for Ubuntu, I saw that it reads:

root hd(0,2)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
intrid /boot/initrd.img-2.6.12-9-386
savedefault
boot

and obviously loads Ubuntu and allows me to log in but freezes on the centered image.

From what I can see, it appears Windows XP doesn't load up its kernal or something like that. Are there any ways I can simply log on to my Windows system?

---

### Post by Mustard on 2006-03-16
From what I can tell it seems that a problem has occured with your MBR (master boot record).  If you are simply wanting to use windows, at this stage, you could use your Windows XP CD and boot to the recovery console and type fixmbr.  If you want confirmation of this I would start a separate thread on how to use the XP CD to fixmbr.  It's a common question.  I don't run XP though, so I can't be more specific.  Someone else will know the specific details though.  A new thread will allow people to who know how to do it to specifically answer that query.  Currently your thread is drawing in people who are looking to help with something that is totally unrelated to what you want to achieve.

-edit-

Using the search funciton in the forum I have found this reference for you...

[http://www.ubuntuforums.org/showpost.php?p=828216&postcount=2](http://www.ubuntuforums.org/showpost.php?p=828216&postcount=2)

---

