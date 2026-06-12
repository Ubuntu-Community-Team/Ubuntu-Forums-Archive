---
title: "[SOLVED] Won't shut down"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2008-02-20
Hey you guys, I have an issue that seems like quite a big one. My computer won't shutdown. It reaches the shutting the network connections down and then it just stops. I don't know if it cannot shut them down or what, but it isn't shutting down. Help?

---

### Post by Het Irv on 2008-02-20
That is a known issue with the Network manager applet. Do you have all the latest updates?  If not look into installing another network manager like Wicid

---

### Post by philinux on 2008-02-20
Click the link for known bugs. Hanging shutdown is one of them.

---

### Post by dork5002002 on 2008-02-20
I did some searching and found a few possible answers.
I'm relatively new to Ubuntu so take my advice lightly 

1.You may just need a bios upgrade.
2 You could try to enable bootclean in System>Preferences>BootUp Manager.
3. You could try adding cpi=force cpi=noacpi to you start up options
                        If this works you can add these to the line starting with 'kernel' in you menu.lst file to try 
                        to keep it permanent  


More info about your hardware would be nice.  I found various threads at other places pertaining to this subject, so you could try searching a little bit more on Google.

---

### Post by toasty_ghosty on 2008-02-20
I removed network-manager and installed Wicd. Everything shuts down as it should. At least now. Thanks guys.

---

