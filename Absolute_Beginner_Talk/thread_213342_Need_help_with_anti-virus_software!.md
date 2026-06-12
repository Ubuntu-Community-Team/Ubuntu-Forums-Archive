---
title: "Need help with anti-virus software!"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by sbu on 2006-07-11
Good day all!
I have installed the Aegis anti virus software using the Synaptic package manager.After installing it I was told that I can access it from Accessories(Accessories-->Aegis anti virus software).
But when I go to accessories I dont see it there and When I return to the synaptic package manager, it is checked which implies that it is already installed.

My question is:Does this indicate that I didnt install the software? How do I use or access this anti virus?

---

### Post by Kobalt on 2006-07-11
Try pressing Alt+F2 and the enter the name of your app...

---

### Post by sbu on 2006-07-11
Qouting:'Try ALT+F2 and enter your applications name'

I get the following error:
'Cannot display location 'file://Aegis anti-virus'

Details: There is no default action associated with this location.'

---

### Post by Kobalt on 2006-07-11
Only enter "aegis" for instance...

---

### Post by sbu on 2006-07-11
I still get the same error!

---

### Post by Kobalt on 2006-07-11
What were the names of the packages you installed with synaptic ?

---

### Post by sbu on 2006-07-11
Aegis anti-virus

---

### Post by Kobalt on 2006-07-11
It's written exactly this in synaptic ? I mean the name of the package, not the description in the text field below the list of package...

---

### Post by mcduck on 2006-07-11
also, you could try to run 'killall gnome-panel' to refresh your menu..

---

### Post by sbu on 2006-07-11
Sorry for the delay!
My system seems to be experiencing problems,I cant open the synaptic package manager.
So I'll try and resolve the problem first.I ll post another thread later!

---

### Post by slimdog360 on 2006-07-11
open synaptic find the anti virus you installed then right click on it. Then go to properties and select the 'installed files' tab. This will show you where the files are installed, in particulaar look for the path 'usr/bin/aegis' or something similar. What ever it says in the part where I wrote aegis (because it will be different to aegis) type that into a terminal.

edit: or first try typing
```
aegis-virus-scanner
```
into a terminal

but to b honest you dont need a virus scanner. I was the same when I started but it was to much of a hassel so I never bothered, low and behold Ive never had a virus or anything like that in linux.

---

### Post by kilis on 2006-07-11
Try [avast!]("http://www.avast.com") :)

---

### Post by T700 on 2006-07-11
Why are you running an antivirus program on Linux?  Unless you are running a mail *server* that relays mail to Windows machines, it is totally unneeded.  (And then it is only needed to protect the Windows boxes.)

Paul

---

