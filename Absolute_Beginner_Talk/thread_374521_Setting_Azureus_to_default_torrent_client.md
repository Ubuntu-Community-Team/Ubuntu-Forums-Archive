---
title: "Setting Azureus to default torrent client?"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by catsmasher on 2007-03-02
I want to use Azureus instead of bittorrent. How do I add it in Firefox? When I click on a torrent, it DL manager asks to open or save (of course), with open, default is bittorrent. Well, that proggy is terrible. I want to use Azureus. Also, when I open Azureus, it seems to minimize and I cannot figure out how to bring the window back up. All help greatly appreciated.

---

### Post by tsanoff on 2007-03-02
Download a torrent file to your desktop or where-ever ,then right click on the file, select Properties, and then hit the open with tab, select azureus, click close and TA-DA!!! worked for me.

Cheers mate

---

### Post by xpod on 2007-03-02
Or just choose "other" instead of the bittorrent option whilst in the download manager and navigate to /opt/azureus or wherever else you have the executable and select that.:) 

If azureus is somehow opening minimized you should still be able to right click it`s icon and "show azureus"....not 100% sure what you mean there though?
If you dont actually have have a windows list displaying  open applications in any of your panels try right clicking on a panel and "add to panel" then adding the "windows list" or "windows selector".

---

### Post by catsmasher on 2007-03-02
That's just it, there is no icon. I can see it open, then it just disappears. I can see the net activity and the file downloads, but where is Azureus? How do I enable the icon in the tray?

---

### Post by catsmasher on 2007-03-02
So no idea why Azureus is disappearing? Why I have no tray icons?

---

### Post by muguwmp67 on 2007-03-02
I think the system tray is supposed to be enabled by default, but try this:

[LIST=1]
[*]Open Azureus.  
[*]Go to tools->Options
[*]Select the interface tab
[*]Check off 'Enable system tray' (you might want to also check off the close to system tray, and minimize to system tray options)
[*]Go to File->Restart Azureus to enable the tray
[/LIST]

---

### Post by catsmasher on 2007-03-02
Can't get that far. As soon as I open it, it disappears. I think I will try to uninstall it and start from scratch.

---

### Post by catsmasher on 2007-03-02
No luck.

---

### Post by omrsafetyo on 2007-03-02
I have a similar problem with the default client (bittorent) - its not in the applications menu; and it doesn't seem to run in the system tray.  Therefore, I have no idea how to launch it.  Of course - I can click a link to a torrent, and that will download the file, opening it with the selected client - but my problem is, say that I am downloading a large file - if I need to reboot my computer for some reason, when I log back in, I have no way of resuming my download - it seems lost forever.  How do I launch the GUI interface for the default bittorent??

I have a work-around - of course, I installed bittornado - and that does show up in the application menu, and I think it will work just fine (though I have yet to use it).  I just hate not figuring things out - so I would really like to find out how to run the default torrent - besides, I have a half-finished 4Gig download that I don't particularly want to start over.

---

### Post by muguwmp67 on 2007-03-02
I had a bunch of problems getting azureus to work the first time I installed it.

I installed from the repositories, and could only get it to work if I ran it from the command line with sudo.

You might want to uninstall the repository version and try installing it through [automatix]("http://www.getautomatix.com/")

You can also install the package from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)
It take a little more thought to configure it though.

---

