---
title: "networking ubuntu with windows xp......"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-05-25
ok when i have 2 xp systems networked i can print on one machine and the networked one (with out the printer on it) can print through the network, so basically printer sharing is what im on about.
ive set up networking with my ubuntu machine and my other halfs xp based system and the kids xp based system (we have 3 pc's networked through a 4 port router, and all sharing the broadband modem) im not bothered about setting it up if it is possible and even if it isnt its easy enough to copy the file i want to print over to the xp system with the printer and print from there, i was just curious if it was possible to set up networking like that.
so just to clarify (my explanations leave alot to be desired at times)
xp system (with printer installed) networked with ubuntu system (no printer)
i click print in ubuntu and the file prints out on the printer via the xp system.
if it was 2 xp systems you'd click print on one and providing you have everything set up right the file would print out on the printer.
cheers

---

### Post by Soybean on 2007-05-25
Yes. It's possible. ;)

I haven't done it in a while, so I don't have any solid advice... but if you just go to System-Administration-Printing and then double-click the "New Printer" button, you could try to work it out from there. There's a "network printer" option, and I imagine it would need a lot of the same configuration information that your Windows system needs.

Some printers don't get along very well with Linux, so you may run into trouble... but it's worth a shot, anyway. :)

---

### Post by lazyart on 2007-05-25
Sounds to me that the printer is connected to one machine and the others print "through" the machine to the printer.

That's a basic print server setup and yes you can do that in ubuntu.

---

### Post by dannyboy79 on 2007-05-25
as long as you "shared" the printer thru your windows computer and note down the name you're sharing it as, then you shouldn't have a problem making it a printer on Ubuntu, this is the same way I have my little network setup. If you're at your  linux box, open a terminal and enter
smbclient -L WINHOSTNAME
then it should ask you for a password, this is the password for logging into the windows computer that you want to share a printer from. if it doesn't work, then setting up the printer won't work as it uses smb protocol I am pretty sure. So you'll need to resolve your computers authenticating each other first and making sure each of the users on your ubuntu box is added to "smbpasswd" and that those users are the same as the winxp user OR use the username.map file to map a linux user to a winxp user. 

You can always just go thru the printer setup adn see what happens right? But like I said, at a minimum, you;ll need to share out your windows printer and possibly open it's firewall (port I am not entirely sure, i just set my windows firewall to allow all traffic from 192.168.0.255, which I believe means all ip's in the range of 192.168.0.1 thru 192.168.0.255, i think) Then let's also hope that you have an HP printer as the HPLIP package will have the required driver then. good luck

---

### Post by dannyboy79 on 2007-05-25
> **lazyart said:**
> Sounds to me that the printer is connected to one machine and the others print "through" the machine to the printer.

That's a basic print server setup and yes you can do that in ubuntu.

well, I think that's far from a print server. That's merely sharing out the printer connected to windows. A print server is way more versatile and has way more options than a simple "sharing" dialog box within winxp, at least that's my understanding.

---

### Post by dstew on 2007-05-25
I did it with my Xubuntu Dapper machine printing on an HP 1200 through my wife's XP machine. You need to share the printer in XP, which it seems you have already done. Then, you create on your Ubuntu machine a new printer using the Samba device. I think mine was something like smb:/MARYS/printer2 in the printer administration dialog. You have to have samba client installed and functioning, but I think that is automatic with Feisty. I had to install it separately in Dapper, however.

EDIT: see dannyboy79's excellent post above.

---

### Post by techno-mole on 2007-05-25
cheers i shall give it a go, like isaid its not important but i thought i might aswell try, im working to getting linux on all 3 pc's as the main os, which should make things easier.
just so im not getting confused would that command be smbclient -L WINHOSTNAME and where you put winhostname, do i need to change this to the name of the pc, eg workgroup or what ever the xp system is called ? the reason i ask is because if i type that command in terminal i get a connection error.
i have set up the network for file sharing.

---

### Post by dannyboy79 on 2007-05-25
yes, that's why I put WINHOSTNAME versus something like, SLAYER (ha, if that were only my hostname). I guess I just thought you'd pick up on the fact that you'd need to smbclient the actual hostname of the host you wanted to check connectivity to. You can always read the man pages on almost every single command that someone suggests to you if you're ever not sure how to use it. THat's done with 
man blahblah

Now please don't put in blahblah  (wink wink, smile smile), you would put the command that you want to read the manual for.
example: man smbclient

---

### Post by techno-mole on 2007-05-25
ive just had alook at the network and for some reason ive got to set it up again ?
never mind ill start from scratch.
cheers, and sorry for the dumb question :D

---

### Post by dannyboy79 on 2007-05-25
wait, what do you mean you have to set up the network? Just make sure your linux workgroup is the same as the windows workgroup. Also, I didn't mean for you to think that it was a dumb question, I was merely stating why I wrote what I wrote. Sometimes I think that everyone thinks like I think and I shouldn't do that because that's definitely not an efficient way of helping others because if I would have just explained that int he first place you wouldn't have had to post again.

---

### Post by techno-mole on 2007-05-25
no worries mate, it was a dumb question on my part.
as for setting up the network again, this is where you will see that what i asked about that command was dumb, especially when you find out that i thought i needed to set up the network again because i couldnt access the network either from windows or ubuntu, but then i remembered i had installed firestarter the other day and set it to run on start up, so i couldnt get access because the firewall would allow it, so i turned it off.
so repeat after me - techno-mole is a plank :D

---

### Post by techno-mole on 2007-05-25
ok, so now im getting somewhere, well almost.
im trying the go through system administration printing way
but ive got as far as installing the driver, the printer i want to use is a lexmark all in one printer, model number is x1270, so im trying to figure out the best driver for it as there isnt one for the x1200's.
maybe i should just keep going through until one works ?
@ dannyboy79 will the way you suggested still need the printer driver for that printer ? if so i may have to look and see if there is a linux driver for this model.
cheers for the help though.

---

### Post by Seisen on 2007-05-25
You can try this and see if it works

[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714) and this link says that the Z600 driver works with the X1200

[http://openprinting.org/show_printer.cgi?recnum=Lexmark-1200]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-1200")

---

### Post by dannyboy79 on 2007-05-25
well I am not sure what you mean when you say, "the way that I suggeste". I am suggesting using the gui to "add a printer". In Fiesty they added a way so that you can just add the username and passowrd for the user to get at the networked computer and primnter which is really cool whereas in dapper you had to actually put in the whole smb path of the printer etc etc. Also, a quick Ubuntu Search found this:
[http://ubuntuforums.org/showthread.php?p=2284606&highlight=x1270#post2284606](http://ubuntuforums.org/showthread.php?p=2284606&highlight=x1270#post2284606) post #211

so just as a friendly reminder for future issues, use the search function before posting because that's one of the reasons the forum is just filled with duplicate questions over and over and over of the all the same stuff. Now don't get all upset here, I am merely just making sure that you're aware of the search function and that it's a good idea to use it. This topic in no way is a common one, I mean for the Lexmark printer anyway but I did find it.

---

### Post by techno-mole on 2007-05-25
cheers, i do use the search option, but more often than not i dont get a solution to my particular problem, or i will get enough info to almost do what i want.
anyway cheers for the link, from what ive read i need another driver, so ill have to find it and install it.
cheers for the help.

---

### Post by dannyboy79 on 2007-05-25
um, no. the driver you need is an option in the printer add dialog box.

---

### Post by techno-mole on 2007-05-26
i know theres drivers in the add printer box, but the drivers dont run the printer, well some will let me print, but all that happens is the printer spits out a blank page, and that happens with the majority of the lexmark drivers in the add printer dialogue, from what ive read in order to get the model of printer i have to run on linux i need the z600 driver, which apparently works for the x1200 series of all in one printers.
so i need to download and install that driver and see if it runs the printer properly

---

### Post by dannyboy79 on 2007-05-27
my bad, you're right. you need to follow the guide which requires you download a tar ball. good luck

---

### Post by techno-mole on 2007-05-29
ive got the printer working, and i can now print through the network, which is good.
it was a bit of a nightmare getting the file and then extracting it and installing it, but got there in the end, and i can confirm that the lexmark z600 printer driver works for the x1200 series printers (least it worked for my x1270 all in one) 
part of the problem was the file you needed to download wasnt working, but after reading through the whole thread i found a link to the right file, it would seem some one at lexmark doesnt understand that tar.gz is different to TAR.GZ :D but never mind.
cheers for the help though.

---

### Post by dannyboy79 on 2007-05-29
awesome, glad you got it working!

---

