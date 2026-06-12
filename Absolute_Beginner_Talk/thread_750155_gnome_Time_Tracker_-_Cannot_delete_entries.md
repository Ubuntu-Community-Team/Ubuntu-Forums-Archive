---
title: "gnome Time Tracker - Cannot delete entries?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by WinterWeaver on 2008-04-09
Hi There,

I've started using gnome Time Tracker for a lightweight app for organizing tasks and small projects.

I have one issue with it though, and I'm hoping someone can help me.

Is there any way to delete a Task/Project after I added one? Even Sub-Projects I'm unable to delete.

Thanks for any advice :)

WW

---

### Post by HanZo on 2008-04-23
have been trying to find that out too... but unfortunately... nobody seems to know how. and I start to believe, there just isn't a way...not shure one should submit this as a bug on the project's sourceforge page, just to point out this is an issue.
On the other hand, this is still version 2.2.3, while the latest version is 2.3.0, so it might have been fixed already.

---

### Post by edsonmedina on 2008-05-14
I also have that problem. The only way I found to delete entries is removing them from the xml file (.gnome2/gnotime.d/gnotime-data.xml)

---

### Post by meonkeys on 2008-05-14
The cut button works to delete a project, as well as using "Edit->Cut" or simply pressing CTRL-X when the project to be deleted is selected.

If you can't (but want to) see the Cut button on the main window toolbar, you can enable it in "Settings -> Preferences -> Toolbar -> Show `Cut', `Copy', `Paste'".

Here's an [issue filed at the gnotime project on sourceforge to fix the right-click menu]("http://sourceforge.net/tracker/index.php?func=detail&aid=1949930&group_id=55463&atid=477103").

---

