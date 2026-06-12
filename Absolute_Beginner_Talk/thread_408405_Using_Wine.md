---
title: "Using Wine"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Orthodox_Celt on 2007-04-13
Hello, everyone...

Recently I installed wine in order to run some win applications on my dapper (Macromedia Dreamweaver, Flash... etc) and for that I used this tut.

[http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)

Now... Both Dreamweaver and Flash runs like Charm but when I try to start Macromedia Fireworks I get this output:

err:module:import_dll Library gdiplus.dll (which is needed by L”C:\\Program Files\\Macromedia\\Fireworks 8\\Fireworks.exe”) not found
err:module:LdrInitializeThunk Main exe initialization for L”C:\\Program Files\\Macromedia\\Fireworks 8\\Fireworks.exe” failed, status c0000135

I'm starting it just like other apps (Dreamweaver...)

wine “/home/MY_USER_NAME/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe”

Hmm...
What do I do wrong? :-?

---

### Post by bcmiller on 2007-04-13
I can't help your problem specifically, but...

I got away from using wine and I installed the XP that I own or rather lease from MS inside of VirtualBox.  Now I can run any MS program natively.  It was a much better solution for me.

VirtualBox was easy to install and then I did the normal XP install. 

If you cant find an answer you may want to try this.  An other advantage of this is that it will allow you to run programs that lack wine support and avoid dual booting.  However, DirectX games will still not work.

---

### Post by rai4shu2 on 2007-04-13
The gdiplus is still in development.  See this:

[http://www.winehq.com/?issue=325#GDIPlus](http://www.winehq.com/?issue=325#GDIPlus)

---

### Post by david_kt on 2007-04-13
> **Orthodox_Celt said:**
> 
err:module:import_dll Library gdiplus.dll (which is needed by L&#8221;C:\\Program Files\\Macromedia\\Fireworks 8\\Fireworks.exe&#8221;) not found
err:module:LdrInitializeThunk Main exe initialization for L&#8221;C:\\Program Files\\Macromedia\\Fireworks 8\\Fireworks.exe&#8221; failed, status c0000135

I'm starting it just like other apps (Dreamweaver...)

wine &#8220;/home/MY_USER_NAME/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe&#8221;

Hmm...
What do I do wrong? :-?

Download gdiplus.dll from [here]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/G/GDIPLUS.DLL")

Put it on your ~/.wine/drive_c/windows/system32.
Run again your program using below command:

```
WINEDLLOVERRIDES="GDIPLUS.DLL=n" wine &#8220;/home/MY_USER_NAME/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe&#8221;
```

If still could complain about gdiplus.dll, rename GDIPLUS.DLL in your system32 and the above command to lower case (gdiplus.dll).

DK

---

### Post by Orthodox_Celt on 2007-04-14
> **david_kt said:**
> Download gdiplus.dll from [here]("http://www.dlldump.com/cgi-bin/testwrap/downloadcounts.cgi?rt=count&path=dllfiles/G/GDIPLUS.DLL")

Put it on your ~/.wine/drive_c/windows/system32.
Run again your program using below command:

```
WINEDLLOVERRIDES="GDIPLUS.DLL=n" wine “/home/MY_USER_NAME/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe”
```

If still could complain about gdiplus.dll, rename GDIPLUS.DLL in your system32 and the above command to lower case (gdiplus.dll).

DK



Thank you all...

This just works :guitar: 

THnX again

---

### Post by david_kt on 2007-04-14
> **Orthodox_Celt said:**
> Thank you all...

This just works :guitar: 

THnX again

That's good. But to make it easier, you could run winecfg, and "add applications" Fireworks.exe. And  while highlighting Fireworks.exe, click libraries tab, and add gdiplus to library overrides, set it to native.

After that, cou could run your program normally:
```
wine “/home/MY_USER_NAME/.wine/drive_c/Program Files/Macromedia/Fireworks 8/Fireworks.exe”
```

DK

---

