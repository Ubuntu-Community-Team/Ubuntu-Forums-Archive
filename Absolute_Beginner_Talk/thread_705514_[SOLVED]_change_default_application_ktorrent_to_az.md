---
title: "[SOLVED] change default application ktorrent to azureus"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Harisz750 on 2008-02-23
I am new in ubuntu. . .  from firefox i clicked a torrent file from a tracker and chose to automatically open file with ktorrent 2.2.5 and remember this option. my private tracker doesn't support ktorrent so i had to install Azureus 3.0.4.2 but everytime i try to download a torrent file from a tracker it remembers my choice and opens Ktorrent. I unistalled ktorrent but it now does not open anything at all  posting an error saying than helper application does not exist!!!!!  i tried with right click on an already downloaded torrent file and by propreties change to azureus.. but still nothing works...    PLEASE HELP

---

### Post by harold4 on 2008-02-23
I don't use azureus, so not sure where the executable resides.  

When firefox asks to save/open with, choose open with other and navigate to /usr/bin/azureus.  If it's not there, you'll have to point open with other dialog to wherever the azureus executable is.

EDIT: Looks like you need to point to /usr/local/azureus/azureus

As a suggestion, give deluge-torrent a try :)

---

### Post by wolfen69 on 2008-02-23
right click a torrent file and go to properties. then the "open with" tab. just remove ktorrent from the list. if azureus is not on the list, next time you start a torrent file, right click it and choose azureus. next time azureus will be the default. 

as i have tried every torrent client out there, i also have to say give Deluge a try. has worked perfectly for me. this is coming from someone that does bittorrent 24/7. if you need to know how to peerguardian files to work with deluge, PM me and i'll post it here.

---

### Post by Harisz750 on 2008-02-23
the thing is that it firefox does not anymore asks to open/save file....  because i clicked the option to automatically do this for this type of files...  so.... tell me how i can activate this windows again... and then i will choose azureus from the list 
WOLFEN69  i did this.. as i said in the thread... not working!!!!!!!

---

### Post by harold4 on 2008-02-23
Tools > Options > Content tab > Manage button at the bottom > find default action for torrents and change

EDIT: If you're partial to ktorrent, let me know and I'll post my altered .deb.  I removed the inability to mess with private torrents in the original code.

---

### Post by harold4 on 2008-02-23
> **wolfen69 said:**
> right click a torrent file and go to properties. then the "open with" tab. just remove ktorrent from the list. if azureus is not on the list, next time you start a torrent file, right click it and choose azureus. next time azureus will be the default. 

as i have tried every torrent client out there, i also have to say give Deluge a try. has worked perfectly for me. this is coming from someone that does bittorrent 24/7. if you need to know how to peerguardian files to work with deluge, PM me and i'll post it here.

The only major gripe I have with deluge is the lack of "force torrent," like utorrent has.  Minor gripe is the greater memory usage than utorrent.

---

### Post by Harisz750 on 2008-02-23
tools--- options--- content tabs....  please be more spesific as i am new in ubuntu and don;t know what exactly you mean...  where do i find tools--- options etc???  in firefox????  because in tools of firefox does not have all these....  thanks again for your support...

---

### Post by harold4 on 2008-02-23
Open firefox

At the top you should see "File Edit View History Bookmarks TOOLS Help"

Select "Tools" and you should see "Options"  at the bottom.

A window will open, select "Content"

At the bottom of the window you should now see "File types" and a button that says "Manage"

Select the "Manage" button and you'll get yet another window.

In that window, look for .torrent

---

### Post by Harisz750 on 2008-02-23
thanks... that worked fine...

---

### Post by harold4 on 2008-02-24
Mark thread solved in "Thread tools" if your issue has been resolved :)

---

