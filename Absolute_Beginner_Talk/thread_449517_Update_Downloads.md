---
title: "Update Downloads"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by BAS54 on 2007-05-20
Hi,I've had Ubuntu 6.06 up and running for week. Dual boot,printer and modem all fine. Not going any further at present. It was obvious that I was not going anywhere fast without the terminal command line experience. So now I'm doing a tutorial on learning commands. Enjoying it and the fog is starting to clear.



        In the meantime I did a Ubuntu Update via Aptitude apt-get, and being the first after the install it was of course fairly large.. I didn't install, being on dial-up, I wanted to find out a few things.

So the questions.  

       Am I right in thinking that Ubuntu updates are different from other packages downloads, in that they download and install themselves?
       
       Do I need to get all files going back to the Dapper Drake release date, to allow the following updates to work?  Or can I just nominate the latest ones?

       I have access to broardband at the local library which I have used for large downloards and burnt to disk.  Is this option available when you click to install Ubuntu updates? I ask because my reasoning goes around in circles; all to do with security. If not, can I nominate files and spread the number over several session on line?  3 to 5 kb/sec is no joke, and ISP dropouts are not uncommon here.   




       Later, an update notification arrived with 243 packages (247 mb) that could be downloaded.   At first glance I don't need half of them but need time to know what is what. In other words, I should/could install those apt-get files to get Ubuntu system and security etc., up to speed, and sort through the other updates at my leisure? These files I could transfer from broardband via CD? Assuming I get to lesson 6 on file types.

  
  Any advise appreciated. 
      




For any other newbie in the first days, if it helps;

   My Ubuntu 6.06 version has hundreds of drivers for Epson Printers. Doubt you will have trouble.
    Liteon DVD RRW  LH-18A1P   No problems.
    No name exterior serial modem called 'Standard V90 56KFlex' in Windows, no problem.
       ( If during install, Auto Find Modem, comes up with something like DEV/tty0, go with it. 
         It won't name or model it. It's saying it has you modem on the port.)
   Lexar Jumpdrive and Verbatim Thumb both work fine without install.
  



BAS54

---

### Post by Happy_Man on 2007-05-20
Every day or so, Ubuntu automagically runs an update, and then puts a little reminder up in the tray: you have ____ updates available. Click on that, and it opens the update manager. That's how the updates work... and yes, you need most of those updates, even if you will never use them. And even so, you can run ```
sudo apt-get update && sudo apt-get upgrade
``` every day before going to sleep... when you wake up, your system is perfectly updated.

---

### Post by BAS54 on 2007-05-20
Thanks a lot for that happy_Man.
Will do.

BAS54

---

