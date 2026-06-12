---
title: "Can't print OpenOffice... All other apps print fine?!?"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by theline9 on 2007-02-04
I've spent about 16 hours researching and can't find help... Using "Edgy"... All updates... ALL apps print fine on Canon ip2200. None of the Koffice or OpenOffice apps print. When I go to "print setup" in Writer, it recognizes my printer. Previews fine and when I click "print" it appears that it sent it but nothing happens. I printed a test page from "spadmin" with no problem. The printer icon in Writer/Calc/Base all have a lightning-bolt through it (no link ?). PLEASE HELP!!!! SAVE ME FROM CONSIDERING WINDOWS EVER AGAIN!!! Thank you in advance for any help.

---

### Post by NonPapa on 2007-02-07
this may sound funny, but I think I had the same problem. However, I believe that I installed the printer and shut the machine down/restarted it, and then it was fine from OpenOffice.

Does the problem still persist?

Plinonpli

---

### Post by theline9 on 2007-02-08
Here's what I did since my last post...
1. Format hard drive and clean re-install Kubuntu 6.10 (Edgy)
2. Installed Automatix and Synaptic and got all updates
3. Installed Canon ip2200 printer and tested it ...
. . . . Korganizer:     PRINTS fine
. . . . Kate:              PRINTS fine
. . . . Adobe Reader: PRINTS pdfs fine
. . . . Gimp:             PRINTS images fine
4. Installed OpenOffice 2.1. In "KMenu > Office > Printer Administration... OpenOffice recognizes my printer and PRINTS TEST PAGE perfectly.

When I open any Office program (Writer / Calc / Base)... NONE OF THEM PRINT ?!?!?!?!?

Anyone have a clue??? I don't know what else to try. I've searched the web for the past 82 hours... no joke. Thanks to anyone trying to help.

---

### Post by Maestro23 on 2007-02-08
> **theline9 said:**
> Here's what I did since my last post...
1. Format hard drive and clean re-install Kubuntu 6.10 (Edgy)
2. Installed Automatix and Synaptic and got all updates
3. Installed Canon ip2200 printer and tested it ...
. . . . Korganizer:     PRINTS fine
. . . . Kate:              PRINTS fine
. . . . Adobe Reader: PRINTS pdfs fine
. . . . Gimp:             PRINTS images fine
4. Installed OpenOffice 2.1. In "KMenu > Office > Printer Administration... OpenOffice recognizes my printer and PRINTS TEST PAGE perfectly.

When I open any Office program (Writer / Calc / Base)... NONE OF THEM PRINT ?!?!?!?!?

Anyone have a clue??? I don't know what else to try. I've searched the web for the past 82 hours... no joke. Thanks to anyone trying to help.

Man, I went over to the OpenOffice forums to try and find you some help... Then I saw your exact same post over there.:) 

Good luck with this man.

---

### Post by lns on 2007-05-07
I've been trying to figure out printing issues in OOo 2.2 since my Feisty upgrade. I don't have the symptoms, but here's what happens:

I go into Calc and try to print a spreadsheet (all sheets). There is text + borders on the first sheet (1 page), graphs in the second sheet (3 pages) and text in the third (1 page). 

When I go to Print Preview, the first sheet doesn't even show up (blank page for page 1 print preview), and the graphs on the second page are all out of whack, some off the page borders completely (above the white page in the grey area). The fourth page doesn't show either.

I've re-created my spreadsheet from scratch, including graphs, and did $rm -rf .openoffice* - neither have helped. I'm pretty sure this has been since the upgrade to Feisty (which upgraded OOo to 2.2 from....was it 2.1 or 2.0?)

I also re-installed my CUPS printer driver (an HP Photosmart 8150 using hpij driver), and come to think of it, CUPS altogether, though I did do this because of a problem with network printing that ended up to be the checkbox "Share this printer" magically un-checking itself after the Feisty upgrade. Blah.

Thanks for any insight!! 

- Jordan

---

### Post by Surtr on 2008-01-09
I have the same problem. Test page works, but spreadsheet doesn't. I get a "Error while printing" message.

---

### Post by mikeyphi on 2008-01-09
One suggestion - Open Office seems to have page size set to Letter by default, this could cause an issue with some printers.......
have you tried to set your specific page size under file/printer properties - (printer) / properties

---

### Post by Surtr on 2008-01-09
Yes, I did. I've put it to A4 already.

---

### Post by philphil on 2008-02-19
Hi, I had the same trouble just now.  It turned out my cups scheduler needed restarting! ha!  

I found this: [https://answers.launchpad.net/ubuntu/+question/22028](https://answers.launchpad.net/ubuntu/+question/22028)

and I did what was written in the first reply which is this: 

"Try to check if cupsys is running

Please open a Terminal from the menu Applications->Accessories->Terminal and type:
<code>
sudo /etc/init.d/cupsys restart
</code>
give your user password when requested, you don't see nothing when you type it, then press enter.

Hope this helps"

---

### Post by atatistcheff on 2008-03-05
I'm having the same problem with Gutsy on my laptop.  All other apps print fine but Openoffice (Writer and Spreadsheet) don't print.  My Brother printer display lights up like it's thinking about printing but then it goes out and does nothing.  I can export my Writer docs to PDF and print them from the viewer, can print from Firefox, test page, you name it.  Nada from OpenOffice...

If anyone finds a good answer to this please post up.

Mine is a network printer using CUPS.

Thanks!

---

### Post by n6yga on 2008-03-13
Ok. I just found a solution to this insidious problem.

Backgroud: Trying to print from Open Office aps, or ANY app for that matter. Can't print from anything. Last week, printing worked fine to a networked, Laserjet 2100m. This week? Nothing. Damn!

Ok, so I started thinking (I know, bad idea) and remembered that I have HPLIP creating printers at home. I'm on my laptop at work. So, I installed HPLIP from Add-Remove programs. Built a new printer using that front-end and BAM! Works like a charm. I will venture a guess and say that Cups has some bugs, to say the least.

Anyway, all of you guys having the same issue should try installing HPLIP and building network printers that way. Worked great for me!

Mark.

---

