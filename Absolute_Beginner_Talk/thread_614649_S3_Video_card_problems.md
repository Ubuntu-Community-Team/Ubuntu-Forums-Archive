---
title: "S3 Video card problems"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by Ebrutus on 2007-11-16
I have a S3 Trio 64V+ video card, and when I set the driver to the S3 card, it does not use it properly.

I am only able to use the "Vesa" driver at this point.  Which give me the stunning graphics that only 640x480 resolution can give you.

Does anyone have any ideas on how to install the proper s3 driver to get me going, or some other solutions.

Thanks,
Ebrutus

---

### Post by overdrank on 2007-11-16
> **Ebrutus said:**
> I have a S3 Trio 64V+ video card, and when I set the driver to the S3 card, it does not use it properly.

I am only able to use the "Vesa" driver at this point.  Which give me the stunning graphics that only 640x480 resolution can give you.

Does anyone have any ideas on how to install the proper s3 driver to get me going, or some other solutions.

Thanks,
Ebrutus

HI and are you using feisty or gutsy and have you tried to reconfigure your xorg with this command? ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Ebrutus on 2007-11-16
I'm pretty sure that I landed on:

Xubuntu 7.10 alternate

I did not try "-phigh", but I did try

sudo dpkg-reconfigure xserver-xorg

it lets me pick the s3 driver, and even recommeds it.  And the minimum res I can pick is 1280x1024.

But when I reboot, black screen....

---

### Post by Ebrutus on 2007-11-16
Could it be that my monitor is not set properly?

I am using "generic monitor".

But it's a CTX and I think that I found it on the list, but it might have been set back to "generic" in my many different "reconfigurings".

---

### Post by Ebrutus on 2007-11-16
sometimes I think that I should be using Ubuntu instead of Xubuntu, just so I can use the same codes as everyone else...

am I dreaming. or are they so close to the same that it really doesn't matter?

My computer is approaching dinosaurhood (AMD K62-200, with 196MB ram).

Stop laughing!!!!!

---

### Post by Ebrutus on 2007-11-16
test

---

### Post by overdrank on 2007-11-16
> **Ebrutus said:**
> I'm pretty sure that I landed on:

Xubuntu 7.10 alternate

I did not try "-phigh", but I did try

sudo dpkg-reconfigure xserver-xorg

it lets me pick the s3 driver, and even recommeds it.  And the minimum res I can pick is 1280x1024.

But when I reboot, black screen....

Ok so now you are a blank screen and if you choose the vesa driver you can only get the low resolution?

---

### Post by Ebrutus on 2007-11-16
> **overdrank said:**
> Ok so now you are a blank screen and if you choose the vesa driver you can only get the low resolution?

Yeah, I gave up on the S3 driver, so I switched it to "vesa", to at least be able to see something (in 640x480).

---

### Post by overdrank on 2007-11-16
> **Ebrutus said:**
> Yeah, I gave up on the S3 driver, so I switched it to "vesa", to at least be able to see something (in 640x480).

OMG  just saw the new avatar 

Have you tried to change the resolutions in system, administration, screens and graphics?

---

### Post by Ebrutus on 2007-11-16
I have a gift for picking cute avatars!

When I try to change it in "screens and graphics", the only option is 640x480.  Probably a default for the vesa driver.  And when I use the S3 driver, I cannot get into "screens and graphics", because I cannot display the GUI..

---

### Post by overdrank on 2007-11-16
> **Ebrutus said:**
> I have a gift for picking cute avatars!

When I try to change it in "screens and graphics", the only option is 640x480.  Probably a default for the vesa driver.  And when I use the S3 driver, I cannot get into "screens and graphics", because I cannot display the GUI..

Ok could you post the xorg with this command in the terminal ```
cat /etc/X11/xorg.conf
```

---

### Post by Ebrutus on 2007-11-18
Ok, I attached the file.  This driver thing is driving me nutty!

---

### Post by Ebrutus on 2007-11-20
Is this a dead thread or what?

Ok, I have changed things around a little bit.  I installed Ubuntu 

over Xubuntu.  My machine seems to do fine with it, even though it's 

only a little ole AMD K62-500 with 196MB of memory.  Yeah it's the 

"lil computer that could".

I changed the splash settings like most people advise, and it didn't 

like it.  It gave me a "Gnome" error, I think.  So I changed the 

splash settings back to 1280x1024, and it does fine.

So finally with Ubuntu I can get to 800x600, but I'm going to keep 

pushing the envelope until I get to 1024x768, and then I'll be as 

happy as a clam.

These are my video settings and such.

"S3 Inc. 86c764/765 [Trio32/64/64V+]" Generic Monitor DefaultDepth	

16 Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

I am still only able to use the "vesa" driver to get 800x600.  Can anyone help me get to that next level?

Overdrank,

sorry I have not tried:

sudo dpkg-reconfigure -phigh xserver-xorg

is that still going to help me, or should I not bother.  Sorry...

---

### Post by overdrank on 2007-11-20
> **Ebrutus said:**
> Is this a dead thread or what?

Ok, I have changed things around a little bit.  I installed Ubuntu 

over Xubuntu.  My machine seems to do fine with it, even though it's 

only a little ole AMD K62-500 with 196MB of memory.  Yeah it's the 

"lil computer that could".

I changed the splash settings like most people advise, and it didn't 

like it.  It gave me a "Gnome" error, I think.  So I changed the 

splash settings back to 1280x1024, and it does fine.

So finally with Ubuntu I can get to 800x600, but I'm going to keep 

pushing the envelope until I get to 1024x768, and then I'll be as 

happy as a clam.

These are my video settings and such.

"S3 Inc. 86c764/765 [Trio32/64/64V+]" Generic Monitor DefaultDepth	

16 Modes "1280x1024" "1280x960" "1024x768" "800x600" "640x480"

I am still only able to use the "vesa" driver to get 800x600.  Can anyone help me get to that next level?

Overdrank,

sorry I have not tried:

sudo dpkg-reconfigure -phigh xserver-xorg

is that still going to help me, or should I not bother.  Sorry...

Hi since you have reinstalled and the default depth at 16 did not work for you then I have no other  suggestion. I myself have not used that card but other users have reported that using the 16 depth has solved there issues. It may be that your system is not able to adjust the about or memory to the graphics and other users were able to. Sorry and best of luck!

---

