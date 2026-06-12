---
title: "No Sound ( Using lenovo 3000 n200 )"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by holaco20005 on 2008-02-25
Ok , I just installed ubuntu 64 on my laptop lenovo 3000 n200 
There's no sound but every thing else is work perfect 
can any one tell my in detail , what should i do ?

---

### Post by superprash2003 on 2008-02-25
try this...may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by holaco20005 on 2008-02-25
> **superprash2003 said:**
> try this...may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

thx for trying to help me , tried this but didn't work 
:confused:

---

### Post by zeydun on 2008-02-28
i have had the same problem on my N200 mod. 0769.
I solved it with updating alsa/elsa modules.
After that you have to Edit alsa-base.
For me it worked with the line "options snd-hda-intel model=lenovo".
Don't forget to Reboot:)

---

### Post by ABX on 2008-02-28
I have the same issue.

Can you explain a little more how you fixed the issue?

Ok, got it working, thanks.

```
sudo edit /etc/modprobe.d/alsa-base
```
and add 
```
options snd-hda-intel model=lenovo
```
to the end of the file,

---

### Post by axel112 on 2008-03-12
Works for me to. Thats great! Thank you very much.

---

### Post by holaco20005 on 2008-03-12
When i try to edit /etc/modprobe.d/alsa-base file 
the following warning appear 

Could not save the file /etc/modprobe.d/alsa-base.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How can i figure this out !!

---

### Post by axel112 on 2008-03-13
Use nano och gedit to edit the file. Use sudo to get root-permissions.

```
sudo nano /etc/modprobe.d/alsa-base
```

You will be prompted for your password. Type it in (nothing will show while you type) and then hit enter.

---

### Post by swagathnavin on 2008-03-13
thanks a lot...atlast i was able to hear some sound--

---

### Post by holaco20005 on 2008-03-13
thx alot 
it worked :)

---

### Post by Haalle on 2008-03-30
Works for me too. Thanks a lot!

---

### Post by eeried on 2008-04-01
Hello, 
I installed Gutsy on two Lenovo 3000 n200 for members of our LUG.

Can you confirm the sound works after just adding the line ```
options snd-hda-intel model=lenovo
``` in ```
/etc/modprobe.d/alsa-base
```??

I read some instructions elsewhere and they said you need to install the linux backport module as well.

Our problem is we have too much sound. It comes out of the laptop rotten speakers and it comes out from the external speakers at the same time, and I can't figure out how to mute the laptop speakers.

Any ideas? :confused:

cheers

---

### Post by barbedsaber on 2008-04-01
same model copy, sound worked out of the box, but when I plug in headphones, it still comes out of the speakers (and the headphones) really irritating.

---

### Post by roboa1983 on 2008-04-20
Hi
This quick fix also works for my lenovo desktop.
Thanks!

---

### Post by eeried on 2008-04-21
Now if you have sound coming out of the computer's speakers and a pair of external speakers or headphones, here's what I did after reading the Ubuntu wiki:

Click twice on the gnome-volume-manager (sound icon on your  upper bar) to open it, 
menu Edit > Preferences, 
Check "Headphone", "Front", "PCM" and other stuff like "Front Mic", "Front Mic Boost", "speakers"...
leave the boxes alone if they are already checked
click Okay to close the small window and you're back on the main window 
You can see various controls, like PCM, and Front,a nd every item you check a minute ago
Just click on the volume icon at the bottom of the "Front" control.

Now you should hear sound coming from only your headphone or external speakers.

If you never use the laptop's speakers I suppose you can uncheck "Front" altogether. But you may need some sound without having to carry your headphones along.

Hope this help!

BTW, with Ubuntu Gutsy you don't need to install any package. Just edit the file as noted above and you should be okay.

---

### Post by bullgr on 2008-04-25
works perfect... thank you!!!

---

### Post by Sky.akash on 2008-05-23
> **ABX said:**
> I have the same issue.

Can you explain a little more how you fixed the issue?

Ok, got it working, thanks.

```
sudo edit /etc/modprobe.d/alsa-base
```
and add 
```
options snd-hda-intel model=lenovo
```
to the end of the file,

I have the same notebook (model: 0769) and I haven't been able to get the sound to work with the above fix in both Gutsy and Hardy:(. 

On reboot (after editing /etc/modprobe.d/alsa-base as above) there is this loud sharp piecing noise emitted from the speakers:(.

Has anyone else experienced this?:confused:

---

### Post by eeried on 2008-05-23
```
options snd-hda-intel position_fix=1 model=lenovo
```

If you paste this line at the end of your /etc/modprobe.d/alsa-base file instead of simply options snd-hda-intel model=lenovo, you don't need to turn off Front at all. Turn on Front again, then Reboot.

This works fine on Gutsy haven't tried with Hardy yet.

Hope that helps :popcorn:

---

### Post by CazperII on 2008-05-24
Great this finally resolved the headphones problem, I can confirm that it works with Hardy too

---

### Post by Sky.akash on 2008-05-24
> **eeried said:**
> ```
options snd-hda-intel position_fix=1 model=lenovo
```

If you paste this line at the end of your /etc/modprobe.d/alsa-base file instead of simply options snd-hda-intel model=lenovo, you don't need to turn off Front at all. Turn on Front again, then Reboot.

This works fine on Gutsy haven't tried with Hardy yet.

Hope that helps :popcorn:

I tried that line and I still get the noise on startup ](*,)

---

