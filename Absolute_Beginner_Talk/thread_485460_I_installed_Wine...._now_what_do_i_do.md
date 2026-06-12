---
title: "I installed Wine.... now what do i do?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-26
I just installed Wine and would like to try a see how it works.  Does any one have a link to good guide which shows how to use wine?

---

### Post by aktiwers on 2007-06-26
Just type:
```
winecfg
```

in Terminal and check if the settings is as you like.
Changing nothing is ok, but you need to run that command atleast once.

Then just double-click the .exe you want to try.

(Sometimes if the exe doesnt run, it has worked for me to set wine into window mode, in the winecfg).

Good luck :)

---

### Post by normworthy on 2007-06-26
I found that I had to right click one *.exe program then preferences and the at open with.... put in .wine   I think I had to type it in as it was not on the drop down.  there is a dot before the wine ( .wine)

After that, it will work with just double clicking anything.

I hope I am right on this, I tried a lot of things and suddenly it worked.

Hope that helps
Norm

---

### Post by cogadh on 2007-06-26
Also check these places for detailed Wine info:
[http://wiki.winehq.org/](http://wiki.winehq.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by videocheez on 2007-06-26
Thanks guys.  So when using Wine, do i install the apps in linux or do i open the existing apps. on the Windows partition/drive?

---

### Post by aktiwers on 2007-06-26
Install them on Linux. They will be installed in:
/home/yourusername/.wine/drive_c/Program Files/

You need to install them again, as the registry files on a current windows installed app is in Windows and not Wine. Installing it again through wine will put them in Wine as well..

EDIT:
The .wine in the path means wine is a hidden folder. To view hidden folders press CTRL+h

---

### Post by videocheez on 2007-06-26
So can I just move a *.exe file to my linux desktop and double click it?

---

### Post by aktiwers on 2007-06-26
yeah pretty much..  but as Normworthy said, maybe it doesnt open in Wine by default (it does for me though) then right click on it and say "open with wine".

But remember not all exe's work with Wine .

---

### Post by cogadh on 2007-06-27
> **videocheez said:**
> So can I just move a *.exe file to my linux desktop and double click it?
You can do that, but it usually better to run the *.exe from the terminal. If the installation or application encounters any problems, Wine will fail silently without any error messages when you use the right-click or double-click launch methods. When you run the application from the terminal, any errors are logged in the terminal window and can be used to troubleshoot and correct problems. To run an app through Wine from the terminal, just do this:
```
wine /path/to/windows/executable.exe
```
Obviously, change the path to the actual path.

---

### Post by Pizzarth on 2007-06-27
and to handle those pesky fullscreen yet lowresolution programs, you can type
```
 wine explorer /desktop=foo, [x screen resolution(say 1280)] x [y screen resolution(say 1024)] filename(including path if not already in folder
```

usually it ends up for me as
```
 wine explorer /desktop=foo,1024x768 FILENAME.exe
```

if there's a shorter way, please tell me :P I'd also like to know

---

### Post by videocheez on 2007-06-27
Ok so now that I have installed a windows remote desktop app, using wine......How do I run the program to see if the install worked?

---

### Post by davidwfox on 2007-06-27
The simplest way is through your Toolbar. If you click on Applications, you should now find that Wine appears at, or near, the bottom of your drop-down list. So click on Applications -> Programs -> and just follow your way across to the executable of the programme you installed.

Failing that you'll need to start it via Terminal. Come back if you need directions on how to do that


Sorry - that should read "... click on Applications -> Wine -> Programs -> and ... "

---

### Post by cogadh on 2007-06-27
> **videocheez said:**
> Ok so now that I have installed a windows remote desktop app, using wine......How do I run the program to see if the install worked?
The Linux native rdesktop client can connect to Windows machines, you don't need to use Wine for that. But if you are just using it to play with Wine, then either follow davidwfox advice or the info I posted on using the terminal to launch the app.

---

### Post by videocheez on 2007-06-27
> **davidwfox said:**
> The simplest way is through your Toolbar. If you click on Applications, you should now find that Wine appears at, or near, the bottom of your drop-down list. So click on Applications -> Programs -> and just follow your way across to the executable of the programme you installed.

Failing that you'll need to start it via Terminal. Come back if you need directions on how to do that


Sorry - that should read "... click on Applications -> Wine -> Programs -> and ... "

Perhaps the program did not install properly because the only thing in the directory at this location is an uninstall program.  Via terminal I typed:

don@don-ubuntu:~$ wine /home/don/.wine/drive_c/Program Files/Radmin Viewer 3.0/Radmin.exe
wine: cannot find '/home/don/.wine/drive_c/Program'

[QUOTE=cogadh]The Linux native rdesktop client can connect to Windows machines, you don't need to use Wine for that. But if you are just using it to play with Wine, then either follow davidwfox advice or the info I posted on using the terminal to launch the app.[/QUOTE]

Is this rdesktop a terminal program?   How does it connect to windows machines?  I'm basically trying the program in order to see wine in action but if I could get it working I would be happy since I really like Radmin for remote desktop services.

Thanks in advance, any suggestions will be appreciated,

VC

---

### Post by cogadh on 2007-06-27
Rdesktop uses the same RDP protocol Windows Remote Desktop uses. You can read about it [here]("http://www.rdesktop.org/") and [here]("http://en.wikipedia.org/wiki/Rdesktop").

---

### Post by Angelbeast on 2007-06-28
Hellooooo...I'm having a couple of issues with this...first off...i installed the 32 bit version of wine onto 64 bit ubuntu via automatix...and i'm not seeing it anywhere in my apps menu...second...i tried to install an adobe trial and got the error you will fond on the attached screenshot...is there any way to fix this? Thanks...

---

### Post by swoll1980 on 2007-06-28
Install the chesse to go with it :b

---

### Post by cogadh on 2007-06-28
> **Angelbeast said:**
> Hellooooo...I'm having a couple of issues with this...first off...i installed the 32 bit version of wine onto 64 bit ubuntu via automatix...and i'm not seeing it anywhere in my apps menu...second...i tried to install an adobe trial and got the error you will fond on the attached screenshot...is there any way to fix this? Thanks...
Please don't hijack someone else's thread with an unrelated problem, it's rude. It is best to post a new thread with this error (after properly searching the forums for existing threads that have this error). That way, everyone who frequents the forum will have an opportunity to address the problem. By adding to this thread, only those of us who are following videocheez's question are seeing it and will respond to it.

---

### Post by Angelbeast on 2007-06-28
> **cogadh said:**
> Please don't hijack someone else's thread with an unrelated problem, it's rude. It is best to post a new thread with this error (after properly searching the forums for existing threads that have this error). That way, everyone who frequents the forum will have an opportunity to address the problem. By adding to this thread, only those of us who are following videocheez's question are seeing it and will respond to it.

Well...Please, excuse me then...I do apologize...I did not realize that i was hijacking since this is a thread about getting wine to work. No matter though. I found my answer on a different site. Thanks for the assistance and advice...Again i do apologize for my 'rudeness'...

---

### Post by davidwfox on 2007-06-29
> **videocheez said:**
> Perhaps the program did not install properly because the only thing in the directory at this location is an uninstall program.  Via terminal I typed:

don@don-ubuntu:~$ wine /home/don/.wine/drive_c/Program Files/Radmin Viewer 3.0/Radmin.exe
wine: cannot find '/home/don/.wine/drive_c/Program'
VC

This is because of the spaces in the path - between "Program" and "Files", between "Radmin" and "Viewer", and between "Viewer" and "3.0". You have two options:
1. Enclose the entire path string in quotes: 
~$ wine "/home/don/.wine/drive_c/Program Files/Radmin Viewer 3.0/Radmin.exe" or
2. Use excase symbols before each space:
~$ wine /home/don/.wine/drive_c/Program\ Files/Radmin\ Viewer\ 3.0/Radmin.exe

Either way will work; using the quotes is probably the easier way. Use one of those methods to install your programme, and you should then find it OK following Application -> Wine -> Programs ..etc..

---

### Post by videocheez on 2007-06-30
don@don-ubuntu:~$ wine "/home/don/.wine/drive_c/Program Files/Radmin Viewer 3.0/Radmin.exe"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
don@don-ubuntu:~$ 

Okay what does the above stuff mean?  Also, what does the quotes do for me?  
Also, when I try to run, a small box pops up and says KERNEL32.dll.

---

### Post by d_xtremw on 2007-07-01
I installed Wine using all the instructions on the thread (thanx everyone for the help)  but im still running into some trouble

wen i double click on the .exe fle. nothing happens. i already set it up to open with wine but nothing happens when i double click on it. also when i try to use the terminal to open the file i get a whole set of errors telling me that some specific files needed for the program werent found.
 
heres an example:

err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found

---

### Post by cogadh on 2007-07-01
If you have a Windows install, you will need to copy those DLLs from the Windows install into the Wine system32 folder then add a DLL override in winecfg for them. Not sure if MSN Messenger will actually work in Wine though. You should check Wine's AppDB to see if it usable in Wine. Unfortunately, Wine's website is down for maintenance right now, so you won'tt be able to check it until it is back.

---

### Post by d_xtremw on 2007-07-01
well i do have a windows install. So what you're saying is i need to go thru the list and check each of the missing components and copy it into a wine system 32 folder??  and what exactly is the DLL override in the wine config? or am i getting too far ahead of myself

---

### Post by cogadh on 2007-07-01
That's exactly what I am saying. After you copy the missing DLLs from your Windows installation into the Wine system32 folder, open a terminal and run "winecfg". Click on the Libraries tab and enter the full DLL file name in the "New override for library:" field. Click add and it will create an override entry telling Wine to use a native DLL first (i.e. the one you copied) before trying to use a Wine builtin DLL. Since Wine does not have an implementation of all Windows DLLs, this is sometimes the only way to get Windows apps to work.

However, I cvannot stress enough that some Microsoft apps will never work with Wine correctly and MSN Messenger may be one of them. You may be better off to wait for Wine's AppDB site to come back up and check to see if MSN Messenger is even worth trying.

---

### Post by d_xtremw on 2007-07-01
aight thanx alot. I'll reply to the thread once i find out for sure

---

### Post by cogadh on 2007-07-01
The site's back up and I just checked, it is listed as "Garbage" in AppDB. Version 5 and 7 have a Bronze rating on a few Linux distributions, but nearly all list it as completely non-functional.

---

### Post by d_xtremw on 2007-07-01
oh damn.  do you know if bitcomet is listed on that site? or can you paste a link so that i can check it out

---

### Post by cogadh on 2007-07-01
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

