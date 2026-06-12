---
title: "Not all updates can be installed / install Real Player - Software Selections"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by franny on 2007-06-28
Hello to all.
):P
I am an official absolute beginner to Ubuntu.

I've had Ubuntu Feisty Faun installed on my new Dell Inspiron E1705 for about 3 weeks now, thanks to my son and I LOVE Ubuntu.  I want to express my respect and thanks to everyone who has contributed to the free (not a reference to $) spirited way of life, sharing and giving and no greed involved. I am proud to be using an OS that it is being created by people who are smart enough to understand the value of working together for the good of all. 

OK - Here is **1st PROBLEM**  

Since Monday night I have had the update icon tell me I had 20 updates -today it is up to 25-but when I opened the list up and click the 'install updates' button I get a message box: 

"**Not all updates can be installed**"
"Run a partial update to install as many updates as possible.
This can be caused by:
   *A previous upgrade which didn't complete
   *Unofficial software packages not provided by Ubuntu
   *Normal changes of a pre-release version of Ubuntu"

I have tried the 'partial update option each time but nothing at all would install.
This is where I am right now (as I write this), about to try the partial upgrade. Once again, it opened and a new box "Do you want to start the upgrade?" and lists these details: 2 packages are going to be removed, 7 new will be installed, 28 packages will be upgraded.
Here goes: Running partial upgrade.... (so far so good)
Applying changes.  OK - I finally made it today.

So that settles that question for now except I would like to know why couldn't I install the updates before? What should I do in the future? Do I just wait a few days as I did this time? Or is there something I should do to make it work right then?

**A Question**
Last night I tried to install the Linux version of Real Player 10 Gold alpha but could not figure out how to install it. The choices were vast and I need time and help with that. I tried to figure out what I needed and downloaded 2 bin files:
legacy-realplay-0.3.0.120-linux-2.2-libc6-i386.bin
and
realplay-0.3.0.120-linux-2.2-libc6-gcc32-i586.bin
but was insecure about placing a command anywhere and I could not figure out what to do or how to find where they went. The 2 bin files above are still in my trash now and could be recovered if I actually should use either. Were they even the right kind of thing I needed to use?
	:confused:

Following directions correctly and making choices is difficult as I am unfamiliar with most of the terms used and with programing language in general except for HTML.

Realplayer10 Gold is still sitting on my desktop uninstalled. I only wanted it so I could watch videos from Alex Jones' [www.prisonplanet.com](www.prisonplanet.com) where it stated my choices were Real Player or Apple Quick Time, and I found they are both are available for Linux. But there were a lot of choices to confuse me. I am not sure it the software version was the best or even right for my system.

Any suggestions? If so, I would need step by step instructions. 

Thanks in advance for any comments and help to come my way.

This is my first venture in a forum (not just Ubuntu but any forum) ever.

**Issue 3**

As for additional software downloads, I am taking things slow as I do not want to make a mess of my system.
I am trying to decide which graphics and web site editor to select. I have seen and am interested in Bluefish for web editing and Gimp Image Editor. Is Gimp the best and closest software to photoshop?

I previously used PhotoShop 7 for all web graphics and Macromedia's HomeSite (the predecessor to Dreamweaver) - using both programs was all self taught and so, while I am not an expert in either, I do know what I want and could get it done with good results - hopefully, the software I select will be similar in ease of learning and use. One of the features I want for web editor are being able to color the code commands for easy reading. Also I like having shortcut for types of code. I do not use the wysiwyg.

OK - this is sooooo long - sorry if it is overload for one post. 
           
       Franny

---

### Post by mali2297 on 2007-06-28
Regarding realplayer, cited from [http://ubuntuguide.org]("http://ubuntuguide.org"):

> 
Alternative Source (RECCOMENDED)

    * Download Realplayer's Official Linux Version 

Then add execute permissions to the installer and execute it.

chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin


The official linux version can be found at [http://www.real.com/linux]("http://www.real.com/linux"). Put the file in your home directory, open a terminal and type the two lines cited above. Then you just answer the questions given to you (choose the default option if uncertain).

---

### Post by franny on 2007-07-01
ooops... forget this one. My reply is below. 

Can't I remove this one?

---

### Post by franny on 2007-07-01
Thank you mali2297 for your help. 

I still had to get my son to help as I didn't even get how easy this was to do. But he said I needed to make the command read (hope I am remembering it correctly) something like this:
_ sudo chmod +x RealPlayer10GOLD.bin_.
Sort of a combination from the commands you gave me. It worked although I don't get how he knew to do that. He is a still a beginner but obviously, a ways beyond me.

**New Question**
I now have RealPlayer working. It is listed and able to launch from my applications menu but I still have the icon from the original download on my desktop. ( I had already downloaded this file from the site you suggested before I got your reply, only it downloaded to the desktop and did not seem to want to move to the home directory. So I went ahead with the instructions with the file still on the desktop.)  
As of now, the properties say it is an executable file but it does not launch RealPlayer.  I tried to make it active to launch but ended up creating a new active "short cut" (a windows term I know) icon that is not an executable file but it does launch RealPlayer and while I do not need it (and can probably trash this or try to move it to the menu bar) I still have the original file on the desktop and I am afraid to delete this original file. It is useless to me sitting there but I cannot seem to move it anywhere else. Do you know whats up with that? I suspect this executable file is the actual software/program files and if I delete it, Realplayer be gone. Am I correct? How can I move it somewhere off the desktop, where it won't be visible? Would I have to re-write the launch command if the file is (able to be) moved?

I have since located a wealth of Ubuntu and Linux tutorials on line and will do my best to get a grip on the language and how to use commands. But I have not got an answer for this yet.


Oh, most of those  updates finally came through yesterday for whatever reason. :) 
Anyhow,  I thank you again.
 Have a great day.

Franny

---

### Post by robertc36 on 2007-07-01
Not an answer to your question but if you install automatix it can install a lot of 3rd party apps for you

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
and just choose your version.
Download and open to install.

---

### Post by mali2297 on 2007-07-02
Once Realplayer has been installed (which it has if it is available in one of the menus), you can safely remove the files from your desktop. If I'm wrong, you can always reinstall it.

The "sudo" command gives you root privileges which means you take the role of the administrator. When you get an error like "permissions denied", you might have to add that command. From the fact that you had to add it to the chmod command and that you can't move the .bin file,  I suspect that somehow the root stands as owner of the file. If that's true you might also get a problem when you try to remove it. If so, type 
```

gksudo nautilus

```
in a terminal. (Alternatively, you could press the keys Alt and F2 and type the line in the "Run program" field.)
That will get you the file browser nautilus from which you should be able to find the file and remove it. The command gksudo acts just like sudo but is for some reason preferred when opening applications in a graphical window. 

Ordinarily, you shouldn't have go through all this trouble when installing some program. Most programs can be found in Synaptic which has a graphical user interface.

---

### Post by franny on 2007-11-11
I found out I can [COLOR="Blue"]**get Real Player**[/COLOR] and it works perfectly by **[COLOR="Blue"] using the synaptic package manager [/COLOR]** to download and install Real Player with all the proper files, librries, etc. instead of trying to follow any one of many different approaches and advice that went from fairly complicated to super complicated with all sorts of different code to compile, to "just insert"... whatever... all of them were way beyond my current user abilities.
 
whew!

---

