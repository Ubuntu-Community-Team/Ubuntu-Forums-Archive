---
title: "Recovering Windows with Linux"
date: 2011-10-03
forum: Any Other OS
---

### Post by m2xtreme on 2011-10-03
Hi all,

I wanted to share a recent experience I had repairing a Windows install using Linux.  Before I begin, let me be clear that **these results are not typical** and just because I solved this particular Windows error in following manner **doesn't mean it will work for you**.  Lastly, don't ask me for Windows advice, I do not condone the use of Windows.

It all started when my girlfriend's computer at work gave the notorious BSOD error.  This particular error was in regards to a file called

> \SystemRoot\System32\Config\SOFTWAREI decided to do some research and came across this thread on Microsoft's website (I know... linking to Microsoft is bad form, but considering this tutorial is about using a superior operating system to fix a broken Windoze install I think it's okay ;) )

     [http://support.microsoft.com/kb/307545](http://support.microsoft.com/kb/307545)

The support thread recommended I boot into a Windows Recovery Console to fix this error but after reading through I saw the recovery process only involved moving a few files around.  So I decided to put the broken hard drive into my existing Linux desktop and copy the files over the easy way; by dragging and dropping with my Linux file manager!

Long story short, I backed up all the existing files in C:\Windows\System32\Config\ to a temporary folder (just in case) and copied the backup system restore "SOFTWARE" file from the following location: 

> [LEFT][COLOR=#000000][FONT=Segoe UI]C:\System Volume Information\_restore{D86480E3-73EF-47BC-A0EB-A81BE6EE3ED8}\RP1\Snapshot[/FONT][/COLOR][/LEFT]
*The path above is only an approximate path, it was definitely called something different.  I just sorted all the _restore files by date and used the most recent backup from a know good configuration (so the *"SOFTWARE" *file was in  _restore{XXXXXX etc...}*

After that, I booted into Windows and made it to the log in screen, this time with readable characters (not like the Wingdings-esque garbage I was seeing before!).

The only caveat was that every time I tried to log in Windows kept prompting me for a serial number even though the serial number had already been entered.   It wouldn't let me past the log in screen without this annoying prompt :(   Then I remembered that Microsoft likes to lock their software to the hardware of the particular computer it was originally installed on (I assume by MAC address or something...).

So I decided to give the hard drive back to my girlfriend to bring back to work and try booting up in the original computer, hoping my assumptions were correct.  Luckily, when she tried the hard drive it booted up just fine and everything was back to normal.

In closing, I think it's a shame that Microsoft doesn't doesn't recommend some sort of gui recovery process.  Of course, it's not at all surprising that using Linux isn't on their list of recommendations because why would they want to promote their biggest competition?  Especially when considering that Linux is free and is being used to fix Windows... it's not the most flattering of circumstances.  But you'd think at very least Microsoft would have some sort of dumbed down live booting recovery solution with a graphical user interface.  Then again, they would probably charge for it :grin:

Hopefully someone finds this useful/entertaining...

---

### Post by msx728 on 2011-10-03
Micro$oft is a shame by itself...

---

### Post by m2xtreme on 2011-10-03
> **msx728 said:**
> Micro$oft is a shame by itself...

Lol, that didn't take long...

:lolflag:

---

