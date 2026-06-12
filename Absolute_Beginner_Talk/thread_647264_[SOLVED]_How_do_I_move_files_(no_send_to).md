---
title: "[SOLVED] How do I move files? (no send to?)"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by alx010 on 2007-12-22
IThe biggest problem I'm having with migrating to Ubuntu (Studio 7.10), is that I can't figure out how to move files from one folder to another without copying & pasting. When I right click & choose 'send to' I get an error that says "Could not load any plugins, please verify your installation". 
I've tried reinstalling Nautilus, & the extra plugins, but still no luck. Any advice at all? 
Thanks

---

### Post by vishzilla on 2007-12-22
What about Cut and Paste?

---

### Post by Josh1 on 2007-12-22
> **alx010 said:**
> IThe biggest problem I'm having with migrating to Ubuntu (Studio 7.10), is that I can't figure out how to move files from one folder to another without copying & pasting. When I right click & choose 'send to' I get an error that says "Could not load any plugins, please verify your installation". 
I've tried reinstalling Nautilus, & the extra plugins, but still no luck. Any advice at all? 
Thanks

GUI:
CTRL+C (Copy), CTRL+V (paste) same as WIndows.

Command line:
```
cp home.txt ~/new
```

---

### Post by alx010 on 2007-12-22
Thanks, but I'm already doing the copy/cut & paste method, & it's a pretty slow way of moving files. I'm used to just right clicking & sending to in XP. I guess thats not possible in Ubuntu?

---

### Post by JillSwift on 2007-12-22
"Send To..." in Nautilus (the file browser in Ubuntu) is for sending a file to someone via e-mail.

What do you usually "send to" when you do in Windows? There's probably a way to get it set up with Nautilus, since it's easily extensible.

---

### Post by hyper_ch on 2007-12-22
usind midnight commander in the terminal

---

### Post by hums07 on 2007-12-22
I usually open two file browsers (e.g. nautilus), one for source folder the other for target folder. Then I drag and drop. I do the same in Windows, open two explorers. It is quicker way than using Send To which limits the number of target folders.

---

### Post by Pumalite on 2007-12-22
[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by insane_alien on 2007-12-22
drag and drop when i don't use the commandline.

---

### Post by chuck79 on 2007-12-22
Use KDE ;)

---

### Post by alx010 on 2007-12-22
Ok, in XP, you simply right click an item, choose send to, & then choose where you want to send. 
[http://www.oreillynet.com/pub/a/network/excerpt/winxphacks_chap1/index1.html](http://www.oreillynet.com/pub/a/network/excerpt/winxphacks_chap1/index1.html)
explains the process & ways to customize it.
I guess until I have time to learn scripts, (which I don't have) I'll be booting into Windows when I need to manage my files.

---

### Post by hyper_ch on 2007-12-22
or use konqueror... it has multi-pane capabilities

I think XP makes it more complicated... I prefer multi-pane ;)

---

### Post by alx010 on 2007-12-22
I was just doing some reading on Konqueror. In order to install it, will I need to uninstall Nautilis? Or for that matter, switch from Gnome to KDE? 
Thanks

---

### Post by webdr on 2007-12-22
This works just like in MS WIN...

[LIST=1]
[*]Drag the files from location to location...
[*]Hold down the shift key while releasing the dragged items to 'Move' the item(s)
[/LIST]

To copy rather than move hold down the CTRL key upon releasing the item(s).
-Mark Williams

---

### Post by hyper_ch on 2007-12-22
you can just install konqueror... no need to uninstall nautilus or Gnome.....

Once installed, right-click the bottom bar and select "split horizontally" or "split vertically" --> you can then independentaly browse with those two (or even more) windows and copy/move among them.

---

### Post by MrKlean on 2007-12-22
A couple of ways ; )   In Nautilus..drag the files where you want it....press alt....and select move ....or use gnome-commander (install from synaptic) a 2 pane file manager..1 pane is your from.. the 2nd is your to.....highlite the file...press F6 ..and move it...  if you don't have permissions..run sudo gnome-commander--and do what you want...BUT...BE CAREFUL... you will be able to delete or move anything !!

---

### Post by MrKlean on 2007-12-22
Also...for XP.. there is a free 2 pane manager called Xplorer2.. I think..been so long since I used XP LOL!   I really love my Ubuntu !!!!!!    LOL!!

---

### Post by alx010 on 2007-12-22
> **hyper_ch said:**
> you can just install konqueror... no need to uninstall nautilus or Gnome.....

Once installed, right-click the bottom bar and select "split horizontally" or "split vertically" --> you can then independentaly browse with those two (or even more) windows and copy/move among them.

Thanks, I'll give that a try. It's just that I'm so used to the right click method for individual files. (sorting photos for example) The only time I use drag & drop is if I'm moving an entire directory.

---

### Post by hyper_ch on 2007-12-22
I used Windows (and later it was renamed to Total) Commander in windows ;)

---

### Post by Biggy on 2007-12-22
in Home folder selsect View-Show Hidden Files and open gnome2 folder,open nautilus-scripts folder and put this scripts : download from attachments 2 scripts.(before extract file from tar.gz)

---

### Post by alx010 on 2007-12-22
> **Biggy said:**
> in Home folder selsect View-Show Hidden Files and open gnome2 folder,open nautilus-scripts folder and put this scripts : download from attachments 2 scripts.(before extract file from tar.gz)

 :) Thank you VERY much! The Move to script is exactly what I was looking for :guitar:

Now if I can get either Photofiltre or Irfanview to work with Wine, I can say goodbye to Window! :KS

---

### Post by alx010 on 2007-12-22
BTW, I'm sure I'm not the only ex-Windows user who has encountered this frustration. if these scripts can be stickied somewhere, they would probably help quite a few folks who are making the transition. 
Again, thanks to all who chimed in!:-)

---

### Post by t0p on 2007-12-22
When I want to move files in the GUI, I sometimes click n drag, sometimes cut n paste.  Or even copy n paste.

But mostly I do it in CLI.  mv and cp are great.

---

### Post by hyper_ch on 2007-12-23
> **alx010 said:**
>  if these scripts can be stickied somewhere, they would probably help quite a few folks who are making the transition.

That wouldn't help.... most people don't read the sticky thread and even less use the forum's search function.

---

### Post by MrKlean on 2007-12-23
Why install scripts when the function is already there ?? Just curious ; )

---

