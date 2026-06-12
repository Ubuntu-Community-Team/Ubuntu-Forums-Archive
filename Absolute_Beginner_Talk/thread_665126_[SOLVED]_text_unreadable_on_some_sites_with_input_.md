---
title: "[SOLVED] text unreadable on some sites with input boxes, digital black theme"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2008-01-11
i am having a problem with the input boxes of some sites. when i type an entry into them, the text doesnt show because the text is the same color as the background and thus cannot see it. i am using the digitaldark-3- blue theme  that came out and i would like to tweak the configuration files in the tar gz file where the input box color background is white and the text is black. i have disabled the use system colors option in the browser preferences and allowed the pages to determine the text, etc and its to no avail. i hope this screenshot helps:

note: in the entry boxes in this example, i have my info typed in it but cant read it but the boxes are all black with no text.

---

### Post by nikoPSK on 2008-01-11
> **thebestofall007 said:**
> i am having a problem with the input boxes of some sites. when i type an entry into them, the text doesnt show because the text is the same color as the background and thus cannot see it. i am using the digitaldark-3- blue theme  that came out and i would like to tweak the configuration files in the tar gz file where the input box color background is white and the text is black. i have disabled the use system colors option in the browser preferences and allowed the pages to determine the text, etc and its to no avail. i hope this screenshot helps:

note: in the entry boxes in this example, i have my info typed in it but cant read it but the boxes are all black with no text.

I am sure you can edit the theme file to change that. :)

---

### Post by thebestofall007 on 2008-01-12
> **nikoPSK said:**
> I am sure you can edit the theme file to change that. :)
after extracting the main folder from the tar, there are three folders inside the main folder: metacity, gtk+ and DigitalDark-3-Blue. which folder do i do my changing, and what part of the script(s) do i modify?

---

### Post by nikoPSK on 2008-01-12
I am not very good at customization but I am sure someone will come along. :)

---

### Post by thebestofall007 on 2008-01-14
i found the solution: in the home folder, hit CTRL H to reveal the hidden files. go to .themes, and in the .themes folder find the DigitalDark-3-1.3 theme. click on it and go to the gtk-2.0 folder. in the gtk-2.0 folder click on the gtkrc folder and change the base background color number from #000000 (black) to #525252 (a shade of grey) or whatever color number you prefer. i used the color number in the panel properties color menu as a reference. 

the number i have highlighted in the screenshot is where i did my changing.

another screenshot shows what the result looks like.

---

### Post by nikoPSK on 2008-01-14
> **thebestofall007 said:**
> i found the solution: in the home folder, hit CTRL H to reveal the hidden files. go to .themes, and in the .themes folder find the DigitalDark-3-1.3 theme. click on it and go to the gtk-2.0 folder. in the gtk-2.0 folder click on the gtkrc folder and change the base background color number from #000000 (black) to #525252 (a shade of grey) or whatever color number you prefer. i used the color number in the panel properties color menu as a reference. 

the number i have highlighted in the screenshot is where i did my changing.

another screenshot shows what the result looks like.

Nice! please mark this thread as "SOLVED".

Best,
nikoPSK

---

