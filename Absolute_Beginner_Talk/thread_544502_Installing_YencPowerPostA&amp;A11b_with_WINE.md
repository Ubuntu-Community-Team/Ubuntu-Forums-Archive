---
title: "Installing YencPowerPostA&amp;A11b with WINE"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-06
If you want to post Binaries then you can use PowerPost-A&A with the aid of WINE. [B](CREDIT to K @ Slyck for this )

[IMG]http://i9.tinypic.com/6cxis9g.jpg[/IMG]


[/B]
Firstly, **use this older version of WINE** - it's a DEB file, so just 'double-click' to install and ignore the message about using the latest build.

```


http://ge.archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.22-0ubuntu3_i386.deb


```

Then grab **PowerPost-A&A**

```


http://powerpost.free.fr/files/YencPowerPostA&A11b.zip


```

Now from your Windows PC you need to grab 2 files and copy them into your WINE directory:

**From Windows/System32**

[B]mfc42.dll  
msvcrt.dll[/B]

Once you have those files you need to go to your **HOME folder**. Press **CTRL+H ** (show hidden files) and you should now see the **WINE** folder.

Now browse to:

**WINE / Drive C / WINDOWS / SYSTEM 32**

then just copy and paste the 2 files into this folder.

[IMG]http://i11.tinypic.com/4xxbhnt.jpg[/IMG]


Finally, extract the PowerPost folder and then find the *.EXE file to run - select it, right click and then select 'Open With WINE'

---

### Post by bluebyt on 2008-03-09
Sorry to bring up a old tread, but Yencpower does'nt work for me and I really need this program!

Here the error message:
[http://pastebin.ca/935622]("http://pastebin.ca/935622")

---

### Post by bluebyt on 2008-03-12
I got the answer at wine forum:

Quote:
wine: Call from 0x405c69 to unimplemented function MFC42.DLL.6625, aborting

You got too old version of that dll (mfc42.dll). Get a newer one.

Or, better yet, get a fresh copy straight from Microsoft with the command
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks vcrun6

You might need to remove your ~/.wine directory to clear
out any old dlls that your or your apps have installed first.
- Dan
Back to top

---

### Post by brewstah on 2008-04-20
> **bluebyt said:**
> I got the answer at wine forum:
get a fresh copy straight from Microsoft with the command
wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
sh winetricks vcrun6

You might need to remove your ~/.wine directory to clear
out any old dlls that your or your apps have installed first.


This worked perfectly for me, bluebyt.  Before this all I was able to get from PP-A&A was the little initial splash screen on both Dapper Drake x86 and Hardy Heron x86_64.  After running that script PP-A&A came up perfectly and I was able to configure and test it.  Excellent. :)

---

