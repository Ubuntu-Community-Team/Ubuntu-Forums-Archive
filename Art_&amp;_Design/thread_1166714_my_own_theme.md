---
title: "my own theme?"
date: 2009-05-22
forum: Art &amp; Design
---

### Post by medicalystoned on 2009-05-22
I would like to really costumize my machines with my own theme. Problem is, I don't know how. Any help or direction would be SWEET....

Thanks for taking the time to help.....

---

### Post by VCoolio on 2009-05-22
It's best to start with an existing theme. Pick one you more or less like and start changing. The gtkrc inside the gtk folder of the theme is the main config file for the controls, that is: everything between the window borders. Open it up in a texteditor and you'll see what is happening. (If it starts with 'include' lines it means there are other config files in the same folder for some items, for example the scroll bars.) It starts with a default style and then defines styles with different settings to which gtk widgets and objects are assigned. You can add styles as much as you like. Also you can change the .png files in the other folders. Window borders listen to the metacity folder. 

Biggest problem is to keep contrast: I'm busy with a black-and-white theme, but it is nearly impossible to keep it simple since obviously applications don't stick to the rules, which means for example that I have black text onder my menu icons, but in evolution that is white (and unreadable against a light background) ?!? So apps can call different items for what you think are the same text / button classes. Also firefox doesn't like black themes, which for example means that if you have black buttons the comboboxes in firefox will have black text on black background. You'll have to fix that with user.css files (but I have never succeeded in that, which doesn't mean much btw). 

Well, happy theming! Here is an exausting [link]("http://library.gnome.org/devel/gtk/unstable/index.html") which can be helpful, especially part III. Also have a look in other themes' gtkrc files to get ideas. If there is a problem open a gtk app (like gedit) in a terminal and read the output. I'm sure there are better ways to get going, but this is a start and others may add the 'professional' way of theming.

---

### Post by Argama on 2009-05-22
Metacity themer is a great program to costumize metacity theme's.

---

