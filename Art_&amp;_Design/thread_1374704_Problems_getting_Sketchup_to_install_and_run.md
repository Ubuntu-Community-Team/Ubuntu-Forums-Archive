---
title: "Problems getting Sketchup to install and run"
date: 2010-01-07
forum: Art &amp; Design
---

### Post by sofasurfer on 2010-01-07
I found and installed the newest wine...wine ppa. I downloaded Sketchup and installed it. It displayed the splash screen and then disappeared. I then uninstalled it and now when I try to reinstall it again I get an error that says...

[I]/home/backupsys/Desktop/GoogleSketchUpWEN.exe]
End-of-central-directory signature not found. Either this file is not
a zipfile, or it constitutes one disk of a multi-part archive. In the
latter case the central directory and zipfile comment will be found on
the last disk(s) of this archive.
zipinfo: cannot find zipfile directory in one of /home/backupsys/Desktop/GoogleSketchUpWEN.exe or
/home/backupsys/Desktop/GoogleSketchUpWEN.exe.zip, and cannot find /home/backupsys/Desktop/GoogleSketchUpWEN.exe.ZIP, period[/I]

Oh, oh!!! What to do?

---

### Post by sofasurfer on 2010-01-20
Hello? Anyone home?
I sure would appreciate some help with this.

---

### Post by samigina on 2010-01-21
Do you have an Intel Graphics Card? Theres a bug with wine and Sketchup in this graphics.

"For Intel grafic owners: Change registry HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK=1"

That is the solution posted [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18506").

---

### Post by butterfryby on 2010-11-06
Right-click on the .exe file and select "properties" from the drop-down menu. Select the "Open With" tab and select "Wine", then select the "Permissions" tab and beside "Execute:" check the box that says "Allow executing file as program." Close and click the file! Tada!
:guitar:
This problem was experienced on Ubuntu 10.10 64bit with Wine 1.2

---

### Post by katmal on 2010-11-21
The link below tells you the complete detail of how to install sketchup.

[http://ronnietucker.co.uk/blog/2010/03/03/how-to-install-google-sketchup-7-with-wine-in-ubuntu/](http://ronnietucker.co.uk/blog/2010/03/03/how-to-install-google-sketchup-7-with-wine-in-ubuntu/)

---

