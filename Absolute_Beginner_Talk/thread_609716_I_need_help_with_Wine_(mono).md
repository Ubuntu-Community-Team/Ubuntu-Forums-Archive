---
title: "I need help with Wine (mono)"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-11-11
I have searched and didn't find the answer I need.

I am trying to run shareapic uploader with wine. I run
```
 wine '/home/tyler/.wine/drive_c/ShareAPicUploader/uploader.exe' 

```
and it returns
```
install the Windows version of Mono to run .NET executables
```

What do I need to do to run this program?

---

### Post by tdrusk on 2007-11-11
I installed windows mono. I try to run shareapic and I get this output
```
tyler@tyler-laptop:~$ wine '/home/tyler/.wine/drive_c/ShareAPicUploader/uplo.exe' 
fixme:win:EnumDisplayDevicesW ((null),0,0x61e614,0x00000000), stub!

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.ThemeEngine ---> System.ArgumentException: The requested FontFamily could not be found [GDI+ status: FontFamilyNotFound]
  at System.Drawing.GDIPlus.CheckStatus (Status status) [0x00000] 
  at System.Drawing.FontFamily..ctor (GenericFontFamilies genericFamily) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Drawing.FontFamily:.ctor (System.Drawing.Text.GenericFontFamilies)
  at System.Drawing.FontFamily.get_GenericSansSerif () [0x00000] 
  at System.Windows.Forms.Theme..ctor () [0x00000] 
  at System.Windows.Forms.ThemeWin32Classic..ctor () [0x00000] 
  at System.Windows.Forms.ThemeEngine..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at System.Windows.Forms.HScrollBar.get_DefaultSize () [0x00000] 
  at System.Windows.Forms.Control..ctor () [0x00000] 
  at System.Windows.Forms.ScrollBar..ctor () [0x00000] 
  at System.Windows.Forms.HScrollBar..ctor () [0x00000] 
  at System.Windows.Forms.ImplicitHScrollBar..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.ImplicitHScrollBar:.ctor ()
  at System.Windows.Forms.ScrollableControl.CreateScrollbars () [0x00000] 
  at System.Windows.Forms.ScrollableControl..ctor () [0x00000] 
  at System.Windows.Forms.ContainerControl..ctor () [0x00000] 
  at System.Windows.Forms.Form..ctor () [0x00000] 
  at uploader.MainForm..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) uploader.MainForm:.ctor ()
  at uploader.MainForm.Main () [0x00000] 

```

---

### Post by tdrusk on 2007-11-12
bump

---

### Post by Frak on 2007-11-12
Did you install the Windows version of [mono]("http://www.mono-project.com/Downloads")?

---

### Post by tdrusk on 2007-11-12
yes, I installed it with wine and got the above error.

---

### Post by Severun on 2007-12-02
Same issue here, trying install Fiddler

---

### Post by AronVanAmmers on 2008-01-20
Somebody on the wine-users mailinglist has [encountered the same issue]("http://www.winehq.org/pipermail/wine-users/2008-January/028530.html"). It turns out that [this function is missing in the Wine implementation of gdiplus]("http://www.winehq.org/pipermail/wine-users/2008-January/028559.html").

Conclusion: your app will not work until that function is implemented in Wine (and of course any other issues you might encounter after this). A [bug]("http://bugs.winehq.org/show_bug.cgi?id=11033") has been filed, last modified yesterday so something is being done.

---

### Post by hotweiss on 2008-05-26
I actually found a simple solution to this problem here:

[http://wine-forum.org/showthread.php?t=121](http://wine-forum.org/showthread.php?t=121)

---

### Post by AronVanAmmers on 2008-06-01
That solves my case indeed, thanks.

Now onto the next weird exception, I don't know if the software I'm trying  ([bLADE Wiki]("http://bladewiki.blogspot.com/")) will ever run on Wine ;)

---

