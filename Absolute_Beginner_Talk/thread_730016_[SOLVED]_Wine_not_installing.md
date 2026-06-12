---
title: "[SOLVED] Wine not installing"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Samurai Penguin on 2008-03-20
I had to re-install Ubuntu last night because for some unknown reason
the 56K modem kept signing itself off line just as soon as it connected to
the server. I thought it might have been the ISP but it wasn't. Anyway,

I'm installing all my stuff again and, unlike the last time I installed WINE,
tis time I'm seeing an install error that says,

root@HAL:/home/tomana# wine setup785.exe
wine: could not load L"c:\\windows\\system32\\setup785.exe": Module not found

I used Add-Remove to uninstall and re-install, then ran that code again
and same result. WINE shows in the Applications drop down list and I can
access Browse C:\Drive and I installed riched20.dll and msls31.dll

setup785.exe wasn't missing the last time I installed Ubuntu ... why now?

---

### Post by jaimerod on 2008-03-20
you can try to clean up your apt in a terminal. Try removing wine first

```
sudo apt-get remove wine
```

Then try update, clean, they install wine again

```
sudo apt-get update
```
```
sudo apt-get clean
```
```
sudo apt-get install wine
```

See if that works.

---

### Post by forrestcupp on 2008-03-20
You could uninstall it, and go to [Wine's official site](http://winehq.org/site/download-deb) and install the newest version by their instructions.  It's very easy.

---

### Post by Samurai Penguin on 2008-03-20
thanks ... I uninstalled and then used clean, went to Wine website and added
latest package to Add/Remove (terminal commands were right there just waiting
for me to use them) and I'm downloading the latest version of Wine as I type ...

thanks

---

### Post by Samurai Penguin on 2008-03-20
ok, I have wine installed, I went to the iexplorer.exe and double-click it and
get the following message:

iexplore.exe can not be opened
No application suitable for automatic installation 
is available for handling this kind of file.

I want to run e-Sword.exe but I get the same error message
whenever I double-click it. I've tried the exe files in Program Files
and many other places within Drive C but still get the same error
message.

Just tried the NOtepad icon in the applications pull down list and it works
so I must be installing the exe's incorrectly ?

---

### Post by Faud on 2008-03-20
What is your error message and just fyi you dont need ie to run e-sword

---

### Post by bwang on 2008-03-20
Try running the programs from the terminal:
```
wine <*program name*>
```
where <*program name*> is the executable you are trying to run.

---

### Post by Samurai Penguin on 2008-03-20
ok, I put the e-sword.exe in the Windows/system32 folder and ran 

wine e-sword

and here's the results

root@HAL:/home/tomana# wine e-sword.exe
wine: could not load L"c:\\windows\\system32\\e-sword.exe": Module not found
root@HAL:/home/tomana# fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!

no program opened. Then I ran

wine notepad
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
root@HAL:/home/tomana# 

notepad opened and functions ok but gave the same error regarding pipe r = 0

how do I install an exe into wine?

---

### Post by forrestcupp on 2008-03-21
If you want to be able to double click an exe, you have to set it up to know to use wine to open them.  Right click on an exe and choose Properties.  Click the 'Open with' tab and set it up to use wine.

Or just 'cd' to the correct directory in your terminal and type:
[code]wine ./filename[code] substituting your correct filename.

[Here](http://frankscorner.org/index.php?p=e-sword) is a guide to getting e-sword working in wine.  It works just fine with some tweaking.

---

