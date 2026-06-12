---
title: "Microsoft office 2003 not working in Ubuntu"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by radlations on 2007-12-19
So I installed Office 2003 in wine successfully.

Ran Word for the first time.  It asked me for my username. Stupidly I put in the username that I set up for ubuntu. 

Now when I run word or any office application it says "Microsoft office has not been installed for current user. Please run set up to install the application.

EDIT: I think I've found the solution, but do not understand its instructions.

```
WINE under .50 now works for both the installer and for running the apps without the "not set up for current user" error.

do NOT follow the above instructions.

1. Install Wine .50
2. Initialize your winecfg
3. Set riched* to native windows, install the richedit30 update from media.codeweavers.com/pub/crossover/office/support/richedit30.exe
4. Install the XML Parser from www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en#filelist, set msxml to native windows.
5. Run the setup from CD, network share, or local copy. 
```

Where is the "set riched* to native windows? 
How do I install the XML parser?

---

### Post by bodhi.zazen on 2007-12-19
re-run the installer ?

---

### Post by stchman on 2007-12-19
> **radlations said:**
> So I installed Office 2003 in wine successfully.

During the installation it asked for my username. But I just kept it as what Wine had on default you know "Change username in regedit" something like that.

Installed just fine.

Ran Word for the first time.  It asked me for my username. Stupidly I put in the username that I set up for ubuntu. 

Now when I run word or any office application it says "Microsoft office has not been installed for current user. Please run set up to install the application.

How do I fix this problem?

I was under the impression that Office 2K3 would not work under WINE.  I have read that Office 2K will.  I just use OO as it suits all my needs.

---

### Post by radlations on 2007-12-19
According to the Winedatabase. 2k3 runs the best.  I didnt know 2k could work.

I've already rerun the installer. I've even reinstalled wine and editted the registry thing to match my username. Same result.

---

### Post by Joeb454 on 2007-12-19
I don't want to force you out of Office 2k3...but why do you need to use that?

What's wrong with Open Office?

---

### Post by radlations on 2007-12-19
Nothings wrong with openoffice. M$ office is just better.


I think I've found my solution but do not understand its instructions


```
WINE under .50 now works for both the installer and for running the apps without the "not set up for current user" error.

do NOT follow the above instructions.

1. Install Wine .50
2. Initialize your winecfg
3. Set riched* to native windows, install the richedit30 update from media.codeweavers.com/pub/crossover/office/support/richedit30.exe
4. Install the XML Parser from www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en#filelist, set msxml to native windows.
5. Run the setup from CD, network share, or local copy. 
```

---

### Post by ptn107 on 2007-12-19
Office 2003, xp, & 2000  are functionally identical in every way to openoffice.org 2.3.0.  Office 2007, however, is different in appearance.

---

### Post by cwmoser on 2007-12-19
> **Joeb454 said:**
> I don't want to force you out of Office 2k3...but why do you need to use that?

What's wrong with Open Office?

Heck, I load Open Office on Windows.  In fact, after I started using Open Office, I prefer it over Office 2003.

Carl

---

### Post by radlations on 2007-12-19
I dont want to debate whether office 2k3 is better than OO

---

### Post by macogw on 2007-12-19
2K3 works with Crossover Office.

OOo is not functionally identical when it comes to graphs on spreadsheets or to macros (well, the macros are in different languages...OOo has fine macros though).  For laying out documents, OOo has a touch of desktop publishing (the frames) which makes it very nice for laying things out how you want them.  Word does not handle captions nearly as well.

---

### Post by LowSky on 2007-12-19
> **radlations said:**
> Nothings wrong with openoffice. M$ office is just better.


I think I've found my solution but do not understand its instructions


```
WINE under .50 now works for both the installer and for running the apps without the "not set up for current user" error.

do NOT follow the above instructions.

1. Install Wine .50
2. Initialize your winecfg
3. Set riched* to native windows, install the richedit30 update from media.codeweavers.com/pub/crossover/office/support/richedit30.exe
4. Install the XML Parser from www.microsoft.com/downloads/details.aspx?FamilyID=28494391-052b-42ff-9674-f752bdca9582&DisplayLang=en#filelist, set msxml to native windows.
5. Run the setup from CD, network share, or local copy. 
```

What is so hard to understand?

make sure your using wine 0.9.50 or greater (the newest is 0.9.51)
install richedit30... code might look like this?  ```
 wine install **location**/richedit30.exe
```
install he xml parser.... code might look like this? ```
 wine install **location**/xml parser?
```
set msxml
rerun install

---

### Post by xxrealmsxx on 2008-01-18
To install the .msi file follow these instructions:

nstalling an .msi

A user asked: How I install .msi files on WINE. J von Thadden [Dec 05] [wine archive [http://www.winehq.org/pipermail/wine-users/2005-December/020055.html]:](http://www.winehq.org/pipermail/wine-users/2005-December/020055.html]:)

wine msiexec /i xyz.msi

Anon [Sept 07]: Another way is just run:

msiexec /i fileinstaller.msi

---

