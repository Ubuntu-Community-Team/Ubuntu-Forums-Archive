---
title: "[SOLVED] Difficult to resize windows"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by bailey86 on 2008-02-03
Simple question.

To resize a window you put the mouse on to one of the corners - I tend to go for the bottom right corner.

On my lovely Dell/ubuntu laptop it hes been upgraded to ubuntu 7.10.  But if I find it really difficult to position the mouse exactly on the corner so that I can resize the window.

Is there any way I can increase the size of the 'grab' corners?

Thanks,

Kevin Bailey

---

### Post by spiderbatdad on 2008-02-03
seems to be a theme dependent issue. You can change aspects of the metacity window themes by editing the .xml file. Have a look at this link if you like.[https://bugs.launchpad.net/ubuntu/+source/human-gtk-theme/+bug/160311](https://bugs.launchpad.net/ubuntu/+source/human-gtk-theme/+bug/160311)

---

### Post by bailey86 on 2008-02-03
Thanks for that.

The link worked fine.

For anyone else here's what I did

Click Applications - Accessories - Terminal

Then type (or cut and paste)

sudo nano /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

and then put in your password.

Change

  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

to 
  <distance name="left_width" value="7"/>
  <distance name="right_width" value="7"/>
  <distance name="bottom_height" value="7"/>

Hold down Ctrl and press 'o' - hit enter to save.

Hold down Ctrl and press 'x' to exit the editor.

Now log out and log back in again.

This just goes to show the power of ubuntu - we can easily get to the underlying configuation files if needed.

BTW - maybe this alteration to the window borders width could be added to the Preferences - Windows dialog box.

BTW - is there any way to apply the changes without loggin out and loggin back in again?

Thanks again for the answer.

Cheers,

Kevin

---

### Post by spiderbatdad on 2008-02-03
please use the thread tools and mark your post as solved.:)  Note: your path specifies the Human theme, so if someone were using a different theme, cutting and pasting that path would not help.

---

