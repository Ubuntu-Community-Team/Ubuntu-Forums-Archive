---
title: "comix viewer question"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by freakzilla on 2005-12-11
I'd like to set .cbr and .cbz files to automatically open with comix but all other .rar archives to open with archive manager.  Does anyone know how to make this happen?  Right clicking on a file and changing "open with" for my comic book files (.cbr) changes the setting for all all .rar archives including .zip .ace etc...:confused:

---

### Post by freakzilla on 2005-12-19
Well, I guess i'll just stick with right clicking the comic book files (.cbr) and choosing "open with".  Not really a big deal but something I thought I could avoid.  Otherwise Comix is working really well.

---

### Post by Wolki on 2005-12-19
Hm, it should be possible, but not easily. Since cbz/cbr archives are just normal zip/rar files, it'll just assume these are mislabled normal archives. Usually that's quite nice - for example, when a jpg file is mislabled as txt or even without extension, it will display it properly. In this case, it's unwanted behavior. :-/

You'll probably have to set a new MIME type for comic archives. Maybe there's a GUI for it somewhere, i doubt it though. Problem is, the documentation for this hasn't been updated since Gnome 2.6. &#172;_&#172; You can find that here:  [http://www.gnome.org/learn/admin-guide/2.6/ch05.html](http://www.gnome.org/learn/admin-guide/2.6/ch05.html) I found some more current info, but this is for FreeBSD, not Linux, so I'm not sure everything applies. [http://www.freebsd.org/gnome/docs/faq2.html#q22](http://www.freebsd.org/gnome/docs/faq2.html#q22) Here's the freedesktop.org tutorial: [http://freedesktop.org/wiki/Standards_2fAddingMIMETutor](http://freedesktop.org/wiki/Standards_2fAddingMIMETutor) (with a link to a ROX Desktop gui app that can do it for you, but may be a bit difficult to install as ubuntu's ROX support beyond the filer currently isn't that great)

Sorry that it has to be this difficult, I don't know an easier way.

---

### Post by freakzilla on 2005-12-19
Thanks for all the information.  
It seems a little beyond my knowlegde level at this point:-k .

---

### Post by Wolki on 2005-12-20
[QUOTE=freakzilla]Thanks for all the information.  
It seems a little beyond my knowlegde level at this point:-k .[/QUOTE]

Ah well, my fault, I was looking for information instead of just trying it out ~_~ Sorry. It's really not difficult, I just did it and will walk you through it now.

1) open ~/.local/share/mime/packages/Override.xml, create it if you don't have it yet. For example, do ```
 gedit ~/.local/share/mime/packages/Override.xml 
```

2) I already had this file with two entries, I think gnome created them for me. It might have for you too, so make a backup copy. Replace the contents of the file with this:
```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="application/x-cbr">
    <comment>Archived Comic Book File</comment>
    <glob pattern="*.cbr" />
	</mime-type>
	<mime-type type="application/x-cbz">
    <comment>Archived Comic Book File</comment>
    <glob pattern="*.cbz" />
  </mime-type>
</mime-info>

```
If you already have entries in that file and a little html/xml knowledge, you should be able to figure out how to merge the documents, if not you'll have to post your old file and I'll do it for you.

3) Run the following command: ```
update-mime-database ~/.local/share/mime/

```

4) Now it should work for your user. It should also be possible to do this for all users, but I'm too lazy to find out how right now. ^^;;

5) right-click the file (one each for cbz and cbr), Open with, choose comix. :)

Still to do (once I find the time):
- find out how to set a proper icon for cbz/cbr files
- see if other cool stuff is possible :)

HTH, ask if you encounter any problems.

W.

---

### Post by freakzilla on 2005-12-20
Brilliant.  Thanks for the help.  I'm one happy ubuntu user.\\:D/

---

### Post by Wolki on 2005-12-21
I found out how to do something cool. :)

I'm still waiting for permission from the original author, once I have that I'll write a How-To. But here's a little preview...

---

