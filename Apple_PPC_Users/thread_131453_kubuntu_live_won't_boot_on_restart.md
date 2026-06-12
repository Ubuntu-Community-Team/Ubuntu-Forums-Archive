---
title: "kubuntu live won't boot on restart"
date: 2006-02-16
forum: Apple PPC Users
---

### Post by K-9 on 2006-02-16
OK - linux ---- I tired getting this live cd disk iamge to boot on startup with the 'c' key down - 5 times and notta - wtf?

damn.....

---

### Post by Ptero-4 on 2006-02-16
Have you burned it to a CD?

---

### Post by K-9 on 2006-02-16
yes I ddid a disk image and burned it to a CD - the CD shows up on desktop and there were many folders and an install - but that is it.  never botted.

thanks!

---

### Post by linear on 2006-02-16
First: what model of Mac?
Did you burn the iso as an image to the CD?
If you reboot and hold down the option (alt) key, does the Kubuntu disk show as one of the choices?

---

### Post by K-9 on 2006-02-17
powerbook g4 866mghz

10.2.8


iso - I guess you mean the hard drive that was on my hard drive... I used the utilities disk image app then drag to cd and then burned it...

I hit 'c' on reboot ---and held down too dfor a long time....nothing...

thank you.



I ended up getting so frustrated - that I decided not to screw with this and I bought a small 12" laptop with Kubuntu installed on it already.... should be here by the end of next week.....I hope.

I screwed around for days to try this live out and notta - I see on another kubuntu forum that many people have had issues trying to get this lice Kubuntu to work.....

I am hoping that this linux experience that I have wanted to get into for 4 years now isn't going to be a windows experience. OS X has been sweet - but I am sick of the updates and the lack of support for the older OS's and also the cost of all of these new apps to run on the new OS.... hence my wanting to get into linux.  not as a geek - just a serious user trying to use my computer to get work done and not writing code or developing stuff - that is way beyond me.

K-9

---

### Post by linear on 2006-02-17
[quote=K-9]I used the utilities disk image app then drag to cd and then burned it...[/quote]
 
That's a problem - doesn't get you to a bootable CD. You need to do it as described [here]("https://wiki.ubuntu.com/BurningIsoHowto").

---

### Post by K-9 on 2006-02-17
Thank you - i am not  sure I follow all of that --- Hmmm..... I will wait for my new laptop with this installed already and go from there.

Thanks.

K-9

---

### Post by Rutabaga on 2006-02-20
Ok, I have a similar problem. I burnt the .iso on a CD with Toast. When I reboot my Emac (700Mhz) Kubuntu load, It asks me some information about my configuration. 
After I see of actions with [COLOR="Green"]*OK*[/COLOR] or [COLOR="Indigo"]* Failure *[/COLOR].
When the list is finish I eard a sound and my screen becomes black. It's like my computer is frozen.
:confused: 
Can you help me?

Thanks

---

### Post by linear on 2006-02-20
Well, you could try the suggestions here, but they were written for an iMac G3:

[http://ubuntuforums.org/showpost.php?p=642271&postcount=2]("http://ubuntuforums.org/showpost.php?p=642271&postcount=2") (one change: the command to restart KDE uses **kdm** instead of **gdm**).

You could also use ctrl-opt-F1 to get to a shell, and try:

```
sudo dpkg-reconfigure xserver-xorg
```

---

