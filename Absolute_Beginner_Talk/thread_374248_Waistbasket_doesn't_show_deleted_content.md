---
title: "Waistbasket doesn't show deleted content"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-03-02
My Ubuntu 6.06/ Gnome installations wastebasket doesn't show anything that I send to it. I imagine there is a way of changing this so that items are not automatically deleted.   How is this done please?

---

### Post by NewOldTimer on 2007-03-02
I thought we had this figured out already? did you even look at any of this or is this a new problem? you mentioned it was a digikam photo delete thingy, something I missed?


[http://docs.kde.org/stable/en/extrag...app-setup.html](http://docs.kde.org/stable/en/extrag...app-setup.html) below taken from said page...
Deleting a Photograph

When you delete a photograph from digiKam it will be moved to the KDE Trash Can. If you prefer that Delete really removes the photograph completely, than you can set this option by selecting Settings->Configure digiKam and selecting the Miscellaneous page. At the top of that page are the settings that control what happens when a photograph is deleted

---

### Post by a.v.l on 2007-03-02
> **NewOldTimer said:**
> I thought we had this figured out already? did you even look at any of this or is this a new problem? you mentioned it was a digikam photo delete thingy, something I missed?


[http://docs.kde.org/stable/en/extrag...app-setup.html](http://docs.kde.org/stable/en/extrag...app-setup.html) below taken from said page...
Deleting a Photograph

When you delete a photograph from digiKam it will be moved to the KDE Trash Can. If you prefer that Delete really removes the photograph completely, than you can set this option by selecting Settings->Configure digiKam and selecting the Miscellaneous page. At the top of that page are the settings that control what happens when a photograph is deleted

I am confused by the reference to KDE's Trash Can as I only have Gnome on my system. Does this mean that deleted images in Digikam are simply deleted and not sent to the Gnome wastebin.

---

### Post by compmodder26 on 2007-03-02
When you installed Digikam, it also installed a lot of KDE specific stuff.  One of these was KDE's trash bin system.  So Digikam is deleting to the KDE trash which should reside at ~/.local/share/Trash

edit: assuming that you haven't told Digikam to completely remove the file.

---

### Post by a.v.l on 2007-03-02
> **compmodder26 said:**
> When you installed Digikam, it also installed a lot of KDE specific stuff.  One of these was KDE's trash bin system.  So Digikam is deleting to the KDE trash which should reside at ~/.local/share/Trash

edit: assuming that you haven't told Digikam to completely remove the file.

Thanks for your advice, how do I access  ~/.local/share/Trash please.

---

### Post by compmodder26 on 2007-03-07
go to Places->Home Folder.  The file manager should show up, click View->Show Hidden Files.  Then find .local

---

