---
title: "Native MSXML3"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-07-17
I need to install MSXML for some programs and I have been trying this How-To from these wine pages
[http://wiki.winehq.org/NativeMSXML3](http://wiki.winehq.org/NativeMSXML3)
[http://wiki.winehq.org/NativeDcom](http://wiki.winehq.org/NativeDcom)
[http://wiki.winehq.org/NativeMsi](http://wiki.winehq.org/NativeMsi)

there is a point on the 2 page where it asks for one to install with this command, but I can't figure it out. Where do i do that command? I tried in terminal, but nothing.

A bit over my head, but determined.

---

### Post by Thenotsowyzewun on 2006-07-17
Could you be more specific?

More specifically, what do you mean by page 2? Are you referring to the 2nd link you've posted?

Which command is it that isn't working?

Thanks, hope we can help :)

---

### Post by KarmaKing on 2006-07-17
sorry, yes I was refering to link 2.  I am not sure how to use those commands highlighted?  Where to use them? They haven't wrked in terminal.

Since the instructions stated to start on the 2nd link that is where I am stuck.

---

### Post by Thenotsowyzewun on 2006-07-17
Yeah there's a mistake in the documentation.
The first command should read:

```
WINEDLLOVERRIDES="ole32=n" wine dcom98.exe
```

and the 2nd is probably OK, but reconfig using winecfg instead (or if it doesn't work).

EDIT: I love Wiki's, fixed :).

---

### Post by KarmaKing on 2006-07-18
thanks for the replies.

when I make the changes in the winecfg theses are the errors I get when I try to start back up the winecfg:

> @karmaubuntu:~$ winecfg
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\shlwapi.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") failed (error c000007b).
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Loading library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135


And then wine doesn't work at all.No programs will even run with wine.

---

### Post by kris2pe on 2006-07-18
I don't understand I already downloaded dcom98 & installed it! but nothing happens! 
Do I have to move it to the wine directory coz the says:
wine: could not load L"c:\\windows\\system32\\DCOM98.EXE.": Module not found

---

### Post by KarmaKing on 2006-07-18
bump

---

### Post by kris2pe on 2006-07-18
Yeah I'm actually looking 4 ways 4 me to b able to find a faster way to download some from bittorrent stuff just like in windows!!!

---

### Post by Thenotsowyzewun on 2006-07-18
I suggest whenever you've got a new question you start a new thread; otherwise things can get very confusing!
What program do you use for BitTorrent in Windows? If you use Azureus that runs on Linux too - [here's]("http://azureus.sourceforge.net/download.php") their site :).

However my installation of Ubuntu Dapper came preconfigured with BitTorrent (albeit it doesn't work (because of an entirely separate issue (I'm bridged to another machine)), nonetheless try clicking on a BitTorrent link in Firefox, you might be pleasantly surprised!

---

