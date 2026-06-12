---
title: "Grabit Irfanview etc etc"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by bobkny on 2008-01-29
I'm on a campaign to replace Windows. I'm running ubuntu on an old laptop and trying to replicate all my major Windows applications. Once I'm there, I'll install Ubuntu on my new laptop  and get rid of Windows forever. There are 2 Windows applications that I especially want to implement:
1. Grabit - Newsreader / manager. I use this to subscribe to and download articles from Internet NewsGroups. 
2. Irfanview - the worlds easiest to use image file processor.
As far as I know, neither of these programs has a Linux implementation. How can I implement these program? Several other blogs, suggested using Wine - a windows emulator. How do I install and use Wine; and then install Grabit and Irfanview. Or - even better - are there good native Linux applications to replace Grabit and Irfanview?

---

### Post by emarkd on 2008-01-29
1.  Try pan.  It's in the repositories and works quite as a gui for usenet.  If all you're doing is grabbing based on .nzb, I recommend hellanzb.  It's the best thing ever!

2.  Sorry, good idea here, but you can check out: [http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

---

### Post by iansane on 2008-01-29
Go here to add wine to the repositories. Then in terminal type "sudo apt-get update" and you should be able to use synaptic or type "sudo apt-get install wine" from terminal. 


[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Then you can get windows made apps in .exe form and open them with wine by right click the exe. and choose open with wine. Not all windows made apps will work though so it's trial and error to see if irfanview for windows will work. It's fun to see what will and won't work anyway.

---

### Post by Shazaam on 2008-01-29
Grabit and Irfanview work using wine just fine. But using a native linux app is better. :)

---

### Post by iansane on 2008-01-29
I must agree. Usin Wine feels like I'm cheeting on mu Ubuntu and that makes me feel bad. LOL

---

### Post by bobkny on 2008-01-30
Thanks for the advice. I tried to install wine following the instructions. Everything seemed to work OK; but when I right click on the Windows .exe and select open with other application, Wine  does not appear in the list. Obviously I missed something. If I click on add remove programs however, it appears with a check mark. What's missing, or what do I still have to do?

---

### Post by pndragon on 2008-01-30
Open a terminal, change directories to the directory where you downloaded iview410_setup.exe, then on the command line:
```
wine iview410_setup.exe
```
You will probably need to download [mfc40.dll]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc40.dll/4.1.001/download.html")  and [mfc42.dll]("http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html") and save them in your ~/.wine/drive_c/windows/system32/ folder

---

### Post by bobkny on 2008-01-30
OK. I tried messing about with Wine. So far, despite all the good advice, I can't quite get all the pieces together. The best result was to get Grabit to install and execute one time. After that, I couldn't find a way to execute it a second time. Wine - as suggested by several helpers, is not an ideal way to go - especially for a beginner. A more preferred route would be to find native Linux app's. which do more or less the same things. 
Pan has some promise; but does not appear to be as user friendly as Grabit. There are several image management app's in the Linux Applications menu that may be adequate replacements for Irfanview; but I'll have to play with them.
Any suggestions for a Linux alternative to Winamp??

---

### Post by emarkd on 2008-01-30
I've never used Grabit so I can't compare them, but I've used Pan extensively and I can say that it is very full-featured.  It's different, as any new software is, but if you just give it a try for a few hours or days, you'll get used to it and may find that it works better than your old software did.  I guess I'm what I'm trying to say is don't mistake different for worse.

I mentioned this earlier but I'll reiterate it:  If you download using .nzb's, definitely try hellanzb!

---

### Post by Christmas on 2008-01-31
You can try Gwenview as a replacement for IrfanView and Akregator as an RSS Feed reader.

---

### Post by Major_Kong on 2008-01-31
> Any suggestions for a Linux alternative to Winamp??

Audacious

---

