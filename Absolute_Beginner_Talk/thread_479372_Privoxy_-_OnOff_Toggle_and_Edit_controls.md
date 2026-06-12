---
title: "Privoxy - On/Off Toggle and Edit controls"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by weedwacker on 2007-06-20
Ad Blocker Privoxy on Feisty - using both Firefox and Opera browsers - cannot use Toggle Privoxy On or Off feature nor can I use the Edit feature to change the user.action file.  I can use the View feature to view the Action files.

When I click on the Edit button I get this message: [INDENT] [COLOR="Red"]Privoxy Configuration access denied

The feature you are trying to access has either been disabled by the Privoxy administrator, or you came here by following an unsafe external link.

All enabled features are accessible from the main menu.[/COLOR][/INDENT]

I get a similar message when I try the Toggle Privoxy On or Off feature.

Has anyone been able to get these features activated?  Or is this something that just does not work with Ubuntu?

I have tried changing Permissions of these files, but without any luck.

If anyone can help I would appreciate it.  Thanks.

---

### Post by weedwacker on 2007-06-20
:popcorn:[SIZE="5"]**[COLOR="Blue"]Solved! Got the answer![/COLOR]**[/SIZE]

I found that you have to make a couple of changes to the [COLOR="Red"]**config**[/COLOR] file which is in the [COLOR="Red"]**etc/privoxy**[/COLOR] folder.

I changed in **section 4.5. enable-edit-actions** the setting from 0 to 1and I changed in **section 4.3. enable-remote-toggle** the setting from 0 to 1.  Setting it to 1 enables the feature.

I also bookmarked the Privoxy Bookmarklets (see Section 14.2.1. Bookmarklets in the Privoxy User Manual) and now it is easy to switch from blocked to unblocked pages by using the bookmark located in my Bookmarks Toolbar.

So, if you don't want ads flying all over the pages that you access you should really consider Privoxy.:KS

---

