---
title: "how do I enable java via ubuntu linux on a chrome OS?"
date: 2022-08-18
forum: Any Other OS
---

### Post by amucia on 2022-08-18
As the title says, Im new to ALL of this. I recently got a New Samsung Galaxy Chromebook Go.
It runs a Chrome OS and Im only familiar with the typical windows. I NEED java on this laptop or It is useless to me. 
I'm not even sure if this is the right forum for the help I need but Ive got to start somewhere so I appreciate any responses.


I have tried following different things it says online and have managed to get Dev mode on and the ctrl alt t command interface but the commands dont seem to work. 
please and thank you anyone! :D

---

### Post by TheFu on 2022-08-18
ChromeOS isn't a general purpose Linux.  It is extremely specialized for what Google things people who want to watch youtube and use google's webapps need.

IF the model can run Android, recent chromebooks have a Java-like JRE, there for Android apps, but it isn't really 100% java. It is the Android version which is different enough that Oracle wasn't able to convince a judge it was the same and stolen by google. There are very important differences, lets just say that.

Further, Java is a hog, so 95% of chromebooks can't run it except limping, slowly, due to restricted memory.  I'm guessing that you didn't buy one of the $800 chromebooks.

So, if you want to run Java and do java development for school, you'll need a better computer or learn to use a $10/month VPS, since the cheap ones are extremely tight on RAM and java is a hog.  If you are a commercial java developer, creating desktop or server applications, you'll want a Core i7 with 64G of RAM and fast NVMe SSDs.

Did I mention that Java is a hog?

OTOH, I did server-side webapp software development with a DBMS on a 2011 dual core Celeron with 2G, after replacing ChromeOS (it was too frustrating) for Lubuntu using the Perl programming language.  Chromebooks are very capable, but we have to be smart about the workloads.

You won't be doing normal  java development on a chromebook. Sorry.  Take the chromebook back or list the hardware specifics, but if you don't already know Linux pretty well, I think you'd be better getting a used $300 workstation to limp along until you can get a better java development workstation.

If you just want to run 1 java application, there are probably some options. I've assumed you want to develop using Java, since I can't imagine why anyone would actually want to run a bloated java application.  Yep - can't imagine that. Just tried again. Nope. Don't see it.

And lastly, ChromeOS isn't Ubuntu, so this thread belongs in a non-Supported OS thread, not Ubuntu Official Flavours.

---

### Post by QIII on 2022-08-18
Moved to Any Other OS.

As stated, ChromeOS is an independent, and very tightly controlled, Linux-based operating system.  That does not mean you can't find help here and it does not mean you are unwelcome to seek it.  However, the Ubuntu Forums is primarily intended to support users of Ubuntu and officially-recognized flavors.

All that said, there are a number of folks here who use Chromebooks -- and some even use ChromeOS on them!  :)

---

### Post by temporos on 2022-08-19
On most new Chromebooks, there is an option in the Chrome OS settings panel to enable a Linux VM. It installs a bare-bones version of Debian (v10, at my last check), and you can install anything on there that you can install on Debian. That said, there is no GUI desktop; you get a terminal window, and that's it. Apps you install can have GUIs, but you need to access them via the terminal. All system maintenance (updates, uninstalls, installs, repository adds, etc.) need to be done from the CLI using tools like vim.

You *can* install Java that way. Like TheFu said, however, it probably won't run very well. I have a pretty high-end Chromebook, and I actually got ThinkOrSwim from TD Ameritrade running on it in the Linux VM, but it was really slow, a lot of features didn't work due to low memory, and it liked to crash if it got overwhelmed with the data stream (again, mainly due to low memory).

If you need to install Java for development purposes, and you need to use a Chromebook, I suggest trying one of the online IDEs out there. Cloud9 on AWS can be relatively cheap, depending on what you need to do with it. Don't even think of installing NetBeans, Eclipse, or BlueJ in the Linux VM on a Chromebook. You'll have a bad time.

---

### Post by amucia on 2022-08-19
> **TheFu said:**
> ChromeOS isn't a general purpose Linux.  It is extremely specialized for what Google things people who want to watch youtube and use google's webapps need.

IF the model can run Android, recent chromebooks have a Java-like JRE, there for Android apps, but it isn't really 100% java. It is the Android version which is different enough that Oracle wasn't able to convince a judge it was the same and stolen by google. There are very important differences, lets just say that.

Further, Java is a hog, so 95% of chromebooks can't run it except limping, slowly, due to restricted memory.  I'm guessing that you didn't buy one of the $800 chromebooks.

So, if you want to run Java and do java development for school, you'll need a better computer or learn to use a $10/month VPS, since the cheap ones are extremely tight on RAM and java is a hog.  If you are a commercial java developer, creating desktop or server applications, you'll want a Core i7 with 64G of RAM and fast NVMe SSDs.

Did I mention that Java is a hog?

OTOH, I did server-side webapp software development with a DBMS on a 2011 dual core Celeron with 2G, after replacing ChromeOS (it was too frustrating) for Lubuntu using the Perl programming language.  Chromebooks are very capable, but we have to be smart about the workloads.

You won't be doing normal  java development on a chromebook. Sorry.  Take the chromebook back or list the hardware specifics, but if you don't already know Linux pretty well, I think you'd be better getting a used $300 workstation to limp along until you can get a better java development workstation.

If you just want to run 1 java application, there are probably some options. I've assumed you want to develop using Java, since I can't imagine why anyone would actually want to run a bloated java application.  Yep - can't imagine that. Just tried again. Nope. Don't see it.

And lastly, ChromeOS isn't Ubuntu, so this thread belongs in a non-Supported OS thread, not Ubuntu Official Flavours.


Appreciate the reply. I'm just totally unfamiliar with this OS. I just know the laptop itself is a galaxy chromebook go. I have a phone service through at&t and was offered this laptop for .99c and was told it has unlimited data for $20 a month, I have a 1 month trial to return it. I use hotspot from my phone for my minimal gaming on Nintendo switch and .jar private server game clients on laptop. I jumped at the offer being so overly excited to downgrade my phone plan (less hotspot data) that I didnt think to consider it may not run java. 

I am totally clueless on where to even find the specs of the computer with how this setup of this computer is. I only recently purchased a windows 11 laptop after using a laptop stuck that was on windows 7 for 4 years. I havent had time to follow the trend, I just play 1 game that requires a .jar extension program to be ran. Could you help me by directing me to the specs and letting me know if this laptop is even worthwhile in doing whatever would be needed to run a simple .jar client?

---

### Post by #&amp;thj^% on 2022-08-19
> **amucia said:**
> 

I am totally clueless on where to even find the specs of the computer with how this setup of this computer is.  Could you help me by directing me to the specs and letting me know if this laptop is even worthwhile in doing whatever would be needed to run a simple .jar client?
Just my 2cents worth, [s]your[/s] ok I wouldn't be happy overall with this rig (reason heavy tester)
And if used as Qlll below suggests its Ok, But your Specs are:
```
Standing screen display size 	&#8206;14 Inches
Max Screen Resolution 	&#8206;1366 x 768 Pixels
Processor 	&#8206;1.1 GHz celeron
Hard Drive 	&#8206;32 GB
Chipset Brand 	&#8206;Intel
Card Description 	&#8206;Integrated
Wireless Type 	&#8206;Bluetooth, 802.11ax
Number of USB 2.0 Ports 	&#8206;2
Number of USB 3.0 Ports 	&#8206;1
Average Battery Life (in hours) 	&#8206;12 Hours
Other Technical Details
Brand 	&#8206;SAMSUNG
Series 	&#8206;Chromebook Go
Item model number 	&#8206;XE340XDA-KA1US
Hardware Platform 	&#8206;Android
Operating System 	&#8206;Chrome OS
Item Weight 	&#8206;3.2 pounds
Product Dimensions 	&#8206;8.88 x 12.88 x 0.63 inches
Item Dimensions LxWxH 	&#8206;8.88 x 12.88 x 0.63 inches
Color 	&#8206;Silver
Processor Brand 	&#8206;Intel
Processor Count 	&#8206;1
Computer Memory Type 	&#8206;DDR4 SDRAM
Flash Memory Size 	&#8206;32 GB
Optical Drive Type 	&#8206;No Optical Drive
Power Source 	&#8206;Battery Powered
Batteries 	&#8206;1 Lithium Ion batteries required. (included) 
```

---

### Post by QIII on 2022-08-19
Not necessarily unhappy if used as a Chromebook is intended, which doesn't include development.

For 99 cents and a good data plan, it sounds great for general web browsing.

---

### Post by TheFu on 2022-08-19
For $1, I'd keep it and use it as intended.  As a 3rd computer or a guest computer for connecting to the internet, using google-apps and watching youtube. It should be fine for that.

If you want a more capable laptop, there's a ASUS VivoBook Touch Laptop - R565EA-US51T : 15.6" 1080p, i5-1135G7, 8GB RAM, 256GB SSD, Win 11 for $300.  I have one from 2017 with an 8th-gen CPU and it works fine.  You'd probably want a larger SSD and perhaps 16G of RAM, but that isn't needed immediately. The only complaint I have is that the keyboard wore out before I'd owned it 2 yrs, but I'm hard on keyboards.  The system works great besides that.
  That deal is at a nationwide computer store in the US - microcenter.  I run a lite Ubuntu on mine and a few virtual machines.

Just saying, there are options and they don't need to be too expensive.  Of course, for $400, you can probably build a desktop with 3x the performance and use remote X11 from the laptop into the desktop for doing most things.  I do that daily, constantly, right now.  This browser is actually running on a different system than where I'm typing.  Use the underlying Linux capabilities to get the most from these things. Compute on the system that makes the most sense, from where every you are in the world.

Calling  "one jar file" a simple application could be true or not.  A jar file is a way to group lots of java modules together, so it could be a monster program or "hello world" from a beginner. We can't tell.

---

