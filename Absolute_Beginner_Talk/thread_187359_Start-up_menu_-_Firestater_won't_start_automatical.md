---
title: "Start-up menu - Firestater won't start automatically."
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by u.b.u.n.t.u on 2006-06-02
Hi,

Firestarter won't start when I log into ubuntu. I have checked the settings but am obviously missing something. I want Firestarter to run everytime I start ubuntu. How do I enable this?

Thanks.

---

### Post by mynimal on 2006-06-02
Have you tried going to System -> Preferences -> Sessions and going over to the Startup Programs tab?

---

### Post by mlind on 2006-06-02
Firestarter is IPTABLES initilization scipt & IPTABLES gui front-end. It's running if
*sudo iptables -L* shows configured firewall rules or *sudo /etc/init.d/firestater status* says "Firestarter is running.."

---

### Post by cstudent on 2006-06-02
Firestarter runs in the background. It should be running when you log on. Check the system processes for it to see for sure. Firestarter is not designed to run as a GUI all the time, but it can be. Go to the Firestater website and check their FAQ documentation on how to do it. The GUI is really there to make your settings. Once you have everything the way you want there is no real need for it to remain open. If you want to check logs you can always go to the menu and open it back up. If you prefer to have it open and setting in the system tray the FAQ has a section on how to configure that.


.

---

### Post by u.b.u.n.t.u on 2006-06-02
Thanks everyone!

For anyone doing a search and getting here, nothing worse than a solution but no details, so here goes.

Instructions at this url:
"http://www.fs-security.com/docs/faq.php"

"Launching Firestarter minimized to the tray on login

Having performed the above configuration of permissions, the system can further be set up to load Firestarter when you log in with your regular user account. Firestarter will in that case load directly into the system tray without user intervention, after which the main interface can be accessed by clicking the tray icon.

Using GNOME:
The GNOME sessions manager

Open up your GNOME menu, select Preferences followed by Sessions. Switch to the Startup programs tab, pictured right.

Click Add and enter
sudo firestarter --start-hidden
as the startup command. Click OK and you're done.

To stop Firestarter from loading on login, simply remove its entry from the startup programs listing. "

There is a screenshot there and further down information to test your firewall.

;)

---

