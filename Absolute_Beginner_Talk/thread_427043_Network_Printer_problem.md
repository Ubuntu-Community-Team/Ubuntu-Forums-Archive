---
title: "Network Printer problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by harks11 on 2007-04-29
With an ubuntu experience level of zero I was persuaded to download a copy of Ubuntu on an old 1.3 P4. I must say I was very impressed and continued to install it on the machine without too much trouble.

However my net connection is thru a router which again the machine had no difficulty detecting. The trouble was i could not hook up my Lexmark C510 colour laser (which is connected to the router).

 After reading everything I could find and understanding about 20% of it I gave up. Not before I had download a driver for the printer called lmaab1p1.ppd

Later on in frustration I direct connected the printer to the machine and used said driver . The Printer worked perfectly. 

However I need it to work through the network. 

Is there a simple way around my problem

---

### Post by viciouslime on 2007-04-29
When you are progressing through the add printer dialogue, can you not select network printer, enter its IP, then select the same driver as for when you connected it locally?

---

### Post by harks11 on 2007-04-29
> **viciouslime said:**
> When you are progressing through the add printer dialogue, can you not select network printer, enter its IP, then select the same driver as for when you connected it locally?

That seems to work fine. Except when I try to print I get the Message
"Paused: job-hold-until-specified"

---

### Post by viciouslime on 2007-04-29
> **harks11 said:**
> That seems to work fine. Except when I try to print I get the Message
"Paused: job-hold-until-specified"

Hmmm not sure what to do about that tbh...

---

### Post by harks11 on 2007-04-30
Thanks for trying. I shall potter on and search the various sites. I have a lot to learn so I am content to enjoy the challenges, its so different from microsoft and that makes it all the more fun

best regards

---

### Post by lilian on 2007-05-10
Hi,

I am encountering the same problem.

I am trying to convert my professional desktop PC from WinXP to Ubuntu Feisty. The bigger problem is to print to a Canon iR 2570 Ci, a network printer that could be configured to ask users a username/password to allow the print.

In windows, when you start a print, a dialog box appears and you must enter you username/password.

On Ubuntu, the printer is well detected but the driver isn't included. I have tried to install the linux one downloaded from canon but the install process failed with "segmentation fault (core dump)".

After uncompressing the content of the official driver, I noticed two folders : ppd and pdd. Looking in the ppd folder, I found a driver : cnr257cf1.ppd. I installed it in CUPS and then found the model of the printer in the list.

But when I try to print, no dialog box asks me for a username/password and in the queue, I can see "paused : job-hold-until-specified".

I asked my admin to disable the username/password configuration on the printer and have been able to print.

Here is my experience, I hope this could help you understand your problem. And maybe someone could help me ?

PS I have looked in the file cnr257cf1.ppd and found a section maybe interresting (I hope I could maybe enter my username/password in this file) :

```
*% ==== Device Capabilities ===============
*LanguageLevel: "3"
*Protocols: TBCP

*FreeVM: "2157000"

*ColorDevice: True
*DefaultColorSpace: CMYK

*TTRasterizer: Type42
*?TTRasterizer: "save
 42 /FontType resourcestatus
 {pop pop (Type42)} {(No Type42)} ifelse = flush
restore"
*End

*% Optional flash rom is treated like a disk.
*FileSystem: True 
*?FileSystem: "save statusdict /diskonline get exec
 {(True)}{(False)} ifelse = flush restore" 
*End

*Throughput: "25"
*Password: "()"
*ExitServer: "
  count 0 eq 
  {false} 
  {true exch startjob}
  ifelse
  not
  {
    (WARNING: Cannot modify initial VM.) =
    (Missing or invalid password.) =
    (Please contact the author of this software.) = flush quit
  } if"
*End
*Reset: "
  count 0 eq
  {false} 
  {true exch startjob}
  ifelse
  not
  {
    (WARNING: Cannot reset printer.) =
    (Missing or invalid password.) = 
    (Please contact the author of this software.) = flush quit
  } if
  systemdict /quit get exec
  (WARNING : Printer Reset Failed.) = flush"
*End
```

---

### Post by PhilKE3FL on 2007-05-10
OK, here's another similar problem.

My network printer HP 7350, is attached to a network print server at an IP address 192.168.2.250

I put that in as the IPP address & it put up:  ipp://192.168.2.250 but when I try to use it nothing happens.

Also, if I move the mouse over the ipp://... box it says, "ipp://hostname/printers/<name>"

What does that mean? what is <name> ?

Oh, just like the 1st posting I can attach the printer to the USB port & add a new printer & it finds the printer & can print to it just fine. I did this & then changed the port to the ipp port & added the IP address.

But again  like the 1st posting I need it to work via the print server since all the other computers on the home network do so.

Thanks,
PhilKE3FL

---

### Post by guysmiley25 on 2007-05-10
If your printers are working via USB or Serial, then it should also work as a network printer.

I'm not sure what means you guys are using to setup your printer, but whatever it is, it will just be a front-end for CUPS.


So goto: [http://localhost:631/]("http://localhost:631/") this will take you to a web interface for cups.

Click on add printer: Type in the Name and Description etc. Then continue.
 
Now you have to select a device: Internet Printing Protocol ipp, LPT etc. Then continue.

Now enter Device URL: eg, http//10.1.1.5/ipp

Now select the make of the printer: HP, Dell, etc.

Now select model: Deskjet 840c, etc.

And you should be all good to go.

Here is an example of how I would setup my network printer from the command line
```

lpadmin -p "My Printer" -E -v lpd://10.1.1.1/lp1 -D "HP Deskjet 840C" -L "Server Room" -m foomatic:HP-DeskJet_840C-hpijs.ppd

lpadmin  -d "Calipso"

```

The first command adds the printer, and the second one makes it the default. The web interface is a lot easier than the command line so that is what I would recommend. However network printers usually have to be setup on multiple machines. So command line would make it easier.

---

### Post by tagra123 on 2007-05-13
> **guysmiley25 said:**
> If your printers are working via USB or Serial, then it should also work as a network printer.

I'm not sure what means you guys are using to setup your printer, but whatever it is, it will just be a front-end for CUPS.


So goto: [http://localhost:631/]("http://localhost:631/") this will take you to a web interface for cups.

Click on add printer: Type in the Name and Description etc. Then continue.
 
Now you have to select a device: Internet Printing Protocol ipp, LPT etc. Then continue.

Now enter Device URL: eg, http//10.1.1.5/ipp

Now select the make of the printer: HP, Dell, etc.

Now select model: Deskjet 840c, etc.

And you should be all good to go.

Here is an example of how I would setup my network printer from the command line
```

lpadmin -p "My Printer" -E -v lpd://10.1.1.1/lp1 -D "HP Deskjet 840C" -L "Server Room" -m foomatic:HP-DeskJet_840C-hpijs.ppd

lpadmin  -d "Calipso"

```

The first command adds the printer, and the second one makes it the default. The web interface is a lot easier than the command line so that is what I would recommend. However network printers usually have to be setup on multiple machines. So command line would make it easier.


The problem is --- most of us can get the printer to work on the local machine, but just try printing a testpage from fiesty or edgy -- even using localhost:631 fails to print.   

I messed then got tired of messing and made the printer workover the network  this way:

[http://ubuntuforums.org/showpost.php?p=2591426&postcount=8](http://ubuntuforums.org/showpost.php?p=2591426&postcount=8)

I'd be very happy for someone to tell me how to get something as simple as the testpage to print.

Testpage doesnt' print Open office, firefox gedit, etc will -- but not over the network.  My little hack lets everything print now.

---

### Post by PhilKE3FL on 2007-05-15
I have to admit that I did not understand much of that but I did use the link & after trying a number of things I selected HP 7300 (I have an HP 7350 Photosmart) & it found it & said the printer was installed. I then tried to print the page in the browser & selected 1 page to print. It then printed a line on one page, spit out a 2nd page & printed the browser page on page 3. I hope it doesn't do that every time.

Phil K

---

### Post by scurry7 on 2007-05-21
I had the same problem as you guys.  I finally got mine working (my issue seemed to be fairly easy).  I was going to system > administration > printing, then add printer.  originally I was using the "detected printer", going through the wizard selecting my driver, once complete trying a test page I got "Paused: job-hold-until-specified".  After asking the master (google) i came across this forum which did not help me out (sorry), so I started playing here is what I did: 
So I deleted the printer and tried again: instead of selecting the detected printer I chose Network printer (from add printer wizard) > tcp/socket, HP JetDirect, Raw Connection > then typed my printer's IP and left port 9100 there > selected my driver (i had to install previously) and all's well that ended well.
hope that helps someone out there!
-scurry7

---

### Post by harks11 on 2007-05-25
Thanks for the discussion, Every day I learn a little more, wonderful things forums.
For now my project is on hold due to high WTF levels so had to move the computer to another room, so now working on wireless networking. Never a dull moment.

---

