---
title: "uninstall program in wine"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by xnszxdotnet on 2005-08-24
how do I uninstall a program under wine. can I get just rm the folder in my /fake_windows /program files?? 

thanx

---

### Post by Benzima on 2005-09-24
Same question here I beleive.

If I installed 'program X' using wine, how do I uninstall 'program X'?

I went to Applications-System Tools-Add/Remove Programs and all I get it the spinning cursor.

Thanxxx in avdvance

---

### Post by Linux_Maths on 2007-06-16
Hi, that is easy.

Just open a terminal and type
```
wine uninstaller
```
and select the program and press remove

---

### Post by scottvan on 2007-06-17
> **Linux_Maths said:**
> Hi, that is easy.

Just open a terminal and type
```
wine uninstaller
```
and select the program and press remove

I am trying to uninstall a program, but I'm having trouble.  When I do the above, I get:

```
scott@scott-desktop:~$ wine uninstaller
fixme:advapi:LookupAccountNameW (null) L"scott" (nil) 0x34dde0 (nil) 0x34dde4 0x34ddd8 - stub
fixme:advapi:LookupAccountNameW (null) L"scott" 0x5d6000 0x34dde0 0x5d51b8 0x34dde4 0x34ddd8 - stub
fixme:msi:MSI_GetProductInfo L"InstallSource"
fixme:msi:MSI_GetProductInfo L"PackageName"
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
```

Any ideas?  I need to uninstall Quicken so I can reinstall it.

---

### Post by Vendetta_NZ on 2007-07-08
When I do this, there is nothing in the list, yet I installed COD2 and XFire that same day?

---

### Post by weblordpepe on 2007-07-22
just type 'uninstaller' on the command line. the normal linux command line.
bash
:)

---

### Post by framebuffer on 2007-10-13
> **weblordpepe said:**
> just type 'uninstaller' on the command line. the normal linux command line.
bash
:)

Hello!

I am trying to uninstall Microsoft-English-TTS-51.msi

No matter how many times I do the uninstall, It doesn't uninstall.

I get the following error:

fixme:advapi:LookupAccountNameW (null) L"manuj" (nil) 0x34f38c (nil) 0x34f390 0x34f384 - stub
fixme:advapi:LookupAccountNameW (null) L"manuj" 0x149178 0x34f38c 0x1497f0 0x34f390 0x34f384 - stub
fixme:msi:ACTION_PerformAction unhandled msi action L"UpdateResources"
fixme:msi:msi_unimplemented_action_stub UnregisterTypeLibraries -> 3 ignored L"TypeLib" table values
fixme:msi:msi_unimplemented_action_stub UnregisterProgIdInfo -> 72 ignored L"ProgId" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values

---

### Post by oldsoundguy on 2007-11-23
This is all well and good, but it seems I have something a little bit more difficult.
I attempted to install the Adobe CS2 suite using WINE and made an error somewhere in the install.  I need to remove it and try again.  The removal tool in WINE does not do it .. and the uninstall in CS2 does not get it either. 
I have gone into the files and removed everything INCLUDING WINE, and, of course, it all disappeared (went into the phony C directory, too!) ...  UNTIL I re install WINE and there they are again.  This completely blocks any attempt to re-install, repair, OR remove.
Any clues would be appreciated.
Not a total newbie to Linux, but AM a newbie to Ubuntu (love it thus far!)

I would hate to have to wipe and start over again, but I will do so if needed (installing the wireless was a stone BEAR!)

---

### Post by mc4man on 2007-11-23
Did you delete your .wine directory (/home/<username>)
If so look in .local/share for wine related stuff
note: both folders are hidden

---

### Post by oldsoundguy on 2007-11-23
did that again .. got everything out, and then re-installed using synaptic and got the same issues.  Read somewhere else that the better way is to install using terminal/deb as there may be an issue with the latest WINE in 7.10 .. will give that a shot later.

Everything else in the build works great thus far and this seems to be my only issue.  (other than screen rotation on a rotatable monitor with a card that SUPPORTS rotation!)(that is assuredly, a back burner issue right now.)

I did get my 1ONE colorimeter installed and the display calibrated using WINE.  THAT is important when doing photographic work.  But lost it in this shuffle.  Reinstalling should not be an issue with it.

---

### Post by pauper on 2007-12-01
```
regedit
```
There you need to open \HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall
Look for the entry of the uninstalled program (it will be the program name) and delete it (right click). In some instances, instead of the program name, you'll see an entry like this: {3075C5C3-0807-4924-AF8F-FF27052C12AE}. In that case, open the DispayName subkey in that entry; it should have the name of the program&#8212;in this instance, Norton Antivirus 2002. When you find the proper entry, delete it.

You may check out this link [http://www.oreilly.com/pub/h/670]("http://www.oreilly.com/pub/h/670")

---

### Post by Business Convert on 2008-03-13
Also, if you delete the files first manually, and do not use the uninstall feature, you will need to do the following:

This is the Command (in the terminal window):   "regedit"  without the quotes

Brings up:
My Computer
HKEY_Current_USER
Software

You will find the program under there.  Delete it there.

If you don't delete it from this hive, the program reinstall will see it there and cause you more issues....

Good Luck!

---

### Post by sgtbob on 2008-04-02
OK - I got rid of [COLOR="Red"]wine[/COLOR] [COLOR="Black"]but the package is still shown in the 'Applications'.  How do I get rid of it and the 4 programs noted under it????[/COLOR] I want to re-install a clean copy of wine, but can't get rid of the trash remaining from the uninstall feature used in the 'Synaptic Package Manager'!!

Been trying to get this rooted out for 2 weeks with no luck.

I lost the instructions to root the files out manually, so if someone knows how to do this, please advise in minute detail for this old man.

Bob:confused::confused::confused::confused:

---

### Post by Thelasko on 2008-04-02
> OK - I got rid of wine but the package is still shown in the 'Applications'. How do I get rid of it and the 4 programs noted under it???? I want to re-install a clean copy of wine, but can't get rid of the trash remaining from the uninstall feature used in the 'Synaptic Package Manager'!!

In your /Home folder you should have a hidden folder (press Ctrl+H to view) called .wine.  Try deleting that and reinstall wine.

---

### Post by Ghost_ARCHER on 2008-07-05
I think this might be helpful, if I understand the question correctly.

[http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391](http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391)

ctrl+F paste
3.1. How do I uninstall Windows applications?

And ctrl+c ....... and ..... and ........



I have successfully removed the faststone I have installed in wine...

---

