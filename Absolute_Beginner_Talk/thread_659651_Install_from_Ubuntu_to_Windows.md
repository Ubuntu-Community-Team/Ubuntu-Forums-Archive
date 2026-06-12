---
title: "Install from Ubuntu to Windows?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by steamgear on 2008-01-05
Hi,

I would like to know if I am able to use a ".exe; .msi" installer file native in Windows and execute them in Linux Ubuntu **LIVECD** (7.10, Gutsy Gibbon) and install the files into my Windows part of my Hard drive.

[B]Q1: Is this even possible?
Q1a: If so, what would the necessary procedures be needed to do to perform this action?
Q1b: Would I need any additional software?

Q2: Also, am I able to edit my '/windows/system/' folders in Windows through Linux Ubuntu?[/B]

Regards,
-Johnny

---

### Post by frup on 2008-01-05
Ubuntu 7.10 has NTFS support and with wine you should be able to run some .exe's but it usually works better the other way round, installing from windows and running in wine I believe. take a look at winehq.org to find out more about wine or navigate to the wine specific part of this forum :)

---

### Post by steamgear on 2008-01-05
> **frup said:**
> Ubuntu 7.10 has NTFS support and with wine you should be able to run some .exe's but it usually works better the other way round, installing from windows and running in wine I believe. take a look at winehq.org to find out more about wine or navigate to the wine specific part of this forum :)

Hi frup, 

Thanks for the response, the reason I'm asking if I am able to run .exe or any other installation file is because my current Windows OS is crashed from the bottom up, rendering it useless. I know exactly which file to replace (uxtheme.dll), but, I am unable to enter my Windows desktop without an interface.

Also, am I able to access it even though there is a password protection on it?

---

### Post by PeterJS on 2008-01-05
> **steamgear said:**
> Hi,

I would like to know if I am able to use a ".exe; .msi" installer file native in Windows and execute them in Linux Ubuntu **LIVECD** (7.10, Gutsy Gibbon) and install the files into my Windows part of my Hard drive.

[B]Q1: Is this even possible?
[/B]
Yes, BUT, the files would end up in wine's fake windows environment and need to me manually copied to where ever you want them. The other thing about doing this would be that the registry keys would get written to wine's fake windows registry and those would be far more difficult to extract, and I believe impossible to correctly insert in to the registry of the actual windows system from the live install, and still extremely hard (but possible) if you saved them separately and then added them when booted in to windows.
> 
[B] Q1b: Would I need any additional software?
[/B]The wine compatibly layer, more commonly called just wine.> [B]
Q2: Also, am I able to edit my '/windows/system/' folders in Windows through Linux Ubuntu?
[/B]Yes, this is far easier, bordering on trivial, use the ntfs-config tool to set up writing to disk, point the file browser where you want and off you go.

---

### Post by PeterJS on 2008-01-05
> **steamgear said:**
>  
Also, am I able to access it even though there is a password protection on it?

Is it an NT account password, or a file system encryption password. If it's the former there's no way to enforce that when the system isn't booted (ie a live environment, or mounted under a full ubuntu install), as for the latter to do not believe that the current NTFS driver support encryption.

Edit:

specifically for your problem, if you can get your hands on a vanilla copy of uxtheme.dll dropping it in place from an Ubuntu CD shouldn't be too hard.

---

### Post by steamgear on 2008-01-06
> **PeterJS said:**
> Is it an NT account password, or a file system encryption password. If it's the former there's no way to enforce that when the system isn't booted (ie a live environment, or mounted under a full ubuntu install), as for the latter to do not believe that the current NTFS driver support encryption.

Hi PeterJS,
A much appreciated "Thanks" for your support :)

It would be an NT Account password, and, I guess it would make sense if the Windows OS isn't booted, hehe, shame on me. 
I'm specifically attempting to modify the "UXTheme.dll" system file that enables theme support in the Windows OS user-interface. But, I incorrectly modified it, which rendered my computer "dead" -- meaning, there is nothing to show dialog, text boxes, command buttons, or form loads. 

But, using Linux as my savior, I will modify them with the default UXTheme.dll supplied by [dll-files dot com].

Again, thank you for support!
-Johnny

---

### Post by mathnerd314 on 2008-01-06
Couldn't you just boot Windows from the command line?

...or am I missing something here?

---

### Post by steamgear on 2008-01-06
> **mathnerd314 said:**
> Couldn't you just boot Windows from the command line?

...or am I missing something here?

No no, I can boot into my Windows OS "Fine". It's just a matter of seeing ANYTHING, absolutely no visuals, just a black screen and a cursor. Safe mode does not help either, simply because they both use the UXTheme.dll to set them.

It's more of a "human-to-computer" compatibility rather than anything else. 
This is why I'm going to boot into Linux Ubuntu and fix my system files.

---

### Post by barbedsaber on 2008-01-06
It IS windows, it should be EASY to find a backdoor, can you boot from windows cd's, maybe.

---

