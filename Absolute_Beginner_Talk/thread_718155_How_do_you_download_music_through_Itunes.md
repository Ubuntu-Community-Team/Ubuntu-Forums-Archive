---
title: "How do you download music through Itunes?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by bluescreenofdeath on 2008-03-07
I'm learning my way around ubuntu 7.10 and I ran into my first problem. Is there a program that I could run that will allow me to use the newest Itunes program? I was able to use wine to open an older version of itunes but then I had the problem that the itunes could not connect to the store because it was an outdated version. 

I saw this article on it and I would like to know how the guy made it work?

[http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/10/itunes-73-on-linux-with-wine.html)

---

### Post by JoshuaRL on 2008-03-07
Looks like it just worked.  Have you tried using a newer version?

---

### Post by bluescreenofdeath on 2008-03-07
> **JoshuaRL said:**
> Looks like it just worked.  Have you tried using a newer version?

Yes, that was the first thing that I tried but it would hang up in the middle of the install. Yet it never said it needed to force quit. 

 I'm confused about the screen shots that are on the web site, it says wine desktop. I had wine but I'm not sure if that's the same?

---

### Post by JoshuaRL on 2008-03-07
Thats one of the options in the Wine Configuration.

Do you know how to run it from the terminal?  If so, what are the errors?

---

### Post by bluescreenofdeath on 2008-03-07
> **JoshuaRL said:**
> Thats one of the options in the Wine Configuration.

Do you know how to run it from the terminal?  If so, what are the errors?

No I don't know how to run it. Can you show me. Should I try it first with the newest itunes?

---

### Post by JoshuaRL on 2008-03-07
Yeah, why not.

Make sure the iTunes.exe is on your desktop.  Then do:
```

cd ~/Desktop
wine iTunes.exe

```

Just make sure the installer name in the terminal is the same as on the desktop.

---

### Post by bluescreenofdeath on 2008-03-07
> **JoshuaRL said:**
> Yeah, why not.

Make sure the iTunes.exe is on your desktop.  Then do:
```

cd ~/Desktop
wine iTunes.exe

```

Just make sure the installer name in the terminal is the same as on the desktop.


brian@brian-desktop:~/Desktop$ cd ~/Desktop
brian@brian-desktop:~/Desktop$ wine iTunesSetup.exe
wine: creating configuration directory '/home/brian/.wine'...
wine: '/home/brian/.wine' created successfully.
fixme:advapi:LookupAccountNameW (null) L"brian" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"brian" 0x153cb8 0x34f7fc 0x153040 0x34f800 0x34f7f4 - stub
fixme:advapi:SetEntriesInAclA 1 0x7d963cc0 (nil) 0x7d963ce8
fixme:advapi:SetNamedSecurityInfoW L"c:\\windows\\profiles\\brian\\Local Settings\\Application Data\\Apple Computer\\" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 1 0x7d963cc0 (nil) 0x7d963ce8
fixme:advapi:SetNamedSecurityInfoW L"c:\\windows\\profiles\\brian\\Local Settings\\Application Data\\Apple Computer\\QuickTime\\" 1 4 (nil) (nil) (nil) (nil)



Error Message "Install Failed" "This itunes installer requires that your computer is running Windows XP or Windows Vista."

I'm going to try it with a older version in the article.

---

### Post by Bri0 on 2008-03-07
Go into the Wine properties and set Windows Version to XP.

Applications > Wine > Config Wine



Tried the last iTunes version and it didn't work well for me (did install tho).

---

### Post by JoshuaRL on 2008-03-07
Try:
```

wineconfig

```

And set the default version to XP like brio said.

---

### Post by bluescreenofdeath on 2008-03-08
> **Bri0 said:**
> Go into the Wine properties and set Windows Version to XP.

Applications > Wine > Config Wine



Tried the last iTunes version and it didn't work well for me (did install tho).


Hey well what do you know it WORKS! Hurray! I was able to acess the store by songs and play them with hangs or errors. It did say that it didn't load the drivers for burning. But I'm not worried about that yet.

---

### Post by Ecclesia on 2008-03-08
I'm glad you got it to work (I might try it myself just to see what works and what doesn't), but it seems that there are more effective (and ultimately portable) ways of buying music for Linux.  Amazon sells a lot of music that's DRM free, for instance. 

Although, when I used Windows I did sometimes find the itunes store helpful for seeing what was out there and listening to little samples.

---

### Post by blockcipher on 2008-03-08
I've tried all of the above and I am not able to get iTunes installed.  It still says I need to have Windows XP...any other workarounds?  I'm trying to install version 7.6

Thanks!

---

### Post by JoshuaRL on 2008-03-08
> **blockcipher said:**
> I've tried all of the above and I am not able to get iTunes installed.  It still says I need to have Windows XP...any other workarounds?  I'm trying to install version 7.6

Thanks!

Alright, just because installing things via Wine is my new hobby, I tried to install iTunes 7.6 last night.  I'm running 7.10 64bit, with Gnome.  There were a couple steps, and I haven't fully tested it yet.

1).  Make sure you're running the newest version of Wine.  If you need steps for that, I can help there too.

2).  Go to Applications->Wine->Configure Wine.  Then make sure it is running as XP, with OSS for sound, and with Hardware Acceleration as Emulated.  Not sure how important this is, but I've always done that on a new install.  I'll monkey with that tonight and see what I can find.

3).  Download and run with Wine the [richedit 3.0 update.](http://www.hexagora.com/download/support/riched30.exe)  This will install the necessary DLLs to your "C:\\Windows\system32" folder.

4.)  Either right click the installer file and Run With Wine, or run it from the CLI (for error output).  I've noticed there is some black overlay when iTunes first starts running.  Not sure why, but if it bothers you just left-click-and-drag on the desktop like you're trying to highlight files and pull the box over the whole desktop.  It should refresh.  If you have any weird errors, make note of them but try to install again.  On the earlier link it said that sometimes errors might come up but that you should give it another go.

Alright, now for the issues and untested features.  Every time I try to change to Cover Flow it crashes.  iTunes just quits out.  I haven't tried that from the terminal to get the error code, but I will soon.  iTunes mini-store loads, but I haven't tried the full store.  I can set it to search for media on /home, and it will find it.  I haven't tried syncing my iPod, but that is the very next thing on my test list.  I'll report when I find anything out.

Also, from that earlier post and some ad-libbing I figured out you can make iTunes run a little faster by doing the following:

1).  Go to Applications->Wine->Browse C Drive.  Go to "C:\\Programs\iTunes" and copy itunes.exe.  Then go to "C:\\Windows\system32" and paste the file there.  If you don't do this, the following command will fail saying that file isn't there.  I haven't seen any difference in usability after this though.

2).  Open the terminal and paste in:
```

WINEDEBUG=-all wine iTunes.exe

```
That will turn debugging off, allowing it to run a bit faster.

If anyone has any ideas, please post them.  I'm open to testing any features anyone is wondering about;  like buying/downloading, podcasts, video, whatever.

---

