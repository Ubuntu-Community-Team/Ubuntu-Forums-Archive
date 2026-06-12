---
title: "Starting out"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by pe1800 on 2007-02-26
Just Ubuntu 6.06 LTS in dual-boot with Windows XP (on separate hard drive).

The installer put icons for my two Windows partitions on the desktop. I like a clean desktop, the partitions are listed with the Places menu, and I would like to remove the icons. Are they SHORTCUTS? I wouldn't want to actually delete my Windows partitions!  If they are are shortcuts, how do I delete them. There's no Delete with a right-hand click context menu and dragging doesn't work either.[/LEFT] 

Firefox is there and it's working but I cannot find it anywhere in the file manager. I would like to find Firefox' bookmark.htm file and  copy my Windows bookmark.htm file to it.

Thank you for your help.
pe :)

---

### Post by ljpm on 2007-02-26
Open the configuration editor (applications/system tools/configuration editor, note: you may need to add this by right clicking on the top bar)

select apps/nautilus/desktop and deselect  volumes visible.

---

### Post by overdrank on 2007-02-26
> **ljpm said:**
> Open the configuration editor (applications/system tools/configuration editor, note: you may need to add this by right clicking on the top bar)

select apps/nautilus/desktop and deselect  volumes visible.

Thanks ljpm  learn something new everyday. :)

---

### Post by pe1800 on 2007-02-26
Thank you. I right-clicked on the top bar and on add-to-panel but I did not see such items as system tools or configuration editor.
:)

---

### Post by Zimmer on 2007-02-26
> 

Firefox is there and it's working but I cannot find it anywhere in the file manager. I would like to find Firefox' bookmark.htm file and  copy my Windows bookmark.htm file to it.

Thank you for your help.
The firefox config folders are in hidden files in your directory.. Use Nautilus and press ctrl+h to reveal folders that are prefixed with a period  (.)  .mozilla etc

or view and click on  'Show hidden files'

---

### Post by johnc4510 on 2007-02-26
pe1800 click on your dropdown menu, go to System Tools, go to Configuration Editor and click on it. Then follow ljpm's instructions

---

### Post by laidback on 2007-02-26
Ref Bookmarks

Suggest you try Firefox's Bookmarks menu>Manage Bookmarks then File>Import, you then get the option to import a file which could I suppose be the exported bookmarks from XP.

The bookmark file is stored within a hidden folder in your home directory called .mozilla/firefox.. then search the folders for bookmarks.html. To view the hidden folders...from within the file browser  View>Show hidden files (or Crtl + H ).

Hope this helps.

---

### Post by Zimmer on 2007-02-26
> **johnc4510 said:**
> pe1800 click on your dropdown menu, go to System Tools, go to Configuration Editor and click on it. Then follow ljpm's instructions
I do not think the configuration editor is there by default, you will need to add it by using Accessories>Alacarte Menu Editor

---

### Post by ljpm on 2007-02-26
My bad,

You will have to add the configuration editor by 

right clicking panel and selecting add to panel
click on the application launcher button
click on system tools
click configuration editor

---

### Post by pe1800 on 2007-02-26
Where's this Nautilus, how do I access it? Why does this Gnome make everything so difficult and obscure?

Thank you again for your help.
pe
:(

---

### Post by johnc4510 on 2007-02-26
Right you are guys, sorry. It's always one of the first things I add, so I just assume it's there for everyone.

---

### Post by johnc4510 on 2007-02-26
Nautilus is your home folder.

---

### Post by ljpm on 2007-02-26
> **pe1800 said:**
> Where's this Nautilus, how do I access it? Why does this Gnome make everything so difficult and obscure?

Thank you again for your help.
pe
:(

Nautilus is like windows explorer. Use the top menu places/home folder or alt F2 and enter nautilus or enter nautilus in terminal.

Linux is not any more difficult and obscure than windows, it is just that you have been using windows and have gotten used to the way they do things.

---

### Post by johnc4510 on 2007-02-26
That's correct, just a different learning curve. You've made a good start, now just read the forums and experiment.

---

### Post by pe1800 on 2007-02-26
> **laidback said:**
> Ref Bookmarks

Suggest you try Firefox's Bookmarks menu>Manage Bookmarks then File>Import, you then get the option to import a file which could I suppose be the exported bookmarks from XP.

The bookmark file is stored within a hidden folder in your home directory called .mozilla/firefox.. then search the folders for bookmarks.html. To view the hidden folders...from within the file browser  View>Show hidden files (or Crtl + H ).

Hope this helps.

Yes, I can now see what CTL+H does. I also imported the bookmarks.

Thank you!
pe
:)

---

### Post by pe1800 on 2007-02-26
> **Zimmer said:**
> I do not think the configuration editor is there by default, you will need to add it by using Accessories>Alacarte Menu Editor

In Accessories, there's no such thing as Alacarte or Sytem Tools or Configuration Editor.

I can see my Windows partitions in computer///. They show on the actual desktop but under desktop in Nautilus.

Thank you for your help.
pe
:confused:

---

### Post by ljpm on 2007-02-26
> **pe1800 said:**
> In Accessories, there's no such thing as Alacarte or Sytem Tools or Configuration Editor.

I can see my Windows partitions in computer///. They show on the actual desktop but under desktop in Nautilus.

Thank you for your help.
pe
:confused:

try this,

right click on the panel and click add to panel
click on custom application launcher
enter Name:               configuration editor 
           Command:       gconf-editor
           Comment:        configuration editor
click ok.

This should put an icon on you panel. Click it and follow previous instructions.

Hope this helps.

---

### Post by pe1800 on 2007-02-26
Yes, I have an icon for Configuration Editor now. Thank you! But where, now, is that Volume Visible switch? I looked all over.

Again, than you.

pe
:confused:

---

### Post by ljpm on 2007-02-26
> **pe1800 said:**
> Yes, I have an icon for Configuration Editor now. Thank you! But where, now, is that Volume Visible switch? I looked all over.

Again, than you.

pe
:confused:

Open configuration editor
select apps/nautilus/desktop and deselect volumes visible.
volume visible is in the right hand box at the bottom.

---

### Post by pe1800 on 2007-02-27
Yes, it worked! Windows partitions are no longer visible on the desktop , I made the trashcan visible and put that icon in the bottom right of the screen, thanks to you guys!

Next. The top was set up with three icons, Firefox, Evolution and Help. Sure, these are what one uses all the time. But now Configuration Editor is there as well, something not often needed. Question, how can I move icons/shortcuts in an out of menus/submenues, along the top bar, etc.?

Thank you again for all your help!

paul eli
:)

---

### Post by laidback on 2007-02-27
Nautilus is just the file browser, click home folder and you're running it. Check out Help>About to see name and version.

The names of programs and files are odd in Linux, but you do get used to it, just treat them as names like ljpm for example.

---

### Post by ljpm on 2007-02-27
> **pe1800 said:**
> Yes, it worked! Windows partitions are no longer visible on the desktop , I made the trashcan visible and put that icon in the bottom right of the screen, thanks to you guys!

Next. The top was set up with three icons, Firefox, Evolution and Help. Sure, these are what one uses all the time. But now Configuration Editor is there as well, something not often needed. Question, how can I move icons/shortcuts in an out of menus/submenues, along the top bar, etc.?

Thank you again for all your help!

paul eli
:)


To remove, just right click and delete (or move to trash)

When you right click the panel and select add to panel you will get a box with two buttons near the top, one adds to your menu one adds icon to panel. 

Also, in the future try to keep you questions to one per post. You will be more likely to get the help you need.

---

### Post by laidback on 2007-03-03
If you just click your file browser you'll be runnuing Nautilu. It's not identified as that in the menus though. In the browser do Help>About.

---

