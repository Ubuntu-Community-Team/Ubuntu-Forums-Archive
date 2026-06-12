---
title: "Change document type"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by The Hedgehog on 2005-11-21
When I want to open certain files (eg. a video file) I sometimes get the following warning "Can open the file, the extension says that this is a video file. The content, on the other hand,says it's plain text. If you open it security risk. Don open the file unless you trust it."

I can still open it by rightclicking. But I would like to know if, and how, I can change the "type".

---

### Post by tedddee on 2005-11-23
bump, also interested in a solution to this rather annoying problem.

ive used the properties / open with, still get the error

---

### Post by jfryman on 2005-11-23
[QUOTE=The Hedgehog]When I want to open certain files (eg. a video file) I sometimes get the following warning "Can open the file, the extension says that this is a video file. The content, on the other hand,says it's plain text. If you open it security risk. Don open the file unless you trust it."

I can still open it by rightclicking. But I would like to know if, and how, I can change the "type".[/QUOTE]

If you are using Nautilus, you can easily change the mime-type assigned to a file. For example: if you have a MPEG file with an .mpg extension, and you have a media player (mplayer/xine), simply right-click on the file and select Properties.

You should get a dialog with information on the file. In addition, there should be a series of tabs. Click on the 'Open With' tab. If your media player application is not listed, click 'Add'

If your application is already listed in the Gnome-Panel, just select it. Otherwise you can type in the full path to the program (usually /usr/bin/xine or /usr/bin/mplayer)

Then, make sure that the ratio-button is on your new program. Click 'OK'. You should be able to double-click on the file to have the associated program open. This can be done for any file/mime type.

Hope that helps!

-James

---

