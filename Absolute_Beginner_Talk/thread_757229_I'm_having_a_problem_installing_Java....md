---
title: "I'm having a problem installing Java..."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by yngvrr on 2008-04-16
Ive downloaded 4 types java install files for linux and none of them will open or install... 

This message comes up to screen : 

"Could not open the file /home/ingvar/Desktop/jre-6u5-linux-x64.bin.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What does that mean and how do I fix it?

---

### Post by spiderbatdad on 2008-04-16
sun-java6 is available in synaptic package manager. Or install all restricted extras with:```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by yngvrr on 2008-04-16
Ok umm... Thanks for that.. Im just not sure what to do with the information.. Do I copy-paste it to the terminal er is it a wab link... Sorry Im just a total noob and I only just installed ubuntu last night...

---

### Post by FuturePilot on 2008-04-16
Yes, paste it into a terminal.
Applications&#8594;Accessories&#8594;Terminal

---

### Post by yngvrr on 2008-04-16
Ok I did that and then I got this : 
"Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package ubuntu-restricted-exstras"

That, I asume, means I failed... Is there another way?

---

### Post by FuturePilot on 2008-04-16
....

---

### Post by Tom--d on 2008-04-16
> **yngvrr said:**
> Ok I did that and then I got this : 
"Reading package lists... Done
 Building dependency tree... Done
 E: Couldn't find package ubuntu-restricted-**exstras**"

That, I asume, means I failed... Is there another way?

Its extras not exstras ;)

---

### Post by stchman on 2008-04-16
> **yngvrr said:**
> Ive downloaded 4 types java install files for linux and none of them will open or install... 

This message comes up to screen : 

"Could not open the file /home/ingvar/Desktop/jre-6u5-linux-x64.bin.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

What does that mean and how do I fix it?

Here to get the complete Java.

```

sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you want 1.6 sub 6 for 5 in the above statement.

---

### Post by objbuilder on 2008-04-16
> **yngvrr said:**
> This message comes up to screen : 

"Could not open the file /home/ingvar/Desktop/jre-6u5-linux-x64.bin.

What does that mean and how do I fix it?

Welcome to linux. I wrote down instructions for what to do with that file at the end of this message... but then I remembered that with Ubuntu there's a much easier way! 

First open up your software package manager and enable the multiverse repository option. (Sorry not in front of a linux box right now) Then open a terminal and type the following:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

That's all there is to it. :):)

FYI, here's how to use that downloaded file, assuming you have the right one:
1. Change to root so you can install it:
su

2. Make the file executable:
chmod +x jre-6u5-linux-x64.bin

3. Run the installer:
./jre-6u5-linux-x64.bin

4. After answering several questions you're done!

---

### Post by yngvrr on 2008-04-16
Neither of that worked.. not even when I spelled extra right;)....

When I did the first one.. It was the same : " E: couldn't find package ubuntu-restricted-extras"

The other one I got the same only.. : " E: couldn't find package sun-java5-bin"

Im totally lost...

---

### Post by FuturePilot on 2008-04-16
Ok try this
System&#8594;Administration&#8594;Software Sources and check all the boxes in the first tab. Uncheck the CD-ROM if it's checked. Then go to the Updates tab and check the first two and optionally the fourth check box to enabled the backports. Then click Close and Reload when prompted. Then try running that command again

---

### Post by yngvrr on 2008-04-16
Thanks for all your tips, really... Its just that I dont understand half of them an now I have done all of those things, I think, and I'm still no closer to my goal... 
If I do ti again from the start where should I begin? 
What files should I download? 
and how can I install them?

---

### Post by FuturePilot on 2008-04-16
> **yngvrr said:**
> Thanks for all your tips, really... Its just that I dont understand half of them an now I have done all of those things, I think, and I'm still no closer to my goal... 
If I do ti again from the start where should I begin? 
What files should I download? 
and how can I install them?

Ok, follow the instructions in my previous post. After that run
```
sudo apt-get install sun-java6-plugin
```

---

### Post by yngvrr on 2008-04-16
Thank you very much! this seems to be working!

---

