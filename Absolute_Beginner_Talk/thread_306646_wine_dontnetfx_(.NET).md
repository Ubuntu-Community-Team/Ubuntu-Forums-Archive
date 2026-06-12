---
title: "wine dontnetfx (.NET)"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by mackyman on 2006-11-25
Okej, another wine thread...

I try to get a program working that uses the .NET 2.0. But I can't install .NET.

It complains about not having IE 5.01. I have installed IE 5.0, 5.5 and 6.0 with IEs4Linux, but after some searching, I found someone saying it is installed outside of my normal wine installation. (DAMED!)

Now I have tried to get IE installed, but no luck there. How the f**k is these microsoft products supposed to work?

Someone got any guides, tips, or help for me here?

I got wine version 0.9.18, the higher versions don't seem to go to well with my system, as said in my [earlier thread]("http://ubuntuforums.org/showthread.php?t=305956&highlight=wine+config").

Thanks in beforehand

---

### Post by bodhi.zazen on 2006-11-25
> **mackyman said:**
> Okej, another wine thread...

I try to get a program working that uses the .NET 2.0. But I can't install .NET.

It complains about not having IE 5.01. I have installed IE 5.0, 5.5 and 6.0 with IEs4Linux, but after some searching, I found someone saying it is installed outside of my normal wine installation. (DAMED!)

Now I have tried to get IE installed, but no luck there. How the f**k is these microsoft products supposed to work?

Someone got any guides, tips, or help for me here?

I got wine version 0.9.18, the higher versions don't seem to go to well with my system, as said in my [earlier thread]("http://ubuntuforums.org/showthread.php?t=305956&highlight=wine+config").

Thanks in beforehand

LOL with microsoft products you are suppozed to run Windows!

Microsoft has limited, at best, interest in Linux compatibility.

Short answer, there is no fix to your problem as of yet.

From wine HQ:> Description
The .NET Framework version 2.0 improves scalability and performance of applications with improved caching, application deployment and updating with ClickOnce, support for the broadest array of browsers and devices with ASP.NET 2.0 controls and services.

What works
Nothing    

What does not
Installation. The program 'seems' to install but any applications that require .NET v2 still think it isn't installed meaning the installation didn't work properly (the progress meter also doesn't move when you install the framework. at the end it just says it's installed. .NET then also won't let you uninstall it. You can bring up the installer option by re-running the setup program again and selecting uninstall, but you get the same issue with the installation, the progress meter doesn't move then the uninstaller just closes. So although the program looks like it installs, it actually doesn't. 

[WineHQ AppDDB .NET](http://appdb.winehq.org/appview.php?iVersionId=3754)

---

### Post by mackyman on 2006-11-25
ok, thanks for the quick answer.

Hopefully some people might stop demanding that you have microsoft **** on your computer to get their programs working.

---

### Post by Deathmoon on 2006-11-25
Has anyone been able to figure this out yet?

I've got some apps that I wrote in VB.NET on Windows and I want to use them in Ubuntu.  Any ideas?

---

### Post by houstonbofh on 2006-11-25
> **mackyman said:**
> ok, thanks for the quick answer.

Hopefully some people might stop demanding that you have microsoft **** on your computer to get their programs working.
A somewhat more painful answer, but there is always qemu.  It is in the repositories, and it works well, if slow.  If you have the option, I would install it with win2k, not winXP.

---

### Post by Deathmoon on 2006-11-25
Believe me, I'm off of MSFT now.  I'm just trying to get this one program that I wrote in VB.NET to work.  :-#

---

### Post by coder_ on 2006-11-25
You could try porting it to [Mono Visual Basic.]("http://www.mono-project.com/VisualBasic.NET_support")

If I remember correctly, Dapper (Which I am still using ;), has Mono installed by default, but I don't know about the mono VB compiler.

I also don't know the state that the Windows Forms are in for Mono yet.  Or about the state of the VB compiler itself.

---

