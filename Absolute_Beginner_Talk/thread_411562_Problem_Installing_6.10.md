---
title: "Problem Installing 6.10"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-04-17
I downloaded and burned the CD for 6.10 desktop.

I originally tried to install 6.06 but I was having troubles with it working with my wi-fi card even though it says it is supported. So I decided to try installing 6.10 and maybe that will work out better with my wifi card.

I am trying to install it on my laptop, so I booted to the cd and went to start in Safe Graphics Mode:

And I got this error before It even started:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? Yes or No

I am not quite sure what to do, before I installed 6.06 and then just updated while I was in 6.06 to 6.10, but whenever i did gksu "update-manager -c -d" it would say, -c is invalid.

Thanks :)

P.S - I saw a post similar to this but it was unasnwered

- Ash

---

### Post by deadgobby on 2007-04-17
Does your LT have AMD?
Gobby

---

### Post by ohmycar on 2007-04-17
Nope, it is an Intel Centrino Duo proc.

Other specs are:
Intel GMA950
1gb RAM
80 gb hdd
Wifi card: Intel Intel(R) PRO/Wireless 3945ABG

---

### Post by Sef on 2007-04-17
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Maybe you need to install with the alterante cd; sometimes that will work where the alternate cd fails.

---

### Post by ohmycar on 2007-04-17
Sorry, but what does md5sum mean?

And no I did not burn it at 4x, I will try that.

Also, if that does not work, is there a reason why the gksu update-manager -c did not work for me in 6.06

---

### Post by deadgobby on 2007-04-17
[https://help.ubuntu.com/community/Checksum](https://help.ubuntu.com/community/Checksum).
 The reason for a slow burn on a ISO image and really any thing els. Data can be lost at fast speeds. When burning at slower speeds on a CDR. It contains most of the data. It is not like the faster the tape speed the better the quality. 
Gobby

---

### Post by ohmycar on 2007-04-17
Well it is burning right now at 8x, it would not let me choose 4x for some reason.
I have my fingers crossed :)

---

### Post by ohmycar on 2007-04-17
sigh, still no luck.
I get the same error message, not quite sure why.

So at this point, not sure what to do. :(

---

### Post by confused57 on 2007-04-17
> **ohmycar said:**
> I downloaded and burned the CD for 6.10 desktop.

I originally tried to install 6.06 but I was having troubles with it working with my wi-fi card even though it says it is supported. So I decided to try installing 6.10 and maybe that will work out better with my wifi card.

I am trying to install it on my laptop, so I booted to the cd and went to start in Safe Graphics Mode:

And I got this error before It even started:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem? Yes or No

I am not quite sure what to do, before I installed 6.06 and then just updated while I was in 6.06 to 6.10, but whenever i did gksu "update-manager -c -d" it would say, -c is invalid.

Thanks :)

P.S - I saw a post similar to this but it was unasnwered

- Ash

When you get the xserver error message, have you tried clicking "Yes" to configure your video controller?

You can probably try "vesa" or "i810" video drivers for your video card.

You might want to read this link for reconfiguring your xserver:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by ohmycar on 2007-04-17
Thank you for the link, I am installing 6.06 right now and when it is done, I am going to try using the 6.10 cd to install again, if I get that same error, I will try the method used in the page on that link you provided :)

hope this works!

---

