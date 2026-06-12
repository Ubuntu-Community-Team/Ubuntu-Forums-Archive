---
title: "Noob needs help, especially with printer"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by bethalicea on 2007-02-02
I've just started testing ubuntu - yesterday we were snowed in so I was glued to my computer for 10 hours!

I'm looking at getting off the Microsoft bandwagon, but this is a daunting task since I am the Tech/Internet manager at my church, also setting up a new personal business that will require at least 3 networked computers hopefully wireless, hopefully wireless print server, hopefully using VOIP for telephone.  

I must admit that printer drivers were not my first concern when I started looking at this!  Surely, someone out there can help!  I have 2 Lexmark printers, one is an X83, the other is at the office so I don't know what it is, also I have an Epson Stylus Photo R340 printer that I just purchased to InkJet print CDs and DVDs for my church - it works great and I don't want to give it up.  

I've been with Windows forever since everyone else was, but now I feel confident enough with my skills to branch out and stop forking over $$$ to Microsoft!    

Can anyone help with the printer driver issue?  I looked into Wine, but it says that it is for Windows apps, not drivers.  Wine directed me to ReactOS, but I don't see printer drivers listed there either.  I have read on these forums that it is impossible to use the Lexmark X83 with Linux; but, I think there just has to be a way!

I'm having a lot of fun and hope to get some good ideas and learn alot from everyone here!  I'm going to need some support especially if I force my people at church to do this!!!!

Thanks and blessings…
:guitar:

---

### Post by x64Jimbo on 2007-02-02
Most printers are supported out of the box with Ubuntu. Just try adding it the same way you would in Windows.

---

### Post by RHTopics on 2007-02-02
bethalicea, Welcome to Ubuntu Forums.

On your Lexmark X83 printer, I believe you are out of luck on that one working with Linux.

Here is a website to check out the Linux compatibility for your other Lexmark printer:

    [http://www.linuxprinting.org/printer_list.cgi?make=Lexmark](http://www.linuxprinting.org/printer_list.cgi?make=Lexmark)

One option to keep using the printer, is to attach it to an old Windows computer which can be used as a print server on your network.  

Here is a thread describing how to do that:

   [http://ubuntuforums.org/showthread.php?p=2072108](http://ubuntuforums.org/showthread.php?p=2072108)

---

### Post by steve.horsley on 2007-02-02
Epson Stylus Photo R340 is listed as an option when you go System->Administration->Printers and add a printer, so that should be OK. **Don't** click the Install Driver button with the CD icon (it's a trap). Just click Forward after selecting the printer type, and it will use the inbuilt driver.

As for the Lexmarks, do you have any doors that need propping open? Actually, some Lexmarks are listed in the Add Printers dialog.

---

### Post by all4linux on 2007-02-02
Neither of the two printers you mentioned are supported in Ubuntu V6.10, however, you can try installing them using drivers for other printers of the same manufacturer. For the Epson Stylus R340, you could try the driver for the Epson Stylus R300, which is listed on the install options. For your Lexmark printers, try installing the Lexmark drivers for the other Lexmark printers listed in the options. If you find one that works, use it.
I have an old Epson LQ570+ dot-matrix printer, which I originally installed with the recommended driver for that printer. Later, I found that I could get better quality prints using the driver for the LQ-850 printer.  A bit of experiminting may prove quite fruitful for you on the Lexmark printers as well.

Dickey_b

---

