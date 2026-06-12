---
title: "can't open simple win app (simple exe)"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by TheLions on 2007-12-15
i can't run simple application (for calculation impedance and currents) through WINE, but i can run all other app like Winrar, winamp etc.

when i click it it just does nothing!

here is the application look:

[IMG]http://www.fer2.net/imagehosting/4037475fbe1a3185f.png[/IMG]

here is the application:
[http://rapidshare.com/files/76802414/OE-4.exe.html](http://rapidshare.com/files/76802414/OE-4.exe.html)

some advice would be great!:(

---

### Post by aktiwers on 2007-12-15
What does that app do? Is it some kind of economic calculator?
Have you checked if there is any native apps that does the same?

Its always best to use apps that run native on linux. Like Winrar you can install that on linux.

---

### Post by SunnyRabbiera on 2007-12-15
well do keep in mind that not all apps will work under wine...
remember: wine can only do so much, and certain apps can only work on winxp

---

### Post by TheLions on 2007-12-15
some student created this app, purpose of this app is to check my homework from electronics.

It calculate power for 3 resistors!

---

### Post by SunnyRabbiera on 2007-12-15
> **TheLions said:**
> some student created this app, purpose of this app is to check my homework from electronics.

It calculate power for 3 resistors!

they probably coded it for XP only, if you know this student give em a whap for me :P

---

### Post by TheLions on 2007-12-15
i asked hip about that app and he said that i need .NET Framework 2.0 to work!

how to install that in wine???

[IMG]http://www.fer2.net/images/smilies/help.gif[/IMG] [IMG]http://www.fer2.net/images/smilies/help.gif[/IMG] [IMG]http://www.fer2.net/images/smilies/help.gif[/IMG]

---

### Post by SunnyRabbiera on 2007-12-16
> **TheLions said:**
> i asked hip about that app and he said that i need .NET Framework 2.0 to work!

how to install that in wine???

[IMG]http://www.fer2.net/images/smilies/help.gif[/IMG] [IMG]http://www.fer2.net/images/smilies/help.gif[/IMG] [IMG]http://www.fer2.net/images/smilies/help.gif[/IMG]

I dont think we have it...
just tell the guy to make it not rely on the .net framework...

---

### Post by pjones0404 on 2007-12-16
you could also try virtual box. 

i dont know if it is that important to you but if u have to have it that should work.

---

### Post by chunderbunny on 2007-12-16
If it's a pure .net app then you might be able to run using mono instead of wine (mono is the Linux reimplementation of the .net framework). 

You will need to install the mono and libmono-winforms2.0-cil packages (they're both in the the Ubuntu repositories). 

Then from the terminal cd to the directory with the .exe and run "mono whatever.exe".

---

### Post by Whiffle on 2007-12-16
So I just ran it in a terminal, and it says:

```

fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
install the Windows version of Mono to run .NET executables

```

So I did, and I got:
```

wine OE-4.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for <Module> ---> System.DllNotFoundException: msvcm80.dll
  at (wrapper managed-to-native) <Module>:<CrtImplementationDetails>.ThrowModuleLoadException (string,System.Exception)
  at <Module>.<CrtImplementationDetails>.LanguageSupport.Initialize (<CrtImplementationDetails>.LanguageSupport* ) [0x00000]
  at <Module>..cctor () [0x00000] --- End of inner exception stack trace ---

```
so I downloaded 
msvcm80.dll, put it in the same directory, and got some more dll not found messages.  It seems that I'm missing a pile of dll's.

Hmm.

---

### Post by h4mx0r on 2008-04-08
google - .net framework appdb
blahblah nice desktop pics

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20 

Success!

return 0;

---

### Post by TeraDyne on 2008-04-08
> **h4mx0r said:**
> google - .net framework appdb
blahblah nice desktop pics

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks corefonts dotnet20 

Success!

return 0;

Oh, thanks for posting that. I was about to come looking for a way to run a couple of old apps. This should work really well.

---

