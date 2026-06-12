---
title: "ndiswrapper problems, loads of help needed"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by yui chan 18 on 2007-06-21
i'm having problems hooking up my wireless usb because of ndiswrapper. i type in:

ndiswrapper -i /media/cdrom/netwg111.inf

it sends this back at me:

The program 'ndiswrapper' is currently not installed. You can install it by typing:
apt-get install ndiswrapper - common
bash: ndiswrapper: command not found

as you can see, i'm trying to install netgear wg111v2. are there any drivers i should know about to install, or even commands to get ndiswrapper up and going?


help?


*slowly sinks below surface*

---

### Post by yui chan 18 on 2007-06-21
bump

---

### Post by MEW on 2007-06-21
The message tells you what to do - > The program 'ndiswrapper' is currently not installed. You can install it by typing:
apt-get install ndiswrapper - common

---

### Post by Brightbelt on 2007-06-21
Hi Yui,
  I'm not the most experienced here, but I did successfully use Dniswrapper for the first time recently and successfully got my wireless going with it. 

I would go to the Synaptic Package Manager, do a search for Ndiswrapper and make sure it's installed there. Also,....I'm in Gnome and this worked for me is all I can say - I went into Add/Remove as well and installed it again there. It even has another name "Windows Wireless Drivers".  I found that I had to install that in order to get the GUI for Ndiswrapper. 

Download the windows driver for your wireless to your desktop...If you don't have a connection, you may have to use another computer or find another way. Once you get the windows driver, you'll need to extract it, open the folders and look for the "inf" file. 

You'll then go to the System Menu/Administration/Windows Wireless Drivers and add the inf file there.

That's the way I did it.

I hope this helps,....Frank B.

---

### Post by yui chan 18 on 2007-06-21
ok, will do. thanks. cheers to hoping this works.

---

### Post by yui chan 18 on 2007-06-21
ok...now i have another problem, lol. where exactly in add/remove do i find windows wireless drivers? i know, total noob. :)

---

### Post by bobplano on 2007-06-22
you need to get the drivers yourself. for you it seemed to be on a cd, so just copy it off the cd and do athe rest of what Brightbelt said

---

### Post by yui chan 18 on 2007-06-22
i tried. that's when i got the error message:

bash: ndiswrapper: command not found

any way to combat this? it doesn't seem to want to accept what's on the cd.

---

### Post by wjhildreth on 2007-06-22
I had to work through this myself the last couple of days. I used this article, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") to do it. Read it carefully and follow it and you should be able to get it going.

Regards,

Joe

---

### Post by wjhildreth on 2007-06-22
The driver HAS to be copied to your hard disk, it will not read it from the CD. I read that in the guide I posted the link for. HTH.

Joe

---

### Post by yui chan 18 on 2007-06-22
i copied it onto the windows partition, other than that, i have no idea what else to do.

---

### Post by Brightbelt on 2007-06-22
Yui,
In Add/Remove there's a drop-down menu in the upper right. That needs to be set at "All Available Programs". 
Then in the search field, type "Windows Wireless Drivers".  Then the program should come up.

If I'm right here - for others in this thread to understand - we're talking about a name of a program that gives a Graphic User Interface (GUI) to Ndiswrapper and the program is called 'Windows Wireless Drivers'.  At least that's what it's called in Add/Remove in Gnome. 

Once that's installed you can go to the System Menu/Administration/Windows Wireless Drivers. There, you can add the INF file. 

I hope this clears things up,.....Frank B.

---

### Post by Brightbelt on 2007-06-22
Yui, 
Once you have your windows driver, extract it and then search the Folder(s) for the INF file. That means a file with INF as the extension (like .jpeg or .gif etc, so it would be named " filename.inf ").

Then go to the System Menu/Administration/Windows Wireless Drivers and add the INF file. 
That should do it for you.

I hope this is clear for you, ...Frank B.

---

### Post by wjhildreth on 2007-06-22
I used ndisgtk as the graphical frontend to install the driver. There is a link to the deb and instructions on how to install it. I used my Windows machine, grabbed the debs and drivers and copied them to a thumb drive, then plugged the thumb drive into my ubuntu box and copied them to my home directory.

Does that help?

Joe

---

### Post by yui chan 18 on 2007-06-22
this is assuming i have an internet connection. all it did was try to install and give me an error message. unfortunately, i have no internet access on my laptop when using ubuntu. nor do i have a cable for it. any thoughts on this?

---

### Post by yui chan 18 on 2007-06-22
and unfortunately the site just has a series of links that lead me nowhere...no download there.

---

### Post by yui chan 18 on 2007-06-22
i tried the ap-get install ndiswrapper - common command again, this time i had a more fruitful...outcome? this time it told me what was wrong, couldn't find package ndiswrapper. at least now i know what the error message is for.

---

### Post by yui chan 18 on 2007-06-22
i installed it onto a thumb drive...what's a home directory? the desktop? that's too simple to be it, right?

---

### Post by yui chan 18 on 2007-06-22
bump

---

### Post by yui chan 18 on 2007-06-22
bump

---

### Post by Brightbelt on 2007-06-22
So Yui,
Where are you at now? Do you have the windows driver for your wireless on your desktop?
Or did you not get that far yet?

Please be specific and hopefully I can help you,....
Frank B.

---

### Post by yui chan 18 on 2007-06-22
honestly, i have no idea what i'm doing. just download the windows driver and plop it on the desktop?

---

### Post by yui chan 18 on 2007-06-22
oh! oh! oh! still not working. problem is, i don't have any internet connection on my laptop when working in ubuntu. and i mean zero. no cable to plug it in to my dsl, nuthin.

---

### Post by Brightbelt on 2007-06-22
That's a start, yes. Then......

A) After downloading the windows driver to your desktop, Extract it, by right-clicking the file and choosing "Extract Here". That will extract the folder and put it right by the original file right there on your desktop. 

B) Then Go to the SYSTEM MENU, Choose Administration and then choose 'WINDOWS WIRELESS DRIVERS'. This choice will ONLY be there if you installed 'WINDOWS WIRELESS DRVIERS' in Add/Remove like I told you. If you didn't do that or you don't see the 'Windows Wireless Drivers' option, then go back and review how I told you to install it. 

c) Once you open this window to the WINDOWS WIRELESS DRIVERS program, click the "ADD+" button. That will bring up your file directory. Browse your folders to your desktop and double-click the folder you extracted  in step A. Look for a file with an extension INF. Click that file and click OK. 

That should install your driver successfully.

I hope I've been clear enough. Ask me if you can't understand something.

Frank B.

---

### Post by Brightbelt on 2007-06-22
Yui, 
If this is a wireless USB you're talking about, it sounds like an external item. IF this is true, it should have come with a CD with the drivers on it. 

Load the CD,  pressing the 'shift' key to keep it from trying to install. Once it opens a window on your desktop, you can browse for the driver and copy it and paste it to your desktop.

I hope this helps,
...Frank B.

---

### Post by yui chan 18 on 2007-06-22
the biggest problem is when i go into add/remove to install the drivers...it tells me i need a working internet connection. i don't have one. how to troubleshoot this one? i'm gonna need a way to work around this seeing as how the drivers aren't going to show up in system-->administration without that installation.

---

### Post by Brightbelt on 2007-06-22
Yes Yui,

My apologies. The 'Windows Wireless Drivers' program might not appear unless you have an internet connection. I didn't think of that at first. 

Do you have a modem on your computer? You could connect that way perhaps.

I can't remember if you're on a desktop PC or a laptop, but if you have a friend with an ethernet connection, you could maybe take your laptop and do it there. Even if you have a tower, you could set it up somewhere else with an ethernet connection. 

What is your computer setup? It would help to know that.

Thanks...Frank B.

---

### Post by yui chan 18 on 2007-06-22
i'm on my parents' computer at the moment. they have dsl, i could probably just take the cable out of theirs and hook it into mine. lemme try this. you'll be hearing from me on my laptop if it works.

---

### Post by yui chan 18 on 2007-06-22
i am now connected on my parents' dsl. windows drivers are now installing. awesome.

---

### Post by Brightbelt on 2007-06-22
That's great! I'll check in here case you have any more questions.

Thanks, Frank B.

---

### Post by yui chan 18 on 2007-06-22
i cannot find a .inf file in any of the drivers i've installed.

---

### Post by yui chan 18 on 2007-06-22
ok...now that's frustrating...to get this far and hit another wall. yargh!

---

### Post by Brightbelt on 2007-06-22
Yui,
Technically the INF file IS what you install when you install the driver with Ndiswrapper. The 'WIndows Wireless Drivers' in Add/Remove is a PROGRAM, not a driver. 

If you downloaded the windows driver for your usb device from the website, then you can extract it, and search through the folders for the INF file.  

Does this help you at all?

Frank B.

---

### Post by Brightbelt on 2007-06-22
If you do have the driver folder on your desktop, extract it by right-clicking the file and choosing "extract here". Then when the extracted version appears right there, you can search through that folder for the INF file.

Frank B.

---

### Post by yui chan 18 on 2007-06-22
now that i've downloaded various drivers, none of them seem to have a .inf file. ??? i am so confused. i've even been trying to find drivers that are linux compatible...should i be doing something different?

---

### Post by Brightbelt on 2007-06-22
Yui,
Let's try this; this is what I would do. First find the brand and model number of your wireless usb. Btw, is this an external plug in device? We never got that established, and it's very important to know.

If it's an external device you can find the brand and model number by looking on the device. If it's an internal wireless card, try running this command:
```
lspci
```
In that list, it'll have your card and model number; remember this is for an internal device.

Then I would do a Google search: for example "Broadcom43xxx with Ubuntu" or whatever your card/device is named.

You can also search these forums - just put in the device name and model number and click search.

But first, what exactly IS your device?

Thanks, Frank B.

---

### Post by yui chan 18 on 2007-06-23
i have an rtl8185l as well as a netgear wg111v2. can't find any drivers for either with a .inf file.

---

### Post by yui chan 18 on 2007-06-23
*searches google for valid drivers*

---

### Post by yui chan 18 on 2007-06-23
ok...i finally found a .inf file on the cdrom...but it's not a driver. it's setup.inf. how do i get the netwg111v2.inf?

---

### Post by yui chan 18 on 2007-06-23
sorry...i meant autorun.inf

---

### Post by yui chan 18 on 2007-06-23
is there anyone that can send me a link for a download of netwg111v2.inf or even email me a copy? it would be much appreciated. i've come too far to let it go.

---

### Post by yui chan 18 on 2007-06-23
ok...after having a nightmare of a night trying to figure out what the hell is going on, i ended up accidentally erasing windows from my hd...but came a few steps closer the that light at the end of the tunnel. i finally got the netwg111v2.inf installed...but now i don't know what to do.

---

