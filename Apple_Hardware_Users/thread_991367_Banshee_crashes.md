---
title: "Banshee crashes"
date: 2008-11-23
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-11-23
I can't use Banshee after upgrading to Intrepid on my TiBook G4. Evertime I try to run it I get an error:
```
banshee An unhandled exception was thrown: SQL logic error or missing database
```

And a whole lot more. I've googled and i get suggestions to delete the banshe files in ~/.config and ~/.gconf as the symptom is of a corrupted sqlite database. this doesn't work as the files get recreated and the same error happens.

The full error:
```
An unhandled exception was thrown: SQL logic error or missing database

  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
Banshee.Core (1.2.1.19110)
Banshee.Services (1.2.1.19112)
Banshee.ThickClient (1.2.1.19117)
Nereid (1.2.1.19119)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.25-2-powerpc ppc unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] 
Exception has been thrown by the target of an invocation.

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

.NET Version: 2.0.50727.42
OS Version: Unix 2.6.25.2

Assembly Version Information:

Migo (1.2.1.19106)
Banshee.Podcasting (1.2.1.19134)
Lastfm (1.2.1.19109)
Banshee.Lastfm (1.2.1.19129)
notify-sharp (0.4.0.0)
Banshee.NotificationArea (1.2.1.19132)
Banshee.CoverArt (1.2.1.19125)
Banshee.Bookmarks (1.2.1.19124)
Banshee.MultimediaKeys (1.2.1.19131)
Banshee.Daap (1.2.1.19126)
Banshee.AudioCd (1.2.1.19123)
pango-sharp (2.12.0.0)
Mono.Cairo (2.0.0.0)
Banshee.Widgets (1.2.1.19114)
Banshee.Dap.Ipod (1.2.1.19120)
Banshee.Dap (1.2.1.19120)
Banshee.Hal (1.2.1.19135)
Banshee.Unix (1.2.1.19137)
Banshee.GStreamer (1.2.1.19137)
gconf-sharp (2.20.0.0)
Banshee.Gnome (1.2.1.19136)
Banshee.NowPlaying (1.2.1.19133)
System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.2.1.19104)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.2.1.19102)
System (2.0.0.0)
glib-sharp (2.12.0.0)
gdk-sharp (2.12.0.0)
Banshee.Core (1.2.1.19110)
Banshee.Services (1.2.1.19112)
Banshee.ThickClient (1.2.1.19117)
Nereid (1.2.1.19119)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.25-2-powerpc ppc unknown GNU/Linux

Disribution Information:

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
[/etc/debian_version]
lenny/sid

```

Any suggestions?

---

### Post by ubuntubrian on 2008-11-23
I also ran banshee in a terminal:
```
:~$ banshee -dbg
[Info  15:43:16.767] Running Banshee 1.2.1
[Info  15:43:22.334] All services are started 5.018567s
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> Mono.Data.SqliteClient.SqliteExecutionException: SQL logic error or missing database
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt, System.Int32& cols, System.IntPtr& pazValue, System.IntPtr& pazColName) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteStatement (IntPtr pStmt) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 
  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00000] --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] 

```

Maybe a Mono issue?

---

### Post by raxip on 2009-03-20
I was having this problem myself.  To fix this problem, I did the following:

 > mv ~/.config/banshee-1 ~/.config/banshee-1.bak
 > rm -rf ~/.cache/.banshee-1

Deleting .cache/banshee-1 just by itself doesn't appear to do much of anything at all.  I just did it because I figured (just a guess) that it wouldn't hurt.

The real part of the fix is renaming .config/banshee-1.

The problem with this fix is that all of your settings and library definitions will go away.  This means you'll have to re-import everything back into Banshee (including artwork).

---

### Post by ubuntubrian on 2009-03-20
That works-thanks!

---

### Post by carlf on 2009-03-28
carl@carl-laptop:~$ > mv ~/.config/banshee-1 ~/.config/banshee-1.bak
bash: /home/carl/.config/banshee-1: is a directory
carl@carl-laptop:~$ > rm -rf ~/.cache/.banshee-1
bash: -rf: command not found
what am I doing wrong?

---

### Post by matrixblue on 2009-05-02
> **carlf said:**
> carl@carl-laptop:~$ > mv ~/.config/banshee-1 ~/.config/banshee-1.bak
bash: /home/carl/.config/banshee-1: is a directory
carl@carl-laptop:~$ > rm -rf ~/.cache/.banshee-1
bash: -rf: command not found
what am I doing wrong?

I had the same problem so I did

cp ~/.config/banshee-1 ~/.config/banshee-1.bak

then
rm -rf ~/.config/banshee-1 ~/.config/banshee-1.bak

It's the same thing (basically) but with two commands

---

### Post by Machiavelli on 2009-08-01
> **matrixblue said:**
> I had the same problem so I did

cp ~/.config/banshee-1 ~/.config/banshee-1.bak

then
rm -rf ~/.config/banshee-1 ~/.config/banshee-1.bak

It's the same thing (basically) but with two commands

Thanks, this did the trick.

---

### Post by directhex on 2009-08-01
> **Machiavelli said:**
> Thanks, this did the trick.

... why back up the config, then immediately delete the backup?

---

### Post by matrixblue on 2009-08-01
> **directhex said:**
> ... why back up the config, then immediately delete the backup?

That's a typo. The second command should read 

rm -rf ~/.config/banshee-1

---

### Post by heartsbane on 2009-08-31
you could just:

```
cd ~/.config/banshee-1
sqlite3 banshee.db ".dump" > dump
mv banshee.db banshee.db.backup
cat dump | sqlite3 banshee.db
```

That will attempt to rebuild your DB. But then again that is just my $.02 for what it is worth.

---

### Post by benzs_s on 2009-09-18
> **heartsbane said:**
> you could just:

```
cd ~/.config/banshee-1
sqlite3 banshee.db ".dump" > dump
mv banshee.db banshee.db.backup
cat dump | sqlite3 banshee.db
```

That will attempt to rebuild your DB. But then again that is just my $.02 for what it is worth.

This worked a treat, thanks!

---

### Post by JoshuaRL on 2009-10-17
> **heartsbane said:**
> you could just:

```
cd ~/.config/banshee-1
sqlite3 banshee.db ".dump" > dump
mv banshee.db banshee.db.backup
cat dump | sqlite3 banshee.db
```

That will attempt to rebuild your DB. But then again that is just my $.02 for what it is worth.

That worked for me too.  And no need to delete my library either.  Thanks again, this has happened to me twice now and I finally have a way to fix it.  Nothing more annoying than being forced to used amaroK to copy music to my iPod when Banshee works perfectly well.

---

### Post by antoniogarciaiii on 2010-06-18
The delete config idea got banshee to stop crashing after playing a song.

Thank you.

---

### Post by jonjermey on 2010-09-18
I had the same problem -- I am playing music files from an external HDD and after this disk lost its mount point Banshee began crashing when I tried to delete the spurious file names from the library. Thank you!

---

### Post by pbhill on 2010-09-25
I tried this fix. It works once, but crashes when attempting to start Banshee next time.  ??
(The problem is only with Banshee 1.7.6, I can use 1.6 from the repositories with no problem.)

---

### Post by Shadowfire on 2011-05-09
I wanted to offer this up for a fix as it is documented.

[https://bugs.launchpad.net/banshee/+bug/668725](https://bugs.launchpad.net/banshee/+bug/668725)

banshee crash on start

    Banshee
    Bugs
    Bug #668725

As indicated in the upstream bug, you can work around the issue by creating a Podcasts folder in your home folder (mkdir ~/Podcasts).
Banshee should then start without crashing.

---

### Post by pbhill on 2011-05-10
> **Shadowfire said:**
> I wanted to offer this up for a fix as it is documented.

[https://bugs.launchpad.net/banshee/+bug/668725](https://bugs.launchpad.net/banshee/+bug/668725)

banshee crash on start

    Banshee
    Bugs
    Bug #668725

As indicated in the upstream bug, you can work around the issue by creating a Podcasts folder in your home folder (mkdir ~/Podcasts).
Banshee should then start without crashing.

I have a Podcasts folder, still have problem. Exaile works OK.

---

