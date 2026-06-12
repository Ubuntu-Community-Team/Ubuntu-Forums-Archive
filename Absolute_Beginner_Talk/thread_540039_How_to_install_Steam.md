---
title: "How to install Steam"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by MS-DOS4 on 2007-09-01
So I've been having a problem installing steam. I downloaded SteamInstall.msi then placed it my user name folder, then I put this in:

```
wine msiexec /i SteamInstall.msi
```

and yay! It works! However was no font so I clicked random buttons trying to get it to run and I think I broke it. I decided I'd download that missing windows font, oh I forgot what it was called. but after some research I found that missing font and installed it. So I decided to uninstall Steam and try again, this time it brought me to the window "would you like to repair or remove steam?" I chose remove and then tried again. I got the same window so I decided to try to remove it with the wine application uninstaller, still nothing. Then I tried manually removing the steam folder, still nothing. Can somebody help me get rid of steam so I can re-install it freshly? 

Oh and by the way, whenever I try to open up Steam.exe anyway it does an update then tells me: "sorry, you can only run one copy of steam at a time. You are currently running steam"

I tried rebooting to see if I could get steam to stop running but no dice. Help?

2nd PS: This is a screenshot of it:
[img]http://img237.imageshack.us/img237/6656/screenshotcj5.png[/img]

---

### Post by splintercellguy on 2007-09-01
From the Wine AppDb entry ([http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)), you can either copy tahoma.ttf from a Windows install to ~/.wine/drive_c/windows/fonts, or you can add a Wine registry patch so a different font is substituted.

---

### Post by MS-DOS4 on 2007-09-01
After re-installing Wine, I got it to work. However when it was all done updating and I logged into my previous steam account, I got a message saying my computer doesn't meet the system requirements for HL2. :(

Oh well. 

...soo close...

---

### Post by mocoloco on 2007-09-01
If there's nothing else you care about under wine I would just delete your ~/.wine folder and then you can run wineconfig and start over.

Edit: simultaneous post :)
In that case would it be your Windows version under wine?  I think it defaults to NT or something which would explain your error.

---

### Post by splintercellguy on 2007-09-01
> **MS-DOS4 said:**
> After re-installing Wine, I got it to work. However when it was all done updating and I logged into my previous steam account, I got a message saying my computer doesn't meet the system requirements for HL2. :(

Oh well. 

...soo close...

The message about the deprecated DX version can be safely ignored, Steam sees the Wine libraries.

---

### Post by MS-DOS4 on 2007-09-01
So you think I can still play even at the lowest settings?

---

