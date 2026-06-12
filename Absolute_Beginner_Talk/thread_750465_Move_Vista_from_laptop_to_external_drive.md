---
title: "Move Vista from laptop to external drive"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by penguin5 on 2008-04-09
This may be a stupid question but I want to make my laptop ubuntu only OS but I have dual boot ubuntu and vista on my laptop. Is there a way I can just transfer the Vista with all of the files as it is on my laptop to a USB HD? This way I could have all the space to install ubuntu on. Can that be done? So when I want to use vista, ill just plug in the USB HD and use it. 

Thanks, 

-Alex

---

### Post by phidia on 2008-04-09
I actually don't know-I do have ubuntu installed to an external usb drive and it works fine.
I did a search on your questions and found [this]("http://help.lockergnome.com/vista/Installing-Vista-external-USB-drive-ftopict758.html").
It seems like it depends on whether vista can recognize your usb drive at boot and that will depend on the drive/drivers being used.

It does seem like it would be fairly painless to try this though. Put your vista install disc in the optical drive and reboot with the usb drive plugged in.
Will vista install to your specific usb drive?

---

### Post by wolfen69 on 2008-04-09
you could probably use an imaging program to transfer vista to the external drive, then resize ubuntu, and then re-do grub to boot to ubuntu by default. to boot to vista, just choose external drive at boot up.

---

### Post by AndrewEsther on 2008-04-09
I don't think you'll have much success in actually moving vista from one HDD to another and still keep it functional. Vista tends to get very picky (at least with my experiences with it) HOWEVER

here's what I've done in the past.

Install Vista on your external drive, then use vista's nice little "files and settings transfer wizard" and prepare all your files and such for transfer. Stick them somewhere on your external drive. Reboot and load vista from your external drive, then import all your files, settings, bookmarks, pictures and all else from the file you stuck on it somewhere.

I've had to do that a few times with XP Pro, and it gave me a few hiccups, but in the end I got it to work and was able to repeat it.

Hope this helps! :-)


<EDIT>
In retrospect, after having written this and read over it, that probably violates MS EULA code because you're only allowed to have one instance of that license installed at any one time. So, either consider this as a HYPOTHETICAL solution and don't sue me if MS finds out, or just don't register your copy on your external drive until you have completely removed the first installation.
</EDIT>

---

### Post by penguin5 on 2008-04-09
Thanks for your help. Ill look into that.

---

### Post by AndrewEsther on 2008-04-09
Please let me know how it works! I'm curious to see if I'm the only one that's ever gotten that to work lol

Good luck!

---

### Post by penguin5 on 2008-04-09
Ill let you know if it works but im not actually planning on starting it until next month ( too much college work for now :( ) 

A friend of mine helped me install ubuntu 7.10 so I have no clue to what he did. Im planning on reinstalling 8.04 when it comes out. I dont know what format i should do it in, ex: ext2 or ex3. Or whats desktop environment like kubantu etc. I need to access my vista files also and vise versa. 

Sorry for being off topic,  I just dont want to flood the forum with my questions.

---

### Post by AndrewEsther on 2008-04-09
Well, this won't be an expert opinion because I just started using linux a week ago, but I just let the install cd do it's thing (selected auto for every option) and it's been running great.. no problems really, just confusion on my part. I guess the default format is ex3 because that's how ubuntu formatted my drive for me, and it seems to be working just fine, as well... granted, I haven't loaded it up with .mp3's and programs and pictures and all the other garbage that I usually do, but I'm trying to keep away from that on this machine lol I'm as well going to nab 8.04 when it comes out

and accessing your vista files should be easy enough with the default ubuntu install (I think.. it has been for me).. you just mount the drive and navigate as normal, provided it's formatted in NTFS, which I think is required for vista.. I have yet to see one on FAT32 (know it would't work in FAT) but ubuntu will mount NTFS no probl-a-mo

---

### Post by lackofcreativity on 2008-04-09
I've personally had trouble with NTFS partitions in 7.04, so if you're using 7.04 and below, you should upgrade to 7.10.

---

