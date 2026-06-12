---
title: "New Problem!!!"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by smoke558 on 2008-01-19
ok yesterday i had a problem putting the iso onto disk because of winrar but thats solved thanks guys....

then i had a problem finding the right iso file :confused:  but thats solved thanks :KS:KS

Now i have found the right file ***See image below***

[IMG]http://i185.photobucket.com/albums/x115/smoke558/thisfile.jpg[/IMG]

But when i go to burn image i get a message 

ERROR occured while trying to perform selected operation 
I am using infra recorder 
i go to   ACTION>BURN IMAGE>CHOOSE SPEED>12X (slowest)>THEN THIS MESSAGE>ERROR occured while trying to perform selected operation

---

### Post by bwhite82 on 2008-01-19
likely a permissions problem, you can either run the burn app with sudo (root priv.) or you can change the permissions on the iso:

> sudo chown yourusername downloadediso.iso

---

### Post by smoke558 on 2008-01-19
i dont understand that pls mind im using windows to burn this cd for my ps3

---

### Post by bwhite82 on 2008-01-19
> **smoke558 said:**
> i dont understand that pls mind im using windows to burn this cd for my ps3

Ah, silly me, thought you were using Linux. I'll have to leave this one to the Windows pros, out of my league.

Edit: Can you go any lower than 12x? Can you try 8x or even 4x?

---

### Post by smoke558 on 2008-01-19
oh noo!!!!!!!!   i need some help then

---

### Post by Warpedflash on 2008-01-19
i use
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
to recored iso's on windows... makes it all alot easier, just right click then copy image to cd. set it on a slow write speed and go or it

---

### Post by bwhite82 on 2008-01-19
I'll try to help you as much as I can. Have you checksummed the ISO? (Verify that it downloaded correctly), not sure how to do it in Windows.

---

### Post by smoke558 on 2008-01-19
> **Warpedflash said:**
> i use
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)
to recored iso's on windows... makes it all alot easier, just right click then copy image to cd. set it on a slow write speed and go or it



Tried that and it did not work it wont let me pic the recorder

---

### Post by stevescripts on 2008-01-19
> **smoke558 said:**
> Tried that and it did not work it wont let me pic the recorder

Weird - I have never had a problem with isorecorder, and I have used it a *lot* lately...

You *should* just be able to right click the image, pick "Create ISO Image", (or something like that - dont have a windows box handy right now), and isorecorder *should* start,
and correctly identify your burner ... 

If it doesn't try to post some details, if possible.

It *may* be worth your time to burn the iso image at a lower than maximum
burn speed 

re md5cksum on 'doze ... [http://md5deep.sourceforge.net/](http://md5deep.sourceforge.net/)

Steve

---

### Post by Methuselah on 2008-01-19
I use the free imgburn [ [http://www.imgburn.com/](http://www.imgburn.com/) ] for my iso burning on windows and have never had any problems with it. Have you burned other discs recently, could it be a hardware problem or a corrupt iso image?

---

### Post by Majorix on 2008-01-19
Try [CD Burner XP]("http://cdburnerxp.se/"). It is not the easiest thing to get used to it, however it didn't produce any bugs on my side.

You can also always try [PowerISO Trial]("http://www.poweriso.com/"), although I am not 100% sure if it would let you burn in trial mode. You could find out on your own.

Good luck (and I must say you are a lucky b---- to own a PS3, lol :p I will buy one myself sometime too :))

---

### Post by Joeb454 on 2008-01-19
Like the post a couple before mine, I use imgburn, and I have done for any CD I've burnt in the last 2 years, I've never had any issues with it yet :)

Well...except that I couldn't get it to run properly in Wine ;)

---

### Post by smoke558 on 2008-01-19
as i have said in another post u guys are great it runs perfectly and as we speak my ps3 is installing ubuntu

---

