---
title: "Brother DCP-7055 on Linuxmint 17 not working"
date: 2014-06-26
forum: Any Other OS
---

### Post by ckrles on 2014-06-26
Hi, I've installed Linuxmint 17 Qiana (Ubuntu 14.04 LTS) 64 bits version. I'm using KDE. I have a poroblem with my printer Brother DCP-7055 (printer and scanner). I've downloaded the drivers from Brother's site and I installed it with the terminal, but I can't make it work. The printer model is correctly detected but when I try to print it is inactive and doesn't print. This is the ouptput I get when I installed the drivers:

maria@maria-desktop:~ > sudo dpkg -i --force-all /home/maria/Descargas/brgenml1lpr-3.1.0-1.i386.deb
[sudo] password for maria: 
(Leyendo la base de datos ... 157120 ficheros o directorios instalados actualmente.)
Preparing to unpack .../brgenml1lpr-3.1.0-1.i386.deb ...
/var/lib/dpkg/info/brgenml1lpr.prerm: 3: /var/lib/dpkg/info/brgenml1lpr.prerm: /opt/brother/Printers/BrGenML1/inf/braddprinter: not found
Unpacking brgenml1lpr (3.1.0-1) over (3.1.0-1) ...
Configurando brgenml1lpr (3.1.0-1) ...
***/var/lib/dpkg/info/brgenml1lpr.postinst: 3: /var/lib/dpkg/info/brgenml1lpr.postinst: /opt/brother/Printers/BrGenML1/inf/braddprinter: not found***
maria@maria-desktop:~ > sudo dpkg -i --force-all /home/maria/Descargas/brgenml1cupswrapper-3.1.0-1.i386.deb
(Leyendo la base de datos ... 157120 ficheros o directorios instalados actualmente.)
Preparing to unpack .../brgenml1cupswrapper-3.1.0-1.i386.deb ...
Unpacking brgenml1cupswrapper (3.1.0-1) over (3.1.0-1) ...
Configurando brgenml1cupswrapper (3.1.0-1) ...
lpadmin -p BrGenML1 -E -v dnssd://BrGenML1%20%40%20maria-desktop._printer._tcp.local/ -P /usr/share/ppd/brother/brother-BrGenML1-cups-en.ppd
maria@maria-desktop:~ > sudo dpkg -i --force-all /home/maria/Descargas/brscan4-0.4.2-2.amd64.deb
(Leyendo la base de datos ... 157120 ficheros o directorios instalados actualmente.)
Preparing to unpack .../brscan4-0.4.2-2.amd64.deb ...
Unpacking brscan4 (0.4.2-2) over (0.4.2-2) ...
Configurando brscan4 (0.4.2-2) ...
This software is based in part on the work of the Independent JPEG Group.
maria@maria-desktop:~ > 



I wonder if it has something to do with the line in bold type.

My system is 64 bits. Maybe it could also be the fact that first I installed a 32 bit version of the printer's driver meant for ubuntu 12.04 Lts (I thought it would work). If thi the cause of the problem, how could I identify these packets and uninstall them?

I was also concerned when I dowloaded the 64 bit driver because firefox warned me that the deb packages were broken and wouldn't let me donwload them. So, I used Chromium to download them and install them. Could it be the cause? Brother's website also allowed for rpm packages download. I'm gonna try to convert rpm into deb and install them.

I'd appreciate your help.

Thank you.

---

### Post by ckrles on 2014-06-26
PARTIAL SOOLUTION:

I realised I needed:    	 	 	 	    
ia32-libs (reports error)

  

  or lib32stdc++ (installed correctly)

After installing 6 or 7 files I got 2 printers detected. 

1. BrGenML1 (it prints out although it says inactive)
2. DCP-7055 (the name is correct but it doesn't print and it appears as inactive)

So, now I can print, BUT I can't scan.

The  app Simple Scan detects DCP-7055 as scanner but it doesn't scan and  reports error. Then it suggests me to change scan, but DCP-7055 is the  only scanner available and I don't know how to fix it.

Any ideas?

---

### Post by pdc on 2014-06-26
Hi there ckrles; you have certainly been busy;

Brother now offer an install tool; at the top of the list for the software options for each printer; folks seem to find it works well; 

________________

for the scanner you most probably need a small file [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

you get it from here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and there is a click option to help you download the file

I think the file does for you ..............what Brother previously recommended as an instruction >     1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2. Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".

    The lines to be added--------------------------- 


    # Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"
     

    3. Restart the OS.



________________________________________

I think now that running the install script does all that automatically .............for those that start from that point .........................

---

### Post by Bucky Ball on 2014-06-27
*Thread moved to **Other OS/Distro Support**.*

Linux Mint is not supported in the main support forums here. You might have better luck on their forum. They have an active community. Good luck.

---

### Post by ckrles on 2014-06-27
Yes, I was busy for a while. First I installed the drivers one at a time (6 or 7 files which got me confused in the end). Then I realized and understood how to use the install tool. I used it with no result. I couldn't scan, though I could print.

I'll try your recommendation and let you know.

---

### Post by ckrles on 2014-06-27
> **Bucky Ball said:**
> *Thread moved to **Other OS/Distro Support**.*

Linux Mint is not supported in the main support forums here. You might have better luck on their forum. They have an active community. Good luck.



Yeah, I know ;), but because of spam you need to get a ticket to be able to register... Linux Mint 17 is based on Ubuntu 14, so I thought the problem and its solution could be common. I need the scanner up and running asap.

---

### Post by ckrles on 2014-06-27
> **pdc said:**
> Hi there ckrles; you have certainly been busy;

Brother now offer an install tool; at the top of the list for the software options for each printer; folks seem to find it works well; 

________________

for the scanner you most probably need a small file [COLOR=#008000]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

you get it from here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and there is a click option to help you download the file

I think the file does for you ..............what Brother previously recommended as an instruction 

________________________________________

I think now that running the install script does all that automatically .............for those that start from that point .........................



I've just noticed that I had already installed that file from the beginning. I installed it again though.No result.

Is there a way I can remove all the drivers I installed and start again using the install tool. Yesterday I installed all the files via terminal. Maybe If there was a simple way to undo everything and then run a fresh install using the install tool.

Thank you.

---

### Post by coffeecat on 2014-06-27
> **ckrles said:**
> you need to get a ticket to be able to register

No, you don't. All you have to do is to solve the very simple anti-spam human verification puzzle, and then activate your account from the verification email sent to your registered email. This is the same procedure as used for virtually every forum, and the same as for here, except that with ubuntuforums you email verify your Ubuntu One SSO account. 

You are very welcome to seek a solution to your problem here, but Mint != Ubuntu. The problem and solution in your case may be the same, but the first two sections in this forum are for Ubuntu supported flavours only. 

Good luck!

---

### Post by ckrles on 2014-06-27
> **coffeecat said:**
> No, you don't. All you have to do is to solve the very simple anti-spam human verification puzzle, and then activate your account from the verification email sent to your registered email. This is the same procedure as used for virtually every forum, and the same as for here, except that with ubuntuforums you email verify your Ubuntu One SSO account. 

You are very welcome to seek a solution to your problem here, but Mint != Ubuntu. The problem and solution in your case may be the same, but the first two sections in this forum are for Ubuntu supported flavours only. 

Good luck!


Sorry it seems like I ended up in the wrong mint forum. this is where it asks for a ticket [http://community.linuxmint.com/auth/register](http://community.linuxmint.com/auth/register)

I've just noticed that in linux forum I don't need a ticket.

Thanks.

---

### Post by ckrles on 2014-06-27
> **pdc said:**
> Hi there ckrles; you have certainly been busy;

Brother now offer an install tool; at the top of the list for the software options for each printer; folks seem to find it works well; 

________________

for the scanner you most probably need a small file [COLOR=#008000]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

you get it from here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) and there is a click option to help you download the file

I think the file does for you ..............what Brother previously recommended as an instruction 

________________________________________

I think now that running the install script does all that automatically .............for those that start from that point .........................


I edit a files and added those two lines, but still no luck.

Anymore ideas?

---

### Post by Bucky Ball on 2014-06-27
> **coffeecat said:**
> 

You are very welcome to seek a solution to your problem here ...

+1.

---

### Post by kurt18947 on 2014-06-27
> **ckrles said:**
> I edit a files and added those two lines, but still no luck.

Anymore ideas?

I have a suspicion:).  The installer script installs the scanner driver, there are two other issues that need to be resolved.  One is the scanner only working with SUDO privileges which I believe the .deb file should fix.  The second is a Brother installer problem.  It's documented here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

In essence the installer copies some files to the wrong location.  They're copied to /user/lib64 when they should be copied to /user/lib I believe.  I don't know what connection you're using but if you're configuring to scan over a network, you need to enter one line in a terminal to tell the brother device which I.P address to use.

If you want to check that the normal user entry is correct, here's the fix using a terminal.

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

You also need to do a restart after adding the lines to fix the USB problem.  I'd probably restart after copying the files from /usr/lib/64 to /usr/lib as well just to be sure.

---

### Post by rewyllys on 2014-06-28
> **ckrles said:**
> Sorry it seems like I ended up in the wrong mint forum. this is where it asks for a ticket [http://community.linuxmint.com/auth/register](http://community.linuxmint.com/auth/register)

I've just noticed that in linux forum I don't need a ticket.

Thanks.
The main forums for LinuxMint are at [http://forums.linuxmint.com/](http://forums.linuxmint.com/).  No ticket is required to participate there.

---

### Post by ckrles on 2014-06-30
> **kurt18947 said:**
> I have a suspicion:).  The installer script installs the scanner driver, there are two other issues that need to be resolved.  One is the scanner only working with SUDO privileges which I believe the .deb file should fix.  The second is a Brother installer problem.  It's documented here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

In essence the installer copies some files to the wrong location.  They're copied to /user/lib64 when they should be copied to /user/lib I believe.  I don't know what connection you're using but if you're configuring to scan over a network, you need to enter one line in a terminal to tell the brother device which I.P address to use.

If you want to check that the normal user entry is correct, here's the fix using a terminal.

[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on)

You also need to do a restart after adding the lines to fix the USB problem.  I'd probably restart after copying the files from /usr/lib/64 to /usr/lib as well just to be sure.



Still no luck. I tried everythinkg you guys suggested, but still not working.

I've got a small doubt.

One of the suggested solutions solutions was this:

[I]Install the scan driver.

Copy the following files under /usr/lib64/ to /usr/lib/.

For brscan4 Users:
/usr/lib64/sane/libsane-brother4.so.1.0.7
/usr/lib64/sane/libsane-brother4.so
/usr/lib64/sane/libsane-brother4.so.1[/I]

I  find a problem with the second and thrid files. In my system they  appear as direct acceses leading to ..... themselves?????? They are  156kb.

Maybe that's the reason why these solution doesn't work (at least for me)

Any other ideas?

Anyone who made Brother DCP-7055 scanner work on Ubuntu 14.04 64 bits? I'd like to make sure if it does work under Ubuntu 14.04 or if the problem if with Linux Mint 17 Qiana 64 bits. 

Thank you guys.

---

### Post by kurt18947 on 2014-06-30
I'm no expert in this stuff.  The only thought I've had is - I wonder if there's an error in Brother's instructions.  The instructions seem to say copy those 3 files from /usr/lib64/sane to /usr/lib.  I wonder if they should be copied to /usr/lib/sane?  My device is a brscan3.  I had to copy files from /usr/lib64 -> /usr/lib and also from /usr/lib64/sane ->/usr/lib/sane.   Beyond that I don't have a good suggestion.  I've emailed Brother linux support in the past and have gotten a reply in a few days.  In the U.S. at least Brother does not offer phone support for linux, phone support is Windows and Mac only.

---

### Post by ckrles on 2014-06-30
> **kurt18947 said:**
> I'm no expert in this stuff.  The only thought I've had is - I wonder if there's an error in Brother's instructions.  The instructions seem to say copy those 3 files from /usr/lib64/sane to /usr/lib.  I wonder if they should be copied to /usr/lib/sane?  My device is a brscan3.  I had to copy files from /usr/lib64 -> /usr/lib and also from /usr/lib64/sane ->/usr/lib/sane.   Beyond that I don't have a good suggestion.  I've emailed Brother linux support in the past and have gotten a reply in a few days.  In the U.S. at least Brother does not offer phone support for linux, phone support is Windows and Mac only.







What gets me confused is the fact that 2 of those 3 files are not files themselves, but direct accesses to ...... themselves. They are 154kb and hey have that little arrow indicating direct access. I also emailed Brother asking for help, but they simplied replied telling me that they don't support Ubuntu and suggested me reporting to the software manufacturer (I guess they meant Ubuntu). It's rellay strange to have such an answer since they have drivers for Ubuntu. I'm confused.

I'm still hoping someone can tell me how to make it work.

---

### Post by kurt18947 on 2014-07-01
> **ckrles said:**
> What gets me confused is the fact that 2 of those 3 files are not files themselves, but direct accesses to ...... themselves. They are 154kb and hey have that little arrow indicating direct access. I also emailed Brother asking for help, but they simplied replied telling me that they don't support Ubuntu and suggested me reporting to the software manufacturer (I guess they meant Ubuntu). It's rellay strange to have such an answer since they have drivers for Ubuntu. I'm confused.

I'm still hoping someone can tell me how to make it work.

I'm confused by " What gets me confused is the fact that 2 of those 3 files are not files  themselves, but direct accesses to ...... themselves. They are 154kb and  hey have that little arrow indicating direct access." but as I said, I'm no expert.  I suspect you emailed the main Brother help email address.  Brother's linux support group seems to be separate from the Windows & Mac support.  Perhaps this will be of some use:

[INDENT]Due to the diversity of the Linux operating systems, Brother currently does not have phone support for the operating system.
Please click on the following link to email our Linux support team: 
[https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html](https://secure6.brother.co.jp/LinuxContactUs/contact/Linuxform.html) 
 
You may also visit the Brother Linux support page by clicking on the following link: 
[http://support.brother.com/g/s/id/linux/en/index.html](http://support.brother.com/g/s/id/linux/en/index.html) 
[/INDENT]
 
The** secure6.brother.jp/**.....  link is what I used and did get a response.  Sorry I can't be of more help.

---

### Post by ckrles on 2014-07-03
Thank you very much Kurt18947. I emailed secure6brother.jp. I hope they can help. 

I was also suprised to have 154 kb direct accesses pointing to themselves. Strange file size and strange leading.

I let you know how the brother response turns out.

---

### Post by rewyllys on 2014-07-04
FWIW, Linux Mint releaed a substantial set of updates to LM17 last Sunday.  After I had installed them, my Brother MFC-8820D, which had previously refused to print in duplex mode (viz., on both sides of a sheet of paper), became capable of duplex printing.

This step forward removed my last reason for not updating from LM13 as my primary desktop OS to LM17.  

The OP might try the latest updated version of LM17 to see whether his Brother machine now works better.  Good luck.

---

### Post by ckrles on 2014-07-07
> **rewyllys said:**
> FWIW, Linux Mint releaed a substantial set of updates to LM17 last Sunday.  After I had installed them, my Brother MFC-8820D, which had previously refused to print in duplex mode (viz., on both sides of a sheet of paper), became capable of duplex printing.

This step forward removed my last reason for not updating from LM13 as my primary desktop OS to LM17.  

The OP might try the latest updated version of LM17 to see whether his Brother machine now works better.  Good luck.



I'll check it out and let you know. Thank you very much.

---

### Post by ckrles on 2015-01-28
I can't make it work in Mint 17. I moved to Xubuntu 14.04 and still no luck.

It's very frustating, since it did work in ubuntyu 12.04. And it was easy to install.

---

