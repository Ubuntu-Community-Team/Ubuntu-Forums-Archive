---
title: "I need a printer driver"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Georgeiger on 2007-07-24
Hi, All-
I have a Canon PIXMA iP1600 printer and when I follow Ubuntu's installation instructions it automatically selects the i560 driver (with no mention of PIXMA) for me to use. When I go through the rest of the driver list there is no mention of either iP 1600 or PIXMA iP 1600, so I continue on following the instructions using the i560. When it finishes, a printer icon appears in the printers window bearing the label "i560 ready", but when I try to use the printer absolutely nothing happens. What am I supposed to do?
Regards to all, Georgeiger

---

### Post by w4ett on 2007-07-24
According to Openprinting.org, your printer should work:

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP1600)

Recommended driver: cnijfilter-ip2200 from the Mfg website:

[http://software.canon-europe.com/](http://software.canon-europe.com/)

---

### Post by bradmayne on 2007-07-24
i need a purple pony with wings to take me away from the mess that is winblows.  I had problems with my printer too thought when i upgraded to feisty fawn my printer was on the list of supported printers (i am on a wireless smb network).  It took a lot of messing around and patience and i can only use certain fonts!  Otherwise my printer will not print the document.  Printer is a brother dcp 8040.

---

### Post by bigboy_pdb on 2007-07-24
I did a search on google using "linux pixma ip1600" and found that the following site has drivers for your printer:
[http://turboprint.info/](http://turboprint.info/)

Go to download and specify your printer "canon pixma ip1600" and fill in whatever else is required (none of it is personal information). Then you should be able to download a deb package. Open a terminal (Applications -> Accessories -> Terminal) and move to the directory that the package was saved in (using 'cd directory') and then type 'dpkg -i package_name'. It says on the site that you'll need to have 'libgtk1.2' installed. I checked 'Synaptic Package Manager' (System -> Administration -> Synaptic Package Manager) and that library is installed, but in the future if the library is changed and the drivers aren't updated you might need to reinstall the library using 'Synaptic Package Manager'.

**EDIT:** Since I don't have the same printer, there's no way for me to tell if this will work. You'll just have to try it and see. If you have any problems though, you can always post them and we'll do our best to help.

---

### Post by Georgeiger on 2007-07-25
Hi,-
Well, what I now have is an icon on my desktop, downloaded from Canon itself, titled "iP2200_Linux_260.tar.gz" which Properties tells me is a compressed application. What di I do with it? Do I open it and if so what with? Or do I extract it directly on the desktop? And then what? Best regards, Georg
This was in reply to w4ett, message #2, above.

---

### Post by Georgeiger on 2007-07-25
This is in reply to message #4, above. I'll give this a try if what I hear from the guy who wrote message #2 doesn't work. Thank you, Georg
P.S. do others also get the feeling at the end of week 2 that their entire lives are slipping down a black hole labeled "Ubuntu" like we used to about the black hole labeled "Microsoft" in 1995?

---

### Post by bigboy_pdb on 2007-07-25
To extract the application right click on the "tar.gz" file and click "Extract Here". A new folder will appear in the directory where you saved the "tar.gz" file. Go into the new folder. Then I'm guessing that you should follow any instructions that come with the application. The instructions should be in a readme file or something like that.

**EDIT:**
"tar.gz" is a compression file where the original files/folders were first combined into one file using tar and then compressed using a "gzip" compression algorithm. You can think of it as being somewhat similar to zip or rar files.

---

### Post by w4ett on 2007-07-25
To learn the how-to's and where for's of installing drivers and applications in Ubuntu..I highly recommend this WIKI:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

It explains the proceedures completely, and in far more detail than I ever could.

---

### Post by Benbow on 2007-07-25
I have a canon mp170 and after much bother I found that Turboprint was the only answer (apart from buying a HP).
It is fine for text and spot colours but when it comes to photographs it is not so good as the settings are not available to fine tune the printed picture (canon drivers only support windows - my next printer will definitely be a Hewlett Packard).
Another downside is that you have to pay for Turboprint when all it does is gives you a basic printing facility.

Bon chance.

---

### Post by Benbow on 2007-07-25
I have just noticed that drivers for the mp170 now appear in openprinting .org.
I am currently downloading it and will report back.

---

### Post by Mornedhel on 2007-07-25
> **Benbow said:**
> I have a canon mp170 and after much bother I found that Turboprint was the only answer (apart from buying a HP).
It is fine for text and spot colours but when it comes to photographs it is not so good as the settings are not available to fine tune the printed picture (canon drivers only support windows - my next printer will definitely be a Hewlett Packard).
Another downside is that you have to pay for Turboprint when all it does is gives you a basic printing facility.

Bon chance.

HP printers for the win (except for the ink cartridges...) The first printer I installed under Ubuntu was an HP, went through the installation steps, turned around to grab the CD that claimed to have drivers for every conceivable OS, and turned back to find myself standing in front of my now working printer, holding a completely useless CD.

By the way, chance est un mot féminin, donc on dit "bonne chance".

---

### Post by bigboy_pdb on 2007-07-25
Benbow, are you sure that people have to pay for turboprint for private use? It says on their site that "The Free Edition is for test or private use only - for business, governmental or educational use you need to purchase a professional license".

---

