---
title: "Wine help"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-08-11
I have installed Wine and have installed messenger so how do i launch that installed software.

---

### Post by dhani99 on 2007-08-11
bump

---

### Post by eapache on 2007-08-11
Wine should have put a link in your menu, but if not, find the directory it installed to. It should be "/home/username/.wine/drive_c/Program Files/somethingrather". To view the .wine folder in Nautilus press ctrl-h (folders beginning with a . are hidden by default). Find the name of the executable as well. You should now have the full path to the exe file. Simply run```
wine "full path to exe"
```in a terminal. If you want a link, right-click on desktop, click on "create launcher" and enter the above code as the program to run.

---

### Post by dhani99 on 2007-08-11
so this is the path 

 wine  /home/keval/.wine/drive_c/Program Files/MSN Messenger/msnmsgr.exe

it says wine cannot find 
wine: cannot find '/home/keval/.wine/drive_c/Program'

I'm doing something wrong, naah

---

### Post by dhani99 on 2007-08-11
well i've gone to that directory and i've seen that EXE file so can i open from that for now ??

---

### Post by eapache on 2007-08-11
It's stopping at the space. Simply put the path in quotes.

---

### Post by dhani99 on 2007-08-11
then got this 

err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\MSNCore.dll") not found
err:module:import_dll Library MSNCore.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library gdiplus.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\ContactsUX.dll") not found
err:module:import_dll Library ContactsUX.dll (which is needed by L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MSN Messenger\\msnmsgr.exe" failed, status c0000135
keval@keval-desktop:~$

---

### Post by jeremy1138 on 2007-08-11
Hey!  I'm having the same kind of problem.  I tried to install AIM using wine and the install appeared to go well but I can't get the program to start now.  I did as suggested above and here's what the terminal spit back out:

```

jeremy@jeremy-laptop:~$ wine '/home/jeremy/.wine/drive_c/Program Files/AIM/aim.exe' 
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:ntdll:RtlpWaitForCriticalSection section 0x7bc8d6e4 "loader.c: loader_section" wait timed out in thread 000c, blocked by 0009, retrying (60 sec)
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39110

```

Any ideas anyone?  Thanks for you help!

---

### Post by eapache on 2007-08-11
These are just bugs in wine (fixes are being worked on), so the programs probably won't work. You can still connect to MSN and AIM accounts using GAIM under Applications>Internet

---

### Post by jeremy1138 on 2007-08-11
> **eapache said:**
> These are just bugs in wine (fixes are being worked on), so the programs probably won't work. You can still connect to MSN and AIM accounts using GAIM under Applications>Internet

For some odd reason I can't get GAIM or Pidgin to connect.  I can't get them to log in to my yahoo or Aim accounts...  I have no idea what the deal is with them...  Thanks!

---

### Post by dhani99 on 2007-08-11
> **eapache said:**
> These are just bugs in wine (fixes are being worked on), so the programs probably won't work. You can still connect to MSN and AIM accounts using GAIM under Applications>Internet

thanx for letting us know buddy, and cud i use yahoo messenger, will it gonna work ??

---

### Post by dhani99 on 2007-08-11
is there any program such as WINE ?

---

### Post by eapache on 2007-08-12
I'm not sure what you mean by "is there any program such as wine", but yahoo messenger probably won't work either through wine. Your best bet is still to use Gaim / Pidgin.

Jeremy1138, I haven't had any problems getting Gaim to connect to my accounts... what configuration have you tried?

---

### Post by jeremy1138 on 2007-08-12
> **eapache said:**
> I'm not sure what you mean by "is there any program such as wine", but yahoo messenger probably won't work either through wine. Your best bet is still to use Gaim / Pidgin.

Jeremy1138, I haven't had any problems getting Gaim to connect to my accounts... what configuration have you tried?

I've tried messing with all the settings that I can think of and I made another post to try to find out how to fix it but I still have no idea what to do.  Both Gaim and Pidgin say that my connection is timing out when I try to connect.  I assume something is keeping gaim and pidgin from connecting but I'm not sure what.  I tried running them both from the command line but I got no errors at all.  Any ideas?

Thanks for your help!

---

### Post by eapache on 2007-08-12
I have to say that's very odd. Can you please link to the post you made to fix it, as it is technically a separate question?

---

### Post by jeremy1138 on 2007-08-12
> **eapache said:**
> I have to say that's very odd. Can you please link to the post you made to fix it, as it is technically a separate question?

Here is the link to the post.
[http://ubuntuforums.org/showthread.php?t=523909](http://ubuntuforums.org/showthread.php?t=523909)
Thanks for your help on this!

---

### Post by frazelle09 on 2007-08-13
i'm using a program called aMSN, available through the repos and which even offers webcam support which i've been using for several weeks now for my Hotmail account.

Works great.  Doesn't require Wine.

Have a great evening!  :)

---

