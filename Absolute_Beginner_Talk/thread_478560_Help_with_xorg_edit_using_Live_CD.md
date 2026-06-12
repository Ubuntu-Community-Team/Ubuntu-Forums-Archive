---
title: "Help with xorg edit using Live CD"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Jay_in_TN on 2007-06-19
I have an error in my xorg.conf
I see the error. I can fix it. But I can't get the file to open from command prompt. I can boot using the live CD but I don't have write permissions.
Can anyone tell me how to modify the file from the Live CD?
Thanks,
Jay

---

### Post by bodhi.zazen on 2007-06-19
You need to use sudo.

```
sudo nano /etc/X11/xorg.conf
```

If you are trying to edit xorg.conf on your hard drive, mount it first, then sudo as above.

```
sudo mount /dev/hdxy /mnt
sudo nano /mnt/etc/X11/xorg.conf
```

---

### Post by starcraft.man on 2007-06-19
Why can't you open the file from command prompt? Boot up the computer and choose recovery mode in GRUB. Login in, then issue the following command:

```
sudo nano /etc/X11/xorg.conf
```

Then use the arrows and keyboard to edit. Save with Ctrl + O (thats not the number) and exit with Ctrl + X. Then, issue:

```
sudo reboot
```

IMO recovery mode is fastest way.

Edit: Hey there Bodhi, I see ya beat me to it :). How did you get so many links in your sig? Do I have to pay someone off? :p

---

### Post by bodhi.zazen on 2007-06-19
Hi starcraft.man !

If you boot to recovery mode, well then you are root ! so no need for sudo (although you can sudo as root if yo u like).

Off topic : Sorry, I have not tried the KDE thing, but it looked more or less worked through. Let me know if you would like me to look any further.

Edit: Oh the links, I had to be VERY furgal with the code. It took a while to pull off, esp with color.

---

### Post by Jay_in_TN on 2007-06-19
I did exact;y that. I booted in recovery, then did this:
"sudo nano /etc/X11/xorg.conf"

But the file appeared to be empty. It told me I was trying to create a new file, Then it erred with a create error or something. Not sure. But the file is clearly there. I can see it (using Live CD) and see the error {error is a AD" after the monitor type. Missing a set of quotes and probably shouldn't be there at all. What the heck is "AD" anyway?}

Anyway--I just figured I would edit from here (the live cd) as that is what I am using right now. I mean--easier to just edit the file right here and right now, right?

I am still trying to gain access.....

Jay

---

### Post by Jay_in_TN on 2007-06-19
The disk is mounted on the desktop, so I assume it is mounted. But I still can't access the file. Every time I run sudo nano it says "new file"
Grrrrr. It should not be this difficult to modify a single line of a file.
Any suggestions?

---

### Post by bodhi.zazen on 2007-06-19
If you are trying to edit xorg.conf on your hard drive, you need to mount the hard drive first.

If the file is blank, there is usually a typo somewhere.

---

### Post by Jay_in_TN on 2007-06-19
Did This:
sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/X11/xorg.conf

Got an empty file again. Said "New File" at the bottom of the page again. Same thing in recovery mode. This IS NOT a new file. I can double click on it and read it. Please offer some more help.
This is very, very frustrating.

Thanks

---

### Post by starcraft.man on 2007-06-19
> **bodhi.zazen said:**
> Hi starcraft.man !

If you boot to recovery mode, well then you are root ! so no need for sudo (although you can sudo as root if yo u like).



LOL! Right, I knew that. I'm just used to typing sudo, its like second nature :p.

> Edit: Oh the links, I had to be VERY frugal with the code. It took a while to pull off, esp with color.

Hehe, oh well. I will remake my sig eventually... I answer so many new people questions I never get a moment though :p.

> **Jay_in_TN said:**
> I did exact;y that. I booted in recovery, then did this:
"sudo nano /etc/X11/xorg.conf"

But the file appeared to be empty. It told me I was trying to create a new file, Then it erred with a create error or something. Not sure. But the file is clearly there. I can see it (using Live CD) and see the error {error is a AD" after the monitor type. Missing a set of quotes and probably shouldn't be there at all. What the heck is "AD" anyway?}

Anyway--I just figured I would edit from here (the live cd) as that is what I am using right now. I mean--easier to just edit the file right here and right now, right?

I am still trying to gain access.....

Jay

That sounds really weird. I am stumped, are you sure you didn't typo the command? You know that if your just one letter (capital also) off it will make a new file... Other than a typo, I don't know why it returned trouble.

> **Jay_in_TN said:**
> The disk is mounted on the desktop, so I assume it is mounted. But I still can't access the file. Every time I run sudo nano it says "new file"
Grrrrr. It should not be this difficult to modify a single line of a file.
Any suggestions?

Same like console, both means should work without error. Could it be that something worse has gone wrong with your install?

---

### Post by Jay_in_TN on 2007-06-19
This is copied directly from the terminal window:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo nano /mnt/etc/x11/xorg.conf
ubuntu@ubuntu:~$

Do you see a typo?

Thanks


Edit: This is not a new install. I was using it last night. I did edit the nvidia-settings to add the 1280x1024 res. Saved using the fancy GUI. Then on reboot X-serv went belly-up. Maybe it is a capital letter. I think xorg needs to be Xorg. trying again....

---

### Post by starcraft.man on 2007-06-19
> **Jay_in_TN said:**
> Did This:
sudo mount /dev/sda1 /mnt
sudo nano /mnt/etc/X11/xorg.conf

Got an empty file again. Said "New File" at the bottom of the page again. Same thing in recovery mode. This IS NOT a new file. I can double click on it and read it. Please offer some more help.
This is very, very frustrating.

Thanks

Ok, I just got struck by a thought. You can navigate to the file correct? And you double click on it and it is readable. So, drag the file (a copy) to your live Desktop. cd into desktop and edit there, make sure no typo please.

That has to work! If it doesn't, I dunno what on earth is making trouble. If it does work, just copy and paste over the old file. That should do it, I hope >.>.

---

### Post by bodhi.zazen on 2007-06-19
Post the output of :

```
ls /mnt/etc/X11
```

---

### Post by Jay_in_TN on 2007-06-19
THANK YOU!!!!!!!

It was a typo.
The directory should have been X11, not x11

That did it!

You guys are the best!!!
Jay

---

### Post by starcraft.man on 2007-06-19
> **Jay_in_TN said:**
> This is copied directly from the terminal window:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo nano /mnt/etc/**X**11/xorg.conf
ubuntu@ubuntu:~$.

CAPITAL X!!!! Hazzah, problem is solved :).

Edit: ROFL! All that time on a stupid typo, I don't think we did anything :p. Oh well, long as it works out :).

---

### Post by Jay_in_TN on 2007-06-19
Responding from HD install!!!! Yay!

You guys did the following:
1) told me how to mount my HD using sudo in terminal

2) told me that my blank screen was a result of a typo, which sent me looking for typos, leading me to see the X11 versus x11.

3) you guys were very quick to respond and patient with my frustration.

Thanks again.

Problem resolved!!!

Jay

---

### Post by starcraft.man on 2007-06-19
No problem. Next time, don't make so many TYPOs :p.

Have a nice day :D.

---

