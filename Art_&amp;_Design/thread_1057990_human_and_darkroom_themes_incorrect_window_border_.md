---
title: "human and darkroom themes incorrect window border colors"
date: 2009-02-02
forum: Art &amp; Design
---

### Post by guko1111 on 2009-02-02
Yesterday when changing some themes around (ubuntu 8.10) my human and darkroom themes stopped displaying correctly. The windows borders and progress indicator bars are all now blue for some reason. The human clearlooks theme still works corectly though.
I did a search and a few people had similar problems but their solutions didn't work for me. I tried uninstalling and reinstalling the ubuntu-human theme via synaptic but that didn't change anything. Any ideas?

---

### Post by guko1111 on 2009-02-04
bump

---

### Post by mcduck on 2009-02-05
Select your theme, click the Customize-button, and then on the Colors-tab "Reset to Defaults".

---

### Post by guko1111 on 2009-02-05
That option is greyed out. It already is supposedly at default settings.

---

### Post by mcduck on 2009-02-05
What happens if you change the colors and then click the reset button?

edit: If that doesn't work, try this: press Alt-F2 and run "gconf-editor". Browse to desktop/gnome/interface and find the "gtk_color_scheme"-key. Right-click it and select "Unset Key" from the popup menu.

---

### Post by guko1111 on 2009-02-05
Changed colors and then selected reset no change there. Also used the unset key option in gconf editor and still no change :???:

---

### Post by mcduck on 2009-02-06
that's strange. Have you tried if this problem is only with your own user, or if it's affects the whole system? For example you could use the guest session and change to those themes to see if they work correctly or not..

---

### Post by guko1111 on 2009-02-06
I did try as the themes in a guest session and the same problem persists. It's really odd as I have no idea as to what caused it.

---

### Post by mcduck on 2009-02-06
In that case it can't have anything to do with your own settings, perhaps you should try re-installing gtk2-engines used by those themes (Murrine, at least).

---

### Post by guko1111 on 2009-02-06
This is really odd. I completely removed the murrine engine and then re-installed it a few days ago and still had the problem. Today I marked it for re-installation and now it's working!:confused: but :smile: 

Thanks for the help mcduck.

I don't seem to be getting the option to mark this as solved from the thread tools drop down menu.

---

### Post by afroman10496 on 2009-07-12
i never tried it myself, but go to your Darkroom /usr/share/themes/DarkRoom/gtk-2.0/gtkrc and Human /usr/share/themes/Human/gtk-2.0/gtkrc files and replace everything on it with these 2 things i attached.
Hope it helps. Remember to do it in:

sudo gedit /usr/share/themes/DarkRoom/gtk-2.0/gtkrc
sudo gedit /usr/share/themes/Human/gtk-2.0/gtkrc

---

### Post by afroman10496 on 2009-07-12
attatchments

---

