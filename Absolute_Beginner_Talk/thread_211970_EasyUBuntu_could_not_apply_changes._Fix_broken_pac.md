---
title: "EasyUBuntu: could not apply changes. Fix broken packages first"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by BlackMambo on 2006-07-09
After lots of little issues like trying to get music to play, videos to work, fonts to look better, Flash to install etc, I found this link and thought I'd struck gold: [http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu]("http://http://ubuntuguide.org/wiki/Dapper#How_to_use_Easy_Ubuntu")

But upon installing **Videos: ENbale viewing videos embedded in webpages with Totem**, it said **[COLOR="Red"]Could not apply changes. Fix broken packages first![/COLOR]**

---

### Post by raldz on 2006-07-09
Why not use Automatix instead? I like Automatix better than EasyUbuntu.. and was just recently updated..

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

---

### Post by siccness on 2006-07-09
Well, you might have broken packages on your system. Load up Synaptec (sp?) and there should be a Broken section somewhere.

---

### Post by woedend on 2006-07-09
if you load up synaptic, choose the "custom" button in bottom left and select broken.  mark that package for either reinstallation or removal(if you do not need it and reinstalling fails).  If you do need it, post the message you get here.

---

### Post by FredB on 2006-07-09
Again an automator related problem ?

Go to terminal, and try 

```
sudo dpkg --configure -a
```

It will help. Also try in synaptic. But automator tools are sometimes more problem maker than anything else :(

---

### Post by FredB on 2006-07-09
> **raldz said:**
> Why not use Automatix instead? I like Automatix better than EasyUbuntu.. and was just recently updated..

[http://www.ubuntuforums.org/showthread.php?t=190025](http://www.ubuntuforums.org/showthread.php?t=190025)

I've heard - can anybody confirm this - that automator stole some code from easyubuntu.

So...:-({|=

---

### Post by woedend on 2006-07-09
I'm against ALL of them...guess you are too Fred?  This stuff really is important to know how to do and if it takes longer than an hour or two to figure out with the thousands of guides...then you probably shouldn't be in ubuntu in the first place.

---

### Post by BlackMambo on 2006-07-09
> **woedend said:**
> if you load up synaptic, choose the "custom" button in bottom left and select custom.  mark that package for either reinstallation or removal(if you do not need it and reinstalling fails).  If you do need it, post the message you get here.
shows as 0 broken packages...

anyway, not a biggie for now.. thx.

---

### Post by raldz on 2006-07-09
> **FredB said:**
> I've heard - can anybody confirm this - that automator stole some code from easyubuntu.

So...:-({|=

mmm.. how could it be stolen if it's open source? I don't know easyubuntu's license, but as long as it's GPL and the used code is republished in automatix, then it should not be an issue.. correct me if I'm wrong..

---

### Post by FredB on 2006-07-09
> **woedend said:**
> I'm against ALL of them...guess you are too Fred?  This stuff really is important to know how to do and if it takes longer than an hour or two to figure out with the thousands of guides...then you probably shouldn't be in ubuntu in the first place.

I think that automators are sometimes useful, sometimes not.

I agree with your last phrase. But automatix is kinda useless with add / remove panel in Dapper. At least for Java, and even Flash ;)

---

### Post by jimmygoon on 2006-07-09
Try "sudo apt-get install -f"

---

