---
title: "Video Woes"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by mr.henderson on 2006-10-03
Please be gentle.
I installed 6.06 drake and trying to get my video to display something other than 640 x 480.
From previous post, Bulldog said that my HP Kayak probably uses ATI or Invidia.  (It says Adaptec AIC-7880U, but their site shows nothing.) 
So,
Went to ATI and found a page;
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27]("https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27")
On said page, has a link to new install instructions;
[]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.25.18-inst.html")
On that page it has a link to a program that is supposed to tell me what ATI driver I need.
So when I try and run the program, I think, it tells me I don't have the rights.
It says to run it from the ?console? I've attached a screen shot.
Any ideas?
Thanks

---

### Post by mr.henderson on 2006-10-03
[http://ubuntuforums.org/showthread.php?t=249718]("http://ubuntuforums.org/showthread.php?t=249718")
This thread has some likeness to my question, however it stops upon how to change the xorg.conf file.
When I try to change it, it says I don't have the right....how do I do this>

---

### Post by mysticrider92 on 2006-10-03
I would guess that the error means that you need root privlages. To do this, go into the first account you created when you installed Ubuntu and open  terminal. Since it seems like that command works, type: 
> sudo /home/dad/Desktop/check.sh
It will ask you to type your password and it should work.

One other thing, it looks like you could have a problem with the xfree86 (I  don't fully know what this package does, but it has something to do with the display). You might want to try re-installing the package if the display driver doesn't work.

---

### Post by mr.henderson on 2006-10-03
Thanks.
It did indeed ask for my password.
But, it says it command not found.
When clearly I have it on my desktop.
What's sudo? anyways?

---

### Post by mysticrider92 on 2006-10-03
Sudo means "super-user do". It temporarily gives you root privliges to run different things.

It should say something like "is a directory" when you type that in without sudo, which I don't understand. Have you tried simply clicking on the file on your desktop? That should work since it looks like a shell script.

---

### Post by jISh on 2006-10-03
Alright, to edit your xorg.conf you'll need to do something like this from a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
Don't forget the capital X, Linux is case sensitive.

Sudo gives you root authority, as your user account doesn't have permission to change core system files, or anything outside of your /home, for that matter.

I gave you the gksudo command because I told you to use the gedit editor, which is graphical. gksudo is for graphical applications.

If you want to find which video card you have, use the *lspci* command and look for ATI or nVidia. If you're lazy, you can run *lspci |grep nvidia* and *lspci |grep ati* to have it search for you.

---

### Post by mr.henderson on 2006-10-03
Hello Again,
I've attached a text file that I created in Terminal that tell all about my computer i guess.  I saw it on the boards about getting chipset info...sudo lshw.
Am I even looking for the right video drivers?
Frak this is frustrating.:-#

---

### Post by mr.henderson on 2006-10-03
O.K.
I've attached the lspci output in the OpenOffice format.
I think I'm looking for a wrong driver.
What graphics card driver should I be looking for?
oops...will not let me upload an Opt so I made it an .TXT

---

### Post by mysticrider92 on 2006-10-03
Ok, I am assuming from that text file that you have either a slightly older PCI or AGP graphics card. I don't know a whole lot about graphics in Ubuntu (I have intergrated that seemed to "just work" out of the box), so I don't know the specifics about the drivers you need. Most likely you will need a nVidia or ATI driver because very few other people make the chipsets for graphics cards. I would just try the commands jLSh mentioned in his post and use that to find what you need. Also, try Synaptic to find the drivers. They might not be from the maker of the card, but they would be best for your version of Linux. 

I hope that helps.

---

### Post by bodhi.zazen on 2006-10-03
Try this:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)

---

### Post by mysticrider92 on 2006-10-04
> **bodhi.zazen said:**
> Try this:

[[color=blue]bodhi's resolution solution[/color]](http://ubuntuforums.org/showthread.php?p=1566609#post1566609)
That would probably work, I would just recommend one change: start with a resolution of 1024 by 768 instead of the 1600 by 1200. It is a much easier to use size.

---

### Post by mr.henderson on 2006-10-10
First of all, I want to thank you all who have tried to help.
This BB has been a pleasant experience.
Second, I royally messed something up.  I did the Bodhi's resolution solution and must have typed something wrong when I copied the original file....It didn't copy.  So when I went back to replace the file I had changed, it was not there.
I couldn't remember all the changes that I had made, so I had to re-install the entire U6.06.
I'm back up and running and have even got the refresh rate up to the correct 85 MHz!!!!  But I have not been able to change the screen size.  I've tried everything that is described in Bodhi's page and all the linked pages that it ties to.  I've found out that I have a HP FX-4 video card and I am running it in the Kayak XW D6488N that it is supposed to be in...[http://www.tldp.org/HOWTO/HP-HOWTO/hp-hardware.html]("http://www.tldp.org/HOWTO/HP-HOWTO/hp-hardware.html")
and I have found the specifications for it.  I have also found a HP site that says X server will run on it.  [http://www.tldp.org/HOWTO/HP-HOWTO/hp-hardware.html]("http://www.tldp.org/HOWTO/HP-HOWTO/hp-hardware.html")
I've even found a site that says that it is really an Adaptec video card with a HP branding...[http://america.hongfaith.com/Controller_RAID/Raid/HpFastRAID2.htm]("http://america.hongfaith.com/Controller_RAID/Raid/HpFastRAID2.htm")

I've wasted bunches of time all to no avail.
So maybe you all can answer a couple of easy Linux questions for me.
1) What's with the Command Line Interface?
Why have we gone back to command lines like the DOS Days?  If we want this to be accepted by the masses, ought we to make it easy for people to understand and intuitive to use?
2) Couldn't a default video driver be developed that could back door all video cards?  No, maybe not with all the advanced features, but surely with the basics of refresh and screen resolution.  In searching for the answers to my problem, I have come across a lot of people having the same issue.

Just some observations;
I am not a newb to computers....Ubuntu and Linux, yes.
But if I am having this much problem and I'm willing/able to search for fixes, how is an average person going to get around?
Maybe these question/observations are due directly to my ignorance when it comes to programming.  If so, I accept that and maybe those of you with the programming experience can readily see the holes in my cheese.  But I don't understand.
Please understand, I'm not throwing rocks when I live in the glass house at the top of the hill.  I really like what I have seen of this Ubuntu/Linux and love the whole community share/freeware idea.
So maybe before I spend more time groping around in the dark, you as a community of users could clue me in.
Thank you!

---

### Post by mr.henderson on 2006-10-10
O.K.
Failing at this machine, can any of you reccommend a machine that will be bare bones and will basically be able to install the Ubuntu and have everything working properly? I was looking at  [http://www.pricewatch.com/3/335/335-2.htm?Computer+Systems+-+No+OS]("http://www.pricewatch.com/3/335/335-2.htm?Computer+Systems+-+No+OS")
and see that once again most offer just on board graphics....would that work since it would be a newer system?  Or am I going to have to muck about with the CLI again?
Thanks:confused:

---

### Post by Scarlett on 2006-10-10
I don't really have any answers for you.  I just wanted you to know that I've shared your pain with the refresh rate thing.  It took me two days to find help that was easy enough for a newbie like me to follow. It's extremely frustrating to deal with the voodoo of the command line and a new environment while your monitor is giving you a headache just by looking at it.  I don't know exactly what I did to fix it, but just in case it helps, here's the link to what finally worked for me and somewhere in there is where you can add your own resolutions and refresh rates.  

[http://www.ubuntuforums.org/showthread.php?t=250070](http://www.ubuntuforums.org/showthread.php?t=250070)

In answer to your question about why the command line, I've been assured by some of the most friendly and helpful people here that not only is it incredibly powerful once you learn to use it (I'll have to take their word for it, I'm still learning) it's much easier and precise to walk someone through a problem using exact commands rather than saying "click this, go to that, right click, choose option whatever, blah, blah..."  I found this link helpful for understanding the basics of the CLI.

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

---

### Post by bodhi.zazen on 2006-10-10
> **mr.henderson said:**
> O.K.
Failing at this machine, can any of you reccommend a machine that will be bare bones and will basically be able to install the Ubuntu and have everything working properly? I was looking at  [http://www.pricewatch.com/3/335/335-2.htm?Computer+Systems+-+No+OS]("http://www.pricewatch.com/3/335/335-2.htm?Computer+Systems+-+No+OS")
and see that once again most offer just on board graphics....would that work since it would be a newer system?  Or am I going to have to muck about with the CLI again?
Thanks:confused:

Sorry you are having problems.

First, it should be said Linux is different then windows and the CLI is an integral part of Linux. How many months/years experience do you have with windows? Give Linux time and you will learn. As you become more familiar the CLI will be more user friendly.

Second, there is a default video driver, vesa. In a terminal:```
sudo dpkg -reconfigure xserver-xorg
```
This will take you through all the options, choose vesa as the driver and 16 as the default color depth.

Otherwise stay with the defaults.

Third, hardware problems are a pain in any OS. Before you buy an new box you may want to try an alternate distro on your current box. Consider Knoppix.

Last, if you fail with this current round of configuration, would you please post your xorg.conf?

---

### Post by mr.henderson on 2006-10-13
Again, thanks for your responses.
I did a screen shot capture after I ran your sudo dpkg CL.
It says that something is conflicting?  I've attached it.
I'll try to post my xorg.conf file if I can figure out how.
Thanks for being so patient!


I had to convert the xorg.conf file to xorg.txt b/c it would not upload the xorg.conf file....same words as original, just changed it's extention.

---

### Post by mr.henderson on 2006-10-15
B:confused:

---

### Post by bodhi.zazen on 2006-10-15
There should be no space between "dpkg" and "-recofigure"

(sorry, my typo) :redface:

Like This:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

