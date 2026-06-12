---
title: "xsane error"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by johnlh on 2007-03-21
Hi,
Wasn't sure where to post printer/scanner issues. I'm receiving this "Failed to create file: Permission denied" error when closing xsane.  It pops up 3x before closing.  Nothing needs to be scanned or previewed, an open & close of the app brings it up. I'm using multifunction HP2610xi connected through a router w/ the latest hplip.  It prints & scans fine.  I don't know about faxing from the pc b/c I never do that.  I'm impressed w/ the hplip driver/software - the device manager is fully functional - it never was in XP!  Thank you in advance. :)

---

### Post by Bachstelze on 2007-03-21
AS you can see, using the GUI is generally not thebest way to troubleshoot.. Open a terminal and run

```
sudo apt-get install sane-utils
sane-find-scanner
```

and paste what you get.

---

### Post by johnlh on 2007-03-21
Output in image attachment, sorry about that - not sure how to get in the msg:

---

### Post by Bachstelze on 2007-03-21
Sorry, I guess I misread your post... Try running xsane from a terminal and see if you get more detailed error messages there.

---

### Post by johnlh on 2007-03-21
BTW, I appreciate your help, thank you.  OK, ran xsane through terminal, same result. No err msgs in terminal.  But, I closed it w/ gui. 
There must be a close application key combination in terminal?  If I did close through terminal would the error post in terminal?  
Big "danger" message when attempting to run as root, so I didn't do that.

---

### Post by kolslorr on 2007-03-25
hi, I have the same problem. The workaround is to use root to run xsane.
Type this in the terminal...

sudo xsane

However I do not know whats the cause, appreciate if someone has a proper solution.

*EDIT*

Run this command solves the permission problem.

sudo chmod a+rw /proc/bus/usb/*/*

My guess is something went wrong with the permission when I first installed the brscan2... now everythings good and I am a happy person again.

---

