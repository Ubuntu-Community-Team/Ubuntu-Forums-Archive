---
title: "Trouble installing LimeWire"
date: 2005-12-06
forum: Absolute Beginner Talk
---

### Post by Stone_Wolf on 2005-12-06
Hiyas

Having some trouble installing LimeWire onto my Breezy pc. Java installed fine following the Beginners guide. LimeWire seems to have installed fine also follwing the guide, but it doesn't open. I ran the runLime.sh and i now see these errors.

Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE avail able at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

It appears that it's not finding certain files seeing as i do have JRE 1.5.0.5 installed. I know it's working as i'm able to see java webpages and use java chat. So i'm guessing it's something simple as making links? Question is, to what am i supposed to link to?

Thanks in advance for any help.

Regards
SW

---

### Post by canadianwriterman on 2005-12-06
The easiest way to install LimeWire is to download and install Automatix first, run the program and then select LimeWire (and any other applications you want) for installation. Automatix does a wonderful job installing everything.

You'll find Automatix at:

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix)

---

### Post by Stone_Wolf on 2005-12-07
Hiyas

Thanks for the speedy response. I've already got automatix, but that just seems like the lazy mans way out. I'm trying to do everything using offline installs so i can get to grips with the terminal. Believe it or not, i do actually enjoy tinkering around with my linux. If push comes to shove, i'll use automatix. But as it stands i'd rather find out why and how this is happening, and also how to fix it so i can learn for future reference.

Thanks again
SW

---

### Post by adduds on 2005-12-07
If you like terminal here follow this:

First:

sudo apt-get install j2re1.4 j2sdk1.4

Then try and run it again.

If it doesn't, follow this.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334)

Hope that helps, worked for me

---

### Post by cydec on 2005-12-07
I'm not sure this is going to work for LimeWire but i had almost the same problem with azureus. 
And i'm still new to this too!

[Original Post]("http://ubuntuforums.org/showthread.php?p=496651#post496651").

```
sudo update-alternatives --config java
```

Then select the correct package or latest version
If it doesn't work, just pick the one that was there from the start, just to be sure other programs keep running
Or just select the latest version -> what i did (but that was for azureus).

---

### Post by Stone_Wolf on 2005-12-07
Hiyas

Thanks, that sorted out the problem. ^.^ Any chance of getting the sauce of those two files so i can download them for future use? If not, i'm more than happy to sit and wait for them to download again.

Just on a side note, i'm interested to know how LimeWire affects the cap limit on ADSL. I'd like to hear from other South Africans that use it. Is there anything to worry about, or should i just stick to my donkey of a dial-up?

Thanks again for the help

Regards
SW

---

### Post by cydec on 2005-12-07
[QUOTE=Stone_Wolf]Just on a side note, i'm interested to know how LimeWire affects the cap limit on ADSL. I'd like to hear from other South Africans that use it. Is there anything to worry about, or should i just stick to my donkey of a dial-up?
[/QUOTE]

You can disable sharing, if thats what you're asking.
But that wouldn't be fair to the other that you are downloading from, thats not the point of P2P ofcourse.
But i must say: there are times i have to disable it or i would be in serieus trouble with my limit ;-).

---

