---
title: "Noob needs help with errors in /var/log/messages"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by rustyfx on 2006-02-28
First things first - Ubuntu is amazing to me.  My very first brush with Linux was yesterday.  All of the forums and previous postings have brought me a long way.  I have Breezy working on my Acer laptop - and I'm connecting to the internet using the built in wireless.  Thanks to all of you who make this possible!!!  :KS

There is something that is bothering me at this point.  When I look at the tail end of /var/log/messages, I'm getting some errors.  They keep coming like the rain in Seattle.  Here's the direct info:

[I][INDENT]rrust@rusty1:~$ tail -n 10 /var/log/messages
Feb 28 18:59:05 localhost kernel: [4313052.468000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node cbed7c60), AE_NOT_FOUND
Feb 28 18:59:35 localhost kernel: [4313082.472000]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
Feb 28 18:59:35 localhost kernel: [4313082.472000] search_node cbed7d60 start_node cbed7d60 return_node 00000000
Feb 28 18:59:35 localhost kernel: [4313082.472000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node cbed7c60), AE_NOT_FOUND
Feb 28 19:00:05 localhost kernel: [4313112.477000]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
Feb 28 19:00:05 localhost kernel: [4313112.477000] search_node cbed7d60 start_node cbed7d60 return_node 00000000
Feb 28 19:00:05 localhost kernel: [4313112.477000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node cbed7c60), AE_NOT_FOUND
Feb 28 19:00:35 localhost kernel: [4313142.483000]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
Feb 28 19:00:35 localhost kernel: [4313142.483000] search_node cbed7d60 start_node cbed7d60 return_node 00000000
Feb 28 19:00:35 localhost kernel: [4313142.483000]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node cbed7c60), AE_NOT_FOUND
[/INDENT][/I]

I'm wondering if I've somehow messed something in the system up in my quest to get wireless working.

Thanks a whole bunch!!!
Robert

---

### Post by Pragmatist on 2006-02-28
Well your not alone :-D   Check these out if you haven't already: 
[http://ubuntuforums.org/showthread.php?t=29799&page=3](http://ubuntuforums.org/showthread.php?t=29799&page=3)
[http://ubuntuforums.org/search.php?searchid=4065636](http://ubuntuforums.org/search.php?searchid=4065636)
[http://lists.naos.co.nz/pipermail/wellylug/2005-October/013754.html](http://lists.naos.co.nz/pipermail/wellylug/2005-October/013754.html)

---

### Post by rustyfx on 2006-03-02
Thanks a bunch for the pointers there.

It does seem that this is a power supply/battery issue on the Acer notebook.  I tried to address the problem by installing the KDE desktop.  It seems that some have had success with this route.  However, it did not help my situation.

In my case, the system always says that the battery is not present, and it is running on AC power.  It runs just fine on the battery, I just don't get to have a warning before it dies.

Thanks again.

---

