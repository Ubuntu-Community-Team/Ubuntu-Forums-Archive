---
title: "SANE Epson backend download for Perfection 1650"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Ajarn Jack on 2008-04-18
I have recently replaced my scanner and I chose one that was supposedly supported by Linux, but my XSane Image software doesn't see my Epson Perfection 1650 scanner.  I'm using the latest stable version of Ubuntu/Gutsy Gibbon (7.0) which my computer tech installed two months ago.

I emailed Epson and they referred me to a third party website for support -** khk.net** which indeed had a backend download available.  However it warned that you must "know what you're doing" in order to use this download properly.  That's my problem, I'm not sure about the following and need the forum member's help with the following:
1) Which download version works with my computer?
2) Where do I locate and open the standard SANE backend package in my computer?
3) What's the exact procedure for replacing the respective files with the new files in the tar.gz file?
4) Where can I find the date the patch was released so that I can select the backend version that was current then?

I would appreciate any assistance this forum can give me so that I can start using my new scanner properly.

Many thanks.

---

### Post by LeoSolaris on 2008-04-18
Well the easiest way would be to add it to Ubuntu with Synaptic (System->Admin->Synaptic) Just do a search for sane, and it should be on the list in the S's. Make sure to include the sane-utils right under it.

Leo

---

### Post by Ajarn Jack on 2008-04-19
Thank you very much for taking the time to give me some advice about this problem, but I'm still confused about how to open the SANE package already installed on my computer.  The synaptic package manager only explains what the package is used for, but I need to open that package and replace some files in the backend directory with the new files from the tar.gz file that are offered from khk.net so that my scanner will be recognized.

If anyone could help me accomplish this task it would would be much appreciated.  The directions for doing this sound simple, but only if you know exactly where to look for that package and can get to the files already installed.

---

### Post by Rhubarb on 2008-04-19
The guide here:
[http://ubuntuforums.org/showthread.php?t=627650](http://ubuntuforums.org/showthread.php?t=627650)
Should help you along, just bear in mind your scanner is Perfection 1650, not V200.
Josko's posts are very helpful there, and you should be able to look through there to see what applies to you and your scanner.   - So don't follow it all exactly, just use it as a good guide (as your scanner is different).

If you're not feeling confident, then you should perhaps get the person who installed ubuntu on your PC to help you out - let them know that your scanner should work with ubuntu as there are drivers for it.

---

### Post by prshah on 2008-04-19
> **Ajarn Jack said:**
> If anyone could help me accomplish this task it would would be much appreciated.  

I have an Epson CX2800 scanner/printer. It was not recognized by the default sane package.

While hunting around, I came to know about iscan. I downloaded the RPM (Which is an installation format for other linuxes), then used a program called alien to convert it to deb (which can be installed  easily in ubuntu). Once that was installed, everything worked smoothly for me. 

You can pick up the RPM from here: 
[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do#match](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do#match) -or-
[http://rpm.pbone.net/index.php3?stat=3&search=iscan&srodzaj=3](http://rpm.pbone.net/index.php3?stat=3&search=iscan&srodzaj=3)

I recommend the first site.

--As for converting with alien, will shortly post the instructions here.-- Now not needed.

[UPDATE] There is now no need for the conversion. You can directly download a DEB for the Perfection 1650 from the first link. In the OS selection box on that page, choose "Distribution" as "Debian" and "Distribution Version" as "Others".[UPDATE]

Installing the DEB is easy; point and click and save the download; then double click the saved file when the download is complete.. it will ask for your confirmation and install the drivers/scanning program.

---

### Post by Rhubarb on 2008-04-19
> **prshah said:**
> --As for converting with alien, will shortly post the instructions here.-- Now not needed.

[UPDATE] There is now no need for the conversion. You can directly download a DEB for the Perfection 1650 from the first link. In the OS selection box on that page, choose "Distribution" as "Debian" and "Distribution Version" as "Others".[UPDATE]
Even though it lets you specify Debian, it only gives you rpms to download.
Hence you still need to use alien to convert from rpm to deb.

---

### Post by BandD on 2008-04-20
What happens when you open the version of Sane you already have installed with the scanner plugged in?

I sometimes use the Japanese equivalent to the Perfection 1650 and thought I had some issues.  Sane would open and everything would look ok, I'd click scan, but then nothing would happen.  But one time I thought I'd just let it go for a while after clicking scan, and sure enough, there just seemed to be about a 2 minute lag while Sane initialized the scanner.  After the that initialization, there was virtually no delay after clicking scan, until I closed Sane and unplugged the scanner.  So if Sane opens up and it just seems to freeze or something, try letting it go for several minutes and see if you have a similar issue.

---

### Post by Ajarn Jack on 2008-04-21
Where do I find this "Alien" program so that I can convert the rpm to deb?

---

### Post by prshah on 2008-04-21
> **Ajarn Jack said:**
> Where do I find this "Alien" program so that I can convert the rpm to deb?

```
sudo apt-get install alien
``` will install a bunch of stuff including support for the rpm format. 
Then 
```
sudo alien -k i2cscan-or-whatever.rpm
sudo dpkg -i i2cscan-or-whatever.deb

```

Will convert it to a DEB and the second command will install it.

---

### Post by Ajarn Jack on 2008-04-22
Thanks so much, Prshah, for taking the time to enlighten me about this process.  Unfortunately I'm so new to this operating system that I don't even know where to go to type these commands. Do I go to the 'system - administration' tab and if so, which item in the drop down menu do I open?  Is "Alien" already somewhere in my operating system and just needs to be 'awakened' by these command prompts. 

The computer tech who installed Ubuntu has told me that he wouldn't recommend changing anything in my computer because he can't help me with this problem.  His recommendation was to simply sell this Epson scanner on Ebay and buy one that the manufacturer ensures will work with Ubuntu.  So that is the end of my support at this end.  By your comments it sounds like a simple task to have my XSane Image software recognize this Epson scanner once I convert the software I downloaded from the site you recommended. That would make more sense (if I can do this myself) than just simply getting rid of this scanner.

If it wouldn't be too much of problem for you or anyone, would you please 'walk me through' the procedure step by step, such as: 
1. Go to System and select Administration. Open the (  ) tab and enter the command prompt.
2. Next select -------------- etc.etc...

Most people I've talked with have told me that I should just go back to using Microsoft XP, but I hate to give up so quickly after only trying this operating system for two months. I've never had any formal computer training, but I'm not stupid and can follow step by step directions.

Thanks to everyone for having a forum for people like me. I truly see the benefits of this open-source operating system and would like to stick with it.  Once I get this scanner situation worked out I don't plan on adding any further hardware and will just start enjoying using my computer once again.

---

### Post by prshah on 2008-04-22
> **Ajarn Jack said:**
> Thanks so much, Prshah, for taking the time to enlighten me about this process.  Unfortunately I'm so new to this operating system that I don't even know where to go to type these commands. Do I go to the 'system - administration' tab

OK I feel your pain. Applications-Accessories-Terminal. Then the commands I have given. Any problems, feel free to post back.

> 
The computer tech who installed Ubuntu has told me that he wouldn't recommend changing anything in my computer because he can't help me with this problem.  His recommendation was to simply sell this Epson scanner on Ebay and buy one that the manufacturer ensures will work with Ubuntu.  So that is the end of my support at this end.  

You can make this change absolutely safely without screwing up anything at all. Either your scanner will immediately start working (99% chance) or it will not work (1% chance). It will not do anything to screw up your system. Go at it with confidence.

> By your comments it sounds like a simple task to have my XSane Image software recognize this Epson scanner once I convert the software I downloaded from the site you recommended. That would make more sense (if I can do this myself) than just simply getting rid of this scanner.


I agree with you wholeheartedly and heap scorn on your "tech" support.

> If it wouldn't be too much of problem for you or anyone, would you please 'walk me through' the procedure step by step, such as: 


Walking you through the whole procedure step-by-step is a matter of minutes. I will give you a step by step procedure, but rather than blindly follow the steps, please try to understand what is being done. 

1) Download your file from the before-mentioned website. I wont go into details since you are obviously comfortable with browsing experiences. Remember where you save the downloaded file. (Usually saves on desktop).

2) Open Applications-Accessories-Terminal. Give the "sudo apt-get..." command mentioned earlier.

3) Now go to the location where you have saved the downloaded file. (Eg if it is desktop, give the command "cd ~/Desktop" (for future reference, a "~" in any path refers to your home directory, usually "/home/username").

4) Then give the alien and dpkg commands as mentioned before.

Post back here if you have difficulties with any particular step. Many people will help out.


> 
Most people I've talked with have told me that I should just go back to using Microsoft XP, but I hate to give up so quickly after only trying this operating system for two months. I've never had any formal computer training, but I'm not stupid and can follow step by step directions.

Thanks to everyone for having a forum for people like me. I truly see the benefits of this open-source operating system and would like to stick with it.  Once I get this scanner situation worked out I don't plan on adding any further hardware and will just start enjoying using my computer once again.

I'm glad you have decided to stick the course and not post one of those meaningless rants "Windows is best, linux suxxx" blah blah.

---

### Post by Ajarn Jack on 2008-04-23
Well, I'm learning lots about this, but I'm still not there.  I've downloaded the packages from that site onto my desktop and extracted the folders to the desktop.  I've gotten the alien files loaded, but when I type in the commands  for the i2cscan a message returns saying that the particular file can't be found on the desktop????  What am I doing wrong?  

I'm very close to finishing this and need more help, so please don't give up on me.  Any assistance would greatly be appreciated.

---

### Post by prshah on 2008-04-24
> **Ajarn Jack said:**
>  I've gotten the alien files loaded, but when I type in the commands  for the i2cscan a message returns saying that the particular file can't be found on the desktop????  What am I doing wrong?  


More specific message please? Also, an ```
ls -R | grep -i rpm
ls -R | grep -i deb
``` from the terminal of your home directory will be helpful. 

Note ls -R lists contents from all directories starting with your home directory. The above commands show all RPM and DEB files present in your home directory. You may want to edit out objectionable files, if any.

---

### Post by Ajarn Jack on 2008-04-24
Thanks for your help once again!  Okay, after I gave the first command:           ls -R | grep -i rpm
The file was located with this message: iscan-2.11.0-1.c2.1386.rpm (desktop)
After the second command: ls -R | grep -i deb
The file was also located with this message: debian ./Desktop/iscan-2.11.0/debian: sane_debug.h
                               sane_init_debug.c

So feeling better about having the downloaded files located I went back to your step-by-step instructions for installation.  Knowing that Alien is already in the system (that went smoothly) I just gave the first command to convert it to DEB -- sudo alien -k i2csan-or-whatever.rpm  and this is the message I got: "File "i2cscan-or-whatever.rpm" not found. I double checked to see where it had looked and sure enough it was: desktop:~$ 

After giving the second command to install it I got an error message saying: dpkg: error processing i2cscan-or-whatever.deb (--install) : cannot access archive: No such file or directory.  Errors were encountered while processing: i2cscan-or-whatever.deb

Knowing that the files are in my home directory I'm wondering if maybe I've  given an incorrect command that doesn't match the files exactly as it should. I've tried three times just in case I've entered something incorrectly, but I'm certain that I've entered the commands you have given me precisely. 

So close, yet so far away.  Please excuse my ineptness with this seemingly easy process.  Any help to complete this task is very much appreciated.

---

### Post by prshah on 2008-04-24
> **Ajarn Jack said:**
> Thanks for your help once again!  Okay, after I gave the first command:           ls -R | grep -i rpm
The file was located with this message: iscan-2.11.0-1.c2.1386.rpm 

convert it to DEB -- sudo alien -k i2csan-or-whatevsudo alien -k i2csan-or-whatever.rpmer.rpm  and this is the message I got: "File "i2cscan-or-whatever.rpm" not found. I double checked 


i2cscan-or-whatever.rpm was an example file name. The actual filename is iscan-2.11.0-1.c2.1386.rpm as located by the "ls -R..." command. So now, convert to deb with ```
sudo alien -k iscan-2.11.0-1.c2.1386.rpm
```

---

### Post by Ajarn Jack on 2008-04-26
Once again, thanks for your time in helping me execute this program.  And once again I've failed.  I understand how you look up that file which I've downloaded and unpacked to my desktop and identify that it's positively there. So I used the commands to tell me what the name of that rpm file is and then I used the sudo alien command to convert that exact file name to deb, but once again the message came back "File not found".  ??????

Any suggestions as to why it shows it in my directory on the desktop, but it can't find it with the sudo alien command to convert?

---

