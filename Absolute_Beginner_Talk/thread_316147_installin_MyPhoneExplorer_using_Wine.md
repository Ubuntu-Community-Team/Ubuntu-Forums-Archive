---
title: "installin MyPhoneExplorer using Wine"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by milad on 2006-12-10
I don't know if you've heard of [MyPhoneExplorer]("http://www.fjsoft.at/en/") but it's a very cool  phone manager for SonyEricsson phones which I've been using in Windows$ for quite long time.

I know we can install some of windows applications on Linux using Wine but I didn't find any EASY guide on how to use it. I simply executed the setup file using wine command and installed it in my Home directory, but when I try to run it I see an error message about a dll or something!

So can anybody help me installing it please?

BTW I think it needs Microsoft Visual Basic 6 Runtimes too ...

---

### Post by beefcurry on 2006-12-10
Theres a BIG chance if it not working. Post what exactly what DLL error you have or else no one can help you.

---

### Post by pay on 2006-12-10
Can you please post the error message?

---

### Post by milad on 2006-12-17
Here's the error message:

Runtime error '339'

Component 'sport.dll' or one of its dependencies not correctly registered:a file is missing or invaild

and here's what I get in terminal:

fixme: ole:CoRegisterMessageFilter message filter has been registered, but will not be used
fixme: ole:OLEFontImpl_IPersistStreamInit_InitNew (0x17482c), stub!
fixme: ole:OleLoadPictureEx (0xb993ac,300062,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f8f8), partially implemented.
err: ole:CoGetClassObject class {14e95046-bec7-46d2-b9e3-74b1ad14ac65} not registered
err: ole:CoGetClassObject class {14e95046-bec7-46d2-b9e3-74b1ad14ac65} not registered
err: ole:CoGetClassObject no class object {14e95046-bec7-46d2-b9e3-74b1ad14ac65} could be created for context 0x3
err: ole:CoGetClassObject class {14e95046-bec7-46d2-b9e3-74b1ad14ac65} not registered
err: ole:CoGetClassObject class {14e95046-bec7-46d2-b9e3-74b1ad14ac65} not registered
err: ole:CoGetClassObject no class object {14e95046-bec7-46d2-b9e3-74b1ad14ac65} could be created for context 0x3

---

### Post by milad on 2006-12-17
No one uses a K750 here? :(

---

### Post by N00BIE12345 on 2007-01-05
Hello,

there´s a thread in the official forum (german) about making an old version (1.3.3) work with wine. Versions newer than 1.3.3 are using a library (...sport...dll) that causes trouble. 

I tried to start MyPhoneExp. 1.3.3, but during the start-process, while the splashscreen is showing, I get the followoing error:


```
Run-time error '372':
Failed to load control 'PhoneBook_Tel' from . Your version may be outdated.
Make sure you are using the version of the control that was provided with your application.
```

If you have more luck with it, tell me. I´ll ask the lucky guy in the german thread in the meanwhile...

[http://www.fjsoft.at/forum/viewtopic.php?t=1402&postdays=0&postorder=asc&start=0](http://www.fjsoft.at/forum/viewtopic.php?t=1402&postdays=0&postorder=asc&start=0)

---

### Post by fenixartzz on 2008-01-02
i have w810 and i managed to get it going using the help from
[http://www.fjsoft.at/forum/viewtopic.php?t=2838](http://www.fjsoft.at/forum/viewtopic.php?t=2838)

i think the error you are getting is because you havent regesterd the ocx files

i didnt manage to install some icon dll in main folder and one k something one in DLL folder rest all ocx and dll were registered and app is working

go through the post which says
It rocks.  Thanks ever so much. My K800i sonny ericsson is happy. 

should get it to run without any issue

i have it working with usb yet to try with bluetooth

let me know if have any more issue

---

### Post by trackside on 2008-01-09
I downloaded that MPE for wine version and followed that write-up on FJ Software to a tee and still got that 339 runtime error, along with "Component 'ccrpDtp6.ocx' or one of its dependencies not correctly registered: a file is missing or invalid"

I'm working with Feisty Fawn. 

Some commandline output looked like this:
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject no class object {167066b3-693a-44b0-afb4-422380ff940d} could be created for context 0x3
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject no class object {167066b3-693a-44b0-afb4-422380ff940d} could be created for context 0x3

with some "fixme:win:SetLayeredWindowAttributes" messages preceeding it.

---

### Post by chezzo on 2008-02-18
> **trackside said:**
> I downloaded that MPE for wine version and followed that write-up on FJ Software to a tee and still got that 339 runtime error, along with "Component 'ccrpDtp6.ocx' or one of its dependencies not correctly registered: a file is missing or invalid"

I'm working with Feisty Fawn. 

Some commandline output looked like this:
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject no class object {167066b3-693a-44b0-afb4-422380ff940d} could be created for context 0x3
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject class {167066b3-693a-44b0-afb4-422380ff940d} not registered
err:ole:CoGetClassObject no class object {167066b3-693a-44b0-afb4-422380ff940d} could be created for context 0x3

with some "fixme:win:SetLayeredWindowAttributes" messages preceeding it.

you need to do the "regsvr32" step with the ocx files too

---

### Post by talvon on 2008-02-24
> **fenixartzz said:**
> i have w810 and i managed to get it going using the help from
i have it working with usb yet to try with bluetooth

let me know if have any more issue

Could you please detail how to get it to work with USB? I have the app running but I can't get USB to work following instructions on the MPE site :(

---

### Post by Folvarok on 2008-04-30
I write script that install MyPhoneExplorer uisng Wine: :)

```
#!/bin/bash
export WINEPREFIX=${HOME}/.myphoneexplorer
# Create the myphoneexplorer wine drive
if [ ! -d ${WINEPREFIX} ]; then
   echo --- Creating WINE prefix ${WINEPREFIX}...
   wineprefixcreate > myphoneexplorer.log 2>&1
fi
if [ ! -f "MyPhoneExplorer_wine.zip" ]; then
	echo ---  download http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip...
	wget "http://www.fjsoft.at/files/MyPhoneExplorer_wine.zip"
fi
echo --- Download VB6 runtimes
if [ ! -f "vbrun60sp6.exe" ]; then
	wget "http://download.microsoft.com/download/5/a/d/5ad868a0-8ecd-4bb0-a882-fe53eb7ef348/VB6.0-KB290887-X86.exe"
	rm VB6.0-KB290887-X86.exe
	cabextract -F vbrun60sp6.exe VB6.0-KB290887-X86.exe vbrun60sp6.exe
fi
echo -e REGEDIT4\\n\\n[HKEY_CURRENT_USER\\Software\\Wine\\DllOverrides]\\n\"asycfilt\"=\"native\"\\n\"comcat\"=\"native\"\\n\"msvbvm60\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"oleaut32\"=\"native\"\\n\"olepro32\"=\"native\"\\n\"stdole2.tlb\"=\"native\"\\n[HKEY_CURRENT_USER\\Software\\MyPhoneExplorer]\\n\"Language\"=\"English.lng\" > temp.reg
wine regedit temp.reg
mv ${WINEPREFIX}/drive_c/windows/system32/oleaut32.dll ${WINEPREFIX}/drive_c/windows/system32/oleaut32-alt.dll
mv ${WINEPREFIX}/drive_c/windows/system32/olepro32.dll ${WINEPREFIX}/drive_c/windows/system32/olepro32-alt.dll
wine vbrun60sp6.exe /Q >> myphoneexplorer.log 2>&1
unzip -q MyPhoneExplorer_wine.zip -d ${WINEPREFIX}/drive_c
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpDtp6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/ccrpUCW6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/ShellMgr.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/SSubTmr6.dll
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalExpBar6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalIml6.ocx
wine regsvr32 c:/MyPhoneExplorer/DLL/vbalSGrid6.ocx
ln -is /dev/ttyACM0 ${WINEPREFIX}/dosdevices/com1
ln -is /dev/rfcomm0 ${WINEPREFIX}/dosdevices/com2
sudo chmod 777 ${WINEPREFIX}/dosdevices/com1 ${WINEPREFIX}/dosdevices/com2
#Desktop Icon...
echo -e [Desktop Entry]\\nEncoding=UTF-8\\nType=Application\\nTerminal=false\\nName[ru_RU]=My Phone Explorer\\nExec=env WINEPREFIX=${WINEPREFIX} wine c:/MyPhoneExplorer/MyPhoneExplorer.exe\\nName=My Phone Explorer\\nIcon=20e3_myphoneexplorer.0 > ~/Desktop/MyPhoneExplorer
chmod 777 ~/Desktop/MyPhoneExplorer

```

---

