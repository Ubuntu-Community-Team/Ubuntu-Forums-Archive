---
title: "LightScribe?"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-08-20
I was wondering if there was any lightscribe software out there for linux so that I can burn pictures on my cd's with my lightscribe DVD player.

---

### Post by Marsolin on 2006-08-20
I haven't ever been able to find a Linux app that supports Lightscribe. Nero supports it for Windows, but they don't appear to have added the capability to NeroLinux.

---

### Post by nrwilk on 2006-08-20
I'm pretty sure that there isn't any lightscribe support so far.  Sorry!

I know that K3b definitely does not have lightscribe support.  Although, I did see evidence that they've promised to work on including this feature in K3b in the future.  Apparently, they're working with laCie to get it supported.

I did a google search, and came up with many, many forum posts like yours with even more replies along the lines of this:

"I have no idea whether any linux CD/DVD burning program supports lightscribe, but I know that <insert burning program name here> cannot do it."

---

### Post by JNowka on 2006-08-21
thank you for you help.

---

### Post by usererror on 2007-02-16
Bummer, I'm not surprised, but looking forward to it in the future. ;)

---

### Post by bjornolai on 2007-02-16
usererror there is  one now at least. It's included in automatix. Haven't tested it though since I don't have compatible cd's. Buy me some of those one day i guess :)

---

### Post by Jussi01 on 2007-02-16
Yeah, theres one on automatix. Dunno where else you would find it though.

---

### Post by usererror on 2007-02-16
> **Jussi01 said:**
> Yeah, theres one on automatix. Dunno where else you would find it though.

By "automatix" you mean the package manager or apt-get?

---

### Post by Jussi01 on 2007-02-16
No the script for installing stuff - it can screw things on your system  - but usually its pretty reliable. 

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Jussi01 on 2007-02-16
Hehehe... its on the lacie website as well:

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

---

### Post by usererror on 2007-02-16
> **Jussi01 said:**
> Hehehe... its on the lacie website as well:

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)

Awesome, I downloaded it using automatix and it installs, adding a shortcut to the Applications > Accessories menu in Gnome.

I'll play around with it soon and post back results! :D

Thank you!!

---

### Post by watson540 on 2007-03-07
it works out of the box under dapper, but under edgy you have to complete some extra steps before you can get it to recognize your drive

---

### Post by randomnote1 on 2007-05-21
what extra steps are involved?

---

### Post by becatlibra on 2007-05-26
[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

There appears to be free linux apps there - haven't tested though.

---

### Post by soapyfish on 2007-06-05
Hi 

I have just read  this thread 

[http://ubuntuforums.org/showthread.php?t=106197&page=9](http://ubuntuforums.org/showthread.php?t=106197&page=9)  

I followed the instructions on page 9 with sucess I have Fiesty 7.04.  I  downloaded the two packages as directed and converted them to .deb files using "alien"  (with the  -k switch)  and everything worked   100%  

there is more info in the thread for those with extra bother  !! 

;)

---

### Post by Keen101 on 2007-07-13
FOUND THIS ON PAGE 12.

 Originally Posted by reiki  View Post
For FEISTY users (I have not tried this in Edgy or Dapper or anything else)

I have the Lightscribe System Software as a .deb here
This is lightscribe_1.6.45.1.rpm turned into a .deb using alien -k-c.
You need to install that one first.

Then I have the Lightscribe Labeler here
Install that one second.

You still have to run 4L as sudo so to start it:

sudo 4L-gui

Otherwise you won't be able to print (burn the lightscribe image to the media)

I'll leave those up as long as I don't have bandwidth problems from doing so :)


-haven't tried myself yet
-good luck. -keen101

---

### Post by HellRat on 2007-08-15
> **soapyfish said:**
> Hi 

I have just read  this thread 

[http://ubuntuforums.org/showthread.php?t=106197&page=9](http://ubuntuforums.org/showthread.php?t=106197&page=9)  

I followed the instructions on page 9 with sucess I have Fiesty 7.04.  I  downloaded the two packages as directed and converted them to .deb files using "alien"  (with the  -k switch)  and everything worked   100%  

there is more info in the thread for those with extra bother  !! 

;)

What worked 100%? The installation of the software or the actual lightscribe printing? Does it matter what make and model burner one uses? What hardware setup did you use when you made it work?

Any other success stories?

---

### Post by misfitpierce on 2007-08-15
Yup automatix has one for 32 bit only... but I have not tested it yet. I will soon tho :)

---

### Post by hebetude on 2008-01-27
[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

If it complains about libstdc++.so.5 do this:
```
sudo apt-get install libstdc++5
```

---

### Post by esmerine on 2008-01-29
> **hebetude said:**
> [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

If it complains about libstdc++.so.5 do this:
```
sudo apt-get install libstdc++5
```

Jesus, thank you, I was having this problem, in the end i tried to install libstdc++.so.5 and then i lost my nerve.
;D

---

