---
title: "Removing Thunderbird completely"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-08-19
I thought I'd removed TB. I've tried all these hints [http://ubuntuforums.org/showthread.php?t=509059](http://ubuntuforums.org/showthread.php?t=509059)  Synaptic and terminal both tell me that it isn't installed, the only .mozilla folders are for Firefox. But I keep getting a little pop-up that tells me the latest version of TB is available, click to upgrade. It's only a slight irritation - but has anyone else had this problem and solved it?

---

### Post by por100pre1 on 2007-08-19
Did you installed the recent Ubuntuzilla .deb package? :-k

---

### Post by nanotube on 2007-08-19
> **freesitebuilder said:**
> I thought I'd removed TB. I've tried all these hints [http://ubuntuforums.org/showthread.php?t=509059](http://ubuntuforums.org/showthread.php?t=509059)  Synaptic and terminal both tell me that it isn't installed, the only .mozilla folders are for Firefox. But I keep getting a little pop-up that tells me the latest version of TB is available, click to upgrade. It's only a slight irritation - but has anyone else had this problem and solved it?

you must have used the ubuntuzilla script. and enabled the automatic update checker.
check your crontab:
```
crontab -l
```
if something about ubuntuzilla is in there, edit your crontab:
```
crontab -e
```
delete those lines, then save and exit.

should take care of that.

you might also want to completely uninstall the ubuntuzilla package (can do that from synaptic)

---

### Post by freesitebuilder on 2007-08-20
If I uninstall Ubuntuzilla, will I still be able to run the latest Firefox?

---

### Post by Aishiko on 2007-08-20
I'd just go and download the firefox 1.5 deb or 2.0 from their website. if all you want is the browser.

---

### Post by e6626550w on 2007-08-20
> **freesitebuilder said:**
> I thought I'd removed TB. I've tried all these hints [http://ubuntuforums.org/showthread.php?t=509059](http://ubuntuforums.org/showthread.php?t=509059)  Synaptic and terminal both tell me that it isn't installed, the only .mozilla folders are for Firefox. But I keep getting a little pop-up that tells me the latest version of TB is available, click to upgrade. It's only a slight irritation - but has anyone else had this problem and solved it?

In your terminal 

```
sudo updatedb
```next 

```
locate thunderbird*
```You'll almost certainly see a ton of references to Tbird. Which one is calling for the updates, I haven't a clue, though. 

I had the same problem when I tried to get rid of open office. I finally did what  I suggested above and then manually went through and deleted all the references to open office. The updates then stopped but none of the remove, purge, etc. terminal commands that I know will get rid of all the files a program installs. Is there is one, I'd love to know it. 

eileen...

---

### Post by philinux on 2007-08-20
> **freesitebuilder said:**
> If I uninstall Ubuntuzilla, will I still be able to run the latest Firefox?

If you read the ubuntuzilla documentation it tells you how to remove TB with a terminal command

ubuntuzilla.py -a remove -p thunderbird

---

### Post by nanotube on 2007-08-20
> **freesitebuilder said:**
> If I uninstall Ubuntuzilla, will I still be able to run the latest Firefox?

ubuntuzilla itself is just the installer - even if you uninstall it, firefox, thunderbird, and/or seamonkey that you installed with it will still remain. ubuntuzilla itself only installs, uninstalls, or checks for updates for mozilla software. 
but it really is an independent piece of software from all those.

---

