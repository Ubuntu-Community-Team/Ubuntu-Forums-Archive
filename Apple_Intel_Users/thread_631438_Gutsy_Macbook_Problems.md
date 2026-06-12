---
title: "Gutsy Macbook Problems"
date: 2007-12-04
forum: Apple Intel Users
---

### Post by onlyproductions on 2007-12-04
I've been working with linux for...i'd say 3-5 months and I put it on my home comp and even converted some of my friends to using linux. Now im ready to put gutsy on my macbook. I made a live cd put it in booted it. Then in the live cd made sure that everything worked. I was just about to install when to my dissapointment My wi fi wasn't working. I looked on google and it gave me some 40 step solution and i am a novice. I want my mac to house ubuntu but with no wi fi i dont see the point. in there some easy solution. or at least some distro which is made for the macbook.

---

### Post by Smutronic on 2007-12-04
Hi onlyproductions,
i bought a white MacBook yesterday and i am discovering exactly the same problem. I compiled a new Kernel 2.6.23 with a mactel patch. This is very well explained in a howto in the sticky post. 
But wifi is still not working. 
I also tried to install the madwifi-driver, explained in an other tutorial, but the wireless does not work.

---

### Post by onlyproductions on 2007-12-04
isnt there some kind of linux that was made for mac spiecifically?

---

### Post by cyberdork33 on 2007-12-04
> **onlyproductions said:**
> isnt there some kind of linux that was made for mac spiecifically?

No... There is not, because there is no need for it. You have PC hardware. PCs with that same Wi-Fi card as you get the same result. 

The issue is your Wi-Fi card is not yet supported by the driver in Ubuntu. You will have to compile a newer version of madwifi to get it working. There is a post in the FAQ to get that done. You can alternatively use ndiswrapper, though that might be even more confusing for you at this point.
[COLOR=Black]
Smutronic, since you are using a custom kernel, none of the drivers in the repos will work because they were compiled against the Ubuntu kernel. You will have to compile madwifi manually.


[/COLOR]

---

### Post by Smutronic on 2007-12-05
It´s the first time i am using a custom Kernel. Does that mean i should generally download, compile and install new programs manually instead of installing them with adept-manager? 
Or only in the case of the madwifi-driver?

But thanks for the hint, i will feedback if it works. :D

---

### Post by cyberdork33 on 2007-12-05
> **Smutronic said:**
> It´s the first time i am using a custom Kernel. Does that mean i should generally download, compile and install new programs manually instead of installing them with adept-manager? 
Or only in the case of the madwifi-driver?

But thanks for the hint, i will feedback if it works. :D

no, it will not affect applications, only kernel modules (drivers)

---

### Post by /earth/sam on 2007-12-07
ok i tried using the madwifi driver as well to no avail so could one of you geniuses who posted above actually give directions on how to update it or give links to the FAQs you reference? thanks.

---

### Post by Smutronic on 2007-12-07
> **/earth/sam said:**
> ok i tried using the madwifi driver as well to no avail so could one of you geniuses who posted above actually give directions on how to update it or give links to the FAQs you reference? thanks.

I was referencing to this Sticky-Thread: [http://ubuntuforums.org/showthread.php?t=493393]("http://ubuntuforums.org/showthread.php?t=493393")

---

### Post by tiiim on 2007-12-07
> **/earth/sam said:**
> ok i tried using the madwifi driver as well to no avail so could one of you geniuses who posted above actually give directions on how to update it or give links to the FAQs you reference? thanks.


If you have OS 10.5 you can use ndiswrapper to abstract the Windows driver from the 10.5 cd. I couldnt get mad wifi myself to work, however by extracting the Mac windows driver it works great. :)

---

### Post by onlyproductions on 2007-12-07
Any chance that hardy heron will support the drivers?

---

