---
title: "A Couple of Easy Questions"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Wudugast on 2007-05-20
After struggling with my external hard drives for hours, I can finally mount/unmount them, read/write/delete files, and have even formatted one to ext3. Thanks again!

Q1: Now, I'm having problems with programs I install disappearing. I installed ZSNES, 7zip, unrar, Visual Boy Advance, and others, but they do not show up in the applications menu, and I am too unfamiliar with the Ubuntu file tree to know where to find them. I have heard that I can install something called Debian that will display all of my programs, but when I search for it in the Synaptic Package Manager, I get hundreds of results, none of which clearly say "Debian." Plenty of them are Debian related, but I just don't know which one to choose.

Can someone tell me what I should look for as far as Debian goes, or maybe where to find installed programs in the folder hierarchy?

Q2: Also, I've tried to install tar.gz files plenty of times with no luck. My main concern is installing the extended preferences plugin for the pidgin messenger. I have read other posts on the subject and ended up here - [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but found the instructions to be somewhat unclear and confusing. I have been able to install a few tar.gz files using a program called kconfigure with the gksudo command, but it doesn't work for everything. What can I do?

That's it. Thanks!

---

### Post by Moop on 2007-05-20
The easiest way to find the programs you installed and add them to the menu is to right click on Applications and choose "edit menus". From there you will see you can check the box to add applications to the start menu.

---

### Post by Wudugast on 2007-05-20
I just tried doing this, and the programs I want aren't in the list.

---

### Post by Churnd on 2007-05-20
> **Wudugast said:**
> I just tried doing this, and the programs I want aren't in the list.

You can make your own using the same method.  By the way, that menu editor is called Alacarte.

Can you launch the program from the terminal?  The command to do that is the same one you need to enter into the menu item.  After that, it's just a matter of finding the icons...  they're usually in /usr/share/pixmaps or wherever the program installed by default.  If you don't know, try:

```
sudo updatedb
```
then
```
locate <program>
```

---

### Post by Wudugast on 2007-05-20
I'm not sure if I can launch the program from the terminal because other than the name of the program, I don't know what the executable file is called. At any rate, updating the database didn't work, either.

This is what I get when I updatedb and tell it to find 7zip

/var/cache/apt/archives/p7zip-full_4.43~dfsg.1-1_i386.deb
/var/cache/apt/archives/p7zip_4.43~dfsg.1-1_i386.deb
/var/lib/dpkg/info/p7zip-full.md5sums
/var/lib/dpkg/info/p7zip.list
/var/lib/dpkg/info/p7zip-full.list
/var/lib/dpkg/info/p7zip.md5sums
/usr/share/app-install/desktop/7zip.desktop
/usr/share/p7zip
/usr/share/doc/p7zip
/usr/share/doc/p7zip/TODO
/usr/share/doc/p7zip/ChangeLog.gz
/usr/share/doc/p7zip/README.gz
/usr/share/doc/p7zip/README.Debian
/usr/share/doc/p7zip/DOCS
/usr/share/doc/p7zip/DOCS/7zC.txt.gz
/usr/share/doc/p7zip/DOCS/history.txt.gz
/usr/share/doc/p7zip/DOCS/MANUAL
/usr/share/doc/p7zip/DOCS/MANUAL/switches
/usr/share/doc/p7zip/DOCS/MANUAL/switches/stop_switch.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/method.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/exclude.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/large_pages.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/list_tech.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/recurse.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/stdout.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/output_dir.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/style.css
/usr/share/doc/p7zip/DOCS/MANUAL/switches/volume.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/ar_exclude.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/charset.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/index.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/ar_no.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/email.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/update.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/sfx.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/yes.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/overwrite.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/type.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/include.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/stdin.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/working_dir.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/ar_include.htm
/usr/share/doc/p7zip/DOCS/MANUAL/switches/password.htm
/usr/share/doc/p7zip/DOCS/MANUAL/style.css
/usr/share/doc/p7zip/DOCS/MANUAL/syntax.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands
/usr/share/doc/p7zip/DOCS/MANUAL/commands/delete.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/extract_full.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/style.css
/usr/share/doc/p7zip/DOCS/MANUAL/commands/add.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/index.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/update.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/list.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/extract.htm
/usr/share/doc/p7zip/DOCS/MANUAL/commands/test.htm
/usr/share/doc/p7zip/DOCS/MANUAL/index.htm
/usr/share/doc/p7zip/DOCS/MANUAL/exit_codes.htm
/usr/share/doc/p7zip/DOCS/7zFormat.txt.gz
/usr/share/doc/p7zip/DOCS/lzma.txt.gz
/usr/share/doc/p7zip/DOCS/readme.txt.gz
/usr/share/doc/p7zip/DOCS/Methods.txt
/usr/share/doc/p7zip/changelog.Debian.gz
/usr/share/doc/p7zip/copyright
/usr/share/doc/p7zip/changelog.gz
/usr/share/doc/p7zip-full
/usr/share/doc/p7zip-full/TODO
/usr/share/doc/p7zip-full/ChangeLog.gz
/usr/share/doc/p7zip-full/README.gz
/usr/share/doc/p7zip-full/DOCS
/usr/share/doc/p7zip-full/DOCS/7zC.txt.gz
/usr/share/doc/p7zip-full/DOCS/history.txt.gz
/usr/share/doc/p7zip-full/DOCS/MANUAL
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stop_switch.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/method.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/exclude.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/large_pages.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/list_tech.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/recurse.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdout.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/output_dir.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/style.css
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/volume.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_exclude.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/charset.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/index.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_no.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/email.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/update.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/sfx.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/yes.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/overwrite.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/type.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/include.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdin.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/working_dir.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_include.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/password.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/style.css
/usr/share/doc/p7zip-full/DOCS/MANUAL/syntax.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/delete.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract_full.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/style.css
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/add.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/index.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/update.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/list.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/commands/test.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm
/usr/share/doc/p7zip-full/DOCS/MANUAL/exit_codes.htm
/usr/share/doc/p7zip-full/DOCS/7zFormat.txt.gz
/usr/share/doc/p7zip-full/DOCS/lzma.txt.gz
/usr/share/doc/p7zip-full/DOCS/readme.txt.gz
/usr/share/doc/p7zip-full/DOCS/Methods.txt
/usr/share/doc/p7zip-full/changelog.Debian.gz
/usr/share/doc/p7zip-full/copyright
/usr/share/doc/p7zip-full/changelog.gz
/usr/share/man/man1/p7zip.1.gz
/usr/bin/p7zip
/usr/lib/p7zip
/usr/lib/p7zip/Formats
/usr/lib/p7zip/Formats/z.so
/usr/lib/p7zip/Formats/Tar.so
/usr/lib/p7zip/Formats/split.so
/usr/lib/p7zip/Formats/Zip.so
/usr/lib/p7zip/Formats/Rar.so
/usr/lib/p7zip/Formats/chm.so
/usr/lib/p7zip/Formats/cpio.so
/usr/lib/p7zip/Formats/deb.so
/usr/lib/p7zip/Formats/cab.so
/usr/lib/p7zip/Formats/arj.so
/usr/lib/p7zip/Formats/nsis.so
/usr/lib/p7zip/Formats/bz2.so
/usr/lib/p7zip/Formats/lzh.so
/usr/lib/p7zip/Formats/iso.so
/usr/lib/p7zip/Formats/rpm.so
/usr/lib/p7zip/Formats/7z.so
/usr/lib/p7zip/Formats/gz.so
/usr/lib/p7zip/7z
/usr/lib/p7zip/Codecs
/usr/lib/p7zip/Codecs/7zAES.so
/usr/lib/p7zip/Codecs/Deflate.so
/usr/lib/p7zip/Codecs/AES.so
/usr/lib/p7zip/Codecs/Implode.so
/usr/lib/p7zip/Codecs/Branch.so
/usr/lib/p7zip/Codecs/BZip2.so
/usr/lib/p7zip/Codecs/LZMA.so
/usr/lib/p7zip/Codecs/Swap.so
/usr/lib/p7zip/Codecs/Copy.so
/usr/lib/p7zip/Codecs/PPMD.so

I don't know how to make sense of it all. Where's the executable file? Do all those .gz files mean I need to compile it all again?

---

### Post by tippit78 on 2007-05-20
Just install the package called 'menu', and then make sure you've check marked the Debian menu in the gnome menu. Whenever you add files, just open a terminal and type 'update-menus'.

/usr/bin/p7zip

The stuff in /usr/bin/ are the names of the commands for programs. So, you can also type 'p7zip' into the terminal to start it. And you can manually add the program to your gnome menu.

---

### Post by Wudugast on 2007-05-21
Okay. I've installed menu, but when I go to edit menus and try to enable Debian, the check mark never stays in its box. It disappears after I close the edit menus window and check it again.

---

### Post by tippit78 on 2007-05-21
Yeah, alacarte can be kind of...funky.

Try editing the menus, check on the Debian menu, and then close the menu editor. Log out. Come back on and check to see if it's enabled.

Also: Is there a folder hierarchy inside the Debian menu when you look at it in the menu editor? If yes, you can just look for the program you need and drag it to where ever you want. If you don't see anything, then I'm not sure what the problem is.

Worse come to worse, just create a new launcher in the appropriate area. It'd be lame to do it by hand every time you have a new program, but it'll get you buy until you can figure out the problem.

---

### Post by Campingman on 2007-05-21
For znes just open the  terminal and type zsnes it does not install a frontend application as standard. If you want an emulator with a frontend there is snes9x and the frontend application is called snes9express, this will place a menu item under games.
Zsnes is much better though IMHO, you can always create a menu entry for it in system>preferences>main menu and add an item with the command zsnes

---

