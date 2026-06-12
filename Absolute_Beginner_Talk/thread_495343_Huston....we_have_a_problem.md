---
title: "Huston....we have a problem"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Church.Cameron on 2007-07-07
oookkkay

so i downloaded Ubuntu 7.04 and known it was going to be in iso format,

after completion of the Download i put it into Infra recorder and made sure to  " BURN A IMAGE", i am using a dvd since i don't have any regular cd's :( poor. i let it do its thing and it finished,  i restart my computer with the cd. the computer posts, then it sits with the underscore blinking. it does this for about 2 mins then continues to the splash screen of windows xp. 

I guess i have done something wrong but i don't know what i have done. pls help me be part of the ever growning community of Ubuntu users, i don't know what i am doing wrong





Comp specs:
AMD Athlon processor 64 3400 2.2 Ghz, 1024 ram, Win Xp Home, 100 Gb HD,

---

### Post by k33bz on 2007-07-07
This might be a dumb question, but do you have your computer set up to boot from the cd?

---

### Post by Immolatus on 2007-07-07
Sometimes also certain mobos will not boot from DVD. But yeah check the bios.

---

### Post by Omnios on 2007-07-07
Are you using the free Nero the one that came with my DVD-rw would not burn images.

---

### Post by k33bz on 2007-07-07
i think he is using infra-red, which is a very good windows program to burn iso images, 

but you need to make sure when you burn an image with infra-red that you select burn an image and not burn a cd

---

### Post by Immolatus on 2007-07-07
infra recorder is actually recommended in the official ubuntu instructions on the site.

---

### Post by neoguy2012 on 2007-07-07
Hmm... The two minute pause is a bit troubling... but maybe you need to set the boot order in the BIOS?  It's probably not that, but I thought it might be nice trying the quickest thing first.  

If that doesn't work:

 --  If you still have the downloaded file, try running md5 on it and see if the checksum is the same as stated from the place you downloaded it from.  Windows doesn't include this by default, so you might want to search for an md5 program on your favorite search engine.  I believe this one may work:

[http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)

Throw the executable into the same directory as the iso image.  Then, through the windows command prompt, type in md5sums <--name of image-->.iso replacing <--name of image--> with the name of the iso image.  If it does NOT match with the one listed on the server, then your download was corrupted and you'll have to download again :(.

 --  Try burning at a slower speed so that there would be less of a chance of burning errors. EDIT: never mind... the previous posts mention that your burning software is good.

I'm not sure if any of these suggestions will help... but I thought I might throw in my 2 cents...

 --------------

EDIT:

holy zen!  I replied when I noticed there were no replies to this question.  Hmm...  that was quick.

---

### Post by twiceasworn on 2007-07-07
As everyone else said, I would suggest checking your bios and seeing if you can boot from cd rom.  Make sure it is the first choice.

Other than that, you might want to take a look at the alternate cd installer (text-based install).

Sometimes the discs don't burn right.  I have had it happen to me.

---

### Post by p_quarles on 2007-07-07
Just FYI, you can request a free installation CD from Canonical. It won't be the quickest, but you'll get a reliable live CD.

For burning .ISOs in Windows, I recommend ImgBurn:
[http://fileforum.betanews.com/detail/ImgBurn/1128426215/1]("http://fileforum.betanews.com/detail/ImgBurn/1128426215/1Like")

[Like]("http://fileforum.betanews.com/detail/ImgBurn/1128426215/1Like") others have said, though, you need to check your BIOS settings to make sure you're booting from the CD drive first.

---

### Post by Church.Cameron on 2007-07-07
well i figured if i can install vista and its a dvd it should work umm, i have a HP Pavilion zv6233nr and i don't know if its the mobo but umm i see what i can do to fix this. i just want it to work ahhhh

---

### Post by Vajra Vrtti on 2007-07-07
I think it can be a defect in the CD. Try burning it again **_at low speed _**to prevent errors.
The burned CD should contain several files an folders, and I think it even automounts in Windows.

---

### Post by Church.Cameron on 2007-07-07
ok yea i try to open it in windows and i won't even show up it just tries really hard to read it spins the disk alittle and then stops, then gives it alittle bit more of a spin then stops haaaa

---

### Post by Vajra Vrtti on 2007-07-08
> ok yea i try to open it in windows and i won't even show up it just tries really hard to read it spins the disk alittle and then stops, then gives it alittle bit more of a spin then stops haaaa
That's it. Burn it again.

---

### Post by ramjet_1953 on 2007-07-08
Also remember to burn an image SLOWLY, whether to CD or DVD.

All iso's give problems if you burn them quickly.

Regards,
Roger :cool:

---

### Post by Church.Cameron on 2007-07-08
dose it matter if i am using the i836 or amd 64 i don't know i have a athlon but i son't know if i am using the correct version pls tell me

---

### Post by Church.Cameron on 2007-07-08
what if i use nero 7 and make a "bootable cd that can be booted when i start my computer?

---

### Post by Moop on 2007-07-08
Stick with the i386 version. The 64 bit version doesn't have any real advantages at this point. 
Don't make a bootable cd with Nero, just burn it as an image.

---

### Post by Church.Cameron on 2007-07-08
ok so i am wondering burning it at a low speed for some reason isn't even buring onto the cd but when i do it a maximum its fine ?

AHHHHH i going to g ocrazy with confusion 


:( :( :( :( :( :(

---

### Post by Vajra Vrtti on 2007-07-08
Don't make a bootable CD in Nero. In the first screen, select the option ***Disc image or saved project***. Then choose you iso file and set buning speed to **1x**.

---

### Post by Church.Cameron on 2007-07-08
Job Done well Guys i figured it out and with great luck and no sleep, i made ubuntu work, no i have to get started on the stupid graphics i try to enhance but the screen goes white when i do
LAME

---

