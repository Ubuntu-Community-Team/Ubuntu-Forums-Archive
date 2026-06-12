---
title: "Best way to clean the virus from pc without affecting the system"
date: 2012-04-13
forum: Any Other OS
---

### Post by rpupa on 2012-04-13
I have two os in my laptop. i use windows for games only, however it frequently suffers from viruses. What is the best way to scan and fix the viruses in windows from ubuntu in the same pc without affecting the other programs or the system (windows) . I need an antivirus which is free and powerful enough to disinfect or delete all the viruses from my pc......

---

### Post by drpjkurian on 2012-04-13
Purchase an antivirus thats it

---

### Post by souravc83 on 2012-04-13
Thats hard.From Ubuntu, you might be able to get rid of virus exe files, with an antivirus installed in Ubuntu which scans windows partition (I think this works, never tried it myself).

But viruses also change windows registry, and that is something you cannot remedy from Ubuntu. So, you will probably have to login from Windows. AVG is a pretty good free antivirus, I have heard.

---

### Post by roelforg on 2012-04-13
DrWeb works great, only thing is that the webpage language keeps resetting to russia. 
Edit: It's free and it works on linux as well, and it's very thorough.

---

### Post by Paqman on 2012-04-13
There are bootable antivirus disks available from places like Kaspersky and Bitdefender. Boot up into one and scan your Windows system.

However, prevention is better than cure. If your Windows system is *frequently* getting viruses then something is seriously wrong. Make sure you're using a legitimate version of Windows that's patched up-to-date, install a good antivirus suite and keep that up to date as well. There are free antivirus suites that are good (eg: MSE, Avast), but if you can't afford a legit copy of Windows then you should reconsider whether you should be using Windows at all. Or else just don't connect to the net using Windows. Most games work fine without internet access, although some will require you to be connected when you first install.

---

### Post by daslinkard on 2012-04-13
The first thing that I would do would be to download Malwarebytes & CCleaner (for free) from cnet.  You can do this simply from opening up Google and typing in the following:

For Malwarebytes you would type this:

```
Malwarebytes & cnet
```

For CCleaner you would type this:

```
CCleaner & cnet
```

Once you have these downloaded I would recommend starting Malwarebytes.  You will want to make sure that you process the update for Malwarebytes so you have the latest definitions for the program.  At this point in time you will then run a scan on the machine choosing the quick scan option.  This can take between 5 minutes to 30 minutes to complete on the quick scan.  Once it is completed you will click on show results.

When looking at the show results you will then make sure that every infection is check marked.  Once you have ensured that everything is check marked you will then select remove all.  At this point in time you may be prompted to restart your machine.  Do it.  Once the machine comes back up you will then click on the 'quarantine' section of malwarebytes.  You will select 'Delete all'.  This will remove the infections.

Next you will want to start CCleaner.  Click the first button on the bottom left....going from memory here....I think it may be scan....once it is finished you will then select run scan.  This should clean out your temporary Internet files.  From there you can select registry and fix any registry issues that you may be having.

If you want to do a detailed scan with Malwarebytes you can run a full scan.  However, consider that you have been warned as it can take from 1 hour to 3 hours to run this scan.  Once the scan is completed, repeat the steps above from removing and deleting the infections.

If any questions, write back.

---

### Post by lolpenguin on 2012-04-14
> **daslinkard said:**
> The first thing that I would do would be to download Malwarebytes & CCleaner (for free) from cnet.  You can do this simply from opening up Google and typing in the following:

For Malwarebytes you would type this:

```
Malwarebytes & cnet
```

For CCleaner you would type this:

```
CCleaner & cnet
```

Once you have these downloaded I would recommend starting Malwarebytes.  You will want to make sure that you process the update for Malwarebytes so you have the latest definitions for the program.  At this point in time you will then run a scan on the machine choosing the quick scan option.  This can take between 5 minutes to 30 minutes to complete on the quick scan.  Once it is completed you will click on show results.

When looking at the show results you will then make sure that every infection is check marked.  Once you have ensured that everything is check marked you will then select remove all.  At this point in time you may be prompted to restart your machine.  Do it.  Once the machine comes back up you will then click on the 'quarantine' section of malwarebytes.  You will select 'Delete all'.  This will remove the infections.

Next you will want to start CCleaner.  Click the first button on the bottom left....going from memory here....I think it may be scan....once it is finished you will then select run scan.  This should clean out your temporary Internet files.  From there you can select registry and fix any registry issues that you may be having.

If you want to do a detailed scan with Malwarebytes you can run a full scan.  However, consider that you have been warned as it can take from 1 hour to 3 hours to run this scan.  Once the scan is completed, repeat the steps above from removing and deleting the infections.

If any questions, write back.

Don't forget to boot into **_safe mode_**

---

### Post by rpupa on 2012-04-14
Well , i tried avg-free . downloaded the 96 MB and then scan the media
sudo avgscan -e .exe --heal /media/
and i think the virus is gone. However i dont understand how the virus affect the other programs and what is the meaning of disinfecting those programs mean. Does it inject it's executable machine code inside other programs editing them or what , please telll me if anybody knows.

---

### Post by haqking on 2012-04-14
[http://support.kaspersky.com/viruses/rescuedisk](http://support.kaspersky.com/viruses/rescuedisk)

---

