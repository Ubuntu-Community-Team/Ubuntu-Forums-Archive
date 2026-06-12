---
title: "[SOLVED] swiftweasel and firefox issue"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by reefsrt4 on 2008-01-04
When I launch swiftweasel or firefox, it does not open to my home page, but opens with the following in the address bar:

[http://0/](http://0/)



What causes this and how do I eliminate it?

---

### Post by RomeReactor on 2008-01-04
Hi. Is your homepage set up in Firefox's preferences?

---

### Post by reefsrt4 on 2008-01-04
yes, Google is currently set as the homepage.

Once it initially opens up as I described, I can hit the home button and the homepage will then open up.  It is just when I launch the program......either swiftweasel or firefox......that weird address location is set and the display area shows:


Unable to connect
      
        
        

          

Swiftweasel can't establish a connection to the server at 0.

---

### Post by RomeReactor on 2008-01-04
Try removing the .mozilla folder in your home directory; if you want to backup your bookmarks first, run:
```
cp ~/.mozilla/firefox/*.default/bookmarks.html ~/
```
then, to remove the folder, close Firefox and run:
```
rm -R ~/.mozilla
```
next open Firefox again (so the folder gets recreated), close it again, and recover your bookmarks:
```
cp ~/bookmarks.html ~/.mozilla/firefox/*.default
```

Then, open Firefox again and see if it still behaves the same.

---

### Post by reefsrt4 on 2008-01-04
still opens the same way.  the recovery of the bookmarks didn't work though.

copied that backup into the remade .mozilla folder.  closed again, reopened, but the same default bookmarks were the only ones there.  Those I can regenerate, in time, not sure what is forcing the browser to open as it does....

---

### Post by reefsrt4 on 2008-01-04
disregard the lost bookmarks.  I simply imported them from the backup location and that worked.

---

### Post by RomeReactor on 2008-01-04
Did you install Kiba Dock recently, and if so, are you launching Firefox from there? Right click on the Firefox launcher, select "Properties", go to the "Launcher" tab and change **firefox 0** to **firefox %u**.

---

### Post by reefsrt4 on 2008-01-04
> **RomeReactor said:**
> Did you install Kiba Dock recently, and if so, are you launching Firefox from there? Right click on the Firefox launcher, select "Properties", go to the "Launcher" tab and change **firefox 0** to **firefox %u**.

Yes, I did recently install Kiba Dock.  I made the change to both the Firefox and Swiftweasel launchers and that fixed it.  Thanks again.


What is %u and why did this resolve it?

---

### Post by RomeReactor on 2008-01-04
The command **firefox 0** was telling Firefox to open the address "0"; the **%u** is meant to be substituted for a single URL (in this case, your home page).

You can tell Firefox to open an address from the terminal; for example:
```
firefox opera.com
```

---

### Post by reefsrt4 on 2008-01-04
Excellent!!

Thanks for your help, as always.

---

