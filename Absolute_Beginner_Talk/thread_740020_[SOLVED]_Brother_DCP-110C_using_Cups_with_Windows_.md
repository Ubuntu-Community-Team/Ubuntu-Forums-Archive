---
title: "[SOLVED] Brother DCP-110C using Cups with Windows -"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by fatdadkev on 2008-03-30
I've noticed a lot of people have been trying to get the DCP-110C working, particularly over a network to a Windows XP system i.e shared.

Using several forums and lots of time, I got mine working and hope it may be of use to anyone else.

1st set the printer up in XP and ensure it is shared.

On the Ubuntu system I noticed if I installed the LPR driver then the CUPS driver I could not locate the ppd file to conclude the setup properly, also if I used a similar PPD file then things still didnt work.

The solution is to first remove the CUPS and LPR driver if you have them installed (use synaptic), search for brother and remove the "cupswrapperdcp110c" then remove the "dcp110clpr".

Now the system is clean again....

You may not have a spool directory thats valid so either check its there or make one
sudo mkdir /var/spool/lpd

also make sure tsch is installed, if not CUPS will give an "ERROR csh required"
To install, use synaptics and search for tsch - install that and your almost ready.

Get the LPR and the CUPS drivers for the DCP-110c from Brother (I'm in the UK so this is the link I used) - [http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

I found it a bit easier to be at SU level rather than use sudo for all of this so bear in mind my commands were from SU level, I am also sitting in the directory the .deb packages are located.

Install LPR driver  - 
dpkg -i --force-all --force-architecture dcp110clpr-1.0.2-1.i386.deb

Then install CUPS driver - 
dpkg -i --force-all --force-architecture cupswrapperDCP110C-1.0.2-3.i386.deb

There should be no errors if there are then you may have missed something.

You should now have a printer installed, check in SYSTEM / ADMINISTRATION / PRINTING (in the system menu).
The printer should be called DCP110C and show its using "Brother DCP-110C CUPS v1.1" driver.

What was preventing me using the smb share was the fact I couldn't find the PPD file, this was due to the fact that CUPS was not installing correctly but if you install it using the package manager it does not report that it failed to install properly.
The problem was made worse by the fact tsch was not installed, basically the package installer didn't report that I had a missing directory and other errors !

If it has installed, you should see the pdd file showing in 
/usr/share/cups/model

If it is then in the printer administration, select NEW printer - then navigate to the XP machine that has your Printer - on mine (due to the PC being secured with permissions) I also selected the options to validate the access, if you put the username and password relevent to your XP machine in there it will confirm the share is valid i.e the SMB, username and password are all OK.

Now when it asks for the driver, browse to /usr/share/cups/model and select the 
brodcp110_cups.ppd file.

If all has gone well you should notice the printer is showing "enabled" in the printer configuration policies.

Print a test page and it should work fine.

I have my DCP110 set so that it automatically scans to a folder on the XP machine that's shared over the network so I don't have a need to set the scanner up for Ubuntu.

In total its taken me about 4 weeks of trial and error to get to the steps above, if all goes well it takes about 5 minutes to complete them and you then have a DCP110 running on an XP machine which can be printed to from XP or Ubuntu.

Hope this helps anyone who is trying to get theirs working - it appears that if you only want the printer to work locally that most of these steps will sort that out as well.

I've not tested that theory though but I do have a local dcp110c showing in CUPS and it appears quite happy and just waiting for me to plug the printer in.

---

### Post by Daveth on 2008-03-30
can you please marked this as solved- it looks like a cry for help rather than a rather handy how-to!

---

### Post by Sethalos on 2008-03-30
Just on a note I have a DCP-130c printer and I couldn't get it working either...however, this also worked for me.

Thanks.

---

