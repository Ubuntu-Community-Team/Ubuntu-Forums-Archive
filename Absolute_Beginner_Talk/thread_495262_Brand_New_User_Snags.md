---
title: "Brand New User Snags"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by brucewagner on 2007-07-07
I am a brand new user...  

I just bought a new HP a1744x AMD Athlon 64 X2 Dual Core procesor 4600+ 1.40GHz

I just downloaded ubuntu.... and installed it...

Installing it was easy --- except for the fact that the BACK and CONTINUE buttons were not visible...  and the window was not re-sizable...  so I had to Auto-Hide the top bar and the bottom bar...  and then I could BARELY see the top edge of the CONTINUE button... I had to GUESS that it said CONTINUE...   

But I was very lucky.... the top edge of the buttons became visible, and the right-most button seemed to have been CONTINUE or NEXT or something...

Now, it's installed.

It works well.  I am impressed.  OpenOffice is very slick too.  So far, plenty as good as my old MS Office 2000, if not better.

I was amazed that the printer drivers installed perfectly.   And even more amazed that I was able to immediately connect to my shared drive on my other Windows XP machine, and other Windows Vista machine.

Now, the four stumbling blocks I've encountered, and am stuck on, are:

(1)   Adobe Flash Player --- This is really mission critical.   Many web sites, and nearly ALL internet video depends on it.  It's not available for Linux on an AMD64 platform????  Tell this is not so.  Adobe COULD NOT be so negligent.  There is no way.

(2)   Java --- I understand it's available.  I've seen the download page (here [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80) ), but I'm given FOUR choices:  

      Linux RPM (self-extracting file)
      Linux (self-extracting file)
      Linux x64
      Linux x64 RPM

 I don't know what an RPM file is...  and I don't know how to install these.... 

(3)   I think I installed Wine....  (the program that is supposed to allow me to run Windows programs)...  But I don't think it works.  And I don't even know how to know if it is working or not.  I don't know how to install, or open, a Windows program.... and run it under Wine.

(4)   Skype --- What's the deal with running Skype on ubuntu on AMD64...?   Skype's own FAQ just sends you to a forum thread....   Please tell me the bottom line about this....

I know that this type of information changes monthly... if not daily....  So could someone please give me TODAY's bottom line answer about each of these issues...?

---

### Post by atria on 2007-07-07
1) Flash works on AMD64, you'll have to do a search on the forums.

2) Install java through apt-get/aptitude/synaptic instead of doing a manual installation. It'll be far cleaner this way.
```
sudo aptitude install sun-java6-jre sun-java6-plugin
```

3) To open a windows program with wine, execute it with wine in the terminal (or setup links to the windows program in the menus). For example in your terminal, execute:
```
wine /path/to/windowsprogram.exe
```

If it complains that wine is not configured, configure it with 
```
winecfg
```

4) Not sure about this :(

Good luck!

---

### Post by Sef on 2007-07-07
For installing, read [How to install anything in ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by brucewagner on 2007-09-13
What about this?

[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava)

Is it still accurate?

Still the best way to get Flash, Java, etc...?

---

