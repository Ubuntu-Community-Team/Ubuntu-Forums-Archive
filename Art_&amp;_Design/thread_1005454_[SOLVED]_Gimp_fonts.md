---
title: "[SOLVED] Gimp fonts"
date: 2008-12-08
forum: Art &amp; Design
---

### Post by Ghliofris on 2008-12-08
I have Gimp 2.6.1 on Ubuntu 8.10. I can not change the size of the fonts. The only thing that comes up is the where you type the text in. It will not give me a font dialog box to change the size, style, or anything for fonts. I go to Tools, Text and the text box shows up, same with hitting the "t" key.

Anyone have any ideas or has had this problem? I have 4 images to change for a web site and I am stuck.

---

### Post by unutbu on 2008-12-08
When you start up GIMP there should be 3 windows that appear: The image window, the tool box window and the layer window.
In the tool box window, the lower half shows tool options.
When you press 't' or click the text tool, the lower half of the tool box window has controls for changing the font and the font size.

---

### Post by Ghliofris on 2008-12-08
> **unutbu said:**
> When you start up GIMP there should be 3 windows that appear: The image window, the tool box window and the layer window.
In the tool box window, the lower half shows tool options.
When you press 't' or click the text tool, the lower half of the tool box window has controls for changing the font and the font size.

The only thing it says in the bottom window is "You drop dockable dialogs here" Nothing else shows up in it.

---

### Post by unutbu on 2008-12-08
Please post a screenshot.

---

### Post by eightmillion on 2008-12-08
You need to go to Windows-->Dockable Dialogs and click on Tool Options.

---

### Post by Ghliofris on 2008-12-08
Here is the screenshot

[ATTACH]95670[/ATTACH]

After I click on the text or toll text. then selcect where I want the text to go, this is what pops up:

[ATTACH]95672[/ATTACH]

---

### Post by eightmillion on 2008-12-08
I should add that you can grab it at the top and drop it in the area that says "You can drop dockable dialogs here."

---

### Post by Ghliofris on 2008-12-08
> **eightmillion said:**
> I should add that you can grab it at the top and drop it in the area that says "You can drop dockable dialogs here."

Tried that, didnt work:confused:

---

### Post by eightmillion on 2008-12-08
> **Ghliofris said:**
> Tried that, didnt work:confused:

Check out this screenshot, because it's not very clear where you need to click and drag.

---

### Post by Ghliofris on 2008-12-08
> **eightmillion said:**
> Check out this screenshot, because it's not very clear where you need to click and drag.

That tool box does't come up.

---

### Post by eightmillion on 2008-12-08
> **Ghliofris said:**
> That tool box does't come up.

You can always remove the folder ~/.gimp-2.6/ 

Then restart gimp and it will be restored to defaults with the tool options on the toolbox dock.

---

### Post by Ghliofris on 2008-12-08
> **eightmillion said:**
> You can always remove the folder ~/.gimp-2.6/ 

Then restart gimp and it will be restored to defaults with the tool options on the toolbox dock.

I did a complete remove of all Gimp. Then I did a reinstall. Didn't work :confused:

I then removed the directory you suggested.

It worked. Thanks!!):P

---

### Post by lodp on 2013-03-12
> **eightmillion said:**
> Check out this screenshot, because it's not very clear where you need to click and drag.

Thanks, I just googled in here after accidentally closing the tool options. You *know* something's wrong with the interface if there are youtube videos failing to explain how to work it :)

---

### Post by overdrank on 2013-03-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

