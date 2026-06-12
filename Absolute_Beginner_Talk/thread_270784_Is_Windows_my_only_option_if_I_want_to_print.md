---
title: "Is Windows my only option if I want to print?"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by alanmzifa on 2006-10-03
Printing. How do you get it to work?

I've read numerous how-tos, scoured the web, this forum, printed a ream of paper (in Windows) and I still feel like I've got 200 bits of a 5000 piece jigsaw.

I've read about CUPS, installed my 3 in 1 HP 7110 via CUPS web and yet it still needs to ask me for a password and user name when I want to print something. 
I installed the web interface but I can't say it gave me the options I wanted. I was expecting to get the ability to print in draft and collate documents, more than 1 page per sheet, start printing from last page etc. and all via a GUI.

I've installed something called XPP but if I print something from my browser these other programs don't launch so I don't get any of the options they offer.

Am I being stupid or is this just not available within Linux in a GUI?  

***Is Windows my only option*** if I want to print 2 pages on 1 or collate a document or set default to always print from last page?

---

### Post by b_martinez on 2006-10-03
HP has linux drivers. You say you have a 3-in-1. Do you mean a PSC? If it is, you need the HPLIP package. Should be in repos. 
HPLIP= Hewlett Packard Linux Inkjet Project.
I have the PSC 1610 All-IN-One and it work's great.
Bill

---

### Post by sonny on 2006-10-03
But you add the printers in the printer dialog, just go to system>preferences>printers (I'm guessing the position because I've changed all that) then just add a new printer and that would be all, the problem is that the web interface requires root permission, this way you can print without any hassle at all.

---

### Post by steve.horsley on 2006-10-03
I don't know how you installed that printer, but try this method:

Turn the printer on
Go to the menu System->Admiinistration->Printing
Double-click the add printer icon
Choose a locally detected printer and all the otehr details
Set the new printer as trhe default printer

---

### Post by alanmzifa on 2006-10-03
**b_martinez**, it's an Officejet 7110 which I think was the 3in1 range immediately before PSC.

The HPLIP driver on the Ubuntu repositories is 0.9.7. On the HPLIP page it's 1.6.7 or something so the Ubuntu driver seems miles behind. 
Anyway, If I hit print in my browser the HPLIP doesn't come up, I don't know how to install the newer HPLIP as it's not in Synaptic like the 0.9.7 so I seem to be left with the standard (no) options when I hit print. Going another route, I can launch XPP from Terminal but can't find a way to get to the web browser to print the page I want. And anyway, having to open up terminal to print a page..... nah. That's just too awkward. In Windows we hit Print, Properties and configure what we want, surely it's possible to do that in Ubuntu?

**sonny** and **steve.horsley**, as far as I'm aware I've done all that but when I hit print in the browser all I get are the basic options (print, margin, footer, header).


All..... I'd be interested in seeing screenshots of the printer dialogue you get up when you hit Print or Print Set-up.

thanks

---

### Post by lapsey on 2006-10-03
i had printer problems but turboprint was a great solution for me [http://ubuntuforums.org/showthread.php?t=213055](http://ubuntuforums.org/showthread.php?t=213055)

---

### Post by Sef on 2006-10-03
If you want to do printing and scanning, the .97 driver works fine.  I have PSC 1610, and don't have a problem with either one.  I am sure it would work fine for you.  Why not give try it?

---

### Post by rfruth on 2006-10-03
My 1510 installed without a hitch

   [ATTACH]16833[/ATTACH]

---

### Post by Ocxic on 2006-10-03
this may seem silly to ask, but have you tried just not putting a user/pass combo in and hitting ok anyway??

and turboprint is a good program got my canon i560 workin perfectly. worth the money, not expensive.

---

### Post by harry555 on 2006-10-04
On the hlip website there is a table listing all the HP compatible printers and the version of hlip required.

---

### Post by alanmzifa on 2006-10-04
**lapsley**, turboprint won't support my printer but I'd rather go the free route anyway.

**sef**, I thought I has installed 0.9.7.  I have installed HPLIP toolbox and can see that from my menus, is that the same thing?

rfruth, I can only get a GUI up like the one in your picture after I've sent the page to print and go in to "Printing" from the menus and select properties from the drop down. That doesn't seem right to me. 
Also, whilst "advanced" tab gives to some quality options etc. it still doesn't allow me to print 2 pages a sheet, print in reverse order, collate etc. 

**Oxcic**, I don't seem to be getting the box up anymore asking me for that, but I think it came up after launching HPLIP Toolbox and asked me toinstall the printer (which was alrady installed).

**Harry**, I've found my printer and a newer version of the driver there although others above say 0.9.7 which comes on the repositories should work fine.

**All**, when I hit print in a web browser I get just a plain GUI offering header and footer and margin settings. From what everyone is indicating I should be getting something a lot more fancy popping up.

Is that correct?

By installing HPLIP Toolbox have I in fact installed the HP driver or not? Could that be the problem?

---

### Post by alanmzifa on 2006-10-04
I still don't get this. Look at the screenshot attached.


I've downloaded the latest HPLIP driver 1.6.9 and manually installed it (there's a first) but all I get when I hit print within the browser in this attached below.

Am I missing something here?

HPLIP 1.6.9. is installed and I can open HPLIP Toolbox from the menus (it can print a file form a hard drive location) but how do I access it's functionality when I just hit print, or page set-up from the browser to print a web page?

---

### Post by dannyboy79 on 2006-10-04
it appears that you haven't installed the printer yet. maybe you have installed the latest driver but you haven't. the reason i say this is because I have seen that dialog come up when I hit print and it was because there is no printer installed yet.

---

### Post by alanmzifa on 2006-10-04
I've went through the automated HP printer set-up process so surely I have installed the printer. 

When I go in to HPLIP Toolbox it's there, and the fax.

Anyone?

---

### Post by dannyboy79 on 2006-10-04
when you are in firefox and you hit print, does your installed printer show up? or when you go to system, admin, printers, is your printer there?

you may have installed the HPLIP thingy or whatever but obviously that isn't interfacing with your apps. I have a HP Office Jet D135 and I don't use the HPLIP tool box or whatever. I simply added the printer thru the cups interface. you might of been having problems with the fact that the default cups thing in ubuntu doesn't let admin actions occur, you have to first add the root user or something like that to your cups group. then when you go to the cups interface, it should ask you for a password for your sudo account I think and then you are able to install a printer. i will try and find the link i used and post it here if you want that is.

---

### Post by dannyboy79 on 2006-10-04
here is the link but i also realized that you could always install the gnome-cups-manager. I have heard it is way easier to config than cups. good luck. by the way, i use my hp d135 over smb because it is hooked up to my winxp box, so obvisouly if i can get an hp d135 to work over samba thru a winxp box you should certainly be able to hook an hp ptiner directly to ubuntu box and get it to work. one of the key things is the driver you choose. if I remembered which driver i used I would tell you but I am at work right now.

oh, i just gogled and found this, it should help.
[http://www.freesoftwaremagazine.com/articles/printing_ubuntu#comment-13056](http://www.freesoftwaremagazine.com/articles/printing_ubuntu#comment-13056)

---

