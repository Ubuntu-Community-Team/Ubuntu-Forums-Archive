---
title: "The CUPS server could not be contacted, bad dead"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by PaulHuffman on 2007-10-11
I was trying to follow [these instructions]("http://ubuntuforums.org/showthread.php?t=255490") to install a driver for my Konica Minolta 2430DL but I've really crashed the printing system this time.  Now if I go to System->Admin->Printing tells me the CUPS server could not be contacted. I tried to kick CUPS in the *** with a sudo /etc/init.d/cupsys start command, but I get the following in the terminal window: /usr/sbin/cupsd: symbol lookup error: /usr/sbin/cupsd: undefined symbol: _httpReadGNUTLS Looks like I have a bad symbol or line in the printer files.

I've tried to go to Applications>Add Remove and cycle Print Jobs (CUPS), but still can't get CUPS to start.  At this point, do I dare go to Synatic Package manager and remove gnome-cups-manager, and reinstall?

---

### Post by swisscow on 2007-10-12
This happened to me for no apparant reason either. I reinstalled from synaptic, that did the job.

---

### Post by PaulHuffman on 2007-10-12
I went ahead and uninstalled/installed gnome-cups-manager with Synaptic Package manager. That wasn't so bad.  But I still have the same error.   There must be more of the print system I need to reinstall.

Update - I reinstalled everything I saw in Synaptic Package manager that looked like it had something to do with CUPS.  Now I'm back printing, at least to my HP4050, and the Konica 2400 has disappeared. I wonder if I should try the long procedure to install the Konica 2430DL or just be satisfied with the B/W HP4050.   

CUPS only wants to print to the manual feed tray (tray 1) rather than the default tray 2 despite all I can figure out to do with the printer properties.

---

