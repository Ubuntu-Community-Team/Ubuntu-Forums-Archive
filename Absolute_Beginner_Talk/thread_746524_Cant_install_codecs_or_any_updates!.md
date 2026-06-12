---
title: "Cant install codecs or any updates!"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by Cebonet on 2008-04-05
Hey I`m a newbie.

I have two computers (one laptop) containing ubuntu.

in one of the computers, i'll tried to play a mp3 file and ubuntu sad "Search for suitable codec?" I sad yes, and a list of codecs came, I installed the first one, SMOOTHLY and NICE, it worked.

But.

My laptop searchs for codecs too, and it finds the codecs, but when I try to select(check), 
a massage appears:

"[I]Confirm installation of restricted software

The use of this software may be restricted in some countries. You must verify that one of the following is true:

• These restrictions do not apply in your country of legal residence
• You have permission to use this software (for  example, a patent license)
• You are using this software for research purposes only[/I]"

I do press confirm. but now instead of installing it says:"The list of applications is not availabe" so it sends me back to the list.

Sorry my bad english.

---

### Post by GregRC on 2008-04-05
I believe it grabs the codecs from a server. Check your network?

---

### Post by lswest on 2008-04-05
is your laptop connected to internet at the time? it's required to install the codecs.

---

### Post by Cebonet on 2008-04-05
yes it is connected. I tried both the lan and the wireless.

---

### Post by szymon_g on 2008-04-05
show your 

/etc/apt/sources.list

:P

---

### Post by mali2297 on 2008-04-05
Go to **System -> Administration -> Software Sources** and check that you have the **multiverse** repository enabled.

---

### Post by JoshuaRL on 2008-04-05
mali2297 is right, make sure you have everything in there checkmarked except for the CD and source code.

Then go to System->Administration->Update Manager and install all the updates.

After that, go to Applications->Add/Remove Applications and search for "restricted".  The package you want is labeled "Ubuntu Restricted Extras".  Install that and your problems should be solved.

---

